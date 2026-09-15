---
title: "Hidden Secrets about Instrumenting JVMs for OpenTelemetry"
conference:
  name: "JNation 2021"
  url: "https://2021.jnation.pt/"
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
pdf: "/talks/2021/2021-06-16-hidden-secrets-about-instrumenting-jvms-for-opentelemetry/slides.pdf"
---

OpenTelemetry is the new-kid-on-the-block in API to instrument distributed applications to send telemetry data (logs, metrics, and traces) to backends for visualization and monitoring. It was created to be a de-facto replacement to standards such as OpenTracing and OpenCensus.
The support for Java in OpenTelemetry is generous. It supports both automatic and manual instrumentation. With automatic instrumentation, developers can have known libraries and frameworks instrumented without writing a single code line. Manual support also allows them to decide which parts of the code need instrumentation, and there is a rich set of APIs available to use.
This talk will open the pandora box for both options. It will reveal which knobs are available to use that make a tremendous difference in how the applications report telemetry data — both in terms of performance and details. Knowing these hidden secrets will grant developers fine control over their applications and how observability stacks show them to the world.

<!--more-->
