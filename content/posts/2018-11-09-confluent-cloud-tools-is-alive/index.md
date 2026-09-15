---
title: "Confluent Cloud Tools is Alive"
author: "Ricardo Ferreira"
date: 2018-11-09
nolastmod: true
draft: false
---
It gives me great pleasure to announce that **Confluent Cloud Tools** is officially released as a Confluent's repository. The link to this repository is:

<https://github.com/confluentinc/ccloud-tools>

In a nutshell, the aim of this project is to allow developers to unfold the true agility that [Confluent Cloud](https://www.confluent.io/confluent-cloud/) can provide --allowing them to focus on writing code instead of wasting time with manual and tedious configuration steps.

Very often developers use tools from Confluent such as Schema Registry, REST Proxy, Connect, KSQL and Control Center -- along with their Kafka clusters. This may work fine when they are working On-Premise and making use of the integrated experience that Confluent Platform provides -- whether if it is running Confluent Platform locally and managing things via the CLI or; if it is by using the built-in [Docker containers](https://hub.docker.com/u/confluentinc).

However, things can be quite stressful when they need to implement code on these tools in the Cloud. Though Confluent Cloud can take away the burden of managing the brokers and Zookeeper by themselves -- these tools still need to be manually provisioned, configured, fine tuned and secured.

Networking problems, ports that don't bind correctly, visibility between subnets, scaling in/out processes across availability zones, bastion servers -- are some of the concerns that rises when developers try to provision these tools by themselves.

Well... not anymore 😊
