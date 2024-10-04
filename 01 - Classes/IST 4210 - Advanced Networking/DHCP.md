2024/10/01 23:42
Status: #idea
Tags: [[DHCP]]

# DHCP (Dynamic Host Configuration Protocol)

## Basic Purpose
DHCP automates IP address assignment and network configuration.

## Key Points
- Automatically assigns IP addresses to devices on a network
- Eliminates need for manual IP configuration
- Manages pool of available IP addresses
- Provides additional network configuration info:
  - Subnet mask
  - Default gateway
  - DNS servers

## DHCP Process
1. **DHCP Discover**: Client broadcasts request for IP address
2. **DHCP Offer**: Server offers an available IP address
3. **DHCP Request**: Client requests the offered IP address
4. **DHCP Acknowledge**: Server confirms IP address assignment

## Benefits
- Simplifies network administration
- Reduces configuration errors
- Enables easy addition of new devices to network
- Supports IP address reuse when devices leave network

## Common Uses
- Home networks
- Enterprise networks
- Public Wi-Fi hotspots

## Mathematical Representation
The probability $P$ of IP address conflicts in a network with $n$ devices and $m$ available IP addresses can be approximated by:

$$ P \approx 1 - e^{-\frac{n^2}{2m}} $$

This is known as the "Birthday Problem" applied to IP addressing.

## DHCP Lease Time
DHCP assigns IP addresses for a limited time, called the lease time. The lease time $T$ is typically set based on the network size and device turnover rate:

$$ T = \frac{\text{Total IP addresses}}{\text{Average number of new devices per day}} \times k $$

Where $k$ is a constant factor (usually between 1 and 3) to provide a buffer.





---
# References

- [[DHCP Configuration Facts]]