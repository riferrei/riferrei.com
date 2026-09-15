---
title: "The Right Number of Partitions for a Kafka Topic"
conference:
  name: "Devnexus 2023"
  city: "Atlanta"
  country: "United States"
  country_code: "us"
  latitude: "33.748995"
  longitude: "-84.387982"
  date: 2023-04-04
authors:
  - author: "Ricardo Ferreira"
date: 2023-04-04
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2023/2023-04-04-the-right-number-of-partitions-for-a-kafka-topic/slides.pdf"
---

Every technology has that key concept that people struggle to understand. With databases, is which join clause to use for fetching data from multiple tables. Containers are tricky when you have to pick a storage type given some persistence requirements. With Apache Kafka, the winner is how many partitions to set for a topic. Why this is important? You may ask. Well, sizing Kafka partitions wrongly affects many aspects of the system, such as storage, parallelism, and durability. Worse, it may also affect how much load Kafka can handle. Hence why often the decision about how many partitions to set for a topic is handled by Ops teams, as we see this to be only an infrastructure matter. In reality, this is an architectural design decision that affects even the amount of code you write. This session will peel off the concept of partitions and explain it from the perspective of the Kafka cluster and its clients. It will explain the formula people should use to decide how many partitions to set for a topic, and how to spot a poor decision when they see one.

<!--more-->
