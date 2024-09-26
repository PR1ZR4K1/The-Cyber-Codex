 2024/09/24 15:52
Status: #idea
Tags:

# Trunking Command List

You should be familiar with the commands for configuring and monitoring trunking on a switch. The following table lists important commands for configuring and monitoring trunking on a switch.

|Command|Description|
|---|---|
|Switch(config-if)# **switchport mode trunk**|Enables unconditional trunking on the interface. The port will not use Dynamic Trunking Protocol (DTP) on the interface.|
|Switch(config-if)# **switchport trunk encapsulation dot1q**  <br>Switch(config-if)# **switchport trunk encapsulation isl**  <br>Switch(config-if)# **switchport trunk encapsulation negotiate**|Sets the trunking protocol or allows the trunking protocol to be negotiated.<br><br>Not all Catalyst switches allow configuration of the trunking protocol.|
|Switch(config-if)# **switchport trunk native vlan _[vlan_id]_**|Configures the VLAN that is sending and receiving untagged traffic on the trunk port when the interface is in 802.1Q trunking mode.|
|Switch(config-if)# **switchport mode access**|Disables trunking configuration on the port. The port is set to the access mode unconditionally and operates as a non-trunking, single VLAN interface that sends and receives un-tagged frames.|
|Switch# **show interface trunk**  <br>Switch# **show interface fa0/1 trunk**|Shows interface trunking information with mode, encapsulation, trunking status, and VLAN assignments.|

Be aware of the following when configuring VLAN trunking:

- Two switches, both configured to use auto dynamic trunking, will not trunk. At least one of the switches must be set to manually trunk or use desirable dynamic trunking.
- To avoid auto-negotiation on trunk ports, manually configure the speed and duplex.

In the following example, two distribution-layer switches, SW1 and SW2, are connected through their respective Gi0/1 interfaces. The following commands configure trunking and change the native VLAN from the default value to VLAN 5.

> SW1>**ena**
> SW1#**conf t**
> SW1(config)#**int gi 0/1**
> SW1(config-if)#**switchport mode trunk**
> SW1(config-if)#**switchport trunk native vlan 5**

> SW2>**ena**
> SW2#**conf t**
> SW2(config)#**int gi 0/1**
> SW2(config-if)#**switchport mode trunk**
> SW2(config-if)#**switchport trunk native vlan 5**





---
# References

- [[Vlans]]
- [[VLAN Command List]]
- [[Trunking Facts]]
- [[Trunking Advanced Config]]