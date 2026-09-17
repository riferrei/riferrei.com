---
title: "The Right Number of Partitions for a Kafka Topic"
conference:
  name: "Devnexus 2023"
  url: "https://devnexus.com/"
  city: "Atlanta"
  country: "United States"
  country_code: "us"
  latitude: 33.749
  longitude: -84.388
  date: 2023-04-05
authors:
  - author: "Ricardo Ferreira"
date: 2023-04-05
talk-lang: en
nolastmod: true
draft: false
---

Every technology has that key concept people struggle with, and for Apache Kafka the winner is how many partitions to set for a topic. Sizing partitions wrongly affects storage, parallelism, durability, and how much load Kafka can handle, and while it is often treated as an infrastructure decision left to Ops teams, it is really an architectural design decision that even affects how much code you write. This session peels off the concept of partitions from the perspective of the cluster and its clients, explains the formula to decide how many partitions a topic should have, and shows how to spot a poor decision when you see one.

<!--more-->
