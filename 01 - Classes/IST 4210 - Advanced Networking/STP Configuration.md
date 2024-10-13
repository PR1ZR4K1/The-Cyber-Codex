2024/10/08 22:44
Status: #idea
Tags: [[Spanning Tree Protocol]]

# STP Configuration

By default, spanning tree is enabled on all Cisco switches. When you add switches to the network, spanning tree operates automatically to identify the root bridge and configure each port to prevent loops. In a small environment, you can probably rely on the switches to configure themselves. In a large environment, however, you need to plan the network so that you can control which switch becomes the root bridge and also identify ports that should be blocking or forwarding.

To identify how spanning tree configures switches in a network, you need to know the bridge ID for each bridge. This includes the priority value and the MAC address. If no priority value is included, assume the default priority of 32768. With the bridge ID and MAC addresses, use the following process to identify the state of each port:

1. Identify the root bridge. The root bridge is the switch with the lowest bridge ID:

- The switch with the lowest priority value is the root bridge.
- If two or more switches have the same priority value, the switch with the lowest MAC address is the root bridge.

3. On the root bridge, label each port as a designated port.
4. For every other bridge, identify its root port. The root port is the port with the lowest cost back to the root bridge:

- To identify the cost, add the cost for each segment back to the root bridge.
- If two paths have the same cost, then look at the bridge ID of the next switch in the path.

6. After labeling each root port, identify a designated port for each segment that does not already have a designated port:

- The designated port will be the port that connects to the path with the lowest cost back to the root bridge.
- If two paths have the same cost, compare the bridge ID of the next switch in the path.

8. At this point, each segment should have a designated port identified. Any ports not labeled as a root port or a designated port should be configured as a blocking port.

The following graphic shows a switched network with redundant paths. The priority values and MAC addresses for each switch are identified. Numbers on each link are used to identify the link. Each link has the same cost value.

![Four interconnected switches with redundant paths.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_stconfig_ccna7/swi_spane-01.jpg)

Using the steps outlined above:

1. Switch A is the root bridge because it has the lowest priority (4096).
2. Fa0/1 and Fa0/2 on switch A are designated ports and will be forwarding.
3. Root ports on the other switches are as follows:

- The root port on switch B is Fa0/1.
- The root port on switch C is Fa0/2:

- There are two paths back to the root bridge: B to A or D to A.
- Both paths have the same cost because they involve crossing two segments with equal costs.
- B to A is preferred because the bridge ID for switch B is lower than that of switch D. The priority values are the same, so the lowest MAC address is used (000E.8411.68C0).

- The root port on switch D is Fa0/1.

5. At this point, designated ports already exist for segments 1 and 2. Designated ports for the remaining segments are as follows:

- For segment 3, Fa0/3 on switch B is the designated port because the cost from B to A is less than the cost from C to D to A.
- For segment 4, Fa0/3 on switch D is the designated port for the same reason.
- For segment 5, Fa0/2 on switch B is the designated port:

- There are two paths from segment 5 to the root bridge: B to A or D to A.
- Both paths have the same cost.
- B to A is preferred because the bridge ID for switch B is lower than that of switch D. The priority values are the same, so the lowest MAC address is used (000E.8411.68C0).

7. The following remaining ports are blocking ports:

- Fa0/1 on switch C.
- Fa0/2 on switch D.

The following graphic shows each port labeled after spanning tree converges:

![A diagram of four interconnected switches with each port labeled to show its status after spanning tree converges.](https://cdn.testout.com/_version_7024/ccna2020v7-en-us/en-us/resources/text/t_stconfig_ccna7/swi_spane-02.jpg)

Be aware of the effect that configuration changes make in this example:

- If all switches had the same priority value, then switch B would have been the root bridge because its MAC address is the lowest. Changing the root bridge would also change several other port states.
- Changing the priority on switch D to 8192 would have the following effects:

- The root port on switch C would change to Fa0/1. The path through switch D would be preferred over the path through switch B because of the lower priority number.
- The designated port for segment 5 would change to Fa0/2 on switch D, while Fa0/2 on switch B would be blocking.
- Fa0/2 on switch C would change to blocking.

- Assuming the default cost value of 19 for FastEthernet links, changing the cost of segment 1 to 100 would have the following effects:

- The root port on switch D would be Fa0/2. The total cost of that path would be 38.
- The designated port for segment 4 would be Fa0/1 on switch C. Port Fa0/3 on switch D would now be blocking.
- Port Fa0/1 on switch D would be blocking because Fa0/2 would be used to reach the root bridge.





---
# References

- [[STP Facts]]
- [[Switching Loop Facts]]