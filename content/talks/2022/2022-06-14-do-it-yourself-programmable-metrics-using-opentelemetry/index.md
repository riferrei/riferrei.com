---
title: "Do It Yourself: Programmable Metrics using OpenTelemetry"
conference:
  name: "Berlin Buzzwords 2022"
  url: "https://2022.berlinbuzzwords.de/"
  city: "Berlin"
  country: "Germany"
  country_code: "de"
  latitude: "52.520007"
  longitude: "13.404954"
  date: 2022-06-14
authors:
  - author: "Ricardo Ferreira"
date: 2022-06-14
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2022/2022-06-14-do-it-yourself-programmable-metrics-using-opentelemetry/slides.pdf"
youtube: "QfDU4XSWwhU"
---

Using metrics to measure how good or bad things are going is a proven way to ensure a software-based system is going in the right direction. Most metrics are created and monitored automatically by agent technologies installed in our infrastructure, making us hostages of the set of metrics that these agents are programmed to address. But what if you need to handle your own set of metrics?
This is a question that often drives developers mad because they fear spending development cycles building something that will end up being locked into a particular monitoring/observability vendor. But OpenTelemetry — a CNCF observability framework that provides a vendor-neutral approach to tackle metrics, logging, and tracing needs, can change everything.
This talk will explain how the OpenTelemetry framework allows the creation of custom metrics in a standard, scalable, and reusable way. It will provide an example in Java of a set of metrics that are continuously updated based on the execution of the code and how to hook that data with a compatible observability backend.

<!--more-->
