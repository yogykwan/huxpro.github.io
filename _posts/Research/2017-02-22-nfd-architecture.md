---
layout:     post
title:      "NFD Architecture"
subtitle:   ""
date:       2017-2-22
author:     "Jennica"
header-img: "img/post-bg-wifi.jpg"
catalog: true
tags:
    - 研究
    - NDN
---


# NFD Introduction
* support diverse experimentation with NDN architecture
* improve modularity and extensibility
* keep up with NDN protocol spec
* add new features

## Modules
* Common Services: configuration file, logger, hash computation routines, face monitors, DNS resolver, etc.
* Face: abstraction of various lower level transport mechanisms composed of LinkService and Transport
* Tables: CS, PIT, FIB, Strategy Choice, Measurements, Dead Nonce List, Network Region, Capacity Maintenance 
* Forwarding: processing pathways in the form of forwarding pipelines and interact with Tables and Strategies
* Strategies: decide whether, when and where to forward packets
* Management: allow applications to configure NFD and internal states
* RIB Management: update by different parities to generate consistent forwarding table and sync it up with FIB

## Process Packet
* Face reads incoming stream or datagrams via system API, extracts network-layer packets from link protocol packets, delivers these packets (Data, Interest, Nack) to the forwarder
* on Interest: inserted into PIT, queried in CS; returns data to requester if hit, otherwise uses Forwarding Strategy to decide how to forward Interest
* on Data: check PIT entries; dropped if unsolicited, otherwise inserted into CS, sent to all requesters recorded in in-records of PIT entries
* on Nack: depends on Forwarding Strategy

---
***keep updating...***
