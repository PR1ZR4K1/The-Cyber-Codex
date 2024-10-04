2024/10/01 23:42
Status: #idea
Tags: [[DHCP]]

# DHCP Configuration Facts

When configuring a Cisco router as a DHCP server, be aware that the router uses the DHCPDISCOVER packet to obtain the IP subnet in which the DHCP client resides. The router can assign an IP address from a pool of valid IP addresses in that subnet.
## Pre-Configuration Steps

Before discussing the configuration steps, be aware of the following preparation steps:

1. Identify an external database agent with a URL.
2. Identify the IP address range to be assigned by the DHCP server. This may include:

- The subnet address and mask
- IP address exclusions (addresses you don't want assigned)

4. Identify DHCP options where necessary. This may include:

- The default gateway
- DNS server addresses
- NetBIOS name server
- VoIP options, such as option 150

6. Identify the DNS domain name.

## Configuration Commands

The following table lists commands you can use to configure the DHCP service on a Cisco router:

|Command|Action|
|---|---|
|Router(config)# **service dhcp**|Enables DHCP features on the router.<br><br>This is enabled by default.|
|Router(config)# **no ip dhcp conflict logging**|Forces the DHCP server not to log IP address conflicts.|
|Router(config)# **ip dhcp excluded-address _[address]_**  <br>Router(config)# **ip dhcp excluded-address _[start_ip]_ _[end_ip]_**|Prevents an address from being assigned by the DHCP server. If there is a range of addresses that needs to be excluded, identify the start and ending addresses. Typically, you will exclude the DHCP server's own IP address from the range.<br><br>This command is a global configuration command; it is not issued as part of the pool.|
|Router(config)# **ip dhcp pool _[VLAN_ID]_**|Configures a DHCP address pool on the specified VLAN. Pools are used to define a range of addresses to assign, as well as to create bindings.|
|Router(dhcp-config)# **network _[address]_ _[mask]_**|Sets the network address and subnet mask for a DHCP address pool.<br><br>Clients are assigned IP addresses starting from the lowest possible IP address in the network.|
|Router(dhcp-config)# **domain-name _[domain]_**|Sets the domain name to be delivered to DHCP clients.|
|Router(dhcp-config)# **dns-server _[server1_ip]_ _[server2_ip]_**|Sets the DNS server address to be delivered to DHCP clients. You can configure multiple DNS server addresses. To do this, you include multiple addresses separated by a space. You can specify up to 8 server addresses. Servers should be listed in order of preference.|
|Router(dhcp-config)# **default-router _[router_ip]_**|Sets the default router address to be delivered to DHCP clients. This address should be inside the address pool. You can identify up to 8 addresses. However, most hosts can accept only a single default gateway address.|
|Router(dhcp-config)# **lease _[days]_**|Sets the lease duration (in days) for a DHCP address pool. You can specify a value between **0** and **365**.<br><br>Use the **infinite** keyword for a lease that does not expire.|
|Router(dhcp-config)# **host _[address]_ _[mask]_**  <br>Router(dhcp-config)# **client-identifier _[mac_address]_**|Manually binds a specific IP address and mask to a host. When you create a binding, you create a separate pool that is different than the pool that identifies the subnet. This pool must have a unique name. Observe the following guidelines:<br><br>- You configure the IP address and mask that will be assigned to the host.<br>- Only one manual binding can be configured per host pool.<br>- Bindings for DHCP clients require the client-identifier command. The unique identification of the client is specified in dotted hexadecimal notation; for example, 01aa.bbcc.ddee.ff, where 01 represents the Ethernet media type. Media types are:<br>    - 1:Ethernet<br>    - 5:IEEE 802 Networks<br>    - 17:HDLC<br>    - 20:Serial Line<br>- Devices using a BOOTP request should have their MAC address identified using the hardware-address command.<br>- The host DHCP pool configuration command can use the prefix notation (e.g., /24) or subnet address representation (e.g., 255.255.255.0) to identify the client network mask.|
|Router(config-subif)# **ip helper-address _[address]_**|Enables the DHCP relay agent feature.|
|Router(config)# **no ip forward-protocol udp _[port]_**|Controls which broadcast packets and protocols are forwarded by a DHCP relay agent. The value is either a port number or name, such as the following well-known UDP broadcast ports:<br><br>- 37: Time<br>- 49: TACACS<br>- 53: DNS<br>- 67: BOOTP/DHCP Server<br>- 68: BOOTP/DHCP Client<br>- 69: TFTP<br>- 137: NetBIOS Name Service<br>- 138: NetBIOS Datagram Service|
|Router# **show ip dhcp binding**|Displays information about each IP address lease.|
|Router# **show ip dhcp pool _[pool_name]_**|Displays information about the DHCP address pools, including the following:<br><br>- Pool name<br>- High and low utilization level for the pool<br>- Size of the requested subnets<br>- Total number of addresses in the pool<br>- Number of leased addresses in the pool<br>- Number of allocated subnets to the address pool<br>- IP address range of the subnets<br>- Number of leased addresses from each subnet<br>- Number of excluded addresses<br>- Number of reserved addresses in the pool and the reserved addresses<br>- Short name of the interface connected to the client using the reserved address|
|Router# **show ip dhcp server statistics**|Displays DHCP server statistics.|
|Router# **show ip dhcp conflict**|Displays IP addresses with conflicts as well as the method used to identify them:<br><br>- Gratuitous ARP (detected by the client)<br>- Ping (detected by the server)<br><br>If an address conflict is detected, the address is removed from the pool and the address is not assigned until an administrator resolves the conflict.|
|Router# **clear ip dhcp conflict**|Clears the address conflict list.|
|Router# **show ip dhcp database**|Displays DHCP server database agent information, including the following:<br><br>- Remote file used to store automatic DHCP bindings<br>- Last date and time bindings were read and written from the server<br>- Whether the last read or write of host bindings was successful<br>- Number of failed and successful file transfers|
|Router# **show hosts**|Displays the default domain name, the style of name lookup service, a list of name server hosts, and the cached list of hostnames and addresses.|
|Router(config)# **interface vlan 1**  <br>Router(config-if)# **ip address dhcp**|Configures an interface on a Cisco device to get its IP address from the DHCP server. Most routers and servers have static IP addresses and do not use DHCP for obtaining an IP address. If you choose to use DHCP, then create a binding to make sure the same address is always assigned to network infrastructure devices, such as servers, switches, and routers.|

The following commands configure a DHCP pool on VLAN2 that distributes addresses to DHCP clients from the 172.17.0.0/16 address range using a lease time of 5 days. The IP addresses between 172.17.0.1 and 172.17.0.25 are excluded. The default router and DNS server addresses are also distributed to DHCP clients:

> Router(config)#**ip dhcp excluded-address 172.17.0.1**
> Router(config)#**ip dhcp excluded-address 172.17.0.25**
> Router(config)#**ip dhcp pool VLAN2**
> Router(config-if)#**interface fa0/1.1**
> Router(dhcp-config)#**network 172.17.0.0 255.255.0.0**
> Router(dhcp-config)#**domain-name westsim.com**
> Router(dhcp-config)#**dns-server 172.17.0.2 8.8.8.8**
> Router(dhcp-config)#**default-router 172.17.0.1**
> Router(dhcp-config)#**lease 5**

In the following example, the router's Fast Ethernet 0/0 interface is configured with an IP address in the 172.16.10.0 network and will forward DHCP broadcast messages to a DHCP server that has an IP address of 172.31.1.1. It will also not forward packets sent to the NetBIOS ports:

> Router(config)#**int fa 0/0**
> Router(config-if)#**ip address 172.16.10.254 255.255.255.0**
> Router(config-if)#**ip helper-address 172.31.1.1**
> Router(config-if)#**no ip forward-protocol udp 137**
> Router(config-if)#**no ip forward-protocol udp 138**





---
# References

- [[DHCP]]