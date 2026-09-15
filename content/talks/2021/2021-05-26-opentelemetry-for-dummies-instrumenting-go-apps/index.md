---
title: "OpenTelemetry for Dummies: Instrumenting Go Apps"
conference:
  name: "GopherCon Europe"
  city: "Virtual"
  country: ""
  country_code: ""
  date: 2021-05-26
authors:
  - author: "Ricardo Ferreira"
date: 2021-05-26
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2021/2021-05-26-opentelemetry-for-dummies-instrumenting-go-apps/slides.pdf"
youtube: "NLXABIZ1gUQ"
---

Though tracing technologies are not necessarily a new concept only in the recent years it gained enough traction to become one of the key dimensions required to build observability stacks. Undoubtedly the major force behind this traction are the standards created to help developers to collect telemetry data from their applications, such as OpenTelemetry—an observability framework for cloud-native software.
OpenTelemetry provides a single set of APIs, libraries, agents, and collectors that ensures technology agnostic collection of traces and metrics—but the implementation for each programming language is different. While Java has an agent capable of automatically instrumenting the JVM with additional bytecode, other programming languages like Go have to handle this instrumentation manually.
But Go developers have nothing to fear. This talk will explain in a for-the-rest-of-us style how to instrument applications written in Go and how to send the telemetry data to a backend using a collector.

<!--more-->
