---
title: "Is Using KoP (Kafka-On-Pulsar) a Good Idea?"
conference:
  name: "Pulsar Summit San Francisco 2022"
  city: "San Francisco"
  country: "United States"
  country_code: "us"
  latitude: "37.774930"
  longitude: "-122.419416"
  date: 2022-08-18
authors:
  - author: "Ricardo Ferreira"
date: 2022-08-18
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2022/2022-08-18-is-using-kop-kafka-on-pulsar-a-good-idea/slides.pdf"
youtube: "Rk_5XBciYuk"
---

Building microservices around Apache Kafka is your job, and life is great. One day, you hear community members talking about some neat Apache Pulsar features, and get you intrigued. I mean, we all love Kafka, but you can’t avoid wondering if migrate one of your projects to Pulsar is a good idea. Then it happens. You find Pulsar supports Kafka clients natively via a protocol handler called KoP: Kafka-On-Pulsar.
This gets you pumped. Is that it? Can I go ahead and simply point my microservices to Pulsar and be a hero with this migration? But you must be responsible; and history says you shouldn’t believe migrations like this are refactoring free. Reason you may get interested in this session.
We will revisit the architecture behind protocol handlers to understand what it means having one enabled on Pulsar. Plus, we will discuss the internals of KoP. Finally, we will use a show-and-tell approach to detail the effort to migrate a microservice written for Kafka to Pulsar, and whether the code need to change for this.

<!--more-->
