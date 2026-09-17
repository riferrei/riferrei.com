---
title: "Apache Kafka without Zookeeper: What Changes in my Apps?"
conference:
  name: "Kafka Summit London"
  url: "https://www.kafka-summit.org/"
  city: "London"
  country: "United Kingdom"
  country_code: "gb"
  latitude: 51.5074
  longitude: -0.1278
  date: 2020-04-27
authors:
  - author: "Ricardo Ferreira"
date: 2020-04-27
talk-lang: en
nolastmod: true
draft: false
---

Apache Kafka has historically relied on ZooKeeper for metadata management, but that dependency is being removed in favor of a self-managed quorum. This session explains what the removal of ZooKeeper means in practice, how the new architecture handles metadata and controller responsibilities, and what developers and operators should expect to change in the way they build and run their Kafka-based applications.

<!--more-->
