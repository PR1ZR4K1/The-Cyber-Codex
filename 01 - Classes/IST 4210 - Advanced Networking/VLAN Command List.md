2024/09/24 15:31
Status: #idea
Tags: [[Vlans]]

# VLAN Command List


To configure a simple VLAN, you first create the VLAN and then assign ports to it.

This lesson covers the following topics:

- VLAN configuration commands
- Voice VLAN configuration commands

## VLAN Configuration Commands

The following table shows common VLAN configuration commands:

|Command|Description|
|---|---|
|switch(config)# **vlan _[1-1005]_**|Defines a VLAN.|
|switch(config-vlan)# **name _[unique_name]_**|Gives the VLAN a name.<br><br>Naming the VLAN is optional. VLAN names must be unique.|
|switch(config)# **no vlan _[1-1005]_**|Deletes a VLAN.<br><br>When you delete a VLAN, all ports assigned to the VLAN remain associated with the deleted VLAN and are, therefore, inactive. After a VLAN is deleted, you must reassign the ports to a VLAN.|
|switch(config-if)# **switchport access vlan _[1-1005]_**|Assigns ports to the VLAN.<br><br>If you assign a port to a VLAN that does not exist, the VLAN is created automatically.|
|switch# **show vlan**  <br>switch# **show vlan brief**|Shows a list of VLANs on the system.|
|switch# **show vlan id _[1-1005]_**|Shows information for a specific VLAN.|

The following commands create VLAN 12, names it IS_VLAN, identifies port 0/12 as having only workstations attached to it, and assigns the port to VLAN 12:

> switch#**config t**
> switch(config)#**vlan 12**
> switch(config-vlan)#**name IS_VLAN**
> switch(config-vlan)#**interface fast 0/12**
> switch(config-if)#**switchport access vlan 12**

## Voice VLAN Configuration Commands

Creating a voice VLAN is similar to creating a simple VLAN. The following table shows common voice VLAN configuration commands:

|Command|Description|
|---|---|
|switch(config-if)# **switchport voice vlan _[1-1005]_**|Configures the port to use the specified VLAN for VoIP traffic.<br><br>When an interface is configured with a voice VLAN, all VoIP traffic sent on the network uses the specified VLAN and is tagged with an 802.1Q priority of 5.|
|switch(config-if)# **switchport priority extend cos _[0-7]_**  <br>switch(config-if)# **switchport priority extend trust**|Sets the priority value that voice traffic will be tagged with. The default is 5.  <br>Configures the port to trust the priority value assigned by the IP phone.|
|switch# **sh int _[interface]_ switchport**|Displays the configuration information for the specified interface. Consider the following sample output:<br><br>> Name: Fa0/1<br>>     Switchport: Enabled<br>>     Administrative Mode: dynamic auto<br>>     Operational Mode: down<br>>     Administrative Trunking Encapsulation: dot1q<br>>     Negotiation of Trunking: Off<br>>     Access Mode VLAN: 15 (DATA)<br>>     Trunking Native Mode VLAN: 0<br>>     Administrative Native VLAN tagging: enabled<br>>     Voice VLAN: 20<br>>     ...<br><br>_Access Mode VLAN_ is the VLAN used when sending data traffic. _Voice VLAN_ is the VLAN used when sending VoIP traffic.|

The following commands configure the fa0/1 interface to use VLAN 10 for VoIP traffic (because the VLAN does not exist, it is created):

> switch#**config t**
> switch(config)#**int fa0/1**
> switch(config-if)#**switchport voice vlan 10**
> % Voice VLAN does not exist. Creating vlan 10

The following commands create two VLANs (15 and 20) with the names DATA and VOIP and configure the fa0/1–10 interfaces to use VLAN 15 for data traffic and VLAN 20 for VoIP traffic:

> switch#**config t**
> switch(config)#**vlan 15**
> switch(config-vlan)#**name DATA**
> switch(config-vlan)#**vlan 20**
> switch(config-vlan)#**name VOIP**
> switch(config-vlan)#**int range fa0/1-10**
> switch(config-if)#**switchport access vlan 15**
> switch(config-if)#**switchport voice vlan 20**




---
# References

- [[Vlans]]
- [[VLAN Facts]]