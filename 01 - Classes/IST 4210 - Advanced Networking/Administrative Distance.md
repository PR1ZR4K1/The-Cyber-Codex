2024/10/17 20:41
Status: #idea
Tags:

Administrative distance (AD) is a value used to rank route sources, such as a static route or a specific routing protocol. Routers use administrative distance to determine the best path when there are multiple sources of information about remote networks. It is not uncommon for routers to be configured with a combination of static routes and multiple routing protocols. As a result, there may be more than one route source for the same remote network. The AD determines the trustworthiness of the route source.

AD helps routers determine which source is most trustworthy and which routing protocol or source will populate the routing table. Routing protocols use metrics to determine the path to take when there's more than one way to get to a remote network. Each routing protocol uses different factors for metrics. For example, RIP focuses on the hop count metric. The hop count is the number of routers data will be routed through to get to the destination network. OSPF is a more efficient protocol that relies on a metric called cost. The cost is determined based on the bandwidth of the available connections. EIGRP considers bandwidth, delay, load, and reliability.

Assuming that two routes are available to the same location, the router will use the following criteria for choosing between these routes:

- If a static route is available, it will be selected.
- If a router learns of two routes to a remote network through different routing protocols (such as RIP and OSPF), it will choose the route with the lowest administrative distance; OSPF in this example.
- If a router learns of two routes through the same protocol (for example two routes through EIGRP), the router will choose the route that has the best cost as defined by the routing metric. For EIGRP, the link with the highest bandwidth and least delay will be used.

You can modify how routes are selected by modifying the administrative distance associated with a source. The route with the lowest AD is chosen.

The following table lists the various route sources and their administrative distances:

|Route Source|Description|
|---|---|
|Connected|0|
|Static|1|
|EIGRP summary route|5|
|External BGP|20|
|Internal EIGRP|90|
|IGRP|100|
|OSPF|110|
|IS-IS|115|
|RIP|120|
|External EIGRP|170|
|Internal BGP|200|





---
# References
