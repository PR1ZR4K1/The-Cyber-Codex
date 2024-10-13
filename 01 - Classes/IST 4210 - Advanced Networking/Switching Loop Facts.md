2024/10/08 22:44
Status: #idea
Tags: [[Spanning Tree Protocol]]

# Switching Loop Facts

The Spanning Tree Protocol (STP) assigns one bridge (or switch) for each route as the designated bridge. Only the designated bridge can forward packets. Redundant bridges (and switches) are assigned as backups.

This lesson covers the following topics:

- Switching loops
- Bridge roles
- Port states
- Port types
- STP device configuration process
- STP features

## Switching Loops

To provide fault tolerance, many networks implement redundant paths between devices using multiple switches. However, providing redundant paths between segments causes packets to be passed between the redundant paths endlessly. This condition is known as a _bridge loop_ or _switching loop_ .

To prevent bridge loops, the IEEE 802.1d committee defined a standard called the spanning tree algorithm (STA), or Spanning Tree Protocol (STP). With this protocol, one bridge (or switch) for each route is assigned as the designated bridge. Only the designated bridge can forward packets. Redundant bridges (and switches) are assigned as backups.

The spanning tree algorithm provides the following benefits:

- Eliminates bridge loops.
- Provides redundant paths between devices.
- Enables dynamic role configuration.
- Recovers automatically from a topology change or device failure.
- Identifies the optimal path between any two network devices.

## Bridge Roles

The spanning tree algorithm calculates the best loop-free path through a network by assigning a role to each bridge or switch and by assigning roles to the ports of each bridge or switch. The bridge role determines how the device functions in relation to other devices and whether the device forwards traffic to other segments.

|Role|Characteristics|
|---|---|
|Root bridge|The root bridge is the master or controlling bridge. Be familiar with the following regarding root bridges:<br><br>- There is only one root bridge in the network. The root bridge is the logical center of the spanning-tree topology in a switched network.<br>- The root bridge is determined by the switch with the lowest bridge ID (BID):<br>    - The bridge ID is composed of two parts, a bridge priority number and the MAC address assigned to the switch.<br>    - The default priority number for all switches is 32,768. This means that for unconfigured switches, the switch with the lowest MAC address becomes the root bridge.<br>    - You can manually configure the priority number to force a specific switch to become the root switch.<br>- The root bridge periodically broadcasts configuration messages. These messages are used to select routes and reconfigure the roles of other bridges if necessary.<br>- All ports on a root bridge forward messages to the network.|
|Designated bridge|A designated bridge is any other device that participates in forwarding packets through the network. Be aware that:<br><br>- Designated bridges are selected automatically by exchanging bridge configuration packets.<br>- To prevent bridge loops, there is only one designated bridge per segment.|
|Backup bridge|All redundant devices are classified as backup bridges. Backup bridges:<br><br>- Listen to network traffic and build the bridge database. However, they will not forward packets.<br>- Can take over if the root bridge or a designated bridge fails.|

## Port States

Devices send special packets called Bridge Protocol Data Units (BPDUs) out each port. BPDUs sent and received from other bridges are used to determine the bridge roles and port states, verify that neighbor devices are still functioning, and recover from network topology changes. During the negotiation process and normal operations, each switch port is in one of the following states.

|Port State|Description|
|---|---|
|Disabled|A port in the disabled state is powered on but does not participate in forwarding or listening to network messages. A bridge must be manually placed in the disabled state.|
|Blocking|When a device is first powered on, its ports are in the blocking state. In addition, backup bridge ports are always in the blocking state. Ports in a blocking state receive packets and BPDUs sent to all bridges, but will not process any other packets.|
|Listening|The listening state is a transitory state between blocking and learning. The port remains in the listening state for a specific period of time. This time period allows network traffic to settle down after a change has occurred. For example, if a bridge goes down, all other bridges go to the listening state for a period of time. During this time the bridges redefine their roles.|
|Learning|A port in the learning state is receiving packets and building the bridge database by associating MAC addresses with ports. A timer is also associated with this state. The port goes to the forwarding state after the timer expires.|
|Forwarding|The root bridge and designated bridges are in the forwarding state when they can receive and forward packets. A port in the forwarding state can both learn and forward. All ports of the root switch are in forwarding mode.|

## Port Types

During the configuration process, ports on each switch are configured as one of the following types.

|Port type|Description|
|---|---|
|Root port|The _root port_ is the port on the designated switch with the lowest port cost back to the root bridge.<br><br>- Each designated switch has a single root port (a single path back to the route bridge).<br>- Root ports are in the forwarding state.<br>- The root bridge does not have a root port.|
|Designated port|One port on each _segment_ is identified as the designated port. The designated port identifies the port on the segment that is allowed to send and receive frames onto that segment. Be familiar with the following concepts.<br><br>- All ports on the root bridge are designated ports, unless the switch port loops back to a port on the same switch.<br>- Designated ports are selected based on the lowest path _cost_ to get back to the root switch. Default IEEE port costs include the following:<br><br>- 10 Mbps = 100<br>- 100 Mbps = 19<br>- 1 Gbps = 4<br>- 10 Gbps = 2<br><br>- If two switches have the same cost, the switch with the lowest priority becomes the designated switch. The port on that switch is the designated port.<br>- If two ports have the same cost, the port on the switch with the lowest port ID becomes the designated port:<br><br>- The port ID is derived from two numbers, the port priority and the port number.<br>- The port priority ranges from 0–255, with a default of 128.<br>- The port number is the number of the port. For example, the port number for Fa0/3 is 3.<br>- With the default port priority setting, the lowest port number becomes the designated port.<br><br>- Designated ports are used to send frames back to the root bridge.<br>- Designated ports are in the forwarding state.|
|Blocking port|A blocking port is any port that is not a root or a designated port. A blocking port is in blocking state.|

## STP Device Configuration Process

Devices participating in the spanning tree algorithm use the following process to configure themselves:

1. At startup, switches send BPDUs out each port.
2. Switches read the bridge ID contained in the BPDUs to elect (identify) a single root bridge (the device with the lowest bridge ID). Then, all the ports on the root bridge become designated ports.
3. Each switch identifies its root port, which is the port with the lowest cost back to the root bridge.
4. Switches on redundant paths identify a designated switch for each segment. A designated port is also identified on each designated switch.
5. Remaining switch ports that are not root or designated ports are put in the blocking state to eliminate loops.
6. After configuration, switches periodically send BPDUs to ensure connectivity and discover topology changes.

## STP Features

The biggest disadvantage of STP is that it is slow to respond to topology changes. With a link failure, convergence could take up to 30 seconds. By optimizing switch settings, this delay can be reduced to about 14 seconds, but that is still too long. To improve convergence, Cisco introduced several new proprietary features which can reduce this time to about 1 second. These features include the following:

- PortFast allows ports without any attached switches to transition immediately to the forwarding state. This transition is possible because bridging loops are eliminated on ports that do not have switches attached.
- Uplink Fast enables a switch to maintain an alternate path back to the root bridge. If the root port or link goes down, the alternate port can be quickly used to re-establish communication with the root bridge.





---
# References

- [[STP Configuration]]
- [[STP Facts]]