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



# Module 15 — Application Layer (ITN)

## 15.0 Introduction

## 15.0.1 Why should I take this module?

Welcome to Application Layer!

As you have learned, the transport layer is where data actually gets moved from one host to another. But before that can take place, there are a lot of details that have to be determined so that this data transport happens correctly. This is why there is an application layer in both the OSI and the TCP/IP models. As an example, before there was streaming video over the internet, we had to watch home movies in a variety of other ways. Imagine that you videotaped some of your child's soccer game. Your parents, in another city, only have a video cassette player. You have to copy your video from your camera onto the right type of video cassette to send to them. Your brother has a DVD player, so you transfer your video to a DVD to send to him. This is what the application layer is all about, making sure that your data is in a format that the receiving device can use. Let's dive in!

## 15.0.2 What will I learn to do in this module?

**Module Title:** Application Layer  
**Module Objective:** Explain the operation of application layer protocols in providing support to end-user applications.

| Topic Title | Topic Objective |
|---|---|
| **Application, Presentation, and Session** | Explain how the functions of the application layer, presentation layer, and session layer work together to provide network services to end user applications. |
| **Peer-to-Peer** | Explain how end user applications operate in a peer-to-peer network. |
| **Web and Email Protocols** | Explain how web and email protocols operate. |
| **IP Addressing Services** | Explain how DNS and DHCP operate. |
| **File Sharing Services** | Explain how file transfer protocols operate. |

---

## 15.1 Application, Presentation, and Session

## 15.1.1 Application Layer

In the OSI and the TCP/IP models, the application layer is the closest layer to the end user. As shown in the figure, it is the layer that provides the interface between the applications used to communicate, and the underlying network over which messages are transmitted. Application layer protocols are used to exchange data between programs running on the source and destination hosts.

**Figure callouts (OSI Model vs TCP/IP Model):**
- **OSI Model:** 7. Application; 6. Presentation; 5. Session; 4. Transport; 3. Network; 2. Data Link; 1. Physical
- **TCP/IP Model:** Application; Transport; Internet; Network Access
- The **upper three layers** of the OSI model are grouped as **Application Layers** in the figure.
- The **lower four layers** of the OSI model are grouped as **Data Flow Layers** in the figure.
- Example application layer protocols shown: **Domain Name System**, **Hypertext Transfer Protocol**, **Simple Mail Transfer Protocol**, **Post Office Protocol**, **Dynamic Host Configuration Protocol**, **File Transfer Protocol**, **Internet Message Access Protocol**


Based on the TCP/IP model, the upper three layers of the OSI model (application, presentation, and session) define functions of the TCP/IP application layer.

There are many application layer protocols, and new protocols are always being developed. Some of the most widely known application layer protocols include Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP), Internet Message Access Protocol (IMAP), and Domain Name System (DNS) protocol.

## 15.1.2 Presentation and Session Layer

### Presentation Layer

The presentation layer has three primary functions:

- Formatting, or presenting, data at the source device into a compatible format for receipt by the destination device.
- Compressing data in a way that can be decompressed by the destination device.
- Encrypting data for transmission and decrypting data upon receipt.

As shown in the figure, the presentation layer formats data for the application layer, and it sets standards for file formats. Some well-known standards for video include Matroska Video (MKV), Motion Picture Experts Group (MPG), and QuickTime Video (MOV). Some well-known graphic image formats are Graphics Interchange Format (GIF), Joint Photographic Experts Group (JPG), and Portable Network Graphics (PNG) format.

**Figure callouts (Presentation layer file format standards shown):**
- Matroska video (**MKV**)
- Motion Picture Experts Group (**MPG**)
- Quick Time (**MOV**)
- Graphics Interchange Format (**GIF**)
- Joint Photographic Experts Group (**JPG**)
- Portable Network Graphics (**PNG**)


### Session Layer

As the name implies, functions at the session layer create and maintain dialogs between source and destination applications. The session layer handles the exchange of information to initiate dialogs, keep them active, and to restart sessions that are disrupted or idle for a long period of time.

## 15.1.3 TCP/IP Application Layer Protocols

The TCP/IP application protocols specify the format and control information necessary for many common internet communication functions. Application layer protocols are used by both the source and destination devices during a communication session. For the communications to be successful, the application layer protocols that are implemented on the source and destination host must be compatible.

Click each application protocol type to learn more about each protocol.

### Name System

**DNS - Domain Name System (or Service)**  
- TCP, UDP 53  
- Translates domain names, such as cisco.com, into IP addresses.

### Host Config

**BOOTP - Bootstrap Protocol**  
- UDP client 68, server 67  
- Enables a diskless workstation to discover its own IP address, the IP address of a BOOTP server on the network, and a file to be loaded into memory to boot the machine  
- BOOTP is being superseded by DHCP  

**DHCP - Dynamic Host Configuration Protocol**  
- UDP client 68, server 67  
- Dynamically assigns IP addresses to be re-used when no longer needed  

### Email

**SMTP - Simple Mail Transfer Protocol**  
- TCP 25  
- Enables clients to send email to a mail server  
- Enables servers to send email to other servers  

**POP3 - Post Office Protocol**  
- TCP 110  
- Enables clients to retrieve email from a mail server  
- Downloads the email to the local mail application of the client  

**IMAP - Internet Message Access Protocol**  
- TCP 143  
- Enables clients to access email stored on a mail server  
- Maintains email on the server  

### File Transfer

**FTP - File Transfer Protocol**  
- TCP 20 to 21  
- Sets rules that enable a user on one host to access and transfer files to and from another host over a network  
- FTP is a reliable, connection-oriented, and acknowledged file delivery protocol  

**TFTP - Trivial File Transfer Protocol**  
- UDP client 69  
- A simple, connectionless file transfer protocol with best-effort, unacknowledged file delivery  
- It uses less overhead than FTP  

### Web

**HTTP - Hypertext Transfer Protocol**  
- TCP 80, 8080  
- A set of rules for exchanging text, graphic images, sound, video, and other multimedia files on the World Wide Web  

**HTTPS - HTTP Secure**  
- TCP, UDP 443  
- The browser uses encryption to secure HTTP communications  
- Authenticates the website to which you are connecting your browser  


# Module 15 — Application Layer (Extracted Transcripts)

## ✅ Included in this document
- Full transcript of **15.1.4 Check Your Understanding (Q1–Q5)**
- **Correct answers included**
- Full transcript of **15.2.2 Peer-to-Peer Networks**
- Full transcript of **15.2.3 Peer-to-Peer Applications**
- Full transcript of **15.2.4 Common P2P Applications**
- Figure descriptions clearly explained
- Content extracted from screenshots **15.1.4 → 15.3.1**
- Markdown format (.md)

---

## 15.1.4 Check Your Understanding — Application, Session, Presentation

### Question 1
**This layer of the OSI model is concerned with the protocols that exchange data between programs running on hosts.**

- Network  
- Transport  
- Physical  
- ✅ **Application**

**Correct answer:** Application

---

### Question 2
**MKV, GIF, and JPG standards are associated with which OSI layer?**

- Session  
- ✅ **Presentation**  
- Application  
- Transport  

**Correct answer:** Presentation

---

### Question 3
**These three OSI layers define the same functions as the TCP/IP model application layer. (Choose three)**

- Data Link  
- Network  
- Transport  
- ✅ **Session**  
- ✅ **Application**  
- ✅ **Presentation**  

**Correct answers:** Application, Presentation, Session

---

### Question 4
**Which two are protocols that belong in the OSI application layer? (Choose two)**

- ✅ **DNS**  
- ✅ **SMTP**  
- PNG  
- QuickTime  

**Correct answers:** DNS, SMTP

---

### Question 5
**This is a function of the OSI session layer.**

- Compress and decompress data  
- Provide an interface between applications  
- ✅ **Exchange of information to initiate dialog between peers**  
- Format data for the application layer  

**Correct answer:** Exchange of information to initiate dialog between peers

---

## 15.2.2 Peer-to-Peer Networks

In the peer-to-peer (P2P) networking model, data is accessed from a peer device without the use of a dedicated server.

The P2P model involves two parts:
- P2P networks
- P2P applications

In a P2P network:
- Two or more computers are connected via a network
- Devices can share resources such as files and printers
- No dedicated server is required
- Each peer can function as both a client and a server
- Roles are assigned per request

Additional capabilities:
- Sharing internet connections
- Networked gaming
- File sharing

