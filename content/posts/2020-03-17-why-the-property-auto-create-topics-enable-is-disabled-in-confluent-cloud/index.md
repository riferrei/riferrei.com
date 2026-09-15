---
title: "Why the property 'auto.create.topics.enable' is disabled in Confluent Cloud?"
author: "Ricardo Ferreira"
tags:
  - "apache"
  - "cloud"
  - "confluent"
  - "kafka"
  - "Topic"
categories:
  - "Cloud"
  - "Confluent"
date: 2020-03-17
nolastmod: true
draft: false
---
If you ever used Apache Kafka you may know that in the broker configuration file there is a property named **auto.create.topics.enable** that allows topics to be automatically created when producers try to write data into it. That means that if a producer tries to write an record to a topic named customers and that topic doesn't exist yet -- it will be automatically created to allow the writing. Instead of returning an error to the client.

This property in Kafka is enabled by default, which means that if you never heard about this property before then there is a huge chance that you thought that topics are simply created automatically in Kafka. Technically this is true due to the default value of the property aforementioned before, but it doesn't mean that it makes sense to have it. This is particularly important if you are working with Confluent Cloud, where this property has been disabled by default.

I have seen lots of developers complaining about this behavior in Confluent Cloud and I don't necessarily blame them because as mentioned before -- this is the default behavior in Kafka. However, it is important to understand the reasoning why Confluent decided to disable that property in their fully managed service for Apache Kafka. In this post I will try to explain this reasoning and hopefully that will make sense for you.

## **Automatic topic creation: does it make sense?**

Think about this: have you ever worked with any database (SQL or NoSQL) that would allow tables to be automatically created every time a new record is created? I would arguably say that the answer is no at least in my experience. And there are reasons why databases behave like this, being the most important one the fact that each table has its own characteristics.

Just like tables in databases, topics in Kafka also has their own characteristics such as the number of partitions, replication factor, compaction, etc. In Kafka, each topic generates some overhead in the cluster in the form of computing resources consumption increase -- notably more storage since all data in Kafka is persistent and more network bandwidth since topic partitions may need to be replicated within the cluster . That means that every new topic created doesn't come for free and therefore -- you should think twice when creating one.

Now, with that in mind think about all those situations that developers go through during the early stages of the software construction, such as trying to execute some test against Kafka topics to check things like connectivity, consistency, or simply random experimentation that would ultimately lead to topic creation. I am pretty sure that you get the idea about how often this occurs during development, as well as how many topics would be accidentally created with this.

The reality is that each topic should have a purpose in the system that justifies its underlying resources. Having topics being created automatically every time some code tries to write data into it is allowing the system to consume resources irresponsibly.

## **It is all about costs!**

Now let's come back to the main discussion which is why Confluent Cloud doesn't allow topics to be automatically created. As you probably know, Confluent Cloud is a fully managed service that charges you for the usage of the software, in this case Apache Kafka and all the goodies that Confluent provides. The rationale about how Confluent Cloud charges users is mainly based on the following three items:

  1. **Data In** : the price per GB for data written into topics
  2. **Data Out** : the price per GB for data read from topics
  3. **Data Stored** : the price per GB for data retained in topics

Reference: <https://www.confluent.io/confluent-cloud>

As you can see, it is all about data and topics. Which means that as more topics you have more expensive your bill is going to be. Confluent doesn't want to charge you for topics that have been created during a test, or topics that you sometimes don't even know that ended up being created because certain frameworks encapsulate logic that tries to create them on-demand. For this reason, the property auto.create.topics.enable has been disabled by default in Confluent Cloud.

The discussion about costs in cloud is notably one of the most important ones and any provider that offers some service in the cloud needs to take it responsibly. Confluent understand that and wants to ensure that you have been covered. Ultimately, anything that Confluent runs in the cloud runs on top of an infrastructure that is deemed required to maintain the service up-and-running, and that infrastructure cost is part of what Confluent charges you.

## **I want to hear your thoughts!**

Confluent wants to build the best-in-class service for its customers and that means that they are always open to hear feedback. If you have any use case that requires topics to be automatically created by default and therefore -- the property auto.create.topics.enable needs to be set to true please let me know. I can make sure that your thoughts will be heard by the right people within Confluent.
