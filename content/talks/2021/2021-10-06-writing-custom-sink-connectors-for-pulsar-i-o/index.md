---
title: "Writing Custom Sink Connectors for Pulsar I/O"
conference:
  name: "Pulsar Summit Europe 2021"
  url: "https://pulsar-summit.org/en/event/europe-2021"
  city: "Virtual"
  country: ""
  country_code: ""
  date: 2021-10-06
authors:
  - author: "Ricardo Ferreira"
date: 2021-10-06
talk-lang: en
nolastmod: true
draft: false
pdf: "/talks/2021/2021-10-06-writing-custom-sink-connectors-for-pulsar-i-o/slides.pdf"
youtube: "aK97n-bmld4"
---

You currently have massive amounts of data sitting on Apache Pulsar and likely — even more data coming in every second. But part of your project requires this data to be sent to some system to explore the dataset further. You look into the Pulsar website for built-in connectors to that particular system and realize that there are none. What a bummer.
But you don’t have to give up on Pulsar because of this. You can write custom sink connectors for Pulsar I/O that work just like the built-in ones, and all you will need is a bit of Java development experience and creativity. The rest you can leave to this talk. This talk will explain how to start developing your custom connector, show how the code looks like, demonstrate how to deploy, and discuss some of the design decisions that your custom connector may need to address.

<!--more-->
