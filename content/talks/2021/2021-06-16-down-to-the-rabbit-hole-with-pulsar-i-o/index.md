---
title: "Down to the Rabbit Hole with Pulsar I/O"
conference:
  name: "Pulsar Summit NA 2021"
  url: "https://www.na2021.pulsar-summit.org/"
  city: "Virtual"
  country: ""
  country_code: ""
  date: 2021-06-16
authors:
  - author: "Ricardo Ferreira"
date: 2021-06-16
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2021/2021-06-16-down-to-the-rabbit-hole-with-pulsar-i-o/slides.pdf"
youtube: "60x5eMeBEyI"
---

Apache Pulsar is a distributed messaging and streaming platform that stores messages durably and scalably into its persistent store, making it an attractive technology to store business data. However, merely storing the data is not enough. To make this data useful, the platform must also provide ways to ingest new data and send existing data elsewhere.
While developers can build applications for this using the client libraries, the reality is that most of them don’t want to spend time writing code for repeatable tasks such as — reading data from a database and storing it into Pulsar. Reason why Pulsar abstracts away things like this by providing a connector-based framework called Pulsar I/O.
This talk will provide an overview of how the Pulsar I/O framework works and a deep dive into troubleshooting things — from identifying when the connector is not working correctly to more elaborating investigations that may be useful for debugging purposes. It will give you the required tools to master how to ingest and export data into and out of Pulsar effectively.

<!--more-->
