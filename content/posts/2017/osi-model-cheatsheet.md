+++
date = '2017-04-21T23:17:51-06:00'
draft = false
title = 'OSI Model Cheatsheet'
type = 'post'
tags = ["tech", "beginner-fundamentals", "enterprise-it", "cheatsheet", "networking", "cisco"]
+++
# OSI Model Cheatsheet

The OSI (Open Systems Interconnection) Model is a seven-layer framework for standardizing network communication.

---

## 1. **Application Layer (Layer 7)**
- **Purpose**: Provides network services directly to user applications.
- **Functions**:
  - Enables interaction between software applications and the network.
  - Handles protocols for user interfaces.
- **Examples**:
  - HTTP, HTTPS (Web Browsing)
  - FTP, SFTP (File Transfers)
  - SMTP, IMAP, POP3 (Email)
  - SNMP (Network Management)
  - Telnet, SSH (Remote Access)

---

## 2. **Presentation Layer (Layer 6)**
- **Purpose**: Ensures data is in a readable format.
- **Functions**:
  - Data translation (e.g., ASCII to EBCDIC).
  - Data encryption and decryption.
  - Data compression and decompression.
- **Examples**:
  - SSL/TLS (Encryption)
  - JPEG, PNG (Image Compression Formats)

---

## 3. **Session Layer (Layer 5)**
- **Purpose**: Manages communication sessions between applications.
- **Functions**:
  - Session establishment, maintenance, and termination.
  - Synchronization (e.g., checkpoints in a data stream).
- **Examples**:
  - NetBIOS
  - RPC (Remote Procedure Call)

---

## 4. **Transport Layer (Layer 4)**
- **Purpose**: Ensures reliable or fast delivery of data.
- **Functions**:
  - End-to-end communication.
  - Error detection and correction.
  - Flow control and segmentation.
- **Protocols**:
  - TCP (Reliable, connection-oriented)
  - UDP (Fast, connectionless)

---

## 5. **Network Layer (Layer 3)**
- **Purpose**: Determines data paths and logical addressing.
- **Functions**:
  - Routing and forwarding of packets.
  - Logical addressing (IP addresses).
  - Packet fragmentation and reassembly.
- **Protocols**:
  - IPv4, IPv6 (Logical Addressing)
  - ICMP (Diagnostics)
  - RIP, OSPF, BGP (Routing Protocols)

---

## 6. **Data Link Layer (Layer 2)**
- **Purpose**: Manages node-to-node communication over the physical medium.
- **Functions**:
  - Framing of data packets.
  - Error detection and correction (not recovery).
  - Physical addressing (MAC).
- **Examples**:
  - Ethernet
  - Wi-Fi (802.11)
  - PPP (Point-to-Point Protocol)
  - VLAN Tagging (802.1Q)

---

## 7. **Physical Layer (Layer 1)**
- **Purpose**: Transfers raw binary data over physical media.
- **Functions**:
  - Transmission of bits (1s and 0s).
  - Defines hardware specifications.
  - Determines data encoding and signaling.
- **Examples**:
  - Cables (Ethernet, Fiber Optic, Coaxial)
  - Connectors (RJ45)
  - Radio Frequencies (Wi-Fi, Bluetooth)
  - Hubs, Repeaters

---

## OSI Model Summary Table
| **Layer**         | **Key Function**               | **Examples**                    |
|--------------------|--------------------------------|----------------------------------|
| Application (L7)   | User interface, application   | HTTP, FTP, SMTP                 |
| Presentation (L6)  | Data formatting and encryption| SSL/TLS, JPEG, PNG              |
| Session (L5)       | Session management            | RPC, NetBIOS                    |
| Transport (L4)     | Reliable delivery             | TCP, UDP                        |
| Network (L3)       | Logical addressing, routing   | IPv4, IPv6, OSPF, BGP           |
| Data Link (L2)     | MAC addressing, framing       | Ethernet, Wi-Fi, VLAN           |
| Physical (L1)      | Signal transmission           | Cables, RF, Connectors          |

---

## OSI Model Visualization

[ Layer 7: Application (User Interaction) ] <br />
↕ <br />
[ Layer 6: Presentation (Formatting, Encryption) ]<br />
↕<br />
[ Layer 5: Session (Session Management) ]<br />
↕<br />
[ Layer 4: Transport (TCP/UDP) ]<br />
↕<br />
[ Layer 3: Network (Routing, IP) ]<br />
↕<br />
[ Layer 2: Data Link (MAC, Framing) ]<br />
↕<br />
[ Layer 1: Physical (Signals, Media) ]