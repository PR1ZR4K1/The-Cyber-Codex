2024/02/07 22:34
Status: #idea
Tags:

# # Manage Networking (TCP/IP)

The TCP/IP network model is a four-layered set of communication protocols that describes how data communications are packetized, addressed, transmitted, routed, and received between computers over a network.

*Protocol is specified by RFC 1122, Requirements for Internet Hosts - Communication Layers*

Here are the four layers:

- Application

	 Each application has specifications for communication so that clients and servers can communicate across platforms. Common protocols include SSH, HHTPS, FTP, and SMTP (electronic mail delivery).

- Transport

	 TCP and UDP are transport protocols. TCP is a reliable connection-oriented communication, whereas UDP is a connectionlesss datagram protocol. Application protocols can use either TCP or UDP ports. A list of well-known and registered ports is in the `/etc/services`

- Internet 

	 The internet layer, or network layer, carries data from the source host to the destination host. The IPv4 and IPv6 protocols are internet layer protocols. Each host has an IP address and a prefix to determine network addresses. Routers are used to connect networks.

- Link

	 The link layer, or media access layer, provides the connection to physical media. The most common types of networks are wired Ethernet (802.3) and wireless Wi-Fi (802.11). Each physical device has a MAC address to identify the destination of packets on the local network segment.

### TCP/IP vs. OSI model

![[Pasted image 20240207224538.png]]

Network interface names start with the type of interface:

- Ethernet interfaces begin with 'en'
- WLAN interfaces begin with 'wl'
- WWAN interfaces begin with 'ww'




---
# References
- [RFC 1122](https://datatracker.ietf.org/doc/html/rfc1122)