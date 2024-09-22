2024/08/31 17:20
Status: #idea
Tags: [[Networking Models]]

# Opens Systems Interconnection Model

## Mnemonics

	All
	People
	Seem
	To
	Need
	Data
	Processing

	Away
	Pizza
	Sausage
	Throw
	Not
	Do
	Please

## 1. Introduction

The OSI (Open Systems Interconnection) model is a conceptual framework used to understand network interactions in seven distinct layers. Developed by the International Organization for Standardization (ISO), it provides a standard for different computer systems to communicate with each other.

## 2. The Seven Layers of the OSI Model

### 2.1 Physical Layer (Layer 1)

- Deals with the physical connection between devices
- Transmits raw bit stream over the physical medium

## Key Concepts:

- Bit synchronization
- Bit rate control
- Physical topologies
- Transmission mode (simplex, half-duplex, full-duplex)

## Examples:

- Ethernet cables
- Fiber optic cables
- Wi-Fi radio waves

### 2.2 Data Link Layer (Layer 2)

- Provides node-to-node data transfer
- Detects and possibly corrects errors from the Physical layer

## Key Concepts:

- Framing
- Physical addressing (MAC)
- Error control
- Flow control

## Sublayers:

1. Logical Link Control (LLC)
2. Media Access Control (MAC)

## Protocols:

- Ethernet
- PPP (Point-to-Point Protocol)
- IEEE 802.11 (Wi-Fi)

### 2.3 Network Layer (Layer 3)

- Provides routing and logical addressing
- Manages data packet routing between different networks

## Key Concepts:

- Logical addressing (IP addressing)
- Routing
- Packet forwarding
- Fragmentation and reassembly

## Protocols:

- IP (Internet Protocol)
- ICMP (Internet Control Message Protocol)
- OSPF (Open Shortest Path First)

### 2.4 Transport Layer (Layer 4)

- Provides end-to-end communication control
- Ensures complete data transfer

## Key Concepts:

- Segmentation and reassembly
- Connection-oriented vs. connectionless communication
- Flow control
- Error control

## Protocols:

- TCP (Transmission Control Protocol)
- UDP (User Datagram Protocol)
- SCTP (Stream Control Transmission Protocol)

### 2.5 Session Layer (Layer 5)

- Establishes, manages, and terminates sessions between applications

## Key Concepts:

- Session establishment, maintenance, and termination
- Authentication
- Synchronization

## Protocols:

- NetBIOS
- RPC (Remote Procedure Call)
- SIP (Session Initiation Protocol)

### 2.6 Presentation Layer (Layer 6)

- Translates data between the application layer and the network format

## Key Concepts:

- Data translation
- Encryption/Decryption
- Compression

## Examples:

- JPEG, GIF (image formats)
- MIDI (audio format)
- SSL/TLS (encryption protocols)

### 2.7 Application Layer (Layer 7)

- Provides network services directly to end-user applications

## Key Concepts:

- Network services for applications
- Application functionality

## Protocols:

- HTTP/HTTPS
- FTP (File Transfer Protocol)
- SMTP (Simple Mail Transfer Protocol)
- DNS (Domain Name System)

## 3. Key Mathematical Concepts in OSI Model

### 3.1 Error Detection

Parity Check:

- Even Parity: $\sum_{i=1}^n b_i \equiv 0 \pmod{2}$
- Odd Parity: $\sum_{i=1}^n b_i \equiv 1 \pmod{2}$

Where $b_i$ represents the $i$-th bit.

### 3.2 Cyclic Redundancy Check (CRC)

$R = \text{remainder}\left(\frac{D \cdot 2^r}{G}\right)$

Where:

- $D$ is the data bits
- $r$ is the degree of the generator polynomial $G$
- $R$ is the remainder (CRC)

### 3.3 Hamming Distance

Minimum Hamming distance for detecting $d$ errors: $d + 1$ Minimum Hamming distance for correcting $d$ errors: $2d + 1$

### 3.4 Shannon's Channel Capacity Theorem

$C = B \log_2(1 + \frac{S}{N})$

Where:

- $C$ is the channel capacity in bits per second
- $B$ is the bandwidth of the channel in Hz
- $S$ is the average received signal power
- $N$ is the average noise power

## 4. OSI vs TCP/IP Model Comparison

|OSI Model|TCP/IP Model|
|---|---|
|Application|Application|
|Presentation||
|Session||
|Transport|Transport|
|Network|Internet|
|Data Link|Network Access|
|Physical||

## 5. Advantages and Disadvantages of the OSI Model

### Advantages:

- Standardizes network components and interfaces
- Modular design allows independent development of layers
- Supports both connection-oriented and connectionless services

### Disadvantages:

- Complex implementation
- Some layer functions overlap
- Not all protocols fit neatly into the model





---
# References
