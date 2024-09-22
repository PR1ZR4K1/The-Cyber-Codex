2024/08/29 13:25
Status: #idea
Tags: [[IP Classes]]

# IP Address Classes

IP addresses are divided into different classes based on the number of bits used for the network portion and the host portion of the address. There are five classes of IP addresses: A, B, C, D, and E.

## Class A

- **First bit**: Always 0
- **Network portion**: 8 bits
- **Host portion**: 24 bits
- **Range**: 1.0.0.0 to 126.255.255.255
- **Subnet mask**: 255.0.0.0
- **Number of networks**: $2^7 = 128$
- **Number of hosts per network**: $2^{24} - 2 = 16,777,214$

**Binary representation**: 
$\overbrace{0\underbrace{nnnnnnn}_{7\text{ bits}}}^{\text{Network}} \overbrace{\underbrace{hhhhhhhh}_{8\text{ bits}} \underbrace{hhhhhhhh}_{8\text{ bits}} \underbrace{hhhhhhhh}_{8\text{ bits}}}^{\text{Host}}$

## Class B

- **First two bits**: Always 10
- **Network portion**: 16 bits
- **Host portion**: 16 bits
- **Range**: 128.0.0.0 to 191.255.255.255
- **Subnet mask**: 255.255.0.0
- **Number of networks**: $2^{14} = 16,384$
- **Number of hosts per network**: $2^{16} - 2 = 65,534$

**Binary representation**:
$\overbrace{10\underbrace{nnnnnn}_{6\text{ bits}} \underbrace{nnnnnnnn}_{8\text{ bits}}}^{\text{Network}} \overbrace{\underbrace{hhhhhhhh}_{8\text{ bits}} \underbrace{hhhhhhhh}_{8\text{ bits}}}^{\text{Host}}$

## Class C

- **First three bits**: Always 110
- **Network portion**: 24 bits
- **Host portion**: 8 bits
- **Range**: 192.0.0.0 to 223.255.255.255
- **Subnet mask**: 255.255.255.0
- **Number of networks**: $2^{21} = 2,097,152$
- **Number of hosts per network**: $2^8 - 2 = 254$

**Binary representation**:
$\overbrace{110\underbrace{nnnnn}_{5\text{ bits}} \underbrace{nnnnnnnn}_{8\text{ bits}} \underbrace{nnnnnnnn}_{8\text{ bits}}}^{\text{Network}} \overbrace{\underbrace{hhhhhhhh}_{8\text{ bits}}}^{\text{Host}}$

## Class D (Multicast)

- **First four bits**: Always 1110
- **Range**: 224.0.0.0 to 239.255.255.255
- Used for multicast groups

**Binary representation**:
$1110\underbrace{mmmm}_{4\text{ bits}} \underbrace{mmmmmmmm}_{8\text{ bits}} \underbrace{mmmmmmmm}_{8\text{ bits}} \underbrace{mmmmmmmm}_{8\text{ bits}}$

## Class E (Experimental)

- **First four bits**: Always 1111
- **Range**: 240.0.0.0 to 255.255.255.255
- Reserved for experimental use

**Binary representation**:
$1111\underbrace{eeee}_{4\text{ bits}} \underbrace{eeeeeeee}_{8\text{ bits}} \underbrace{eeeeeeee}_{8\text{ bits}} \underbrace{eeeeeeee}_{8\text{ bits}}$

## Special IP Addresses

- **Network address**: Host portion all 0s
- **Broadcast address**: Host portion all 1s
- **Localhost**: 127.0.0.1

## Subnetting

Subnetting allows for more efficient use of IP addresses by dividing a large network into smaller subnetworks. The subnet mask determines which portion of an IP address belongs to the network and which to the host.

**Subnet mask calculation**:
$\text{Subnet mask} = 2^{32} - 2^{32-n}$

Where $n$ is the number of network bits.

Example for a /24 subnet:
$2^{32} - 2^{32-24} = 2^{32} - 2^8 = 4,294,967,296 - 256 = 4,294,967,040 = 255.255.255.0$
  





---
# References
