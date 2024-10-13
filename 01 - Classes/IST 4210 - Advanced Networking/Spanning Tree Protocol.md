2024/10/08 22:42
Status: #idea
Tags: [[Spanning Tree Protocol]]

# Spanning Tree Protocol (STP)

Spanning Tree Protocol (STP) is a network protocol used to prevent loops in Ethernet networks with redundant links.

## Key Concepts:

1. **Root Bridge**: The switch with the lowest Bridge ID, calculated as: $\text{Bridge ID} = \text{Priority} + \text{MAC Address}$
2. **Port Roles**:
    - Root Port: Port closest to the root bridge
    - Designated Port: Port on each segment closest to the root bridge
    - Blocked Port: Ports that are not root or designated
3. **Port States**:
    - Blocking
    - Listening
    - Learning
    - Forwarding
4. **Path Cost**: Inversely proportional to link speed: $\text{Path Cost} = \frac{1000 \text{ Mbps}}{\text{Link Speed (Mbps)}}$
5. **BPDU (Bridge Protocol Data Unit)**: Messages exchanged between switches to elect the root bridge and determine port roles.
6. **Timers**:
    - Hello Time: $2$ seconds
    - Forward Delay: $15$ seconds
    - Max Age: $20$ seconds

## STP Convergence Process:

1. Elect root bridge
2. Identify root ports
3. Identify designated ports
4. Block remaining ports

STP ensures a loop-free logical topology while maintaining redundant physical links for fault tolerance.





---
# References

- [[STP Facts]]