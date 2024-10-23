2024/10/18 16:44
Status: #MOC
Tags:

# Dynamic Routing Facts

Routing protocols share routing information between devices. These protocols have four main responsibilities:

- Discover remote networks
- Record and store current routing information
- Select the best path to each destination
- Provide a backup path

This lesson covers the following topics:

- RIP vs. dynamic routing
- Internal vs. external routing
- Load balancing
- Best path determination
- Protocols used by IP version

## RIP vs. Dynamic Routing Protocols

As computer networks became more complex and more widespread, Routing Information Protocol (RIP) was improved, but it just wasn’t enough to keep up with the demands larger networks. Although RIP is still used for smaller networks, additional protocols have been designed to support larger networks. Dynamic protocols are now most commonly used, especially for larger networks.

Dynamic routing protocols have three main components:

- Data structures
- Routing protocol messages
- Algorithms

Dynamic protocols are useful for any network with multiple routers. These protocols work well to accommodate network growth. Additionally, dynamic protocols automatically adapt to reroute traffic when needed. Because the router is continuously advertising information about the network to neighboring devices, dynamic protocols are not secure without additional configuration. When considering dynamic routing, keep in mind that it's complex to implement and has increased CPU, RAM, and bandwidth requirements for ongoing communication, processing, and storage.

## Internal vs. External Routing

Each organization with an assigned network address from an ISP is considered an autonomous system (AS). The AS is free to create one large network or divide the network into segments (subnets). Each autonomous system is identified by an AS number. This number can be either locally administered or registered if the AS is connected to the internet.

Routers are used within an autonomous system to segment the network. In addition, autonomous systems are used to connect multiple autonomous systems together. Internal routing protocols, also known as Interior Gateway Protocols (IGPs), are used to send information between devices within an organization’s routing domain. An external routing protocol, External Gateway Protocol (EGP), is used by ISPs to send packets across the internet from one network to another. The following table identifies protocols classified as IGPs and EGPs.

|Classification|Protocols|
|---|---|
|Interior Gateway Protocols (IGPs)|IGPs include the following:<br><br>- Routing Information Protocol (RIP)<br>- Open Shortest Path First (OSPF)<br>- Interior Gateway Routing Protocol (IGRP)<br>- Intermediate System-to-Intermediate System (IS-IS)<br>- Enhanced IGRP (EIGRP)|
|Exterior Gateway Protocols (EGP)|Border Gateway Protocol (BGP) is an EGP.|

BGP is an external routing protocol that coordinates routing between autonomous systems on the internet. BGP routing tables are a list of AS numbers across the internet and the next hop required to get to them. Once the BGP delivers data from the internet to your network, interior gateway protocols (RIP, OSPF, and EIGRP) are used to route traffic within the AS that is your network.

## Load Balancing

In the event a router has more than one path to the same destination with the same cost metric, the router will forward the packets using both paths. This process is called _equal cost load balancing_ . The routing table has one destination but uses a different exit interface to forward packets on each of the equal cost paths. Load balancing is automatically implemented by dynamic routing protocols and can improve network performance.

## Best Path Determination

Routing protocols consider various routes to a destination and select a route based on the distance to that network. The best path is the path with the lowest metric. Each protocol has a different method for setting metrics as shown in the following table:

|Routing Protocol|Metric|
|---|---|
|Routing Information Protocol (RIP)|RIP considers hop count. _Hop count_ is determined by the number of routers along a path. Each router equals one hop count. No more than 15 hop counts are permitted for a route.|
|Open Shortest Path First (OSPF)|OSPF considers the cost. Cost is determined by the total bandwidth available from origination to destination. Better bandwidth gets a lower cost. Slower bandwidth gets a higher cost.|
|Enhanced Interior Gateway Routing Protocol (EIGRP)|EIGRP uses a metric that considers the slowest bandwidth, dependability of a path, load, and delay values.|

There are three primary algorithms used to determine the best path:

- Distance vector
- Link state
- Path vector

## Protocols Used by IP Version

The following table identifies protocols used by IPv4 and IPv6:

|IP Version|Distance Vector|Link-State|Path Vector|
|---|---|---|---|
|IPv4|RIPv2<br><br>EIGRP|OSPFv2<br><br>IS-IS|BGP-4|
|IPv6|RIPng<br><br>EIGRP for IPv6|OSPFv3<br><br>IS-IS for IPv6|BGP-MP|





---

# References

- [[Static Route Command List]]