---
title: "When Kafka is the source of truth; schemas become your source of headaches"
conference:
  name: "Current 2022: The Next Generation of Kafka Summit"
  url: "https://2022.currentevent.io/"
  city: "Austin"
  country: "United States"
  country_code: "us"
  latitude: "30.267153"
  longitude: "-97.743061"
  date: 2022-10-04
authors:
  - author: "Ricardo Ferreira"
date: 2022-10-04
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2022/2022-10-04-when-kafka-is-the-source-of-truth-schemas-become-your-source-of-headac/slides.pdf"
---

One of the coolest things about streaming systems such as Apache Kafka is their ability to handle any type of data. You can store events at Kafka and have different systems processing their event data. You may start with a few systems and add new systems as needed. While certainly possible and attractive, this isn’t simple. Schemas play a key role in how each system consumes the event data and processes them. Reason Schema Registry exists, right? Not really. Schema Registry doesn’t solve any of your data problems. It’s just a registry for your schemas. Admittedly, without it, there would be no policy enforcement. However, data problems can still happen. Issues with encoding, format mismatch between different programming languages, new code not being able to read data written by old code, etc. In this session, we will get into the weeds of data serialization with schemas. We will discuss the differences between formats like JSON, Avro, Thrift, and Protocol Buffers, and how your code must use each one of them to serialize data. It will also clarify the impact of switching Schema Registry with other registries, and whether you can use them together. If you ever wondered why your Python code can’t read something written by Java, why integers are getting confused with strings, or simply how schemas end up in Schema Registry, this session is for you.

<!--more-->
