---
title: "Confluent Go Client with Docker"
author: "Ricardo Ferreira"
tags:
  - "confluent"
  - "docker"
  - "go"
  - "golang"
  - "kafka"
  - "linux"
categories:
  - "Confluent"
date: 2020-02-29
nolastmod: true
draft: false
---
If you are reading this blog post then there is a high chance that you've been looking for ways to make [Confluent's Go Client for Apache Kafka](https://github.com/confluentinc/confluent-kafka-go) work with your Docker images but you're struggling to. Am I right?

![](confluent-gopher-docker-v2.png)

Don't worry, you've came to the right place. After struggling with this myself I decided to share the solution that I've found with everybody else so we all can spend more time writing code than just wasting time with dependency plumbing.

Going straight to the point -- there are two decisions that you need to make for this to work:

  * Which base image to derive from?
  * How to install Golang into your image?

This may sound obvious but the best way to get a Docker image with Go on it is by using [Go's official Docker image](https://hub.docker.com/_/golang). And if you're like me, this might have been your first instinct in the process of building an image for your application.

Try to resist to that instinct. It turns out that in order to have Confluent's Go client you will need to install some extra dependencies -- notably Confluent's implementation of the **librdkafka** library -- and if you derive from the golang base image you won't be able to. Well... at least not easily.

So as your first step, you need to derive from a base image that will allow the installation of the dependencies that ultimately will in turn allow you to get the right librdkafka implementation. In my case I used this one:
```
FROM fedora:latest
```

Then you can now install Confluent's librdkafka:
```
RUN rpm --import https://packages.confluent.io/rpm/5.4/archive.key
COPY confluent.repo /etc/yum.repos.d
RUN dnf install librdkafka-devel -y
```

One of the cool things about this approach is that not only you can now ensure that you're fetching Confluent's librdkafka (instead of any outdated implementation) but also you get to decide which specific version to use.

Now remember when I mentioned the decision about how to install Go into your image?

Since we're not deriving from the golang base image anymore, it is up to you now to get it installed into the image. This is not actually a very hard task since you can use the image's dependency management system (in Fedora's case, [dnf](https://fedoraproject.org/wiki/DNF?rd=Dnf)) for that purpose but the reality is that usually they don't have the exact version of Go you need.

What worked for me was simply to download the latest bits and set it up by myself:
```
RUN wget https://dl.google.com/go/go1.14.linux-amd64.tar.gz && tar -xvf go1.14.linux-amd64.tar.gz && rm go1.14.linux-amd64.tar.gz
RUN mv go /usr/local
ENV GOROOT=/usr/local/go
ENV PATH="${GOROOT}/bin:${PATH}"
```

**That is it** : now you have both Confluent's librdkafka and Go in your Docker image. Bring your code into it, build it, and have fun with your new image.

I have published a [sample application on GitHub](https://github.com/riferrei/confluent-kafka-go-with-docker) that might help you as well.
