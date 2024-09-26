2024/09/24 17:09
Status: #idea
Tags: [[Vlans]]

# Layer 3 Switch InterVLAN Routing Facts

In addition to routers, layer 3 (multilayer) switches are also capable of interVLAN routing. A multilayer switch is a switch that can have its interfaces configured for layer 2 and layer 3 functionality. To allow interVLAN routing, the multilayer switch interface must be configured as a _Switch Virtual Interface_ (SVI).

This lesson covers the following topics:

- SVI characteristics
- Commands to configure and verify SVI

## SVI Characteristics

The following are characteristics of an SVI:

- An SVI is configured with an IP address and is associated with a single VLAN.
- A layer 3 switch treats each interface as a physical link through which it can route traffic.
- The IP address associated with the SVI is the default gateway of the workstation.
- SVIs use hardware switching.
- An SVI is implemented primarily to interconnect the VLANs between distribution-layer and access-layer switches in a multi-switched network, as in the following example:  
    ![A Switch Virtual Interface interconnecting VLANs.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_l3intervlan_ccna7/swi_vrtg_03.png)

Be aware of the following multilayer switch details for interVLAN routing:

- On some multilayer switches, IP routing should be enabled for communication between subnets.
- The no switchport command configures an interface as a layer 3 interface for routed ports.
- VLANs must be present (created) in the VLAN database before creating SVIs.
- The default gateway configuration on each host device must be the VLAN interface IP address on the layer 3 switch.
- Most enterprise and service provider networks use layer 3 switching.

## Commands to Configure and Verify SVI

The following table lists commands used to configure and verify SVI interVLAN routing.

|Command|Description|
|---|---|
|Switch(config)# **ip default-gateway _[a.b.c.d]_**|Configures the default gateway on a switch. This will enable management of the switch from a remote network.|
|Switch(config)# **ip routing**|Enables IP routing on the multilayer switch for an SVI configuration.|
|Switch(config)# **vlan _[id]_**|Creates a VLAN in the VLAN database and enters the VLAN configuration mode.|
|Switch(config)# **router _[routing protocol]_**|Enables a specified routing protocol on the multilayer switch for an SVI configuration.|
|Switch(config)# **interface vlan _[vlan id]_**|Enters VLAN interface configuration mode for the specified VLAN for an SVI configuration.|
|Switch(config-if)# **ip address _[a.b.c.d]_ _[a.b.c.d]_**|Specifies an IP address and subnet mask on the VLAN interface for an SVI configuration.|
|Switch(config-if)# **no shutdown**|Enables the interface.|
|Switch(config-if)# **ip helper-address**|Enables the DHCP relay agent on the multilayer switch for an SVI configuration.|
|Switch# **show running-config**|Displays the interVLAN configurations, including subinterfaces, IP routing information, and SVI addresses.|
|Switch# **ping a.b.c.d**|Tests connectivity to the hosts, VLAN interfaces, and VLAN subinterfaces.|
|Switch# **show ip route**|Displays the available IP routes on the switch or router.|
|Switch# **show ip protocols**|Displays information about the routing protocols that are enabled on the switch or router.|
|Switch# **show ip cef**|Displays brief information of all Forwarding Information Base (FIB) entries.|
|Switch# **show interface vlan _[vlan number]_**|Shows the status of the VLAN interface. Two status codes are displayed for the SVI interface:<br><br>- The first status code is the _Line Status_ . This code should display as up.<br>- The second status code is the _Protocol Status_ . This code should display as up.|
|Switch# **show ip adjacency**|Verifies that an adjacency exists for a connected device, that the adjacency is valid, and that the MAC header rewrite string is correct. The information displayed by the show adjacency commands includes the following:<br><br>- Protocol<br>- Interface<br>- Type of routed protocol traffic using this adjacency<br>- Next hop address|

The following commands configure a VLAN interface to perform interVLAN routing for VLAN 1 and VLAN 12 on a multilayer switch:

> switch(config)#**ip routing**
> switch(config)#**interface vlan 1**
> switch(config-if)#**ip address 192.168.1.1 255.255.255.0**
> switch(config-if)#**no shutdown**
> switch(config-if)#**interface vlan 12**
> switch(config-if)#**ip address 192.168.2.1 255.255.255.0**
> switch(config-if)#**no shutdown**
> switch(config-if)#**exit**
> switch(config)#**vlan 1**
> switch(config-vlan)#**vlan 12**





---
# References

- [[InterVLAN Routing Trouble Shooting Facts]]
- [[InterVLAN Routing Config Facts]]
- [[SVI InterVLAN Troubleshooting Facts]]