### Figure Description
- Peer 1: Print Client, File Server
- Peer 2: Print Server, File Client
- Printer is directly connected to Peer 2
- Both peers communicate directly over the network

---

## 15.2.3 Peer-to-Peer Applications

A P2P application allows a device to act as both a client and a server within the same communication.

Key characteristics:
- Every client is a server
- Every server is a client
- Each device provides a user interface
- Each device runs a background service

### Hybrid P2P Systems
Some P2P applications use a hybrid system:
- Resource sharing is decentralized
- Indexes are stored on a centralized directory server
- Peers query the index server to locate resources
- Data transfer occurs directly between peers

### Figure Description
- Instant messaging example
- Both devices send and receive messages simultaneously
- No dedicated server controls communication

---

## 15.2.4 Common P2P Applications

With P2P applications, each computer running the application can act as a client or server.

Common P2P networks include:
- BitTorrent
- Direct Connect
- eDonkey
- Freenet

Some P2P applications use the **Gnutella protocol**, where:
- Users share whole files with other users
- Clients connect to Gnutella services over the internet
- Users locate and access resources shared by other peers

Examples of Gnutella-compatible clients:
- µTorrent
- BitComet
- DC++
- Deluge
- eMule

### Figure Description
- One peer asks: “Where is mysong.mp3?”
- Multiple peers respond: “I’ve got it.”
- Requests propagate through the network

### BitTorrent Explanation
Many P2P applications allow users to share **pieces of many files simultaneously**.

How BitTorrent works:
- Clients use a torrent file to locate peers
- Torrent file contains tracker information
- Clients download file pieces from multiple peers
- This process is called a **swarm**

Popular BitTorrent clients:
- BitTorrent
- µTorrent
- Deluge
- qBittorrent

### Legal Notice
Any type of file can be shared between users. Many files are copyrighted.
Downloading or distributing copyrighted files without permission is illegal and may result in civil or criminal penalties.

---

## 15.2.5 Check Your Understanding — Peer-to-Peer

### Question 1
**True or False? The peer-to-peer networking model requires a dedicated server for data access.**

- True  
- ✅ **False**

---

### Question 2
**True or False? In a peer-to-peer network environment every peer can function as both a client and a server.**

- ✅ **True**  
- False  

---

### Question 3
**Which peer-to-peer application allows users to share pieces of many files with each other at the same time?**

- ✅ **BitTorrent**  
- Gnutella  
- Hybrid  

---

### Question 4
**Which of the following is a feature of the Gnutella protocol?**

- Users can access an index server to locate resources  
- ✅ **Users can share whole files with other users**  
- Users can share pieces of files with other users  

---

## 15.3.1 Hypertext Transfer Protocol and Hypertext Markup Language

There are application layer–specific protocols designed for common uses such as web browsing and email.

When a URL is entered into a web browser:
- The browser establishes a connection to a web service
- The web service runs on a server using HTTP
- URLs and URIs identify web resources

To understand browser-server interaction, a web page request is examined using:
http://www.cisco.com/index.html



# Module 15 — Application Layer (15.1.4 → 15.3.4)
**Full transcript with answers included**  
Source: Cisco NetAcad – Introduction to Networks

---

## 15.1.4 Check Your Understanding — Application, Session, Presentation

### Question 1
**This layer of the OSI model is concerned with the protocols that exchange data between programs running on hosts.**

- Network  
- Transport  
- Physical  
- ✅ **Application**

**Correct Answer:** Application

---

### Question 2
**MKV, GIF, and JPG standards are associated with which OSI layer?**

- Session  
- ✅ **Presentation**  
- Application  
- Transport  

**Correct Answer:** Presentation

---

### Question 3
**These three OSI layers define the same functions as the TCP/IP model application layer.**

- Data Link  
- Network  
- Transport  
- ✅ **Session**  
- ✅ **Application**  
- ✅ **Presentation**  

**Correct Answers:** Application, Presentation, Session

---

### Question 4
**Which two are protocols that belong in the OSI application layer?**

- ✅ **DNS**  
- ✅ **SMTP**  
- PNG  
- QuickTime  

**Correct Answers:** DNS, SMTP

---

### Question 5
**This is a function of the OSI session layer.**

- Compress and decompress data  
- Provide an interface between applications  
- ✅ **Exchange of information to initiate dialog between peers**  
- Format data for the application layer  

**Correct Answer:** Exchange of information to initiate dialog between peers

---

## 15.2.2 Peer-to-Peer Networks (Full Transcript)

In the peer-to-peer (P2P) networking model, data is accessed from a peer device without the use of a dedicated server.

In a P2P network:
- Two or more computers are connected via a network.
- Each connected device (peer) can function as both a client and a server.
- Roles of client and server are determined per request.
- Resources such as files, printers, and internet access can be shared.

Peers are considered equal in communication. One peer may request data while another responds, and later those roles may reverse.

**Figure description:**  
Two peers are shown connected through a network. Each peer can act as a file server or print server depending on the request.

---

## 15.2.3 Peer-to-Peer Applications (Full Transcript)

A P2P application allows a device to act as both a client and a server within the same communication.

Characteristics:
- Every client is a server.
- Every server is a client.
- Each device runs a user interface and a background service.

Some P2P applications use a **hybrid system**:
- Resource sharing is decentralized.
- Indexes that point to resource locations are stored on a centralized directory server.

**Figure description:**  
Two devices exchange instant messages simultaneously. Both devices send and receive messages at the same time through the network.

---

## 15.2.4 Common P2P Applications

Common P2P networks include:
- BitTorrent
- Direct Connect
- eDonkey
- Freenet

Some P2P applications use the **Gnutella protocol**, where users share whole files.

Examples of Gnutella-compatible clients:
- µTorrent
- BitComet
- DC++
- Deluge
- eMule

### BitTorrent
- Files are split into pieces.
- Clients download pieces from multiple peers simultaneously.
- This group of peers is called a **swarm**.
- Torrent files contain tracker information.

⚠️ **Note:** Downloading or distributing copyrighted material without permission is illegal and can result in criminal charges or civil lawsuits.

---

## 15.2.5 Check Your Understanding — Peer-to-Peer

### Question 1
**The peer-to-peer networking model requires a dedicated server.**  
❌ False is correct.

---

### Question 2
**In a peer-to-peer network, every peer can function as both a client and a server.**  
✅ True

---

### Question 3
**Which peer-to-peer application allows users to share pieces of many files with each other at the same time?**  
✅ BitTorrent

---

### Question 4
**Which of the following is a feature of the Gnutella protocol?**  
✅ Users can share whole files with other users.

---

## 15.3.1 Hypertext Transfer Protocol and Hypertext Markup Language

When a URL is typed into a web browser, the browser establishes a connection to a web service using HTTP.

A URL consists of:
- **http** — protocol
- **www.cisco.com** — server name
- **index.html** — requested file

### Step 1
The browser interprets the URL.

### Step 2
The browser contacts a name server to resolve the domain name into an IP address.  
The client sends an HTTP **GET** request for the page.

### Step 3
The server responds by sending the HTML code of the web page.

**Figure description:**  
HTTP/1.1 200 OK response containing headers and HTML content.

### Step 4
The browser decodes the HTML code and renders the web page.

---

## 15.3.2 HTTP and HTTPS

HTTP is a request/response protocol.

Common HTTP message types:
- **GET** — Request data (HTML pages)
- **POST** — Upload data (form data)
- **PUT** — Upload resources

HTTP is **not secure**:
- Data is transmitted in plaintext.
- Responses are unencrypted.

### HTTPS
- Uses authentication and encryption.
- Secures data using **TLS** (or SSL).
- Same request/response process as HTTP, but encrypted.

---

## 15.3.3 Email Protocols

Email is a store-and-forward service.

Key characteristics:
- Email clients communicate with mail servers.
- Mail servers communicate with other mail servers.
- Clients do not send email directly to other clients.

Protocols used:
- **SMTP** — sending email
- **POP** or **IMAP** — retrieving email

---

## 15.3.4 SMTP, POP, and IMAP

### SMTP
- Uses TCP port **25**
- Requires message headers and body
- Spools messages if destination server is unavailable
- Undelivered messages are eventually returned

### POP
- Uses TCP port **110**
- Downloads and deletes messages by default
- No centralized message storage
- POP3 is most common

