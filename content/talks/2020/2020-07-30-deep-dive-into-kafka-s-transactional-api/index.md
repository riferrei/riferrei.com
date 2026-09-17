---
title: "Deep Dive into Kafka's Transactional API"
conference:
  name: "SouJava Meetup"
  url: "https://soujava.org.br/"
  city: "Virtual"
  country: ""
  country_code: ""
  date: 2020-07-30
authors:
  - author: "Ricardo Ferreira"
date: 2020-07-30
talk-lang: en
nolastmod: true
draft: false
---

Exactly-once semantics in Apache Kafka rely on the often misunderstood Transactional API. This deep dive explains how transactions, idempotent producers, and the read-committed isolation level work together under the hood, and shows Java developers how to build end-to-end pipelines that neither lose nor duplicate messages, even in the presence of failures and retries.

<!--more-->
