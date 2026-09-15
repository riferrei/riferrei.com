---
title: "Boosting your Tests with Elasticsearch using TestContainers-Go"
author: "Ricardo Ferreira"
categories:
  - "Elastic"
  - "Go"
date: 2021-09-30
nolastmod: true
draft: false
---
[TestContainers](https://www.testcontainers.org/) is a popular framework that allows Java developers to create tests that depend on backend systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/). It automatically creates a container instance for the said backend, preventing developers from manually spinning up their dependency instances. Also, it enables them to treat those instances as disposable, meaning that once the tests finish executing, the underlying containers created for the instances are destroyed automatically.

The good news for Go developers is that there is a version of this for them as well. It is called [TestContainers-Go](https://golang.testcontainers.org/). In this post, I will walk you through creating a simple test that connects with Elasticsearch using this framework.

#### 1\. Install de TestContainers-Go dependency
```
go get github.com/testcontainers/testcontainers-go
```

#### 2\. Create a test code named elasticsearch_test.go
```
import (
	"testing"
)

func TestWithElasticsearch(t *testing.T) {
  // All the code is shown below comes here...
}
```

#### 3\. Create a container request for Elasticsearch
```
elasticsearchContainerRequest := testcontainers.ContainerRequest{
	Image:        "docker.elastic.co/elasticsearch/elasticsearch:7.15.0",
	Name:         "elasticsearch",
	ExposedPorts: []string{"9200/tcp"},
	Env: map[string]string{
		"node.name":             "single-node",
		"bootstrap.memory_lock": "true",
		"cluster.name":          "testcontainers-go",
		"discovery.type":        "single-node",
		"ES_JAVA_OPTS":          "-Xms1g -Xmx1g",
	},
	WaitingFor: wait.ForLog("Cluster health status changed from [YELLOW] to [GREEN]"),
}
```

Note that we provided a way for the code to wait until the container is ready for business. This is important to ensure that your code won't start issuing requests to the container if it is not ready. The TestContainers-Go project provides [different ways](https://github.com/testcontainers/testcontainers-go/tree/master/wait) for you to check this. In this example, we used the wait.ForLog() function that monitors when the container log outputs the string provided as a parameter.

#### 4\. Create the actual container and start it
```
elasticsearchContainer, err := testcontainers.GenericContainer(ctx, testcontainers.GenericContainerRequest{
	ContainerRequest: elasticsearchContainerRequest,
	Started:          true,
})
if err != nil {
	t.Errorf("Error creating the container: %s", err)
}
defer elasticsearchContainer.Terminate(ctx)
```

Note that we set the parameter Started to true to ensure that we want the container to be started automatically. Alternatively, you can set this to false and start the container programmatically. It may come in handy if you, for example, want to have fine control over when the container is effectively started.

#### 5\. Execute a request against Elasticsearch
```
endpoint, err := elasticsearchContainer.Endpoint(ctx, "")
if err != nil {
	t.Errorf("Error getting the Elasticsearch endpoint: %s", err)
}

response, err := http.Get(fmt.Sprintf("http://%s", endpoint))
if err != nil {
	t.Errorf("Error invoking the Elasticsearch endpoint: %s", err)
}
```

#### 6\. Use the response to verify correctness
```
type responseMock struct {
	ClusterName string `json:"cluster_name"`
}

body, err := ioutil.ReadAll(response.Body)
if err != nil {
	t.Errorf("Error deserialiizing the body: %s", err)
}

var actualResponse responseMock
json.Unmarshal(body, &actualResponse)

expectedResponse := responseMock{
	ClusterName: "testcontainers-go",
}

if actualResponse.ClusterName != expectedResponse.ClusterName {
	t.Errorf("Test failed. Cluster name was '%s' instead of '%s'",
		actualResponse.ClusterName, expectedResponse.ClusterName)
}

t.Log(string(body))
```

#### 7\. Finally, run the test in the terminal
```
go test -v
```

You should see an output similar to this:
```
=== RUN   TestWithElasticsearch
2021/09/30 13:48:12 Starting container id: 5845f4655900 image: quay.io/testcontainers/ryuk:0.2.3
2021/09/30 13:48:12 Waiting for container id 5845f4655900 image: quay.io/testcontainers/ryuk:0.2.3
2021/09/30 13:48:13 Container is ready id: 5845f4655900 image: quay.io/testcontainers/ryuk:0.2.3
2021/09/30 13:48:13 Starting container id: 01d37e098d0f image: docker.elastic.co/elasticsearch/elasticsearch:7.15.0
2021/09/30 13:48:13 Waiting for container id 01d37e098d0f image: docker.elastic.co/elasticsearch/elasticsearch:7.15.0
2021/09/30 13:48:25 Container is ready id: 01d37e098d0f image: docker.elastic.co/elasticsearch/elasticsearch:7.15.0
    elasticsearch_test.go:55: {
          "name" : "single-node",
          "cluster_name" : "testcontainers-go",
          "cluster_uuid" : "MjmXMAV6QhyBB-fP_JrRZg",
          "version" : {
            "number" : "7.15.0",
            "build_flavor" : "default",
            "build_type" : "docker",
            "build_hash" : "79d65f6e357953a5b3cbcc5e2c7c21073d89aa29",
            "build_date" : "2021-09-16T03:05:29.143308416Z",
            "build_snapshot" : false,
            "lucene_version" : "8.9.0",
            "minimum_wire_compatibility_version" : "6.8.0",
            "minimum_index_compatibility_version" : "6.0.0-beta1"
          },
          "tagline" : "You Know, for Search"
        }

--- PASS: TestWithElasticsearch (13.19s)
PASS
ok      testcontainers-go-elasticsearch 13.506s
```

Alternatively, you can (actually, should) use the [official client for Go](https://github.com/elastic/go-elasticsearch) to interact with Elasticsearch without having to handle low-level HTTP requests:
```
newClient, err := elasticsearch.NewClient(elasticsearch.Config{
	Addresses: []string{
		fmt.Sprintf("http://%s", endpoint),
	},
})
if err != nil {
	panic(err)
}
```

Once the test finishes executing, you will notice that all containers started for this test will be destroyed automatically 😎
