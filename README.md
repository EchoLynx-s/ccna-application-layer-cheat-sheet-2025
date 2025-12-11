# CCNA – Application Layer (Module 15)

Quick-reference notes for NetAcad CCNA – **Module 15: Application Layer**.  
Focus is on how real-world applications (web, email, DNS, DHCP, file sharing, P2P)
use the upper layers of the TCP/IP stack.

I use this repo to revise:

- What the **application, presentation, and session layers** actually do.
- The difference between **client–server** and **peer-to-peer (P2P)** models.
- How the web works: **HTTP/HTTPS + HTML** basics.
- How **email protocols** work together: SMTP, POP, IMAP.
- How **DNS** and **DHCP** provide naming and automatic IP addressing.
- How **FTP** and **SMB** handle file transfer and file sharing on networks.
- Typical **exam questions** around “which protocol for which service” and basic `nslookup` usage.

---

## Table of Contents

- [Module 15 Overview](#module-15-overview)  
- [Module Map](#module-map)  

- [15.0 Introduction](#150-introduction)  
  - [15.0.1 Why should I take this module?](#1501-why-should-i-take-this-module)  
  - [15.0.2 What will I learn to do in this module?](#1502-what-will-i-learn-to-do-in-this-module)  

- [15.1 Application, Presentation, and Session](#151-application-presentation-and-session)  
  - [15.1.1 Application Layer](#1511-application-layer)  
  - [15.1.2 Presentation and Session Layer](#1512-presentation-and-session-layer)  
  - [15.1.3 TCP/IP Application Layer Protocols](#1513-tcpip-application-layer-protocols)  
  - [15.1.4 Check Your Understanding – Application, Session, Presentation](#1514-check-your-understanding--application-session-presentation)  

- [15.2 Peer-to-Peer](#152-peer-to-peer)  
  - [15.2.1 Client-Server Model](#1521-client-server-model)  
  - [15.2.2 Peer-to-Peer Networks](#1522-peer-to-peer-networks)  
  - [15.2.3 Peer-to-Peer Applications](#1523-peer-to-peer-applications)  
  - [15.2.4 Common P2P Applications](#1524-common-p2p-applications)  
  - [15.2.5 Check Your Understanding – Peer-to-Peer](#1525-check-your-understanding--peer-to-peer)  

- [15.3 Web and Email Protocols](#153-web-and-email-protocols)  
  - [15.3.1 Hypertext Transfer Protocol and Hypertext Markup Language](#1531-hypertext-transfer-protocol-and-hypertext-markup-language)  
  - [15.3.2 HTTP and HTTPS](#1532-http-and-https)  
  - [15.3.3 Email Protocols](#1533-email-protocols)  
  - [15.3.4 SMTP, POP, and IMAP](#1534-smtp-pop-and-imap)  
  - [15.3.5 Check Your Understanding – Web and Email Protocols](#1535-check-your-understanding--web-and-email-protocols)  

- [15.4 IP Addressing Services](#154-ip-addressing-services)  
  - [15.4.1 Domain Name System](#1541-domain-name-system)  
  - [15.4.2 DNS Message Format](#1542-dns-message-format)  
  - [15.4.3 DNS Hierarchy](#1543-dns-hierarchy)  
  - [15.4.4 The nslookup Command](#1544-the-nslookup-command)  
  - [15.4.5 Syntax Checker – The nslookup Command](#1545-syntax-checker--the-nslookup-command)  
  - [15.4.6 Dynamic Host Configuration Protocol](#1546-dynamic-host-configuration-protocol)  
  - [15.4.7 DHCP Operation](#1547-dhcp-operation)  
  - [15.4.8 Lab – Observe DNS Resolution](#1548-lab--observe-dns-resolution)  
  - [15.4.9 Check Your Understanding – IP Addressing Services](#1549-check-your-understanding--ip-addressing-services)  

- [15.5 File Sharing Services](#155-file-sharing-services)  
  - [15.5.1 File Transfer Protocol](#1551-file-transfer-protocol)  
  - [15.5.2 Server Message Block](#1552-server-message-block)  
  - [15.5.3 Check Your Understanding – File Sharing Services](#1553-check-your-understanding--file-sharing-services)  

- [15.6 Module Practice and Quiz](#156-module-practice-and-quiz)  
  - [15.6.1 What did I learn in this module?](#1561-what-did-i-learn-in-this-module)  
  - [15.6.2 Module Quiz – Application Layer](#1562-module-quiz--application-layer)  

---

## Module 15 Overview

> **Goal:** Understand the protocols and models at the **application layer** that
> make everyday network services work – web, email, name resolution, addressing
> services, and file sharing – and be able to identify **which protocol does what**
> in common CCNA scenarios.

---

## Module Map

| Topic                           | Focus                                                                 |
|---------------------------------|-----------------------------------------------------------------------|
| 15.1 App / Presentation / Session | Roles of OSI upper layers and common TCP/IP application protocols   |
| 15.2 Peer-to-Peer               | Client–server vs P2P models, pros/cons, typical P2P apps             |
| 15.3 Web and Email Protocols    | HTTP/HTTPS, HTML, SMTP/POP/IMAP, secure vs insecure variants         |
| 15.4 IP Addressing Services     | DNS, DNS hierarchy, `nslookup`, DHCP and leasing addresses           |
| 15.5 File Sharing Services      | FTP for file transfer, SMB for file and printer sharing              |
| 15.6 Practice and Quiz          | DNS/DHCP/HTTP/FTP quiz-style review and summary                      |

---

