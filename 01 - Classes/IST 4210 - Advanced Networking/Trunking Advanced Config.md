2024/09/24 16:14
Status: #idea
Tags: [[Vlans]]

# Trunking Advanced Config


The Dynamic Trunking Protocol (DTP) is used to automatically create a trunk link between two Cisco switches. Be aware that DTP:

- Is enabled by default on Cisco switches.
- Automatically negotiates the trunking encapsulation to be used (either 802.1Q or ISL).
- Operates in one of the following modes:

- Access
- Dynamic auto
- Dynamic desirable
- Trunk

The following diagram shows the link mode that is established depending on the modes of the two ports.

![A table that identifies how switch modes coorelate to other switch modes.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_advtrunking_ccna7/dtp-01.png)

The following table lists important commands for adding and removing VLANs on a trunk and configuring DTP:

|Command|Description|
|---|---|
|Switch(config-if)# **switchport trunk allowed vlan all**  <br>Switch(config-if)# **switchport trunk allowed vlan add _[vlan_id]_**  <br>Switch(config-if)# **switchport trunk allowed vlan remove _[vlan_id]_**|Defines which VLANs are allowed to communicate over the trunk.  <br>Removes the VLANs that are not allowed to communicate over the trunk.<br><br>The default allows all VLANs in the VLAN database to communicate over the trunk.|
|Switch(config-if)# **switchport mode dynamic auto**|Enables automatic trunking discovery and configuration. The switch uses DTP to configure trunking.|
|Switch(config-if)# **switchport mode dynamic desirable**|Enables dynamic trunking configuration. If a switch is connected, it will attempt to use the desired trunking protocol. If a switch is not connected, it will communicate as a normal port.|
|Switch(config-if)# **switchport mode access**|Disables trunking configuration on the port. The port is set to the access mode unconditionally and operates as a non-trunking, single VLAN interface that sends and receives un-tagged frames.|
|Switch(config-if)# **switchport access vlan _[number]_**|Assigns an unused interface to an unused VLAN.|
|Switch# **show interface trunk**  <br>Switch# **show interface fa0/1 trunk**|Shows the following trunking information for interfaces:<br><br>- Mode<br>- Encapsulation<br>- Trunking status<br>- VLAN assignments|

Be aware of the following when configuring VLAN trunking:

- Two switches configured to use auto dynamic trunking will not trunk. At least one of the switches must be set to manually trunk or to use desirable dynamic trunking.
- To avoid autonegotiation on trunk ports, you must manually configure the speed and duplex.

The following commands add VLAN 20 to the Gi0/1 interface and remove VLAN 5 from the Gi0/2 interface:

> Switch>**ena**
> Switch#**conf t**
> Switch(config)#**int gi0/1**
> Switch(config-if)#**switchport trunk allowed vlan add 20**
> Switch(config-if)#**int gi0/2**
> Switch(config-if)#**switchport trunk allowed vlan remove 5**

The following commands change the switchport mode of interface Gi0/1 to dynamic desirable:

> Switch>**ena**
> Switch#**conf t**
> Switch(config)#**int gi0/1**
> Switch(config-if)#**switchport mode dynamic desirable**




---
# References

- [[VLAN Facts]]
- [[VLAN Command List]]
- [[Trunking Command List]]
- [[Trunking Facts]]
- [[VLAN Trunking Protocol]]