### IMAP
- Messages remain on the server
- Supports folder hierarchy
- Synchronizes deletions across clients
- Recommended for centralized access

---

✅ **End of Module 15 Application Layer Transcript**


# Module 15 — Application Layer (Full Transcript)

---

## 15.3.5 Check Your Understanding — Web and Email Protocols

### Question 1
**This message type is used when uploading data files to a web server.**

- GET  
- PUT  
- **POST** ✅

**Correct answer:** POST

---

### Question 2
**This protocol is used by a web browser to establish a connection to a web server.**

- IMAP  
- SSL  
- SMTP  
- **HTTP** ✅

**Correct answer:** HTTP

---

### Question 3
**This protocol is used by a client to send email to a mail server.**

- **SMTP** ✅  
- POP  
- IMAP  
- HTTP  

**Correct answer:** SMTP

---

### Question 4
**Which is a feature of IMAP?**

- **It downloads a copy of email messages leaving the original on the server.** ✅  
- It listens passively on port 110 for client requests.  
- It uploads email messages to a server.

**Correct answer:** It downloads a copy of email messages leaving the original on the server.

---

### Question 5
**True or false? HTTP is a secure protocol.**

- **False** ✅  
- True  

**Correct answer:** False

---

## 15.4.1 Domain Name System (DNS)

### Overview
Domain Name System (DNS) is an application-layer protocol that translates human-readable domain names into numeric IP addresses used by devices on networks.

DNS makes networks scalable by allowing users to remember names instead of numeric addresses.

---

### DNS Resolution Process (Step-by-Step)

#### Step 1
The user types a **Fully Qualified Domain Name (FQDN)** into a browser address bar  
Example: `http://www.cisco.com`

#### Step 2
The client sends a **DNS query** to the designated DNS server requesting the IP address for the FQDN.

#### Step 3
The DNS server matches the FQDN with its corresponding **numeric IP address**.  
Example:  
- `www.cisco.com → 198.133.219.25`

#### Step 4
The DNS server sends a **DNS query response** back to the client containing the IP address.

#### Step 5
The client uses the IP address to make requests directly to the destination server.

---

## Key DNS Concepts

- DNS uses a single message format for queries and responses.
- DNS supports error messages and resource record transfers.
- Domain names remain constant even if IP addresses change.
- This abstraction allows seamless connectivity and easier network management.

---

**Status:**  
✅ Full transcript  
✅ All steps included  
✅ Answers clearly marked  
✅ Ready for study / GitHub / Notion





---


# CCNA ITN – Module 15 Application Layer (Full Transcript + Answers)

---

## 15.4.2 DNS Message Format

**Transcript**

DNS servers store different types of resource records used to resolve names. These records contain the name, address, and type of record.

Common DNS record types:
- **A** – An end device IPv4 address  
- **NS** – An authoritative name server  
- **AAAA** – An end device IPv6 address  
- **MX** – A mail exchange record  

When a client makes a query, the DNS server first checks its local records. If it cannot resolve the name, it contacts other DNS servers. Once resolved, the result is cached temporarily.

Windows systems also cache DNS entries. The command `ipconfig /displaydns` shows cached DNS records.

DNS messages use the same format between servers and clients and contain four sections:

| DNS Message Section | Description |
|--------------------|------------|
| Question | The query for the DNS server |
| Answer | Resource records answering the query |
| Authority | Records pointing to authoritative servers |
| Additional | Extra information records |

---

## 15.4.3 DNS Hierarchy

**Transcript**

DNS uses a hierarchical structure to organize domain names.

- Root level domain
- Top-Level Domains (TLDs):  
  - `.com` – business  
  - `.org` – non-profit  
  - `.edu` – education  
  - `.au` – Australia  
  - `.co` – Colombia  

Domains are divided into zones. Each DNS server manages a small portion of the namespace, improving scalability and performance.

**Figure description**
- Root domain at the top
- TLD servers below
- Second-level domains (e.g., `cisco.com`)
- Subdomains (e.g., `www.cisco.com`, `ftp.cisco.com`, `mail.cisco.com`)

---

## 15.4.4 The nslookup Command

**Transcript**

`nslookup` allows users to manually query DNS servers to resolve hostnames and troubleshoot DNS issues.

Example:
```
C:\> nslookup
Default Server: dns-sj.cisco.com
Address: 171.70.168.183
```

You can query domain names or IP addresses to perform forward or reverse lookups.

---

## 15.4.5 Syntax Checker – nslookup

**Transcript**

The syntax checker allows users to practice DNS lookups on Windows and Linux.

Example:
```
nslookup www.google.com
```

**Result**
- Displays DNS server used
- Shows IPv4 and IPv6 addresses
- Confirms domain name resolution

---

## 15.4.6 Dynamic Host Configuration Protocol (DHCP)

**Transcript**

DHCP automates the assignment of:
- IP addresses
- Subnet masks
- Default gateways
- DNS servers

DHCP assigns addresses from a pool using leases. When the lease expires, the address returns to the pool.

DHCPv6 differs from DHCPv4 because it does **not** assign a default gateway. IPv6 gateways are learned through Router Advertisements.

---

## 15.4.7 DHCP Operation

**Transcript**

DHCP uses a four-step process:

1. **DHCPDISCOVER** – Client broadcasts to locate DHCP servers  
2. **DHCPOFFER** – Server offers IP configuration  
3. **DHCPREQUEST** – Client requests the offered address  
4. **DHCPACK** – Server confirms the lease  

If the address is unavailable, the server sends **DHCPNAK**.

DHCP ensures all IP addresses are unique on the network.

---

## 15.4.8 Lab – Observe DNS Resolution

**Objectives**
- Observe DNS conversion of URLs to IP addresses
- Use `nslookup` for web and mail servers

### Key Answers

**What is the purpose of DNS?**  
➡️ To translate human-readable domain names into IP addresses so devices can communicate.

**Why are IP addresses different when pinging the same site?**  
➡️ Because large organizations use load balancing and geographically distributed servers.

**What are IPv6 addresses shown in nslookup output?**  
➡️ IPv6 records (AAAA records).

**Which mail server is contacted first for cisco.com?**  
➡️ The server with the **lowest MX preference value**.

---

## ✔ End of Module 15.4
# Module 15 — Application Layer (Continued)

---

## 15.4.9 Check Your Understanding — IP Addressing Services

### Question 1
**Which of the following DNS record types is used to resolve IPv6 addresses?**

**Answer:** AAAA  
**Explanation:** AAAA records map hostnames to IPv6 addresses.

---

### Question 2
**True or false? A DNS server that receives a request for a name resolution that is not within its DNS zone will send a failure message to the requesting client.**

**Answer:** False  
**Explanation:** The DNS server forwards the request to another DNS server responsible for the correct zone.

---

### Question 3
**Which of the following is displayed by the nslookup utility?**

**Answer:** The configured default DNS server  
**Explanation:** When nslookup is started, it displays the default DNS server used by the host.

---

### Question 4
**Which of the following DNS resource record types resolves authoritative name servers?**

**Answer:** NS  
**Explanation:** NS (Name Server) records identify authoritative DNS servers for a domain.

---

## 15.5 File Sharing Services

### 15.5.1 File Transfer Protocol (FTP)

FTP is a client/server application layer protocol used to upload and download files between a client and a server.

**FTP Connections:**
1. **Control Connection**
   - Uses TCP port 21
   - Used for commands and replies

2. **Data Connection**
   - Uses TCP port 20
   - Created each time data is transferred

**Data Transfer Direction:**
- Download (pull) data from the server
- Upload (push) data to the server

---

### 15.5.2 Server Message Block (SMB)

The Server Message Block (SMB) protocol is used for sharing network resources such as:
- Files
- Directories
- Printers
- Serial ports

**SMB Characteristics:**
- Client/server model
- Request–response protocol
- Uses TCP/IP for transport
- Enables direct access to remote resources as if they were local

**Common SMB Functions:**
- Start, authenticate, and terminate sessions
- Control file and printer access
- Exchange messages between applications

**Cross-Platform Support:**
- Linux and UNIX use **SAMBA**
- macOS supports SMB natively

---

### SMB File Exchange Process
A file can be copied between Windows PCs using Windows Explorer through SMB, maintaining a persistent connection to the server.

---

## End of Section

# Module 15 — Application Layer (FULL TRANSCRIPT)

