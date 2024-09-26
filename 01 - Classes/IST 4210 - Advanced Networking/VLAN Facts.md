32024/09/24 15:25
Status: #idea
Tags: [[Vlans]]

# VLAN Facts

A virtual LAN (VLAN) is a broadcast domain defined by switch port rather than network address or other criteria. Using VLANs lets you assign devices on different switch ports to different logical (or virtual) LANs.

This lesson covers the following topics:

- VLANs
- Single-switch VLAN configuration
- VLAN advantages
- VLAN disadvantages
- Voice VLANs

## VLANs

A VLAN is a logical grouping of computers based on switch port.

- VLAN membership is configured by assigning a switch port to a VLAN.
- A switch can have multiple VLANs configured on it, but each switch port can be a member of only a single VLAN (with one exception described below).
- VLANs can be defined on a single switch or configured on multiple interconnected switches. With multiple switches, each switch can be configured with the same VLANs. Devices on one switch can communicate with devices on other switches as long as they are members of the same VLAN.
- A trunk port is used to connect two switches together. Be aware of the following regarding trunk ports:

- Typically, Gigabit Ethernet ports are used for trunk ports, although any port can be a trunking port.
- A trunk port is a member of all VLANs defined on a switch and carries traffic between switches.
- When trunking is used, frames that are sent over a trunk port are tagged by the first switch with the VLAN ID so that the receiving switch knows which VLAN the frame belongs to.
- The trunking protocol describes the format that switches use for frame tagging with the VLAN ID.
- Because end devices do not understand the VLAN tags, the switch removes the tag from the frame before the frame is forwarded to the destination device.
- VLAN tagging is used only for frames that travel between switches on the trunk ports.

- In a typical configuration with multiple VLANs, workstations in one VLAN cannot communicate with workstations in other VLANs. To enable inter-VLAN communication, you need to use a router or a layer 3 switch.
- Using VLANs, the switch can create multiple IP broadcast domains. Each VLAN is in its own broadcast domain, and broadcast traffic is sent only to members of the same VLAN.

## Single-Switch VLAN Configuration

Although each switch can be connected to multiple VLANs, each switch port can be assigned to only one VLAN at a time. The following graphic shows a single-switch VLAN configuration:

![A single-switch with two VLANs configured.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_vlan_ccna7/swi_vfct.jpg)

Important VLAN facts include the following:

- In the graphic above, FastEthernet ports 0/1 and 0/2 are members of VLAN 1. FastEthernet ports 0/3 and 0/4 are members of VLAN 2.
- In the graphic above, workstations in VLAN 1 cannot communicate with workstations in VLAN 2 even though they are connected to the same physical switch.
- Defining VLANs creates additional broadcast domains. The above example has two broadcast domains, each of which corresponds to one of the VLANs.
- Switches are configured with the following default VLANs:

- VLAN 1
- VLAN 1002
- VLAN 1003
- VLAN 1004
- VLAN 1005

Default VLANs cannot be deleted or modified.

- By default, all ports are members of VLAN 1.
- Depending on the VLAN number, a VLAN is either normal or extended.

- 1–1005 are normal range VLANs.
- 1006–4094 are extended range VLANs.

## VLAN Advantages

Administrative benefits of creating VLANs with switches include the ability to:

- Create virtual LANs based on criteria other than physical location (such as workgroup, protocol, or service).
- Simplify device moves by modifying a device's port assignment to move it to a new VLAN.
- Control broadcast traffic and create collision domains based on logical criteria.
- Control security by isolating traffic within a VLAN.
- Load-balance network traffic by dividing traffic logically rather than physically.

VLANs are commonly used with Voice over IP (VoIP) to distinguish voice traffic from data traffic. Traffic on the voice VLAN can be given a higher priority to ensure timely delivery.

Creating VLANs with switches offers the following benefits over using routers to create distinct networks:

- Switches are easier to administer than routers.
- Switches are less expensive than routers.
- Switches offer higher performance (introduce less latency).

## VLAN Disadvantages

A disadvantage of using switches to create VLANs is that you might be tied to a specific vendor. Details of how VLANs are created and identified can vary from vendor to vendor. Creating a VLAN might mean you must use only that vendor's switches throughout the network. When using multiple vendors in a switched network, be sure each switch supports the 802.1Q standards if you want to implement VLANs.

Despite advances in switch technology, routers are still needed to:

- Filter WAN traffic.
- Route traffic between separate networks.
- Route packets between VLANs.

## Voice VLANs

In addition to data VLANs, you can also use switches to create voice VLANs. Voice VLANs are configured on access ports and are used to carry VoIP traffic from a Cisco IP phone. Voice VLANs send all VoIP traffic with a higher priority than data traffic to ensure timely delivery. Consider the following facts about voice VLANs:

- To create a voice VLAN, use the switchport voice vlan _[number]_ command.
- By default, IP phone traffic on a voice VLAN is tagged with an 802.1Q priority of 5.
- When an interface is configured with a voice VLAN, the PortFast feature is automatically enabled on the interface.
- A Cisco IP phone automatically uses the VLAN ID of the port it is connected to. Non-Cisco IP phones require the VLAN ID to be manually configured on the IP phone.





---
# References

- [[Vlans]]
- [[VLAN Command List]]
- [[Trunking Command List]]