2024/09/10 13:33
Status: #idea
Tags: [[]]

# Basic Commands n Stuff

**Configure basic settings on both Switches - not all steps are shown.**

1. Configure the device name.
2. Disable DNS lookup.
3. Configure a login MOTD banner.
4. Configure the VLAN 99 management interface IP address, as shown in the Addressing Table, and enable the interface.
5. Assign interfaces to management VLAN using Addressing Table.
6. Assign class as the privileged EXEC mode password.
7. Assign cisco as the console and vty password and enable login.
8. Set logging synchronous to prevents messages from interrupting your keyboard input.
9. Assign static IPv4 information to the PC interfaces
10. Encrypt plain text passwords.
11. Save the running configuration to startup configuration.

**Configure interface IP address as shown in the Addressing Table.**

**Create VLAN 99 on the switches and name it Management**.

- - S1(config)# **vlan 99**
    - S1(config-vlan)# **name Management**
    - S1(config-vlan)# **exit**
    - S1(config)#

**Configure the VLAN 99 management interface IP address, as shown in the Addressing Table, and enable the interface. (this is for SBS1, ORS1 will have different IP)**

- - S1(config)# **interface vlan 99**
    - S1(config-if)# **ip address 192.168.x.x 255.255.255.0** 
    - S1(config-if)# **no shutdown**
    - S1(config-if)# **end**
    - S1#

**Assign port FastEthernet0/1 to VLAN 99 management interface on the switches.**

- - S1# **config t**
    - S1(config)# **interface F0/1**
    - S1(config-if)# **switchport mode access**
    - S1(config-if)# **switchport access vlan 99**
    - S1(config-if)# **end**

---
# References
