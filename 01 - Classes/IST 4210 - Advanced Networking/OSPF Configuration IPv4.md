2024/10/28 22:13
Status: #idea
Tags: [[OSPF Facts]]

# OSPF Configuration IPv4


OSPF dynamically creates and maintains routing tables on each router. Based on the information it gathers, it determines the shortest route to each subnet in the network. OSPF is scalable on very large networks. On these large networks, it’s not cost-effective to manually create, maintain, and update routing tables. OSPF creates and maintains these routing tables using three processes: neighbor discovery, topology exchange, and route identification.

This lesson covers the following topics:

- Neighbor discovery
- Topology exchange
- Router identification

## Neighbor Discovery

For routers to become neighbors, they must:

- Share a data link.
- Have matching basic OSPF settings, including the OSPF area.
- Maintain an exchange of hello packets.

A designated router (DR) is used in multi-point OSPF as follows:

- The router with the highest OSPF priority is selected as the DR.
- If there is a tie for the highest priority, the router with the highest Router identification (RID) is chosen.
- The router with the second highest priority is usually selected as the backup designated router (BDR).
- Once the designated router is chosen, all of the non-designated routers exchange link-state data with it, but not with each other.

## Topology Exchange

The following table identifies the OSPF communication process.

|State|Description|
|---|---|
|Down|When an interface becomes active after being in a down state, the router multicasts an hello packet. Be aware of the following facts about hello packets:<br><br>- Hello packets contain the following information:<br><br>- A RID<br>- The area ID<br>- The priority<br>- The hello and dead intervals<br>- The designated and backup designated routers<br>- A list of neighbors<br><br>- The hello packets are sent at a configurable interval (in seconds):<br><br>- The defaults are 10 seconds for an Ethernet link and 30 seconds of a non-broadcast link.<br>- Hello packets include a list of all neighbors for which a hello packet has been received within the dead interval.<br>- The dead interval is also a configurable interval (in seconds).<br><br>- Hello packets and dead intervals work together to maintain connectivity by indicating that the link is operational. If a router does not receive a hello packet from a neighbor within the dead interval, it will declare that neighbor to be down.<br><br>The value for each hello interval must be the same within a network. Likewise, the value for each dead interval must be the same within a network.|
|Attempt|Initially, a router's list of neighbors has a null value. As soon as it receives an hello packet, it checks the following information:<br><br>- Subnet mask<br>- Subnet number<br>- Area ID<br>- Hello and dead interval settings<br>- Authentication settings|
|Init|If all of the information in the hello packet matches the router's settings, the router indicates to the neighbor that it is in the init state. The router begins to include the new RID in its list of neighbors.|
|2-way|As soon as a router receives a hello packet that includes its own RID in a list of neighbors, it has reached the 2-way state. When the 2-way state has been reached, routers may exchange link-state databases (LSDB) as follows:<br><br>- If the connection between routers is point-to-point, they will exchange link-state data.<br>- If the connection is multi-point with multiple routers attached, one of the routers is elected as a designated router (DR).<br><br>2-way is a stable neighbor state for a multi-point network.|
|Exstart|In the exstart state, the routers negotiate how the data transfer will take place and choose the initial sequence number for adjacency.|
|Exchange|In the exchange state, the two routers exchange database descriptions. Each router analyzes the description and determines the information it needs from the other router's database.|
|Loading state|In the loading state, the routers exchange link-state updates (LSUs) that contain link-state advertisements (LSAs). Once the routers exchange this information, they will have matching databases.|
|Full state|When the routers have matching databases, they have entered the full state. Full is a stable neighbor state for a multi-point network.|

A router monitors each neighbor's relationship using hello packets, the hello interval, and the dead interval. Be aware that:

- Routers react when the topology changes.
- The LSA is re-flooded throughout the network every 30 minutes as the LSA's timer refreshes.
- The database exchange process on an Ethernet link does not happen between every pair of routers on the same VLAN or subnet.
- OSPF uses the backup designated router (BDR) concept because the designated router is so important to the database exchange process. The BDR watches the status of the DR and takes over if the DR fails.
- There are two neighbor states for DR and BDR processes:

- The two-way state in which the neighbor has sent an hello packet that lists the local router's ID and the list of seen router IDs. Entering this state implies that all the neighbor verification checks passed.
- A full state in which two routers know the same link-state database details and are fully adjacent.

## Router Identification

The RID serves as a router's unique identifier for OSPF and therefore plays an important role in many of the OSPF internal functions. Given the importance of the RID, you may want to manually configure the RID of routers in the OSPF environment. Be aware of the following facts about RIDs:

- When routers send hello packets to other routers, the neighbors identify each other by their RIDs.
- Router LSAs use the RID of the originating router as the link-state ID.
- If two routers do not become neighbors, they will never exchange any information.w




---
# References

- [[OSPF Facts]]
- [[OSPF Command List]]