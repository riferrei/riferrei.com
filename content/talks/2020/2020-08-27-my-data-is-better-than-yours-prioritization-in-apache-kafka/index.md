---
title: "My Data is Better than Yours! Prioritization in Apache Kafka"
conference:
  name: "The Developers Conference"
  url: "https://thedevconf.com/tdc/2020/"
  city: "Virtual"
  country: ""
  country_code: ""
  date: 2020-08-27
authors:
  - author: "Ricardo Ferreira"
date: 2020-08-27
talk-lang: en
nolastmod: true
draft: false
---

Apache Kafka is built around an immutable commit log rather than a traditional message broker, so it has no native concept of message priority the way JMS or AMQP does. This session presents the bucket priority pattern, which groups messages into buckets of partitions at production time and allocates more partitions and consumers to higher-priority buckets, using Kafka's pluggable custom partitioners and assignors to give important messages a greater chance of being processed first and faster.

<!--more-->