This document contains **full, verbatim transcriptions** of all provided screenshots from:
- 15.3.5 Check Your Understanding — Web and Email Protocols
- 15.4 DNS, DHCP, and IP Addressing Services
- 15.5 File Sharing Services
- 15.6 Module Practice and Quiz

All **answers are explicitly included**.

---

## 15.3.5 Check Your Understanding — Web and Email Protocols

### Question 1
**This message type is used when uploading data files to a web server.**  
- GET  
- PUT  
- POST  

✅ **Correct Answer:** POST

---

### Question 2
**This protocol is used by a web browser to establish a connection to a web server.**  
- IMAP  
- SSL  
- SMTP  
- HTTP  

✅ **Correct Answer:** HTTP

---

### Question 3
**This protocol is used by a client to send email to a mail server.**  
- SMTP  
- POP  
- IMAP  
- HTTP  

✅ **Correct Answer:** SMTP

---

### Question 4
**Which is a feature of IMAP?**  
- It downloads a copy of email messages leaving the original on the server.  
- It listens passively on port 110 for client requests.  
- It uploads email messages to a server.  

✅ **Correct Answer:** It downloads a copy of email messages leaving the original on the server.

---

### Question 5
**True or false? HTTP is a secure protocol.**  
- False  
- True  

✅ **Correct Answer:** False

---

## 15.4.2 DNS Message Format

DNS resource record types:
- **A** — IPv4 address  
- **NS** — Authoritative name server  
- **AAAA** — IPv6 address  
- **MX** — Mail exchange record  

DNS message sections:
| Section | Description |
|------|-----------|
| Question | The question for the name server |
| Answer | Resource Records answering the question |
| Authority | Records pointing toward an authority |
| Additional | Records holding additional information |

---

## 15.4.3 DNS Hierarchy

- Root level domain
- Top-level domains (TLDs): `.com`, `.edu`, `.net`, `.au`, `.co`
- Second-level domain: `cisco.com`
- Subdomains: `www.cisco.com`, `ftp.cisco.com`, `mail.cisco.com`

DNS is hierarchical and scalable.

---

## 15.4.4 The nslookup Command

`nslookup` allows manual DNS queries.

Example output includes:
- Default DNS server
- Server address
- Host name
- IPv4 and IPv6 addresses
- Aliases

---

## 15.4.6 Dynamic Host Configuration Protocol (DHCP)

DHCP automatically assigns:
- IPv4 address
- Subnet mask
- Gateway
- DNS server

DHCP lease process:
- Address is leased for a period
- Returned to pool on expiration

DHCPv6:
- Does **not** provide default gateway
- Uses Router Advertisement instead

---

## 15.4.7 DHCP Operation

DHCP message sequence:
1. DHCPDISCOVER
2. DHCPOFFER
3. DHCPREQUEST
4. DHCPACK

Ensures unique IP addresses.

---

## 15.4.9 Check Your Understanding — IP Addressing Services

### Question 1
**Which DNS record resolves IPv6 addresses?**  
- AAAA  
- MX  
- A  
- NS  

✅ **Correct Answer:** AAAA

---

### Question 2
**True or false? A DNS server sends a failure if the name is outside its zone.**  
- False  
- True  

✅ **Correct Answer:** False

---

### Question 3
**Which is displayed by the nslookup utility?**  
- The configured default DNS server  
- The IP address of the end device  
- All cached DNS entries  

✅ **Correct Answer:** The configured default DNS server

---

### Question 4
**Which DNS record resolves authoritative name servers?**  
- NS  
- AAAA  
- A  
- MX  

✅ **Correct Answer:** NS

---

## 15.5.3 Check Your Understanding — File Sharing Services

### Question 1
**How many connections does FTP require?**  
- 3  
- 1  
- 2  
- 4  

✅ **Correct Answer:** 2

---

### Question 2
**True or false? FTP supports push and pull transfers.**  

✅ **Correct Answer:** True

---

### Question 3
**Which ports are used by FTP? (Choose two.)**  
- 110  
- 20  
- 21  
- 25  

✅ **Correct Answers:** 20 and 21

---

### Question 4
**True or false? SMB is only supported on Microsoft OS.**  

✅ **Correct Answer:** False

---

## 15.6.2 Module Quiz — Application Layer

### Question 1
**Which device provides dynamic IPv4 addressing in a home network?**  
- A home router  
- A dedicated file server  
- A DNS server  
- An ISP DHCP server  

✅ **Correct Answer:** A home router

---

### Question 2
**What part of the URL represents the top-level domain?**  
- www  
- index  
- .com  
- http  

✅ **Correct Answer:** .com

---

### Question 3
**Two characteristics of the TCP/IP application layer:**  
- Responsibility for logical addressing  
- Responsibility for physical addressing  
- Creation and maintenance of dialogue  
- Closest to the end user  

✅ **Correct Answers:**  
- Creation and maintenance of dialogue  
- Closest to the end user

---

### Question 4
**What HTTP message type requests data?**  
- GET  
- POST  
- PUT  
- ACK  

✅ **Correct Answer:** GET

---



# CCNA ITN — Module 15: Application Layer
## Ultra-detailed study guide + practice bank (with answers & explanations)

> This is an **original study guide** written for revision and exam prep (not a verbatim copy of NetAcad text).  
> It covers **all topics 15.0 → 15.6** and includes an **extra-large practice question bank** with answers and explanations.  
> At the end, you’ll also find the **verbatim questions you shared in screenshots** (since you provided them).

---

## Table of Contents

