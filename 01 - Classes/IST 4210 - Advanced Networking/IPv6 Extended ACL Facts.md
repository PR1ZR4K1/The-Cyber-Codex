2024/11/29 15:17
Status: #idea
Tags:

# IPv6 Extended ACL Facts


Access control lists (ACLs) can be used to filter both IPv4 and IPv6 traffic.

This lesson covers the following topics:

- IPv6 ACL differences
- IPv6 ACL characteristics
- IPv6 ACL syntax

## IPv6 ACL Differences

Although the ACLs used for IPv4 and IPv6 are similar, be aware of the following differences. IPv6 ACLs:

- Are similar to IPv4 extended named ACLs in functionality.
- Use only named ACLs. No numbered ACLs exist.
- Do not use inverted wildcard masks.
- Can exist alongside IPv4 ACLs on the same interface.
- Can be one of two types:
    
    - Router ACLs  
        Filters inbound and outbound traffic on Layer 3 interfaces (e.g., routed ports, switch virtual interfaces (SVIs), etc.)
    - Port ACLs  
        Filter inbound traffic on layer 2 interfaces.
    
    Router ACLs are applied only to packets that are routed. Port ACLs are applied to all packets, and therefore take precedence.
    

## IPv6 ACL Characteristics

Two types of IPv6 ACLs can be created:

- Router ACLs filter inbound and outbound traffic on layer 3 interfaces (e.g., routed ports, switch virtual interfaces (SVIs), etc.)
- Port ACLs filter inbound traffic on layer 2 interfaces.

Router ACLs are applied only to packets that are routed. Port ACLs are applied to all packets, and therefore take precedence.

IPv6 ACLs can control traffic based on:

- Source address and port number.
- Destination address and port number.
- Protocol designations, such as IP, TCP, UDP, and ICMP.

Configuring IPv6 ACLs is very similar to configuring standard named ACLs and involves the same two general steps:

1. Create the list and list entries with the access-list command.
2. Apply the list to a specific interface or line:
    - Use the ipv6 traffic-filter command to apply the list to an interface.
    - Use the ipv6 access-class command to apply the list to a line.

## IPv6 ACL Syntax

When constructing IPv6 access list statements, keep in mind the following:

- List statements include an action of either permit or deny.
- Use the keyword any in either the source or destination to match all packet addresses.
- IPv6 access lists match traffic in the order they appear in the list. As such, enter access list statements in order, with the most restrictive statements at the top.
- Each access list has an implicit deny any statement at the end of the access list.
- Your access list must contain at least one allow statement or no traffic will be allowed.

Use the following syntax to create and implement IPv6 ACLs:

|Command|Description|
|---|---|
|Router(config)# **ipv6 access-list _[name]_**|Creates an IPv6 ACL with the specified name and enters the IPv6 ACL configuration mode.|
|Router(config-ipv6-acl)# **permit\|deny _[protocol]_ _[source]_ _[destination]_**  <br>  <br>Router(config-ipv6-acl)# **permit\|deny _[protocol] [source] [destination]_ eq _[port]_**  <br>  <br>Router(config-ipv6-acl)# **permit\|deny _[protocol] [source] [destination]_ established**|Configures an ACL entry in the IPv6 ACL.<br><br>- protocol is the name or number of an IPv6 protocol, such as:<br>    - **tcp**<br>    - **udp**<br>    - **icmp**<br>- source and destination can be either a single host, network, or any<br>- The **eq** keyword and port argument specifies only packets on the given port number.<br>- The **established** keyword indicates that traffic will be permitted only if the TCP ACK or reset (RST) bits are set, which indicate that the packet is a response to a request that originated from an internal host.|
|Router(config-if)# **ipv6 traffic-filter _[name]_ in\|out**|Applies the IPv6 ACL to an interface.<br><br>- name is the name of the ACL that has been configured.<br>- Use the **in** or **out** keyword to specify which direction to apply the rule.|
|Router(config-if)# **ipv6 access-class _[name]_ in\|out**|Applies the IPv6 ACL to a line.<br><br>- name is the name of the ACL that has been configured.<br>- Use the **in** or **out** keyword to specify which direction to apply the rule.|
|Router# **show ipv6 access-list**|Displays the saved IPv6 access lists.|

The following commands create an IPv6 access list named DENY_HOSTA. This ACL will reject packets from host 2001:db8:4898:1::1 sent to host 2001:db8:4898:1::2, and then applies the list to the second serial interface:

> Router(config)#**ipv6 access-list DENY_HOSTA**
> Router(config-ipv6-acl)#**deny host 2001:db8:4898:1::1 host 2001:db8:4898:1::2**
> Router(config-ipv6-acl)#**permit ipv6 any any**
> Router(config-ipv6-acl)#**int s0**
> Router(config-if)#**ipv6 traffic-filter DENY_HOSTA in**

The following commands create an IPv6 access list named DOMAIN1. This ACL will not forward TCP packets from any host on network fd40:e5a1:01f5:4e44::/64 to network fd5c:b8d5:cf80:6ff2::/64, and then applies the list to the first serial interface:

> Router(config)#**ipv6 access-list DOMAIN1**
> Router(config-ipv6-acl)#**deny tcp fd40:e5a1:01f5:4e44::/64 fd5c:b8d5:cf80:6ff2::/64**
> Router(config-ipv6-acl)#**permit ipv6 any any**
> Router(config-ipv6-acl)#**int s0**
> Router(config-if)#**ipv6 traffic-filter DOMAIN1 in**

The following commands create an IPv6 access list named DENY_FTP. This ACL prevents FTP traffic from leaving your company (20 is the FTP control channel port, 21 is the FTP data channel port) while also allowing all other traffic. It then applies the list to the first serial interface:

> Router(config)#**ipv6 access-list DENY_FTP**
> Router(config-ipv6-acl)#**deny tcp any any eq 20**
> Router(config-ipv6-acl)#**deny tcp any any eq 21**
> Router(config-ipv6-acl)#**permit ipv6 any any**
> Router(config-ipv6-acl)#**int s0**
> Router(config-if)#**ipv6 traffic-filter DENY_FTP in**




---
# References
