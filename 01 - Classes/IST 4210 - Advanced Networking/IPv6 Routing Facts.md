2024/10/29 16:46
Status: #idea
Tags: [[IPv6 Routing Facts]]

# IPv6 Routing Facts

IPv6 is the next generation Internet Protocol (IP) standard. It was designed to provide enough IP addresses for every device or entity world-wide that is capable of communicating over the internet.

An IPv6 address is made up of 32 hexadecimal numbers organized into eight quartets. Each quartet is separated by a colon. Each quartet has 16 bits. The value of each quartet can range from 0 to FFFF. An IPv6 address is composed of two parts, the prefix and the interface ID. The address’s first 64 bits is the prefix. It’s equivalent to an IPv4 network’s address and includes both the network and the subnet address. The last 64 bits are the interface ID. This is similar to the node address in IPv4. The interface ID is a unique address that’s assigned to a particular network interface on a host.

Be familiar with the following IPv6 concepts:

|Concept|Description|
|---|---|
|Unicast addressing|There are three types of unicast addressing:<br><br>- Link-local addresses are addresses that are valid on only the current subnet--hosts and routers running IPv6 create link-local addresses for interfaces on the subnet. Protocols give packets that remain within the subnet link-local addressing.<br>- Global addresses--unique addresses similar to public addresses in IPv4. An organization is assigned a global unique address prefix by an ISP. Each entity within the organization uses this unique prefix.<br>- Unique local unicast addressing--similar to private addresses in IPv4. Organizations use unique local addressing to communicate within a site or between a limited number of sites.|
|DHCP|DHCP follows the same general process in IPv6 as in IPv4. The options for assigning IPv6 addresses are:<br><br>- Static address assignment, which can be static full assignment or static partial assignment.<br><br>- Static full assignment assigns the entire 128-bit IPv6 address and configuration information to the host.<br>- Static partial assignment assigns the prefix. Then the remaining address is the modified EUI-64 format derived from the MAC address.<br><br>- An updated version of DHCP (DHCPv6) has two modes, stateful DHCPv6 and stateless DHCPv6.<br>- A stateful DHCPv6 address:<br><br>- Follows the same process in IPv6 as in IPv4. A DHCPv6 server exists on the network, and hosts contact the DHCP server to lease an IP address and obtain other settings.<br>- Does not supply default router information. Hosts send packets requesting local routers to provide information using Neighbor Discovery Protocol (NDP).<br><br>- Stateless address autoconfiguration (SLAAC) automatically generates the interface ID and uses NDP to learn the subnet prefix, the prefix length, and the default gateway. This method builds the host's IPv6 address on the host without network messages and learns DNS server addressing using stateless DHCPv6 from a DHCP6 server.|
|IPv6 configuration|You can configure IPv6 routing as follows:<br><br>- To enable IPv6 using the **global** command, use **ipv6 unicast-routing** .<br>- To enable IPv6 on each interface, use the **ipv6 address address/length** command.|

The following are common IPv6 routing commands:

|Command|Description|
|---|---|
|**ipv6 uni-cast routing**|Used to enable IPv6 routing on Cisco routers.|
|**ipv6 address**|Used to enable IPv6 on each interface and configure the interface address and prefix. Use this command only on interfaces that will be in use.|
|**ipv6 route _[route address]_** _**[exit interface]**_|Statically adds IPv6 routes to the routing table.|





---
# References

- [[EIGRPv6 Routing Facts]]
