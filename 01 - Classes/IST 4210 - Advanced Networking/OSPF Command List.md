2024/10/28 22:54
Status: #idea
Tags: [[OSPF Facts]]

# OSPF Command List

## router ospf

This lesson covers the following topics:

- OSPF configuration
- OSPF configuration commands

## OSPF Configuration

When configuring OSPF:

- Enter OSPF configuration mode for a particular OSPF process using the router OSPF command followed by the process ID.
- Configure the OSPF router ID.
- Use network subcommands to configure matched interfaces enabled for the OSPF process that are assigned to a listed area.
- Use the following commands to verify OSPF:

- **show IP protocol**
- **show IP route**
- **show IP OSPF database**
- **show IP OSPF neighbor**

## OSPF Configuration Commands

The following table lists the commands and details for configuring OSPF:

|Command|Description|
|---|---|
|Router(config)# **router ospf _[process-id]_**|Enters configuration mode for OSPF. The process ID identifies a separate routing process on the router.<br><br>Process IDs do not need to match between routers. In other words, two routers configured with different process IDs can share OSPF information.|
|Router(config-router)# **network _a.b.c.d w.w.w.w_  <br>area _[number]_**|Identifies networks that participate in OSPF routing:<br><br>- _a.b.c.d_ is the network address. This can be a subnetted, classless network.<br>- _w.w.w.w_ is the wildcard mask. The wildcard mask identifies the subnet address.<br>- _number_ is the area number in the OSPF topology. The area number must match between routers.|
|Router(config-router)# **router-id _a.b.c.d_**|Configures the router ID for the OSPF process.<br><br>The router ID is used to identify the DR/BDR if two routers have matching priority values.|
|Router(config)# **interface ethernet0/1**  <br>  <br>Router(config-if)# **ip ospf priority [0-255]**|Sets the OSPF priority number for an interface:<br><br>- The priority number is used in the DR/BDR election process. The router with the highest priority becomes the DR.<br>- Configure a value of 0 to ensure that a router never becomes the DR or BDR.<br><br>The priority is set on an interface and applies to the DR/BDR election process on that interface.|
|Router(config)# **interface loopback0**  <br>  <br>Router(config-if)# **ip address _a.b.c.d m.m.m.m_**|Sets an IP address for a loopback interface.<br><br>The IP address is used as the router ID and to determine the DR and BDR if two routers have the same priority value.|
|Router(config-router)# **passive-interface _[interface]_**|Configures a single OSPF interface on the router as a passive interface.|
|Router(config-router)# **passive-interface default**|Makes all OSPF interfaces on the router passive by default.|
|Router(config-router)# **no passive-interface _[interface]_**|Configures a single OSPF interface on the router as a non-passive interface.|
|Router# **show ip ospf interface _[interface]_**|Displays the configuration of an OSPF interface.|

The following graphic shows a sample network with two OSPF areas:

![A network with two OSPF areas.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_ospf_commands_ccna7/ospf_cfg.png)

The following commands were used to configure OSPF on each router:

|Router|Configuration|
|---|---|
|SFO|**router ospf 1  <br>network 10.1.0.0 0.0.15.255 area 0  <br>network 10.1.16.0 0.0.15.255 area 1  <br>network 10.1.32.0 0.0.15.255 area 1**|
|LAX|**router ospf 2  <br>network 10.1.16.1 0.0.0.0 area 1  <br>network 10.2.0.1 0.0.0.0 area 1**|
|PHX|**router ospf 1  <br>network 10.1.32.0 0.0.15.255 area 1  <br>network 10.3.0.0 0.0.255.255 area 1**|

Notice the following in the configuration:

- The process ID on each router does not have to match. OSPF uses areas to identify sharing of routes, not the process ID.
- You can use the subnet address with the appropriate wildcard mask (such as 10.1.16.0 0.0.15.255), or you can use the IP address of the router interface with a mask of 0.0.0.0.
- The network command identifies the subnet, wildcard mask, and the OSPF area of the subnet. A subnet can be only in one area.

The following commands configure all OSPF interfaces as passive interfaces and then configure Fa 0/0 as a non-passive interface:

> Router(config)#**int fa 0/0**
>     Router(config-if)#**ip address 192.168.2.250 255.255.255.0**
>     Router(config-if)#**router ospf 5**
>     Router(config-router)#**network 192.168.2.0 0.0.0.255 area 0**
>     Router(config-router)#**passive-interface default**
>     Router(config-router)#**no passive-interface fa 0/0**





---
# References

- [[OSPF Facts]]
- [[OSPF Configuration IPv4]]