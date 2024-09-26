2024/09/24 15:25
Status: #idea
Tags:

# VLANs (Virtual Local Area Networks)

## Definition
- VLAN: A logical grouping of network devices within the same broadcast domain, regardless of their physical location.

## Purpose
- Improve network performance
- Enhance security
- Simplify network management
- Reduce hardware costs

## Key Concepts

### VLAN Tagging
- Method: IEEE 802.1Q standard
- Adds a 32-bit field to the Ethernet frame header
- VLAN ID range: 1-4094 (0 and 4095 reserved)

### VLAN Types
1. Data VLAN: For user-generated traffic
2. Default VLAN: VLAN 1 (often used for management)
3. Native VLAN: Untagged VLAN on a trunk port
4. Management VLAN: For admin access to network devices
5. Voice VLAN: Dedicated to voice traffic (VoIP)

## VLAN Configuration

### Access Ports
- Belong to a single VLAN
- Typically connect to end devices (PCs, printers)

### Trunk Ports
- Carry traffic for multiple VLANs
- Usually connect switches to other switches or routers

## Inter-VLAN Routing
- Methods:
  1. Router on a stick
  2. Layer 3 switch
  3. Firewall

## VLAN Best Practices
- Use VLANs to segment traffic logically
- Implement VLAN pruning to optimize trunk links
- Secure the native VLAN
- Use private VLANs for isolation in larger networks

## Common VLAN Commands (Cisco)
```
# Create a VLAN
vlan 10
name Marketing

# Assign a port to a VLAN
interface FastEthernet0/1
switchport mode access
switchport access vlan 10

# Configure a trunk port
interface GigabitEthernet0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30

# Show VLAN information
show vlan brief
```

## Advantages of VLANs
- Improved security
- Better performance
- Simplified network management
- Reduced hardware costs
- Logical grouping of users

## Limitations
- Complexity in large networks
- Potential for misconfiguration
- Broadcast domain limitations (up to 4094 VLANs)

---

Remember to expand these notes as you learn more about VLANs and their implementation in your specific network environment.





---
# References

- [[VLAN Facts]]