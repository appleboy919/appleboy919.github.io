---
title: "[Backend Dev] #2 Internet"
excerpt: "How does Internet work?"

categories:
  - Backend Development
tags:
  - [Internet, Backend, Backend Dev]

toc: true

date: 2021-09-24
last_modified_at: 2021-09-26
---

## 1. What is Internet?

- Computer Network: two or more connected computers that can share resources such as data, printer, Internet connection
- Internet: a network of networks connecting globally based on certain **protocols**.
- Internet is usually built upon **Client/Server** or **P2P**

## 2. Protocol

- Internet use specific protocols to form a systematic connection
- **Protocol = Common "language" behind the Internet**
- **TCP/IP Layer Model**
  - Transmission Control Protocol / Internet Protocol
  - 4 Layers: Application, Transport, Internet, Network Layers
  - **Application Layer**
    - Support for different user applications (e.g. web browsers)
    - includes HTTP, HTTPS, FTP, SMTP
      - HTTP: World Wide Web's Hypertext Transfer protocol for accessing websites from web servers
      - HTTPS: more secured version of HTTP
      - FTP: File Transfer Protocol
      - SMTP: Simple Mail Transfer Protocol
      - SSH: Secure Socket Shell, Unix-based command oline interface and protocol for securely getting access to remote computer
  - **Transport Layer**
    - creates "packets" of data to tranmit which contains sequence numbers and a checksum
    - Protocols:
      - **TCP/IP**: useful when all data needs to arrive, but time is not a significant factor / connection-oriented / slower
      - **UDP**: useful when time is a factor and packet / connectionless / faster
    - Packet Management
      - make sure all data packets arrived in the same order in which they are sent out
      - packet _not received_ or _received in eorror_ are retransmitted