- [Module 15 Overview](#module-15-overview)
- [Module Map](#module-map)
- [High-value memorization tables](#high-value-memorization-tables)
- [15.0 Introduction](#150-introduction)
- [15.1 Application, Presentation, and Session](#151-application-presentation-and-session)
  - [15.1.1 Application Layer](#1511-application-layer)
  - [15.1.2 Presentation Layer](#1512-presentation-layer)
  - [15.1.2 Session Layer](#1512-session-layer)
  - [15.1.3 TCP/IP Application Layer Protocols](#1513-tcpip-application-layer-protocols)
  - [15.1.4 Exam traps and quick checks](#1514-exam-traps-and-quick-checks)
- [15.2 Peer-to-Peer](#152-peer-to-peer)
  - [15.2.1 Client–Server model](#1521-clientserver-model)
  - [15.2.2 P2P networks](#1522-p2p-networks)
  - [15.2.3 P2P applications](#1523-p2p-applications)
  - [15.2.4 Common P2P applications](#1524-common-p2p-applications)
  - [15.2.5 Pros/cons and CCNA-style reasoning](#1525-proscons-and-ccna-style-reasoning)
- [15.3 Web and Email Protocols](#153-web-and-email-protocols)
  - [15.3.1 HTTP and HTML](#1531-http-and-html)
  - [15.3.2 HTTP vs HTTPS](#1532-http-vs-https)
  - [15.3.3 Email as a service](#1533-email-as-a-service)
  - [15.3.4 SMTP, POP3, IMAP](#1534-smtp-pop3-imap)
  - [15.3.5 “Which protocol?” decision guide](#1535-which-protocol-decision-guide)
- [15.4 IP Addressing Services](#154-ip-addressing-services)
  - [15.4.1 DNS](#1541-dns)
  - [15.4.2 DNS message format + record types](#1542-dns-message-format--record-types)
  - [15.4.3 DNS hierarchy + zones](#1543-dns-hierarchy--zones)
  - [15.4.4 nslookup (and friends)](#1544-nslookup-and-friends)
  - [15.4.5 Troubleshooting flow](#1545-troubleshooting-flow)
  - [15.4.6 DHCP](#1546-dhcp)
  - [15.4.7 DORA process (DHCPv4)](#1547-dora-process-dhcpv4)
  - [15.4.8 DNS lab study notes](#1548-dns-lab-study-notes)
  - [15.4.9 DHCPv6 note (CCNA expectation)](#1549-dhcpv6-note-ccna-expectation)
- [15.5 File Sharing Services](#155-file-sharing-services)
  - [15.5.1 FTP](#1551-ftp)
  - [15.5.2 SMB](#1552-smb)
  - [15.5.3 FTP vs SMB vs TFTP](#1553-ftp-vs-smb-vs-tftp)
- [15.6 Module Practice and Quiz](#156-module-practice-and-quiz)
  - [15.6.1 Summary](#1561-summary)
  - [15.6.2 What you must be able to do on the exam](#1562-what-you-must-be-able-to-do-on-the-exam)
- [Practice Question Bank (original)](#practice-question-bank-original)
  - [A. Rapid-fire “which protocol/port?” (30)](#a-rapid-fire-which-protocolport-30)
  - [B. Concepts and reasoning (25)](#b-concepts-and-reasoning-25)
  - [C. DNS/DHCP troubleshooting mini-cases (10)](#c-dnsdhcp-troubleshooting-mini-cases-10)
  - [D. Short-answer & commands (15)](#d-short-answer--commands-15)
  - [Answer Key + Explanations](#answer-key--explanations)
- [Your screenshot questions (verbatim) + answers](#your-screenshot-questions-verbatim--answers)

---

## Module 15 Overview

**Goal:** Understand what happens at the “top of the stack” when humans use network services (web, email, name resolution, addressing, file sharing).  
You should be able to answer questions like:
- *“Which protocol does the client use to retrieve email?”*
- *“Why is DHCP preferred on large networks?”*
- *“What does a DNS server actually return?”*
- *“What are the two FTP connections and why do we need them?”*
- *“Where does encryption happen in the OSI upper layers?”*

---

## Module Map

| Topic | What CCNA expects you to know |
|---|---|
| 15.1 Application/Presentation/Session | What each does, and how TCP/IP “Application” merges them |
| 15.2 Client–server vs P2P | Roles can change, why P2P scales differently, typical examples |
| 15.3 Web + Email | HTTP request/response, HTTPS adds security, SMTP/POP/IMAP roles |
| 15.4 DNS + DHCP | DNS names→IPs + hierarchy, DHCP automatic addressing, DORA steps |
| 15.5 FTP + SMB | FTP file transfer with 2 connections; SMB file/printer sharing |
| 15.6 Quiz/Review | Identify protocols/ports + reason through simple scenarios |

---

## High-value memorization tables

### Application-layer protocols (core CCNA list)

| Service | Protocol | Typical Transport/Port | What it *does* (plain English) |
|---|---:|---:|---|
| Web browsing | HTTP | TCP/80 (and often 8080) | Browser fetches web pages/resources |
| Secure web | HTTPS | TCP/443 (sometimes UDP/443 with QUIC in real life) | HTTP + encryption + server authentication |
| Send email | SMTP | TCP/25 | Client submits mail to server; servers relay mail |
| Retrieve email (download) | POP3 | TCP/110 | Client downloads email to local device (often removes from server by default) |
| Retrieve email (sync) | IMAP | TCP/143 | Client keeps mail on server, syncs folders/states across devices |
| Name resolution | DNS | UDP/53 (common), TCP/53 (some cases) | Translate names ↔ IPs |
| Auto IPv4 addressing | DHCP | UDP/67 server, UDP/68 client | Automatically assigns IP settings |
| File transfer | FTP | TCP/21 control, TCP/20 data (classic) | Upload/download files with separate control/data connections |
| Simple file transfer | TFTP | UDP/69 | Minimal overhead, no authentication, used for boot/IOS/limited cases |
| File/printer sharing | SMB | TCP/445 (common) | Access shared files/printers like they’re local |
| Network management | SNMP | UDP/161/162 | Monitor/manage devices (not “app use,” but still application layer) |

> CCNA-style thinking: if the question says **secure** web → HTTPS. If it says **retrieve email** → POP3/IMAP (not SMTP). If it says **automatic addressing** → DHCP. If it says **translate name** → DNS.

---

# 15.0 Introduction

## 15.0.1 Why should I take this module?
You learned that transport (TCP/UDP) moves data between hosts. **Before transport can do its job**, applications must:
- agree on *what the data means* (format),
- agree on *how a conversation is started/kept alive*,
- agree on *which service/protocol is used* (web, email, file transfer, etc.).

**Mental model:** The top layers are “human-friendly.” They make network services usable.

## 15.0.2 What will I learn to do?
Explain how application-layer protocols support end-user applications and services:
- Web, email, DNS, DHCP, file transfer/sharing, and P2P.

---

# 15.1 Application, Presentation, and Session

## 15.1.1 Application Layer
### What it is
- **Closest to the user**.
- Provides the **interface** between user applications and the network.

### What it does (exam-friendly wording)
- Defines **rules** for application processes to communicate over the network.
- Handles **service identification** (e.g., “this traffic is HTTP”).
- Defines message types and **request/response behavior** for many services.

### Key idea for TCP/IP vs OSI
- TCP/IP has a single **Application** layer that roughly combines OSI:
  - **Application + Presentation + Session**.

### CCNA trap
- If you see **protocols like HTTP/FTP/DNS**, they belong to **application layer**.
- If you see **TCP/UDP/IP**, those are lower layers (transport/internet).

---

## 15.1.2 Presentation Layer
### What it is
Presentation is the “data format” layer: making sure the receiving device can interpret the data.

### Three classic functions
1. **Format/translate data** (example: character encoding, file format standards)
2. **Compress/decompress** (reduce size; destination reverses it)
3. **Encrypt/decrypt** (confidentiality; destination decrypts)

### Real-world examples (helpful for memory)
- Images: JPG, PNG, GIF
- Video: MP4/MOV/MKV, MPEG
- Compression: ZIP, gzip
- Encryption: TLS (works above transport, conceptually “presentation-ish”)

> CCNA trick: Questions that mention **GIF/JPG/MKV** are about **presentation**, not application.

---

## 15.1.2 Session Layer
### What it is
Session is “conversation control” between applications.

### What it does
- Establishes and maintains **sessions** (dialogs) between applications.
- Controls **dialog state**: start, manage, and end a conversation.
- Can help with **restarting** disrupted sessions.

### Easy memory hook
- Presentation = “**how the data looks**”
- Session = “**keeping the conversation alive**”

---

## 15.1.3 TCP/IP Application Layer Protocols
### Compatibility rule
Communication only works if both ends use compatible protocols.
- Browser ↔ Web server (HTTP/HTTPS)
- Mail client ↔ Mail server (SMTP/POP/IMAP)
- Host ↔ DNS server (DNS)
- Host ↔ DHCP server (DHCP)

### What “protocol” means here
- Defines message formats, expected responses, error handling, and “who speaks first.”

### Key protocol roles
- **DNS**: name → IP
- **DHCP**: give IP settings automatically
- **SMTP**: send mail to server/relay
- **POP3/IMAP**: retrieve mail
- **HTTP/HTTPS**: web resources
- **FTP/TFTP**: file transfer
- **SMB**: shared files/printers

---

## 15.1.4 Exam traps and quick checks
- **GIF/JPG/MKV** are *formats* → Presentation layer concept.
- **“Maintain dialogue”** → Session layer concept.
- **“Protocols between programs on hosts”** → Application layer concept.
- TCP/IP “Application” includes OSI’s top 3 layers.

---

# 15.2 Peer-to-Peer

## 15.2.1 Client–Server model
### Roles
- **Client**: requests a service/resource.
- **Server**: provides a service/resource.

### What CCNA loves to test
- Clients “initiate” requests; servers “listen” for requests.
- Upload vs download:
  - **Upload**: client → server
  - **Download**: server → client

### Examples
- Email: client asks server for unread mail.
- Web: browser requests a page from web server.
- File server: user uploads/downloads files.

---

## 15.2.2 P2P networks
### What it is
No dedicated server required. Each peer can share resources directly with others.

### Key characteristics
- Each peer can be both **client and server**, depending on the request.
- Roles can change per transaction.

### Practical examples
- Home file sharing between two PCs
- Direct printer sharing
- Sharing a network connection (basic)  

### CCNA trap
P2P is **not** automatically “internet file sharing.” P2P can be a simple LAN with two PCs sharing a printer.

---

## 15.2.3 P2P applications
### What it is
A P2P **application** enables each host to function as both sender and receiver (client/server behavior in the app itself).

### Typical requirements
- UI + background service on each device
- Each device can accept inbound connections and make outbound connections

### Hybrid P2P
Some systems use:
- **central directory/index** (to locate resources)
- direct peer ↔ peer for actual file transfer

> CCNA angle: hybrid P2P is “central index, decentralized transfer.”

---

## 15.2.4 Common P2P applications
- BitTorrent, eDonkey, Direct Connect, Freenet (examples vary by curriculum version).

### Gnutella idea (conceptual)
- Peer discovery/search floods to multiple peers to find who has the resource.

### BitTorrent idea (conceptual)
- Files split into **pieces**
- Clients download pieces from multiple peers simultaneously (a **swarm**)
- “Tracker” helps coordinate who has which pieces

### Legal note
Many shared files are copyrighted; downloading/distributing without permission is illegal.

---

## 15.2.5 Pros/cons and CCNA-style reasoning
### Client–server pros
- Centralized control (easier security, backups, access control)
- Easier management

### Client–server cons
- Server becomes bottleneck/single point of failure (unless redundancy exists)

### P2P pros
- Simple for small setups
- No dedicated server cost

### P2P cons
- Harder security/control
- Scalability/management problems in large environments

---

# 15.3 Web and Email Protocols

## 15.3.1 HTTP and HTML
### What happens when you type a URL
1. Browser parses the URL (protocol, hostname, resource path)
2. Browser needs an IP → uses **DNS**
3. Browser establishes a transport session (usually TCP) to server
4. Browser sends an HTTP request (often **GET**)
5. Server responds with status + data (HTML + resources)
6. Browser renders the page

### URL anatomy (must know)
Example: `http://www.cisco.com/index.html`
- `http` = protocol
- `www.cisco.com` = hostname (needs DNS)
- `/index.html` = resource path

### HTTP request/response concept
- Client sends **request**
- Server sends **response**
- HTTP is stateless by design (state handled via cookies/sessions at app level)

### HTTP message types (high frequency)
- **GET**: request data/resource
- **POST**: submit data to server (forms, uploads, etc.)
- **PUT**: upload/replace resource (less common in basic CCNA questions)

---

## 15.3.2 HTTP vs HTTPS
### HTTP (not secure)
- Data can be read/modified in transit if intercepted (plaintext).

### HTTPS (secure)
- Adds encryption (TLS) + server authentication (certificates).
- Goal: confidentiality + integrity + authenticity (for the website identity).

> CCNA pattern: “secure web browsing” → HTTPS/443.

---

## 15.3.3 Email as a service
Email is store-and-forward:
- Client does not deliver directly to another client.
- Mail server accepts and relays messages to other mail servers.
- Recipient client retrieves the message from their mail server.

Email “roles”:
- **SMTP**: sending/relaying
- **POP3/IMAP**: retrieving

---

## 15.3.4 SMTP, POP3, IMAP
### SMTP (send)
- Client submits mail to server.
- Servers relay mail server-to-server.
- Typical port: TCP/25.

### POP3 (retrieve by download)
- Client downloads messages.
- Often removes from server by default (behavior depends on configuration).
- Typical port: TCP/110.

### IMAP (retrieve by sync)
- Mail stays on server.
- Multiple devices can sync folders/status.
- Typical port: TCP/143.

### POP vs IMAP (exam shortcuts)
- **POP3** = download to device (often “offline” feel)
- **IMAP** = keep on server + sync across devices

---

## 15.3.5 “Which protocol?” decision guide
- **Send email** → SMTP
- **Retrieve email** → POP3 or IMAP
- **Web page** → HTTP or HTTPS
- **Secure web** → HTTPS
- **Upload web form/data** → POST
- **Request web page** → GET

---

# 15.4 IP Addressing Services

## 15.4.1 DNS
### Why DNS exists
Humans remember names better than numeric IPs.
DNS maps:
- name → IP (forward lookup)
- IP → name (reverse lookup, if configured)

### High-level resolution steps (conceptual)
1. User enters hostname (FQDN) in browser.
2. Client sends DNS query to configured DNS server.
3. DNS server finds IP (local cache/records or by querying other DNS servers).
4. DNS returns answer to client.
5. Client connects to returned IP address.

### Caching (important for troubleshooting)
- Clients cache DNS answers for a time (TTL-based).
- DNS servers also cache responses to speed up resolution.

---

## 15.4.2 DNS message format + record types
### Record types you must know
- **A**: hostname → IPv4
- **AAAA**: hostname → IPv6
- **NS**: authoritative name servers for a domain
- **MX**: mail exchange servers for domain

### DNS message sections (CCNA-level)
- **Question**: what the client asks
- **Answer**: the records answering it
- **Authority**: info pointing to authoritative servers
- **Additional**: extra helpful records (like related servers)

---

## 15.4.3 DNS hierarchy + zones
DNS is hierarchical:
- Root (.) at top
- TLD (.com, .org, etc.)
- Second-level (example.com)
- Subdomains (www.example.com, mail.example.com)

**Zones**:
- A DNS server is authoritative for a particular zone/domain.
- If it’s not authoritative, it may forward/recursively query other servers (depending on configuration).

---

## 15.4.4 nslookup (and friends)
### nslookup (what it’s for)
- Manual DNS queries (test resolution).
- Identify which DNS server is being used.
- Check A/AAAA/MX/NS records (depending on query usage).

### Typical outputs you must interpret
- Default server name
- Default server IP address
- Resolved IP addresses for a host

### Related Windows commands (helpful)
- `ipconfig /all` → shows configured DNS servers
- `ipconfig /displaydns` → shows local cache
- `ipconfig /flushdns` → clears cache
- `ping hostname` → tests name resolution + reachability
- `tracert hostname` → routing path (not DNS, but used in troubleshooting)

---

## 15.4.5 Troubleshooting flow
If “website won’t load”:
1. **Check DNS resolution**: `nslookup www.site.com`
2. If fails: verify DNS server settings (`ipconfig /all`)
3. Try another DNS server (if allowed)
4. Check reachability to resolved IP (ping/tracert)
5. Check HTTP/HTTPS port/service availability

If “DNS works but wrong IP”:
- Could be cached stale record (flush cache, wait TTL, check authoritative records)

---

## 15.4.6 DHCP
### Why DHCP exists
Static addressing on large networks is slow and error-prone.
DHCP automates:
- IP address
- subnet mask
- default gateway
- DNS server (and others)

### Leasing concept
- Address is assigned for a **lease time**
- When lease expires, address can return to pool and be reused

> CCNA idea: DHCP is preferred in large networks because it’s **efficient and centralized**.

---

## 15.4.7 DORA process (DHCPv4)
Four-message exchange:
1. **Discover**: client broadcast looking for DHCP server
2. **Offer**: server offers an address/config
3. **Request**: client requests the offered address
4. **Ack**: server acknowledges and finalizes lease

### Common CCNA tips
- Discover/Request are typically **broadcast** from client on a LAN.
- DHCP is **UDP** (not TCP).

---

## 15.4.8 DNS lab study notes
What to learn from the lab (exam-relevant):
- DNS is used when you type a URL.
- Large orgs may resolve to different IPs due to load balancing / CDNs.
- nslookup helps reveal record types and the DNS server used.
- MX records identify mail servers and preference values (lower = higher priority).

---

## 15.4.9 DHCPv6 note (CCNA expectation)
- DHCPv6 exists, but on IPv6 networks the **default gateway** is usually learned via **Router Advertisements (RA)**, not from DHCPv6.
- CCNA often tests the idea: “DHCPv6 does not provide the default gateway.”

---

# 15.5 File Sharing Services

## 15.5.1 FTP
FTP is a classic file transfer protocol (client/server).

### Two connections (this is the #1 FTP concept)
- **Control connection**: TCP/21 (commands, login, control messages)
- **Data connection**: TCP/20 (classic) or dynamic ports depending on mode

**Why 2 connections?**
- Control channel stays up for commands.
- Data channel is used to actually move file contents.

### Push vs Pull (exam favorite)
- Pull = download (client pulls from server)
- Push = upload (client pushes to server)
FTP supports both.

### Security note
Basic FTP is not encrypted (credentials can be exposed). (CCNA mentions this conceptually.)

---

## 15.5.2 SMB
SMB provides file/printer sharing on a network.

### What SMB lets you do
- Browse and access shared folders (network drives)
- Access printers and other shared resources
- Access remote resources as if they were local

### Cross-platform detail
- Windows uses SMB natively
- Linux/UNIX often use **Samba** to interoperate
- macOS supports SMB as well

### SMB vs FTP (concept)
- SMB feels like “open a shared folder” (persistent access)
- FTP is more like “transfer a file” (copy to/from)

---

## 15.5.3 FTP vs SMB vs TFTP
| Protocol | Best for | Transport | Security | Typical use |
|---|---|---:|---|---|
| FTP | file transfer with authentication | TCP | weak in plain FTP | upload/download files |
| SMB | file/printer sharing | TCP | depends on environment | shared folders/printers |
| TFTP | lightweight file transfer | UDP | no authentication | simple device boot/updates |

---

# 15.6 Module Practice and Quiz

## 15.6.1 Summary
If you can do these, you’re good:
- Map service → protocol → port (HTTP/HTTPS/SMTP/POP3/IMAP/DNS/DHCP/FTP/SMB)
- Explain what each OSI upper layer does
- Describe DNS resolution steps and record types
- Describe DHCP DORA messages
- Explain why FTP uses two connections
- Decide POP3 vs IMAP based on scenario

## 15.6.2 What you must be able to do on the exam
- Identify protocols from scenarios
- Interpret basic nslookup output
- Pick the right statement about HTTP/FTP/DHCP/DNS
- Identify client/server roles in a scenario
- Identify why DHCP scales better than static addressing

---

# Practice Question Bank (original)

> These questions are **original** (not copied from NetAcad).  
> Use them like a mini mock exam.  
> Each has an answer + explanation in the Answer Key section.

---

## A. Rapid-fire “which protocol/port?” (30)

**A1.** A user types `https://example.com`. Which protocol and default port are used?  
A) HTTP/80 B) HTTPS/443 C) FTP/21 D) DNS/53

**A2.** A mail client sends an email message to its mail server. Which protocol?  
A) POP3 B) IMAP C) SMTP D) SNMP

**A3.** A mail client synchronizes mailbox folders across multiple devices. Which protocol?  
A) IMAP B) POP3 C) SMTP D) FTP

**A4.** A host requests an IPv4 address automatically when joining a network. Which protocol?  
A) DNS B) DHCP C) ICMP D) HTTP

**A5.** A client resolves `www.cisco.com` to an IP address. Which protocol?  
A) DNS B) DHCP C) FTP D) SMTP

**A6.** Which port is commonly used by DNS?  
A) 25 B) 53 C) 67 D) 110

**A7.** Which ports are associated with DHCP (server/client)?  
A) 53/53 B) 67/68 C) 20/21 D) 110/143

**A8.** Which protocol is used for file sharing and printer sharing on many LANs?  
A) SMB B) FTP C) HTTP D) POP3

**A9.** Which protocol typically uses TCP port 25?  
A) POP3 B) IMAP C) SMTP D) DNS

**A10.** Which protocol typically uses TCP port 110?  
A) POP3 B) IMAP C) SMTP D) DHCP

**A11.** Which protocol typically uses TCP port 143?  
A) POP3 B) IMAP C) SMTP D) DNS

**A12.** Which protocol uses TCP port 21 for control?  
A) SMB B) FTP C) HTTP D) TFTP

