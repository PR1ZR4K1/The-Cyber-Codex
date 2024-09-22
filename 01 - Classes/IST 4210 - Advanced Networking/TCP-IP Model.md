2024/08/31 17:00
Status: #idea
Tags: [[TCP-IP Model]], [[Networking Models]]

# TCP/IP Model Notes

## 1. Introduction

The TCP/IP (Transmission Control Protocol/Internet Protocol) model is a concise version of the OSI model. It describes the standards and protocols used in internet communication.

## 2. Layers of the TCP/IP Model

The TCP/IP model consists of four layers:

1. Data Link Layer
2. Internet Layer
3. Transport Layer
4. Application Layer

### 2.1 Network Access Layer

- Equivalent to the Physical and Data Link layers in the OSI model
- Responsible for physical addressing and data transmission over the network medium

## Key Protocols:

- Ethernet
- Wi-Fi (IEEE 802.11)
- PPP (Point-to-Point Protocol)

### 2.2 Internet Layer

- Equivalent to the Network layer in the OSI model
- Handles logical addressing and routing of data packets

## Key Protocols:

- IP (Internet Protocol)
    - IPv4
    - IPv6
- ICMP (Internet Control Message Protocol)
- ARP (Address Resolution Protocol)

### 2.3 Transport Layer

- Equivalent to the Transport layer in the OSI model
- Responsible for end-to-end communication and data flow control

## Key Protocols:

- TCP (Transmission Control Protocol)
    - Connection-oriented
    - Reliable delivery
    - Flow control
    - Error checking
- UDP (User Datagram Protocol)
    - Connectionless
    - Faster but less reliable than TCP

### 2.4 Application Layer

- Combines the Session, Presentation, and Application layers of the OSI model
- Provides network services directly to end-users or applications

## Key Protocols:

- HTTP/HTTPS (Hypertext Transfer Protocol)
- FTP (File Transfer Protocol)
- SMTP (Simple Mail Transfer Protocol)
- DNS (Domain Name System)
- SSH (Secure Shell)

## 3. TCP/IP Model vs OSI Model

|TCP/IP Model|OSI Model|
|---|---|
|Application|Application|
||Presentation|
||Session|
|Transport|Transport|
|Internet|Network|
|Network Access|Data Link|
||Physical|

## 4. Mathematical Concepts in TCP/IP

### 4.1 IP Addressing

IPv4 address space: $2^{32} \approx 4.3$ billion addresses

IPv6 address space: $2^{128}$ addresses

### 4.2 Subnetting

Subnet mask calculation:

$\text{Number of available host addresses} = 2^n - 2$

Where $n$ is the number of host bits.

### 4.3 Checksum Calculation

TCP checksum algorithm (simplified):

$\text{Checksum} = \neg (\sum_{i=1}^{n} \text{data}_i)$

Where $\neg$ represents the one's complement.

## 5. Key Formulas and Equations

### 5.1 RTT (Round Trip Time) Estimation

Estimated RTT: $\text{ERTT}_\text{new} = (1-\alpha) \times \text{ERTT}_\text{old} + \alpha \times \text{RTT}_\text{sample}$

Where $\alpha$ is typically 0.125.

### 5.2 Throughput

$\text{Throughput} = \frac{\text{Window Size}}{\text{RTT}}$

### 5.3 Congestion Window (CWND) Growth

Slow Start: $\text{CWND}_\text{new} = \text{CWND}_\text{old} + \text{MSS}$

Congestion Avoidance: $\text{CWND}_\text{new} = \text{CWND}_\text{old} + \frac{\text{MSS}^2}{\text{CWND}_\text{old}}$

Where MSS is the Maximum Segment Size.







---
# References
