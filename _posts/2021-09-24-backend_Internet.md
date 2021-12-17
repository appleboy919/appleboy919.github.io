---
title: "[Backend Dev] #2 Internet"
excerpt: "How does Internet work?"

categories:
  - Backend Development
tags:
  - [Internet, Backend, Backend Dev]

toc: true

date: 2021-09-24
last_modified_at: 2021-10-10
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
    - support for different user applications (e.g. web browsers)
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
  - **Internet Layer**
    - provides instructions(addresses) used to transport packets across the network
    - **IP addresses** are assigned to packets
    - Protocols:
      - IPv4
      - IPv6
    - Functions:
      - select the **next-hop host(or gateway)**
      - capture packets (incoming packets) and pass them to applciation
      - error detection using checksum
  - **Network Layer**
    - exchange of data between **computer** and **network**
    - Devices: **Ethernet**, Network device drivers, Switches
  
  - Example: Requesting a web page from a web server
    1. **HTTP** (application): Web browser generates request for specific files on a web server
    2. **TCP** (transport): splits requests into **small pacekts** providing a _sequence number_ and _checksum_
    3. **IP** (internet): **IP packets** are sent to servers (IP addresses)
    4. **Ethernet** (network): binary data which makes up each IP packet is sent through network

## 3. What is HTTP?

- HyperText Transfer Protocol (HTTP)
- uses **client-server mode** to **fetch web pages from web servers to client browsers**
![HTTP](/assets/images/HTTP.png)
- **specify actions** for web servers and browsers


## 4. Domain Name Server and System
- Domain name system locates domain names and translates into **IP addresses**
- DNS Servers **resolves names to IP addresses**
    
