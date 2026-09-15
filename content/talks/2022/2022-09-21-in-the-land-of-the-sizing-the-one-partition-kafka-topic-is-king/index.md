---
title: "In the land of the sizing, the one-partition Kafka topic is king"
conference:
  name: "Strange Loop 2022"
  city: "St. Louis"
  country: "United States"
  country_code: "us"
  latitude: "38.627003"
  longitude: "-90.199404"
  date: 2022-09-21
authors:
  - author: "Ricardo Ferreira"
date: 2022-09-21
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2022/2022-09-21-in-the-land-of-the-sizing-the-one-partition-kafka-topic-is-king/slides.pdf"
youtube: "fMISi0mJ51g"
---

Every technology has that key concept that people struggle to understand. With databases, is which join clause to use for fetching data from multiple tables. Containers are tricky when you have to pick a storage type given some persistence requirements. With Apache Kafka, the winner is how many partitions to set for a topic.
Why this is important? You may ask. Well, sizing Kafka partitions wrongly affects many aspects of the system, such as consistency, concurrency, and durability. Worse, it may also affect how much load Kafka can handle. Hence why often the decision about how many partitions to set for a topic is handled by Ops teams, as we see this to be only an infrastructure matter. In reality, this is an architectural design decision that affects even the amount of code you write.
This session will peel off the concept of partitions and explain it from the perspective of the Kafka cluster and its clients. By using a what-if presentation style, it will explain the overall impact on the system given a number. This will help you build more confidence about how to size Kafka partitions correctly, and to spot a poor decision when you see one.

<!--more-->
