2024/10/28 21:20
Status: #idea
Tags: [[OSPF Facts]]

# OSPF Facts

The Open Shortest Path First (OSPF) routing protocol is a robust link-state routing protocol well suited for large networks.

This lesson covers the following topics:

- OSPF characteristics
- OSPF configuration
- Areas and borders
- Passive interfaces and default routes

## OSPF Characteristics

OSPF dynamically creates and maintains routing tables on each router based on the information it gathers. Be aware that OSPF:

- Is a public (non-proprietary) routing protocol.
- Is considered a classless routing protocol because it does not assume the default subnet masks are used.

- Sends the subnet mask in the routing update.
- Supports manual route summarization and VLSM.
- Does not perform automatic route summarization.

- Is not susceptible to routing loops.

- Uses built-in loop avoidance techniques.
- Eliminates the need for mechanisms such as hold-down timers, split horizon, or poison reverse.

- Is scalable and does not have the 16-hop limitation of RIP.
- Uses link costs (bandwidth) as a metric for determining best routes. The Shortest Path First (SPF) algorithm (also called Dijkstra's algorithm) is used to identify and select the optimal route.
- Supports load balancing over equal-cost paths. Up to 16 equal-cost paths can be used; the default is 4.
- Sends out only updated information rather than exchanging the entire routing table under normal conditions.
- Converges faster than a distance vector protocol. Following convergence, sends updates when routes change or every 30 minutes.
- Requires additional processing power and, therefore, increased system requirements. Good design can minimize this impact.

Be familiar with the following OSPF terms:

|OSPF Terms|Description|
|---|---|
|Link-State Routing Protocol|A set of rules the router uses to obtain information about neighboring routers and the state of their links.|
|Hello packets|Messages that are sent out and received by OSPF routers. These messages are used to establish adjacencies. Adjacencies are also referred to as neighbor relationships.|
|Link-state advertisements (LSA)|Messages that routers send out to routers within their own areas. LSAs include the routing topology of local routers.|
|Link-state database|Data stored in each OSPF router that contains a global view of every link in the autonomous system.|

## OSPF Configuration

OSPF routers share route information only with adjacent neighbor routers. The following conditions must be met for two routers to become fully adjacent:

- Both routers must be on the same subnet and use the same subnet mask.
- Both routers must have the same hello and dead intervals configured.
    
    The dead interval indicates the time allowed without an expected hello packet. If a periodic hello packet has not been received within the dead interval, the router assumes its neighbor has gone offline.
    
- Both routers must use the same OSPF area.
- If authentication is required, both routers must pass the authentication requirements.
- The stub area flag (value) for each router must match.

To minimize the traffic caused by routing updates, OSPF defines the following router roles:

|Role|Description|
|---|---|
|Designated Router (DR)|On each subnet, one OSPF router is chosen as the DR. The DR coordinates the routing table updates for all routers on the subnet:<br><br>- Other routers send information to the DR.<br>- The DR manages the changes and forwards any necessary information to the other routers on the subnet.|
|Backup Designated Router (BDR)|On each subnet, a single OSPF router is identified as the BDR. The BDR becomes the DR if the DR becomes unavailable.|

Be aware of the following facts about the DR and BDR:

- Based on the network link type, a DR/BDR might not be used.

- A DR/BDR is used on broadcast networks (such as Ethernet) where multiple routers exist on the same subnet.
- For point-to-point networks, a DR/BDR is not used.
- By default, the network type is identified based on the media type used.
- You can manually configure the network type if desired.

- If the network type uses a DR/BDR, a single DR and a single BDR is identified for each subnet.
- When routers first come online, they exchange hello packets. Part of this process is used to elect (identify) the DR and the BDR. The following values are used to elect the DR and BDR:

- The router with the highest OSPF priority becomes the DR. The priority value is a number between 0-255. By default, all routers have a priority of 1.
- If two or more routers have the same highest priority value, the router with the highest router ID becomes the DR. The router ID is a 32-bit number expressed in A.B.C.D format. The router ID for a specific router is chosen in the following order:

1. For a specific OSPF process, you can manually configure a router ID. If a router ID has been configured, that value is used.
2. If no router ID has been manually configured, the system uses the highest IP address assigned to a loopback address.
3. If the router does not have a loopback address, the router ID is the highest IP address assigned to any interface in the up state.

Using a loopback address is preferred over using the interface IP address because it allows you to control which router becomes the DR and because loopback interfaces never go down. If an interface address is used for the router ID, the router ID might change if that interface goes down.

- In most cases, the BDR is the router with the next highest priority or router ID.
- Configuring a priority of 0 for a router means that the router will never become the DR or BDR.
- Once a DR has been elected, it remains the DR, even if another router with a higher priority or router ID comes online. You must clear or reset the OSPF process to force a new election.
- If the DR goes down, the BDR automatically becomes the DR.
- When the original DR comes back online, it will not automatically resume the DR role unless a reset is performed.

## Areas and Borders

Areas are used to subdivide large networks. Routers within an area share information about the area.

|Terms|Description|
|---|---|
|Area border routers (ABR)|Routers on the edge of areas that share summarized information between areas.|
|Backbone|A backbone:<br><br>- Is a specialized area connected to all other areas.<br>- Contains networks not held within another area and distributes routing information between areas.<br>- Has an address of 0.0.0.0.<br>- Is required on all OSPF networks.|
|Stub|An area with a single path into and out of the area.|

## Passive Interfaces and Default Routers

If you configure a passive interface in OSPF, the interface:

- Won't send hello messages.
- Ignores received hello messages.
- Won't form adjacencies (neighbor relationships).
- Won't send or receive LSAs.
- Won't build routing tables.

There are times when a passive interface is the best choice. For example, when:

- OSPF is running on a low-bandwidth connection.
- OSPF updates are traversing the WAN.
- The connection between routers is being serviced by a static route. Static routes don't need OSPF running across the link.

When there is no specified path to get to a location, data will follow a default route. This default route is sometimes called a gateway of last resort. It is best practice to define a default route on a single exit point that connects to the internet because:

- It keeps public routes from being propagated and stored on the routing tables of the internal routers.
- It points to the ISP. The ISP will be the gateway of last resort.
- When a request comes to reach a network that isn't in your routing table, it will be forwarded to the ISP.

Default routes can be defined on internal routers, too. This will send any unrecognized packets to the border router, which will then send the packets to the ISP. To define a default route on all the internal routers, use the default-information originate command on the border router. This command will advertise that default route to its downstream neighbors.





---
# References

- [[OSPF Configuration IPv4]]