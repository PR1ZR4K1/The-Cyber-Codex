2024/10/27 23:33
Status: #MOC
Tags:

# Homework 9

P1a.     Looking at the topology diagram, how many networks are there in total?

5

P1b.    How many networks are directly connected to R1, R2, and R3?

3

P1c.     How many static routes are required by each router to reach networks that are not directly connected?

2

P1d. 
Why were you unsuccessful?

Without a routing protocol or defined static routes the routers have no clue how to get to the specified destination and instead drops the packet.

1a.     What is recursive static route?
A recursive static route includes the ip address of the next hop it will have to take in order to reach the specified network

1b.    Why does a recursive static route require two routing table lookups?
First the router would need to look up the destination ip in the routing table and finds the next hop address. The second lookup identifies the interface the router should use to reach the destination.

2a.     How does a directly attached static route differ from a recursive static route? 
A directly attached static route specifies the exit interface the router will use to reach the destination whereas a static route will specify the next hop's ip address.

2b.    Which command only displays directly connected networks?
show ip route connected

2c.     Which command only displays the static routes listed in the routing table?
show ip route static

2d.    When viewing the entire routing table, how can you distinguish between a directly attached static route and a directly connected network?

The letters `C` and `S` denote directly connected and directly attached static route respectively

3a. How does a default route differ from a regular static route? 
A default route should normally be somewhat of a last resort route in that any packets with destination addresses that don't match with what is currently in the routing table it will go to the default route.

3b. How is a static route displayed in the routing table?

S

4a. a static route that specifies the next-hop and exit interface route command: ip route 172.31.0.0 255.255.255.0 S0/0/1 172.31.1.197 
4b. route for R3 to R2: ip route 172.31.0.0 255.255.255.0 S0/0/1 172.31.1.197 route for R3 to network between r2 and R1: ip route 172.31.1.192 255.255.255.252 S0/0/1 172.31.1.197 
4c. ip route 172.31.1.0 255.255.255.128 S0/0/1 172.31.1.197



---
