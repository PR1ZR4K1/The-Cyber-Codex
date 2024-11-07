

2024/11/05 15:42
Status: #idea
Tags:

# Wireless Architecture Facts

When you implement a radio frequency wireless network, hosts are connected by radio waves rather than wires. Radio waves are considered unbounded media because unlike wires, nothing encases them. The most commonly used frequency for wireless networking is the 2.4 GHz frequency band. The following table describes several aspects of wireless networking architecture.

|Characteristic|Description|
|---|---|
|Signaling method|Frequency Hopping Spread Spectrum (FHSS)|FHSS uses a narrow frequency band and hops data signals in a predictable sequence from frequency to frequency over a wide band of frequencies.<br><br>- Because FHSS shifts automatically between frequencies, it can avoid interference that may be on a single frequency.<br>- Hopping between frequencies increases transmission security by making eavesdropping and data capture more difficult.|
|Direct-Sequence Spread Spectrum (DSSS)|With DSSS, the transmitter breaks data into pieces and sends the pieces across multiple frequencies in a defined range. DSSS is more susceptible to interference and less secure then FHSS.|
|Orthogonal Frequency-Division Multiplexing (OFDM)|OFDM breaks data into very small data streams to send the information across long distances where environmental obstacles may be an issue. OFDM:<br><br>- Modulates adjacent radio signals orthogonally, meaning a linear transfer that preserves length and distance. This allows for a very large number of small data streams in a single frequency.<br>- Reduces the effects of signal interference caused by environmental obstacles such as walls or buildings.<br>- Is used by 802.11g/a/n and ac wireless networks to achieve higher transfer speeds.|
|Topology|Ad hoc|An ad hoc network works in peer-to-peer mode without an access point. The wireless NICs in each host communicate directly with one another. An ad hoc network:<br><br>- Uses a physical mesh topology with a logical bus topology.<br>- Is cheap and easy to set up.<br>- Cannot handle a large number of hosts.<br>- Requires special modifications to reach wired networks.<br><br>You will typically use an ad hoc network only to create a temporary direct connection between two hosts.|
|Infrastructure|An infrastructure wireless network uses an access point (AP) that functions like a hub on an Ethernet network. Infrastructure networks have the following characteristics:<br><br>- The network uses a physical star topology with a logical bus topology.<br>- You can easily add hosts without increasing administrative efforts.<br>- The AP can be connected to a wired network easily, allowing clients to access both wired and wireless hosts.<br>- The placement and configuration of APs require planning to implement effectively.<br><br>You should implement an infrastructure network for all but the smallest of wireless networks.|
|Media access|Wireless networks use carrier sense multiple access/collision avoidance (CSMA/CA) to control media access and avoid (rather than detect) collisions. Collision avoidance uses the following process:<br><br>1. The sending device listens to make sure that no other device is transmitting. If another device is transmitting, the device waits a random period of time (called a backoff period) before attempting to send again.<br>2. If no other device is transmitting, the sending device broadcasts a request to send (RTS) message to the receiver or AP. The RTS includes the source and destination, as well as information on the duration of the requested communication.<br>3. The receiving device responds with a clear to send (CTS) message. The CTS also includes the communication duration period. Other devices use the information in the RTS and CTS to delay send attempts until the communication duration period (and subsequent acknowledgement) has passed.<br>4. The sending device transmits the data. The receiving device responds with an acknowledgement (ACK). If an acknowledgement is not received, the sending device assumes a collision occurred and retransmits the affected packet.<br>5. After the time interval specified in the RTS and CTS has passed, other devices can start the process again to attempt to transmit.<br><br>The use of RTS and CTS (steps 2 and 3) is optional and depends on the capabilities of the wireless devices. Without RTS/CTS, collisions are more likely to occur.<br><br>Wireless communication operates in half-duplex (shared two-way communication). Devices can both send and receive, but not at the same time. Devices must take turns using the transmission channel. Once a party begins receiving a signal, it must wait for the transmitter to stop transmitting before it can reply.|   |
|Devices|Below are some common devices that are used on a wireless network:<br><br>- A wireless NIC sends and receives signals.<br>- A wireless AP is the equivalent of an Ethernet hub. The wireless NICs connect to the AP, and the AP manages network communication.<br>- A wireless bridge connects two wireless APs into a single network or connects a wireless AP to a wired network. Most APs include bridging features.<br><br>Many wireless APs include ports (hubs, switches, or routers) to connect the wireless network to the wired portion of the network.|   |





---
# References

- [[Wireless Infrastructure Facts]]