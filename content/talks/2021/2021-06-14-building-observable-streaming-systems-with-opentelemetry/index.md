---
title: "Building Observable Streaming Systems with OpenTelemetry"
conference:
  name: "Berlin Buzzwords"
  url: "https://2021.berlinbuzzwords.de/"
  city: "Virtual"
  country: ""
  country_code: ""
  date: 2021-06-14
authors:
  - author: "Ricardo Ferreira"
date: 2021-06-14
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2021/2021-06-14-building-observable-streaming-systems-with-opentelemetry/slides.pdf"
youtube: "XpEQTqaawyk"
---

Building streaming systems is a popular way for developers to implement applications that react to data changes and process events as they happen. It is an exciting new world that technologies like Apache Pulsar made available for anyone to use. But all this goodness doesn’t come for free. One of the challenges of this type of architecture is that its distributed nature makes it hard and sometimes even impossible to identify the root cause of problems quickly.
That is why distributed tracing technologies are so important. By gluing together disparate services into a single and cohesive transaction, developers can provide to the operations team a way to pragmatically observe the system and to quickly identify the root cause of problems such as slowness and unavailability. This talk will explain how to implement distributed tracing in Pulsar applications using OpenTelemetry—an observability framework for cloud-native software. A demo will be used to clarify the concepts.

<!--more-->
