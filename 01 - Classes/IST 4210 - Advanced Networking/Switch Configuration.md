2024/09/18 15:23
Status: #idea
Tags: [[Switch Configuration]]

# Switch Configuration Facts


The basics of configuring a Cisco Layer 2 switch is relatively simple because all the interfaces on Cisco switches are live by default. You can pull a Cisco switch out of the box, plug it in, start plugging workstations into it, and it will start learning the MAC addresses of those workstations automatically. It will start building its CAM table, and then start forwarding data intelligently or filtering data when it doesn't have to forward them. So switches are plug-and-play in the Cisco world. However, you still need to configure a few things.

This lesson covers the following topics:

- Switch configuration
- Configuration commands

## Switch Configuration

After plugging in a switch, you should always configure the following:

- Passwords - console, virtual terminal, or VTY, and enable mode
- IP addresses
- Default gateway

By default, most Cisco switches come configured as described in the following table:

|Configuration|Description|
|---|---|
|Ports|All ports:<br><br>- Are enabled (no shutdown).<br>- Will automatically detect the duplex mode.<br>- Will automatically detect the port speed.<br>- Will perform automatic trunking negotiation.|
|Switch|The switch uses fragment-free switching. On some switch models, you may be able to configure the switching method.|
|Topology|Spanning tree is enabled.|
|VTP mode|VTP mode is set to server.|
|VLAN|All ports are members of VLAN 1. Default VLANs of 1, 1002, 1003, 1004, and 1005 exist.|
|Trunking|802.1Q trunking is used.|
|Port numbers|Port numbering on some switches begins at 1, not 0. For example, FastEthernet 0/1 is the first FastEthernet port on a switch.|
|Speed and duplex settings|Speed and duplex settings are as follows:<br><br>- Through autonegotiation, the 10/100/1000 ports configure themselves to operate at the speed of attached devices. If the attached ports do not support autonegotiation, you can explicitly set the speed and duplex parameters.<br>- If the speed and duplex settings are set to auto, the switch uses auto-MDIX to sense the cable type (crossover or straight-through) connected to the port and automatically adapts itself to the cable type used. When you manually configure the speed or duplex setting, it disables auto-MDIX, so you will need to be sure to use the correct cable.<br>- By default, the link speed and duplex configuration for Ethernet interfaces in Cisco devices are set using IEEE 802.3u autonegotiation. The interface negotiates with remote devices to determine the correct settings.<br>- However, autonegotiation can be disabled on the Cisco device and/or other Ethernet network hosts and static values manually assigned. When this happens, other devices with autonegotiation enabled try to negotiate link speed and duplexing but get no response. When autonegotiation fails, Cisco devices that have autonegotiation enabled default to the following:<br><br>- The interface will attempt to sense the link speed, if possible. If not, the slowest link speed supported on the interface is used (usually 10 Mbps).<br>- If the link speed selected is 10 Mbps or 100 Mbps, half-duplex is used. If it is 1000 Mbps, full-duplex is used.|

## Configuration Commands

The following table lists common switch configuration commands:

|Command|Description|
|---|---|
|switch(config)# **interface FastEthernet 0/14**  <br>switch(config)# **interface GigabitEthernet 0/1**|Moves to interface configuration mode|
|switch(config)# **interface range fastethernet 0/14 - 24**  <br>switch(config)# **interface range gigabitethernet 0/1 - 4**  <br>switch(config)# **interface range fa 0/1 - 4 , 7 - 10**  <br>switch(config)# **interface range fa 0/8 - 9 , gi 0/1 - 2**|Moves to configuration mode for a range of interfaces|
|switch(config-if)# **speed 10**  <br>switch(config-if)# **speed 100**  <br>switch(config-if)# **speed 1000**  <br>switch(config-if)# **speed auto**|Sets the port speed on the interface|
|switch(config-if)# **duplex half**  <br>switch(config-if)# **duplex full**  <br>switch(config-if)# **duplex auto**|Sets the duplex mode on the interface|
|switch(config-if)# **no shutdown**  <br>switch(config-if)# **shutdown**|Enables or disable the interface|
|switch# **show interface status**|Shows interface status of all ports|
|switch# **show ip interface brief**|Shows line and protocol status of all ports|




---
# References

- [[Switch Configuration Mode Facts]]
