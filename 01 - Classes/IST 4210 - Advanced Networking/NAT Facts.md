2024/11/29 11:01
Status: #idea
Tags:

# NAT Facts

Network Address Translation (NAT) allows you to connect a private network to the internet without obtaining registered addresses for every host. Private addresses are translated to the public address of the NAT router. NAT can be used to provide a measure of security for your private network or to provide internet connectivity with a limited number of registered IP addresses.

This lesson covers the following topics:

- NAT terminology
- NAT methods
- NAT configuration
- NAT monitoring

## NAT Terminology

As you work with NAT, it's important to understand the following terminology:

|Term|Definition|
|---|---|
|Inside|The inside network is the private network. A router interface that connects to the private network is also called the inside interface.|
|Outside|The outside network is the public network (the internet). A router interface that connects to the public network is also called the outside interface.|
|Inside local address|The inside local address is the IP address of the host on the inside network.|
|Inside global address|The inside global address is the IP address of the host after it has been translated for use on the internet. The term global refers to the registered IP address that identifies the inside host on the internet.|
|Outside global address|The outside global address is an IP address of an internet host. For example, when you visit a web site, your computer uses the global outside address to contact the web server.|
|Outside local address|An outside local address is an outside global address that has been translated for inside (or private) use. In other words, the NAT router translates an internet host IP address into a private IP address. Instead of using the web server address, the internal computer will use the translated address.|

## NAT Methods

When configuring NAT, you can use the following methods:

|Method|Description|
|---|---|
|Dynamic NAT|Use dynamic translation to translate a range of outside addresses to a range of inside addresses. Use this option when you have multiple public addresses for multiple private addresses. If the number of inside addresses is greater than the number of outside addresses, use the overloaded option with dynamic NAT.<br><br>To configure dynamic NAT, use the following general process:<br><br>1. Define the pool of outside addresses that can be used for translation.<br>2. Create an access list that allows the specified inside addresses to be translated.<br>3. Link the pool with the access list.<br>4. Identify the router interface that is the inside interface and the interface that is the outside interface.<br><br>The number of inside hosts that can gain outside access will be limited to the number of outside addresses in the pool. When you have fewer outside addresses than inside hosts, add the overloaded parameter to step 3. This uses dynamic NAT with PAT.|
|Static NAT|Use static translation to translate a single outside address to a single inside address. To configure static NAT, use the following general process:<br><br>1. Define a static map that associates the inside address with the outside address.<br>2. Identify the router interface that is the inside interface and the interface that is the outside interface.|
|Overloaded NAT  <br>or PAT|Use overloaded NAT or Port Address Translation (PAT) to translate multiple inside addresses to a single public address. Port numbers are used to identify specific inside local hosts. The port number associated with the private host is appended to the inside global IP address. Use this option to allow multiple inside hosts to access the internet using a single public IP address.<br><br>To configure overloaded NAT, use the following general process:<br><br>1. Create an access list that allows the specified inside addresses to be translated.<br>2. Link the access list to the internal interface using the overloaded option. The IP address assigned to the outside interface is automatically used as the outside address for all inside hosts.<br>3. Identify the router interface that is the inside interface and the interface that is the outside interface.|

## NAT Configuration

Configuring NAT on a Cisco router may be done through the command line interface (CLI) or the Security Device Manager (SDM). When using the SDM to configure NAT, start the wizard to help you choose the NAT configuration parameters:

- Choose Basic NAT to identify the inside and outside interfaces. Selecting this option configures overloaded NAT with PAT. The public address assigned to the public interface is used for all private hosts.
- Choose Advanced NAT to:

- Identify the outside interface.
- Configure additional public addresses that can be used for dynamic translation.
- Identify inside interfaces and additional network addresses that are not directly connected to the NAT router that will be translated. This option lets you configure a single NAT router for your entire private network, even when your network consists of multiple subnets accessible through other routers on the private network.
- Perform static mappings that translate a public IP address to a private host address. With this option, hosts on the private network are assigned a private IP address, and the private IP address is mapped to a public IP address. Incoming communications sent to the public IP address are translated and forwarded to the private host. The wizard calls these mappings NAT rules.

