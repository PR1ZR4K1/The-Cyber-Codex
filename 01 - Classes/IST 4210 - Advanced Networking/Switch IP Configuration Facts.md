2024/09/18 15:55
Status: #idea
Tags:

# Switch IP Configuration Facts

Basic switches operate at Layer 2 and do not need an IP address to function. Switches are able to perform switching functions with no IP address configured. You need to configure a switch IP address only if you want to manage the switch from a Telnet or web session. The switch itself has only a single (active) IP address. Switch ports do not have an IP address (unless the switch is performing Layer 3 switching, a function which is not supported on all switches). The IP address identifies the switch as a host on the network but is not required for switching functions.

This lesson covers the following topics:

- Host configuration settings
- IP address configuration

## Host Configuration Settings

The following table summarizes key host configuration settings on a TCP/IP network:

|Parameter|Purpose|
|---|---|
|IP address|Identifies both the logical host and logical network addresses. Two devices on the same network must have IP addresses with the same network portion of their addresses to communicate without a router.|
|Subnet mask|Identifies the portion of the IP address that is the network address. Two devices on the same network must be configured with the same subnet mask to communicate without a router.|
|Default gateway|Identifies the router to which packets for remote networks are sent. The default gateway address is the IP address of the router interface on the same subnet as the local host. Without a default gateway set, most clients will be unable to communicate with hosts outside of the local subnet.|
|Hostname|Identifies the logical name of the local system.|
|DNS server|Identifies the DNS server that is used to resolve hostnames to IP addresses.|
|MAC address|Identifies the physical address. On an Ethernet network, this address is burned in to the network adapter hardware.|

A host requires an IP address and subnet mask to communicate on a single subnet. A default gateway address is required to enable inter-subnet communications. At least one DNS server address is required for the host to use hostnames when contacting other hosts.

## IP Address Configuration

To configure the switch IP address, set the address on the VLAN interface. This is a logical interface defined on the switch to allow management functions. By default, the VLAN is VLAN 1. Use the following commands to configure the switch IP address:

> switch#**config terminal**
> switch(config)#**interface vlan 1**
> switch(config-if)#**ip address 1.1.1.1 255.255.255.0**
> switch(config-if)#**no shutdown**

To enable management from a remote network, you must also configure the default gateway. Use the following command in global configuration mode:

> switch(config)#**ip default-gateway 1.1.1.254**

You can also assign TCP/IP configuration settings using the following methods:

|Method|Description|
|---|---|
|Dynamic Host Configuration Protocol (DHCP)|A DHCP server is a special server configured to pass out IP address and other IP configuration information to network clients:<br><br>- The DHCP server is configured with a range of IP addresses it can assign to hosts.<br>- The DHCP server can also be configured to pass out other IP configuration, such as the default gateway and DNS server addresses.<br>- The DHCP server ensures that each client has a unique IP address.<br>- DHCP is a TCP/IP protocol. Any client configured to use DHCP can get an IP address from any server configured for DHCP, regardless of the operating system.<br><br>DHCP requires a DHCP server and minimal configuration. You can use the **ip address dhcp** command to configure a switch (or a router) to get its IP address from a DHCP server. The DHCP server can be configured to deliver the default gateway and DNS server addresses to the Cisco device as well. The manually configured default gateway address overrides any address received from DHCP.|
|Automatic Private IP Addressing (APIPA)|APIPA is a Microsoft implementation of automatic IP address assignment without a DHCP server. Using APIPA, hosts assign themselves an IP address on the 169.254.0.0 network (mask of 255.255.0.0). With APIPA:<br><br>- The host is configured to obtain IP information from a DHCP server (this is the default configuration).<br>- If a DHCP server can't be contacted, the host uses APIPA to assign itself an IP address.<br>- The host configures only the IP address and mask. It does not assign itself the default gateway and DNS server addresses. For this reason, APIPA can be used only on a single subnet.<br><br>Use APIPA as a fail-safe to provide limited communication capabilities when a DHCP server is unavailable.|
|Static (manual) assignment|Using static addressing, IP configuration information must be manually configured on each host. Use static addressing:<br><br>- On networks with a very small number of hosts.<br>- On networks that do not change often or that will not grow.<br>- To permanently assign IP addresses to hosts that must always have the same address (such as printers, servers, or routers).<br>- For hosts that cannot accept an IP address from DHCP.<br>- To reduce DHCP-related traffic.<br><br>Static addressing is very susceptible to configuration errors and duplicate IP address configuration errors (where two hosts are assigned the same IP address). Static addressing also disables both APIPA and DHCP capabilities on the host.|





---
# References
