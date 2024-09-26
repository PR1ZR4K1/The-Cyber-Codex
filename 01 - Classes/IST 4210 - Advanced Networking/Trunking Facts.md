2024/09/24 15:49
Status: #idea
Tags: [[Vlans]]

# Trunking Facts

_Trunking_ is a term used to describe the connection of two switches.

This lesson covers the following topics:

- Trunking
- Trunking protocols
- Default switch configuration

## Trunking

Trunking is important when you configure VLANs that span multiple switches, as in the following diagram.

![VLANs spanning multiple switches through a trunk.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_trunking_ccna7/swi_tfct.jpg)

Be aware of the following facts regarding trunking and VLANs:

- In the above graphic, each switch has two VLANs. One port on each switch is assigned to each VLAN.
- Workstations in VLAN 1 can communicate only with workstations in VLAN 1. This means that the two workstations connected to the same switch cannot communicate with each other. Communications within the VLAN must pass through the trunk link to the other switch.
- Trunk ports identify which ports are connected to other switches.
- Trunk ports can automatically carry traffic for all VLANs defined on the switch. You can prevent traffic from a specific VLAN from being carried on the trunk through a specific configuration.
- Typically, Gigabit Ethernet ports are used for trunk ports, although any port can be a trunking port.

When trunking is used, frames that are sent over a trunk port are tagged with the VLAN ID number so that the receiving switch knows which VLAN the frame belongs to. Tags are appended by the first switch in the path and removed by the last. Only VLAN-capable devices understand the frame tag. Tags must be removed before a frame is forwarded to a non-VLAN-capable device.

## Trunking Protocols

A _trunking protocol_ is the format that switches use for tagging frames with the VLAN ID. The following table describes the two trunking protocols that Cisco supports:

|Trunking Protocol|Characteristics|
|---|---|
|Inter-Switch Link (ISL)|The Inter-Switch Link trunking protocol:<br><br>- Is a Cisco-proprietary trunking protocol.<br>- Can be used only between Cisco devices.<br>- Encapsulates the frame with an ISL header and trailer instead of tagging (modifying) the frame.<br>- Supports VLAN numbers 1–1005.<br><br>Be aware of the following facts regarding the ISL trunking protocol:<br><br>- If a non-ISL configured trunk port receives an ISL-encapsulated Ethernet frame, it may consider those frames to be transmission errors because the ISL header and trailer cause the frame to have an excessive size.<br>- Switches that do not support ISL drop ISL frames because they can't decode the ISL encapsulation.|
|802.1Q|The 802.1Q trunking protocol:<br><br>- Is an IEEE standard for trunking and is supported by a wide range of devices.<br>- Supports VLAN numbers 1–4094.<br>- Does not tag frames from the default VLAN. Frames from all other VLANs are tagged. For example, if an 802.1Q port has VLANs 1, 2, and 3 assigned to it and VLAN 1 is the default VLAN, frames on VLAN 1 that exit the port are not given an 802.1Q header. Frames that enter this port and have no 802.1Q header are put into VLAN 1.<br><br>- If the default VLAN on one end of the trunk is different from the native VLAN on the other end, the traffic of the native VLANs on both sides can't be transmitted correctly on the trunk.<br>- The native VLAN is VLAN 1 by default, but may be reconfigured.<br><br>When using multiple vendors in a switched network, be sure each switch supports the 802.1Q standards if you want to implement VLANs.|

Cisco switches have the ability to automatically detect trunk ports and negotiate the trunking protocol used between devices. Switches use the Dynamic Trunking Protocol (DTP) to detect and configure trunk ports. For example, when you connect two switches together, they will automatically recognize each other and select the trunking protocol to use.

## Default Switch Configuration

By default, most Cisco switches are configured as follows:

- All ports are enabled (no shutdown).
- All ports automatically detect duplex mode.
- All ports automatically detect port speed.
- All ports perform automatic trunking negotiation.
- The switch uses fragment-free switching.
- Spanning tree is enabled.
- VTP mode is set to server.
- All ports are members of VLAN 1.
- Default VLANs of 1, 1002, 1003, 1004, and 1005 exist.
- 802.1Q trunking is used.





---
# References

- [[Vlans]]
- [[VLAN Command List]]
- [[Trunking Command List]]