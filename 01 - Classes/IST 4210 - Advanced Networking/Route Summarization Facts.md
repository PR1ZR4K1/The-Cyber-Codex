**2024**/10/17 19:21
Status: #idea
Tags: [[Route Summarization]]

Route summarization groups contiguous networks that use the same routing path and advertises a single route as the destination for the grouped subnets.

This lesson covers the following topics:

- Route summarization
- Automatic summarization

## Route Summarization

The router identifies subnetted networks and combines them based on the default subnet mask. For example, a router connected to networks 10.1.0.0/16 and 10.2.0.0/16 would combine the two networks into a single network 10.0.0.0/8. This network would be reported to neighboring routers during routing exchanges.

![A router implementing route summarization by combining two networks and reporting it to neighboring routers one network.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_rtg_summ_ccna7/summarization-01.png)

Summarization reduces the size of the routing table. A single route to the summarized network takes the place of multiple routes to individual subnets. It also speeds convergence. The accessibility of each subnet address is indicated by the accessibility of the summarized address. It retains all necessary routing information, so all networks are still reachable after summarization. Also, it can happen in one of two ways:

| Method    | Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Automatic | With automatic summarization, the router identifies adjacent networks and calculates the summarized route:<br><br>- Auto-summarization is supported on classless and classful routing protocols.<br>- Auto-summarization uses the default class boundary to summarize routes.<br>- RIP (version 1 and version 2) and EIGRP support auto-summarization; OSPF does not.<br>- For RIPv2 and EIGRP, you can disable automatic summarization. |
| Manual    | With manual summarization, an administrator identifies the summarized route to advertise. The route you specify includes the summarized subnet address with the subnet mask that includes all summarized subnets.                                                                                                                                                                                                                        |

## Automatic Summarization

Automatic summarization summarizes routes along class boundaries only when advertising those routes on a network of a different classful network. Consider the following graphic:

![An example of automatic summarization with Router B summarizing all of the networks attached to Router A into the same network.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_rtg_summ_ccna7/rtg_summ.png)  

In this example, if both routers were using automatic summarization:

- Router A would not automatically summarize routes from the 10.3.1.0/24 or the 10.3.2.0/24 networks when advertising those networks to Router B. This is because subnet 10.2.0.0/16 that connects the two routers is in the same classful network (10.0.0.0/8) as the subnets connected to Router A.
- Router B would automatically summarize all routes as 10.0.0.0/8 when advertising routes on the 12.0.0.0/8 network. This is because this network is a different classful network than the 10.0.0.0/8 network.
- To prevent Router B from summarizing routes when advertising them to the 12.0.0.0/8 network, disable automatic route summarization on Router B.
- Route summarization works not only for grouping subnetted addresses into a single route, but can also be used to advertise multiple classful network addresses into a single summarized route. For example, the subnets of 192.168.1.0/24 through 192.168.255.0/24 could be summarized as a single route of 192.168.0.0/16.

To identify a summarized route for a group of subnets, identify a subnet address and mask that includes all of the routes that need to be summarized. While in many cases you could simply advertise the default class boundary, this will often result in a route being advertised that includes subnets and addresses that aren't being used. To eliminate this problem, choose the subnet and mask so that only existing subnets are included. To do this:

1. Convert the last significant octet of the first and the last subnet in the contiguous range to binary. For example, if you had networks 172.16.16.0/24 through 172.16.31.0/24, you would have the following two binary values:
    
    > 16 = 0 0 0 1 0 0 0 0  
    > 31 = 0 0 0 1 1 1 1 1
    
2. Identify the last consecutive binary bit that is shared. In this case, the last shared bit is the fourth bit position.
3. Convert all bits to the right of the shared bit to 0. In this example, this gives you the binary value of 00010000. This will be the subnet address of the summarized route. In this example, use 172.16.16.0.
4. Convert all bits to the left of the shared bit to 1. In this example, this gives you the binary value of 11110000. This will be the mask value of the summarized route. In this example, use 255.255.240.0.
5. Finally, identify any subnet addresses included in the range indicated by the advertised subnet and mask. Be aware that you will be unable to use these subnets without additional configuration for discontiguous networks. For example, if the first subnet you used in this example was 172.16.17.0 and the last subnet was 172.16.30.0, you would be unable to use the 172.16.16.0 and 172.16.31.0 subnets using a summarized route of 172.16.16.0/20.






---
# References

- [[Route Summarization]]
- [[Route Summarization Command List]]