To start the NAT wizard, the router must have at least two enabled interfaces.

When configuring a router for NAT, be sure to use an IP address in the private IP address ranges for the inside local IP addresses. If you don't, hosts on your network might not be able to access outside hosts with the same IP address. A Cisco router can be configured to overcome this problem, but the configuration is difficult. Private IP addresses do not need to be registered and fall within the following ranges:

- 10.0.0.0 to 10.255.255.255
- 172.16.0.0 to 172.31.255.255
- 192.168.0.0 to 192.168.255.255

The following table lists the configuration steps and commands for each method:

|Method|Configuration Task|Command Examples|
|---|---|---|
|Static NAT|Configure static mappings (map inside local addresses to outside local addresses)|router(config)# **ip nat inside source static 192.168.1.1 203.44.55.1**|
|Identify inside and outside interfaces|router(config)# **interface ethernet0**  <br>router(config-if)# **ip nat inside**  <br>router(config-if)# **interface serial0**  <br>router(config-if)# **ip nat outside**|
|Overloaded NAT or PAT|Identify allowed translated inside local addresses|router(config)# **access-list 1 permit 192.168.1.0 0.0.0.255**|
|Associate the allowed list with the outside interface and identify the translation type as overloaded|router(config)# **ip nat inside source list 1 interface serial0 overload**|
|Identify inside and outside interfaces|router(config)# **interface ethernet0**  <br>router(config-if)# **ip nat inside**  <br>router(config-if)# **interface serial0**  <br>router(config-if)# **ip nat outside**|
|Dynamic NAT|Define an inside global address pool|router(config)# **ip nat pool pooled_addr 203.44.55.1 203.44.55.254 netmask 255.255.255.0**|
|Identify allowed translated inside local addresses|router(config)# **access-list 1 permit 192.168.1.0 0.0.0.255**|
|Associate the allowed list with the pool|router(config)# **ip nat inside source list 1 pool pooled_addr**|
|Identify inside and outside interfaces|router(config)# **interface ethernet0**  <br>router<(config-if)# **ip nat inside**  <br>router(config-if)# **interface serial0**  <br>router(config-if)# **ip nat outside**|

In the following example, you have been given six public addresses from your ISP (177.211.5.89 to 177.211.5.94) which use a 29-bit mask. You will use one of those addresses for the router interface. Use the remaining 5 addresses for dynamic NAT with PAT for inside hosts. Configure internet access for all inside hosts on the 10.0.1.0/24 network. The following commands create the pool, define the allowed inside addresses, link the access list to the pool, and configure the inside and outside interfaces:

> router(config)#**ip nat pool public_addr 177.211.5.90 177.211.5.94 netmask 255.255.255.248**
> router(config)#**access-list 1 permit 10.0.1.0 0.0.0.255**
> router(config)#**ip nat inside source list 1 pool public_addr overload**
> router(config)#**int eth0/1**
> router(config)#**ip addr 10.0.1.1 255.255.255.0**
> router(config-if)#**ip nat inside**
> router(config-if)#**int ser0/1/0**
> router(config-if)#**ip addr 177.211.5.89 255.255.255.248**
> router(config-if)#**ip nat outside**

The ip nat pool command can use the prefix-length keyword instead of the netmask keyword, as in the following example:

> **ip nat pool public_addr 177.211.5.89 177.211.5.94 prefix-length 29**

## NAT Monitoring

Use the following commands to monitor NAT:

| Command                              | Description                                                                                      |
| ------------------------------------ | ------------------------------------------------------------------------------------------------ |
| router# **clear ip nat translation** | Deletes the dynamic entries in the NAT table.                                                    |
| router# **show ip nat statistics**   | Displays counters for packets and NAT table entries, as well as basic configuration information. |
| router# **show ip nat translations** | Displays the NAT/PAT translation table entries.                                                  |





---
# References
