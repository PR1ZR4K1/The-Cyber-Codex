2024/09/24 16:49
Status: #idea
Tags: [[Vlans]]

# InterVLAN Routing Config Facts

In addition to show commands, there are other commands available to verify and troubleshoot interVLAN routing. If your router will route packets to subnets other than those off the VLAN trunk, you need to configure upstream routing.

This lesson covers the following topics:

- Commands to verify and troubleshoot configuration.
- Upstream routing

## Steps to Verify and Troubleshoot Configuration

The following table lists commands used to configure and verify interVLAN routing:

|Command|Description|
|---|---|
|Router(config)# **interface fa0/1**  <br>Router(config-if)# **no shutdown**  <br>Router(config-if)# **interface fa0/1.1**  <br>Router(config-subif)#|Enables the interface.<br><br>##|
|Router(config-subif)# **encapsulation dot1q _[vlan id]_**  <br>Router(config-subif)# **encapsulation isl _[vlan id]_**|Sets the trunking encapsulation method for the VLAN on the subinterface for a router-on-a-stick configuration.<br><br>Only some switches support ISL encapsulation. You need to configure the router with the supported trunking encapsulation.|
|Router(config-subif)# **encapsulation dot1q _[vlan id]_ native**|Configures the VLAN that is sending and receiving untagged traffic on the trunk port when the interface is in 802.1Q trunking mode. This should match the native VLAN on the connected switch for a router-on-a-stick configuration.<br><br>By default, the native VLAN is 1.|
|Router(config-subif)# **ip address _[a.b.c.d]_ _[a.b.c.d]_**|Specifies an IP address and subnet mask on the subinterface for a router-on-a-stick configuration.|
|Router(config-subif)# **ip helper-address**|Enables the DHCP relay agent feature for a router-on-a-stick configuration.|

## Upstream Routing

The router may also need to route packets to other subnets in the network, not only between the subnets off the VLAN trunk. This is called _upstream routing_ . If this is the case, you must configure other router interfaces to forward packets to other upstream routes.

The following commands configure a router with a single interface (a _router-on-a-stick_ configuration) to perform interVLAN routing for VLAN 1 and VLAN 20:

> Router(config)#**interface fa0/1**
> Router(config-if)#**no shutdown**
> Router(config-if)#**no ip address**
> Router(config-if)#**interface fa0/1.1**
> Router(config-subif)#**description subinterface for VLAN 1**
> Router(config-subif)#**encapsulation dot1Q 1**
> Router(config-subif)#**ip address 192.168.1.1 255.255.255.0**
> Router(config-subif)#**interface fa0/1.20**
> Router(config-subif)#**description subinterface for VLAN 20**
> Router(config-subif)#**encapsulation dot1Q 20**
> Router(config-subif)#**ip address 192.168.2.1 255.255.255.0**






---
# References

- [[VLAN Trunking Protocol]]
- [[Trunking Advanced Config]]
- [[InterVLAN Routing Trouble Shooting Facts]]