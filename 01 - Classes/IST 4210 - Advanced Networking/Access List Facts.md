2024/11/29 14:04
Status: #idea
Tags:

# Access List Facts

Routers use access control lists (ACLs) to control incoming or outgoing traffic. As such, a carefully designed access list provides a measure of security to both the router and any connected networks. You can use an access list to prevent some forms of internet attacks or to restrict the devices that are allowed to send packets through a router.

A router that uses access lists is a form of firewall because it allows or denies the flow of packets between networks. You can use a Cisco router with access list statements to protect your private network from the internet or to protect internet servers from specific attacks.

This lesson covers the following topics:

- Access control lists
- Access list types
- ACL placement

## Access Control Lists

Be familiar with the following characteristics of an ACL:

- An access list describes the traffic type that will be controlled.
- Access list entries:
    - Describe the traffic characteristics.
    - Identify either permitted or denied traffic.
    - Can describe a specific traffic type. They can also allow or restrict all traffic.
- When created, an access list contains an implicit deny any entry statement at the end of the access list (although not shown). This means that if an ACL rule has not been applied by the end of the list, that packet will be dropped or denied. As a result, each access list must have at least one permit statement, either permitting a specific traffic type or permitting all traffic not specifically restricted.
- Each access list applies only to a specific protocol.
- Each router interface can have up to two access lists. One can be used for incoming traffic and the other for outgoing traffic.
- When an access list is applied to an interface, it identifies whether the list restricts incoming or outgoing traffic.
- Access lists exist globally on the router but filter traffic for only the interfaces to which they have been applied.
- Each access list can be applied to more than one interface. However, each interface can have only one incoming and one outgoing list per protocol.
- Access lists can be used to log traffic that matches the list statements.
- Access lists applied to inbound traffic filter packets before the routing decision is made. Access lists applied to outbound traffic filter packets after the routing decision is made.

## Access Lists Types

When working with Cisco routers, there are two types of ACLs commonly used; standard and extended.

|ACL Type|Description|
|---|---|
|Standard IP|Standard ACLs can be used to permit or deny traffic based only on the source IP address. Standard ACLs don't care about where the package is being sent, just the packet origin. Standard ACLs should be placed as close to the destination as possible.|
|Extended IP|An extended ACL can be used to permit or deny traffic based on source and destination IP address. Extended ACLs are also used to permit or deny traffic based on port numbers and different types of traffic such as TCP and UDP.|

Both standard and extended ACLs can be created using either an ID number or a name. When a name is used, the access list is known as a named access list.

Standard access lists:

- Filter only on source hostname or host IP address
- Should be placed as close to the destination as possible
- Use the following numbering ranges:
    - 1–99
    - 1300–1999

## ACL Placement

After you have created an access list, you must apply it to an interface. In many cases, this means you will need to decide which router, which port, and which direction to apply the access list.

Keep in mind the following:

- The access list is applied to traffic with a specific direction (either in or out).
- Each interface can have only one inbound and one outbound access list for each protocol. This means that an interface can have either a standard inbound or an extended inbound IP access list, but not both.
- You can have two access lists for the same direction applied to an interface if the lists restrict different networking protocols. For example, you can have one outbound IP access list and one outbound Telnet access list.
- When constructing access lists, place the most restrictive statements at the top. Traffic is matched to access list statements in the order they appear in the list, top to bottom. As soon as traffic matches a statement in the list, subsequent (lower) statements will not be applied to the traffic.
- As a general rule, apply standard access lists as close to the destination router as possible. You do this because standard access lists can filter only on source address. Placing the list too close to the source will prevent any traffic from the source from getting to any other parts of the network.
- As a general rule, apply extended access lists as close to the source router as possible. This way the packet can be dropped as quickly as possible.
- When making placement decisions, carefully read all access lists statements and requirements. Identify blocked and allowed traffic, as well as the direction that traffic will be traveling. Place the access list on the interface where a single list will block, or allow, all necessary traffic.





---
# References