**A13.** Which protocol is “lightweight” and uses UDP/69?  
A) FTP B) TFTP C) HTTP D) IMAP

**A14.** Which record type maps a hostname to an IPv6 address?  
A) A B) AAAA C) MX D) NS

**A15.** Which record type identifies mail servers for a domain?  
A) NS B) A C) MX D) AAAA

**A16.** Which record type identifies authoritative name servers?  
A) NS B) A C) MX D) AAAA

**A17.** A browser requests a web page resource. Which HTTP method is most likely?  
A) POST B) PUT C) GET D) ACK

**A18.** A user submits a login form to a web server. Which method is most likely?  
A) POST B) GET C) ACK D) NSLOOKUP

**A19.** A network admin monitors devices via a management protocol. Which one fits?  
A) SMTP B) DNS C) SNMP D) FTP

**A20.** A user accesses a shared folder over the LAN like a local drive. Which protocol fits best?  
A) SMB B) FTP C) HTTP D) POP3

**A21.** Which protocol is *not* an application-layer protocol?  
A) HTTP B) TCP C) DNS D) SMTP

**A22.** Which layer is responsible for encryption/decryption (conceptually)?  
A) Presentation B) Transport C) Network D) Physical

**A23.** Which layer is responsible for maintaining dialogs (conceptually)?  
A) Session B) Presentation C) Network D) Data Link

