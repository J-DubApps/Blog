+++
date = '2017-04-21T23:17:51-06:00'
draft = false
title = 'TCP Model Cheatsheet'
type = 'post'
tags = ["tech", "beginner-fundamentals", "enterprise-it", "cheatsheet", "networking", "cisco"]
+++
# TCP/IP Model Cheatsheet

The TCP/IP model is a concise, four-layer framework used to understand and implement network communication.

---

## 1. **Application Layer**
- **Purpose**: Interfaces between the network and user applications.
- **Functions**:
  - Provides network services to user applications.
  - Handles high-level protocols.
- **Protocols**:
  - HTTP, HTTPS (Web Browsing)
  - SMTP, IMAP, POP3 (Email)
  - FTP, SFTP, TFTP (File Transfers)
  - SNMP (Network Management)
  - DNS (Domain Name Resolution)
  - Telnet, SSH (Remote Access)

---

## 2. **Transport Layer**
- **Purpose**: Ensures reliable communication between devices.
- **Functions**:
  - End-to-end communication.
  - Flow control and error handling.
  - Multiplexing and session management.
- **Protocols**:
  - TCP (Transmission Control Protocol): Reliable, connection-oriented.
  - UDP (User Datagram Protocol): Fast, connectionless.

---

## 3. **Internet Layer**
- **Purpose**: Handles logical addressing and routing.
- **Functions**:
  - IP addressing.
  - Routing and forwarding of packets.
  - Packet fragmentation and reassembly.
- **Protocols**:
  - IPv4, IPv6 (Addressing and Routing)
  - ICMP (Error Reporting and Diagnostics)
  - ARP (Address Resolution Protocol)
  - IGMP (Multicast Management)

---

## 4. **Network Access Layer**
- **Purpose**: Interfaces with physical network hardware.
- **Functions**:
  - Encapsulation of IP packets into frames.
  - Physical addressing (MAC).
  - Access to physical transmission medium.
- **Technologies/Protocols**:
  - Ethernet, Wi-Fi (LAN Technologies)
  - PPP (Point-to-Point Protocol)
  - Frame Relay, ATM (WAN Technologies)
  - MAC Addressing

---

## TCP/IP Model vs OSI Model Comparison
| **TCP/IP Layer**        | **Corresponding OSI Layers**          |
|--------------------------|---------------------------------------|
| Application              | Application, Presentation, Session   |
| Transport                | Transport                            |
| Internet                 | Network                              |
| Network Access           | Data Link, Physical                 |

---

## Key Characteristics
- **Layer Independence**: Each layer operates independently while passing data to/from adjacent layers.
- **Protocol Suite**: Flexible and adaptable for various applications.
- **Connection Types**:
  - TCP: Ensures reliability through acknowledgments and retransmissions.
  - UDP: Optimized for speed, no error recovery.

---

## Visualization

[ User Data/Application ]<br />
↕<br />
[ Transport Layer (TCP/UDP) ]<br />
↕<br />
[ Internet Layer (IP/ICMP/ARP) ]<br />
↕<br />
[ Network Access Layer (Ethernet/Wi-Fi) ]