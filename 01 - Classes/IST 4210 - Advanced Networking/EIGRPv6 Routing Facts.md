2024/10/29 17:17
Status: #idea
Tags:

# EIGRPv6 Routing Facts


The Enhanced Interior Gateway Routing Protocol version 6 (EIGRPv6) is an IPv6 routing protocol that's similar to its IPv4 counterpart, EIGRPv4. The commands differ slightly, but methods for communication, metric calculation, and establishing neighbors are mostly the same. Differences between EIGRPv4 and EIGRPv6 include the following:

- EIGRPv6 advertises IPv6 prefixes instead of IPv4 subnets.
- EIGRPv6 allows neighbors on different subnets.
- EIGRPv6 does not support the network command.
- The commands to set the AS number are different ( **ipv6** is added before the command).
- The commands to set the hello and hold timers are different ( **ip** is changed to **ipv6** ) **.**
- The commands to enable EIGRP on an interface are different (see above).
- Auto-summarization is not needed in EIGRPv6.
- EIGPRv6 has a different configuration setting for maximum paths.
- EIGPRv6 has its own variance commands in EIGRPv6 configuration mode.
- Show commands in EIGRPv6 use the **ipv6** keyword instead of **ip.**

Similar to OSPFv3, EIGRPv6 uses two modes for configuration commands to create the EIGRPv6 process:

|Mode|Command|
|---|---|
|EIGRP mode|router(config)# **ipv6 router eigrp** _**[as-number]**_  <br>  <br>router(config-rtr)# **eigrp router-id** _**[a.b.c.d]**_|
|Interface mode|router(config-if)# **ipv6 eigrp** _**[as-number]**_|

The following table lists commands that can be used to verify and troubleshoot EIGRPv6:

|Command|Description|
|---|---|
|router# **show ipv6 eigrp interfaces**|Displays all the interfaces on which EIGRP has been enabled.|
|router# **show ipv6 eigrp neighbors**|Displays discovered neighbors and each neighbor's status.|
|router# **show ipv6 protocols**|Displays the parameters and current state of the active IPv6 routing protocol processes.|
|router# **show ipv6 eigrp topology**|Displays the EIGRP topology table.|

When troubleshooting EIGRPv6, look for the following:

- EIGRPv6 not being enabled on an interface.
- An EIGRPv6-enabled interface without an AS number or with AS numbers that don't match. You can overlook this if the interface does not have neighbors.
- An EIGRPv6 interface incorrectly configured as passive.
- Neighbor relationships that are not established according to the network design.
- Neighbor relationships, bandwidth metrics, and delay metrics on the optimal route.
- ACLs blocking EIGRPv6 messages.




---
# References