**A24.** Which layer is closest to the end user?  
A) Application B) Transport C) Network D) Physical

**A25.** Which protocol is used to retrieve email from a server to a client?  
A) SMTP B) POP3 C) HTTP D) SNMP

**A26.** Which protocol allows retrieving email but keeps messages on the server for synchronization?  
A) POP3 B) IMAP C) SMTP D) FTP

**A27.** DNS most commonly uses which transport?  
A) TCP B) UDP C) ICMP D) ARP

**A28.** FTP provides reliability because it uses:  
A) UDP B) TCP C) ICMP D) ARP

**A29.** DHCP uses:  
A) TCP B) UDP C) ICMP D) IPsec

**A30.** A domain `example.com` changes its web server IP but users still reach it by name. Why?  
A) MAC learning B) DNS mapping updated C) ARP cache D) DHCP reservation

---

## B. Concepts and reasoning (25)

**B1.** Explain the difference between **client–server** and **P2P** in one sentence each.  

**B2.** A laptop uploads a document to a publisher’s file server. In that interaction, the laptop is the:  
A) Server B) Client C) Master D) Slave

**B3.** Why does DHCP scale better than static addressing on large networks? (choose best)  
A) Fewer DNS queries B) Central management + fewer manual errors C) Uses TCP reliability D) Prevents copyrighted files

**B4.** Why does FTP use two connections?  
A) It can’t use TCP B) Separate control and data C) It’s peer-to-peer D) It replaces DNS

**B5.** A company wants employees to access the same mailbox from phone + laptop with synced folders. Pick best protocol and why.  

**B6.** What’s the difference between DNS **A** and **AAAA** records?  

**B7.** What is the purpose of an **MX** record?  

**B8.** What is the purpose of an **NS** record?  

**B9.** What is the “Question” section in a DNS message used for?  

**B10.** What is the “Answer” section in a DNS message used for?  

**B11.** A user can resolve a name but cannot reach the site. Name 2 likely causes **beyond DNS**.  

**B12.** HTTP is described as “stateless.” What does that mean at a basic level?  

**B13.** Give one example of a **presentation layer** function and one of a **session layer** function.  

**B14.** A host uses `nslookup` and sees a different IP than yesterday for the same name. Give two reasons this can happen.  

**B15.** In DHCP DORA, which messages are typically broadcast and why?  

**B16.** When does a DHCP address return to the pool?  

**B17.** Compare POP3 and IMAP in terms of where mail is stored and multi-device use.  

**B18.** What does SMB provide that feels different from FTP to end users?  

**B19.** What is a “hybrid P2P” design?  

**B20.** Why can P2P be harder to secure/manage in enterprises? (2 reasons)  

**B21.** True/False: DNS always uses TCP.  

**B22.** True/False: HTTPS authenticates the web server identity (via certificates).  

**B23.** True/False: SMTP is used to retrieve email messages from a mail server.  

**B24.** True/False: The OSI presentation layer can be associated with file format standards like JPG/PNG.  

**B25.** True/False: DHCP uses a reliable transport protocol.

---

## C. DNS/DHCP troubleshooting mini-cases (10)

**C1.** `ping www.example.com` fails with “could not find host”. What do you check first?  

**C2.** `nslookup www.example.com` returns “server can’t find.” What are two possible root causes?  

**C3.** `nslookup` works, returns an IP, but web still fails. Name two next checks.  

**C4.** A host gets `169.254.x.x` on IPv4. What does that suggest?  

**C5.** Clients are not getting addresses; DHCP server is up. What network device feature might block DHCP broadcasts?  

**C6.** A user can access the web by IP but not by name. What service is broken?  

**C7.** DNS works for some domains but not others. Name two possibilities.  

**C8.** A user changed DNS servers and now resolution is slow. What might explain that?  

**C9.** DNS changes were made but clients still resolve to old IP. What action can help immediately?  

**C10.** If DHCP is preferred in large networks, why might servers still use static addressing? (2 reasons)

---

## D. Short-answer & commands (15)

**D1.** Write the DHCPv4 DORA sequence in order.  

**D2.** Which command shows the DNS servers configured on Windows?  

**D3.** Which command displays the DNS cache on Windows?  

**D4.** Which command clears the DNS cache on Windows?  

**D5.** What does `nslookup` show immediately when you start it (without arguments)?  

**D6.** What does an HTTP status code “200” generally mean?  

**D7.** Name two HTTP methods and what they do.  

**D8.** Explain “upload” vs “download” using client/server direction.  

**D9.** Name the two FTP connections and their purpose.  

