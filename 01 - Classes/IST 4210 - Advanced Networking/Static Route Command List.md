2024/10/18 15:27
Status: #MOC
Tags:

# Static Route Command List

You can add remote network routes to a routing table using static routing protocols or dynamic routing protocols. Routing tables manually enter static routes that go from one device to another.

This lesson covers the following topics:

- Configure IP static routes
- Configure IP default static routes
- Configure floating static routes

## Configure IP Static Routes

When you are configuring a static route, the next hop can be provided using an IP address or an exit interface. The following table identifies the static routes used:

|Route|Description|
|---|---|
|Next-hop route|The next-hop IP address is provided|
|Directly connected static route|The next-hop IP address and the exit interface are both specified|

The following commands can be used to configure a static route on a network:

| Command                                                                                                           | Description                                                                                                         |
| ----------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| Router(config)# **ip route** **_network-address subnet-mask { ip-address \| exit-intf [ip-address]} [distance]_** | Configures a static route on an IPv4 network. Note that the administrative distance defaults to 1 if not specified. |
| Router(config)# **ip route** **_network-address subnet-mask { ip-address \| exit-intf [ip-address]} [distance]_** | Configures a static route on an IPv6 network. Note that the administrative distance defaults to 1 if not specified. |

## Configure IP Default Static Routes

The command for an IPv4 default static route is similar to other static routes, except that you use the network address 0.0.0.0 and the subnet mask 0.0.0.0. This way, the route will match any destination address. Because of this format, default static routes are frequently referred to as quad-zero routes.

| Command                                                                  | Description                                           |
| ------------------------------------------------------------------------ | ----------------------------------------------------- |
| Router(config)# **ip route 0.0.0.0 0.0.0.0 _{ip-address \| exit-intf}_** | Configures a default static route on an IPv4 network. |
| Router(config)# **ipv6 route ::/0 _{ipv6-address \| exit-intf}_**        | Configures a default static route on an IPv6 network. |
| Router# **show ip route static**                                         | Shows the static routes listed in the routing table.  |

## Configure Floating Static Routes

To configure a floating static IP route, you use the following commands:

|Command|Description|
|---|---|
|Router(config)# **ip route** **_network-address subnet-mask { ip-address \| exit-intf [ip-address]} [distance]_**|Configures a floating static route on an IPv4 network. You must increase the administrative distance of the floating route to ensure that it is higher than your default static route and that it is used only as a backup.|
|Router(config)# **ip route** **_network-address subnet-mask { ip-address \| exit-intf [ip-address]} [distance]_**|Configures a floating static route on an IPv6 network. Note that the administrative distance defaults to 1 if not specified. You must increase the administrative distance of the floating route to ensure that it is higher than the default static route and that it is used only as a backup.|

The floating static routes will not show up in **show ip route** or **show ipv6 route** .





---

# References

- [[Dynamic Routing Facts]]