**D10.** Give one reason to prefer IMAP over POP3.  

**D11.** Which DNS record type is used for IPv6?  

**D12.** Which DNS record type identifies mail servers?  

**D13.** Which protocol is used to send email from client to server?  

**D14.** Which protocol is used to retrieve email while keeping messages on server?  

**D15.** Which protocol is used for file/printer sharing on Microsoft networks (and via Samba on Linux)?  

---

# Answer Key + Explanations

## A. Rapid-fire answers
A1 **B** (HTTPS/443) — secure web  
A2 **C** (SMTP) — sending mail  
A3 **A** (IMAP) — sync mailbox across devices  
A4 **B** (DHCP) — automatic IPv4 addressing  
A5 **A** (DNS) — name to IP  
A6 **B** (53) — DNS  
A7 **B** (67/68) — DHCP server/client  
A8 **A** (SMB) — file/printer sharing  
A9 **C** (SMTP/25)  
A10 **A** (POP3/110)  
A11 **B** (IMAP/143)  
A12 **B** (FTP/21 control)  
A13 **B** (TFTP/69)  
A14 **B** (AAAA → IPv6)  
A15 **C** (MX → mail server)  
A16 **A** (NS → authoritative servers)  
A17 **C** (GET) — request resource  
A18 **A** (POST) — submit data  
A19 **C** (SNMP) — management  
A20 **A** (SMB) — shared folder access  
A21 **B** (TCP is transport layer)  
A22 **A** (Presentation) — encrypt/decrypt concept  
A23 **A** (Session) — maintain dialogs  
A24 **A** (Application) — closest to user  
A25 **B** (POP3 retrieves mail)  
A26 **B** (IMAP syncs and keeps mail on server)  
A27 **B** (UDP is common for DNS)  
A28 **B** (TCP provides reliability)  
A29 **B** (DHCP uses UDP)  
A30 **B** (DNS mapping updates keep name constant)

## B. Concepts answers
B1 Client–server: a client requests resources from a dedicated server. P2P: peers share resources directly and can act as client and server.  
B2 **B** Client — it requests upload service from file server.  
B3 **B** Central management + fewer manual errors.  
B4 **B** Separate control and data channels.  
B5 IMAP — it syncs messages and folders across devices while mail stays on server.  
B6 A = hostname→IPv4, AAAA = hostname→IPv6.  
B7 MX points to mail servers for domain (with preference).  
B8 NS lists authoritative DNS servers for domain.  
B9 “Question” = what name/type client is asking for.  
B10 “Answer” = records that resolve the question (e.g., A/AAAA).  
B11 Examples: web server down; firewall/ACL blocking; wrong gateway/routing; HTTPS cert issues; application issue.  
B12 Stateless: each request is independent; server doesn’t inherently remember previous requests without cookies/sessions.  
B13 Presentation: encryption/compression/format. Session: keep dialog active/restart.  
B14 Reasons: load balancing/CDN; DNS record changed; different resolver; cache/TTL differences.  
B15 Discover and Request often broadcast so client can find server and request address without having an IP yet.  
B16 When lease expires (or released) it can return to pool.  
B17 POP3 = download to device; IMAP = sync with server mailbox.  
B18 SMB offers browsing/working with shared folders like local storage; FTP is transfer-centric.  
B19 Hybrid P2P: central index/directory + direct peer transfers.  
B20 Harder: no central control; inconsistent security; many endpoints hosting resources; auditing difficult.  
B21 **False** — UDP common; TCP used sometimes.  
B22 **True** — certificates authenticate server identity.  
B23 **False** — SMTP is send/relay, not retrieve.  
B24 **True** — file formats are presentation concept.  
B25 **False** — DHCP uses UDP (not reliable TCP).

## C. Troubleshooting answers
C1 Check DNS: `nslookup`, DNS server config (`ipconfig /all`).  
C2 Wrong DNS server; DNS server down; record missing; blocked UDP/53; typo.  
C3 Try `ping` IP; check firewall/proxy; check HTTP/HTTPS port; tracert route.  
C4 APIPA — DHCP failed/no lease.  
C5 DHCP snooping/ACL or missing DHCP relay (on routers) can block; broadcast domain issues.  
C6 DNS.  
C7 Split-horizon DNS; forwarding issues; specific zone not reachable; caching/TTL issues.  
C8 New DNS server farther/slow; packet loss; wrong forwarders; latency.  
C9 Flush DNS cache (`ipconfig /flushdns`) or wait TTL.  
C10 Servers need static for predictability; DNS records; services; reservations; troubleshooting; security policy.

## D. Short answers
D1 Discover → Offer → Request → Ack.  
D2 `ipconfig /all`  
D3 `ipconfig /displaydns`  
D4 `ipconfig /flushdns`  
D5 Default DNS server and its address.  
D6 OK/success (resource returned).  
D7 GET (request), POST (submit).  
D8 Upload: client→server; Download: server→client.  
D9 Control (TCP/21) for commands; Data (TCP/20 classic) for file transfer.  
D10 Multi-device sync; mail stays on server; folder support.  
D11 AAAA.  
D12 MX.  
D13 SMTP.  
D14 IMAP.  
D15 SMB.

---

# Your screenshot questions (verbatim) + answers

> These are transcribed from the screenshots you shared in this chat.

## 15.1.4 Check Your Understanding — Application, Session, Presentation (Q1–Q5)
1) OSI layer concerned with protocols exchanging data between programs on hosts → **Application**  
2) MKV, GIF, JPG are associated with which OSI layer → **Presentation**  
3) Three OSI layers define same functions as TCP/IP application layer (choose three) → **Application, Presentation, Session**  
4) Two protocols that belong in OSI application layer (choose two) → **DNS, SMTP**  
5) Function of OSI session layer → **Exchange of information to initiate dialog between peers**

## 15.2.5 Check Your Understanding — Peer-to-Peer (Q1–Q4)
1) P2P model requires dedicated server for data access → **False**  
2) In P2P, every peer can function as both client and server → **True**  
3) P2P application that shares pieces of many files simultaneously → **BitTorrent**  
4) Feature of Gnutella protocol → **Users can share whole files with other users**

## 15.3.5 Check Your Understanding — Web and Email Protocols (Q1–Q5)
1) Message type used when uploading data files to a web server → **POST**  
2) Protocol used by browser to establish connection to web server → **HTTP**  
3) Protocol used by client to send email to mail server → **SMTP**  
4) Feature of IMAP → **Downloads a copy leaving the original on the server**  
5) HTTP is a secure protocol → **False**

## 15.4.9 Check Your Understanding — IP Addressing Services (Q1–Q4)
1) DNS record type used to resolve IPv6 addresses → **AAAA**  
2) DNS server sends failure if request outside its zone → **False**  
3) Displayed by nslookup utility → **Configured default DNS server**  
4) DNS record type resolves authoritative name servers → **NS**

## 15.5.3 Check Your Understanding — File Sharing Services (Q1–Q4)
1) How many connections does FTP require → **2**  
2) FTP supports push and pull transfers → **True**  
3) Ports used by FTP (choose two) → **20 and 21**  
4) SMB is only supported on Microsoft OS → **False**

## 15.6.2 Module Quiz — Application Layer (from your screenshots so far)
> You provided screenshots for Q5–Q11. Q12–Q15 were not included in the images I received.

Q1) Device provides dynamic IPv4 addressing in a home network → **Home router**  
Q2) Part of URL representing top-level domain → **.com**  
Q3) Two characteristics of TCP/IP application layer → **Creation/maintenance of dialogue; Closest to the end user**  
Q4) HTTP message type requests data → **GET**  

Q5) Protocol used to transfer messages from an email server to an email client → **POP3**  
Q6) Application layer protocol for file-sharing and print services to Microsoft applications → **SMB**  
Q7) Three protocols/standards used at application layer of TCP/IP model (choose three) → **GIF, MPEG, HTTP**  
Q8) Why is DHCP for IPv4 preferred on large networks → **More efficient management than static assignment**  
Q9) Author uploads document from personal computer to file server. PC role → **Client**  
Q10) True statement about FTP → **Client can download or upload data to the server**  
Q11) Wireless host needs to request an IPv4 address. Protocol → **DHCP**

---

## Next step (if you want)
If you upload the last screenshot(s) for **15.6.2 Q12–Q15**, I’ll append them here (verbatim) and keep the same structure.
