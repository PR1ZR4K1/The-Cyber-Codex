2024/09/24 16:59
Status: #idea
Tags: [[Vlans]]

# InterVLAN Routing Trouble Shooting Facts

When implementing interVLAN routing in a router-on-a-stick configuration, there are several show commands that will allow you to verify the configuration.

This lesson covers the following topics:

- Steps to verify configuration
- Show commands to verify and troubleshoot configuration

## Steps to Verify Configuration

When problems arise, verify the configuration by checking the following:

- Cables are connected to the correct router and switch ports.
- Correct IP configuration settings are being used. Frequently, routing issues are caused by misconfigured IP protocol settings. Verify that the following are appropriate for the VLAN:
    - IP address.
    - Subnet mask.
    - Default router address.
- Appropriate subinterface has been created and configured on the router for each VLAN:
    - Verify that a unique VLAN subinterface has been created using the interface _[type]_ _[number.subinterface]_ command.
    - Verify that 802.1Q has been enabled and that a VLAN has been associated with the subinterface using the encapsulation dot1q _[vlan_id]_ command.
    - Verify that the correct IP address and mask have been assigned to the subinterface using the ip address _[address]_ _[mask]_ command.
- Native option is used with the encapsulation command on the router (encapsulation dot1q _[vlan_id]_ native) for the native VLAN.
    
    You can use the ping command to determine if you can access the gateway routers and hosts on different subnets.
    

## Show Commands to Verify and Troubleshoot Configuration

The show following commands can be used to display interVLAN routing configuration settings for verification and troubleshooting.

|Command|Description|
|---|---|
|show vlan brief|Displays which VLANs are in the VLAN database and the VLAN membership of each port. The following output is generated from the show vlan brief command:<br><br>> VLAN Name                  Status    Ports<br>> ---- --------------------- --------- -------------------------------<br>> 1    default               active    Fa0/3, Fa0/4, Fa0/5, Fa0/6,<br>>                                      Fa0/7, Fa0/8, Fa0/9, Fa0/10,<br>>                                      Fa0/11, Fa0/12, Gi0/1, Gi0/2<br>> 2    VLAN0002              active    Fa0/2<br>> 1002 fddi-default          active<br>> 1003 token-ring-default    active<br>> 1004 fddinet-default       active<br>> 1005 trnet-default         active|
|show ip route|Displays route information. The following is output generated from the show ip route command and a table describing the associated fields relating to interVLAN routing on a router:<br><br>> Router#**show ip route**<br>> Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP<br>>        D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area<br>>        N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2<br>>        E1 - OSPF external type 1, E2 - OSPF external type 2<br>>        i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2<br>>        ia - IS-IS inter area, * - candidate default, U - per-user static route<br>>        o - ODR, P - periodic downloaded static route<br>> <br>> Gateway of last resort is not set<br>> C    192.168.2.0/24 is directly connected, FastEthernet0/1.2<br>> C    192.168.4.0/24 is directly connected, FastEthernet0/1.4<br><br>The command output contains the following information:<br><br>- The first characters of a routing table entry identifies the source or type of the route:<br>    - C is for directly connected networks.<br>    - S is for static routes.<br>    - R is for routes learned through RIP.<br>    - Additional codes indicate routes learned through other routing protocols.<br>- Following the route type is the network address and subnet mask. This identifies the specific subnet address for the route.<br>- The FastEthernet0/1. _[vlanid]_ identifies the configured subinterfaces and the associated VLAN number. In this example, subinterfaces for VLAN 2 and VLAN 4 have been configured.<br><br>Routes are shown only if:<br><br>- The interface has been assigned an IP address.<br>- The interface is enabled.<br>- The interface line protocol is up.<br>- Subinterfaces have been configured.|
|show run|Displays interVLAN routing information. The following is a portion of the output generated from the show run command relating to interVLAN routing using a router-on-a-stick:<br><br>> output omitted<br>> !<br>> interface FastEthernet0/1<br>> description Link to SwitchA<br>> no ip address<br>> shutdown<br>> !<br>> interface FastEthernet0/1.2<br>> ip address 192.168.2.1 255.255.255.0<br>> encapsulation dot1q 2<br>> !<br>> interface FastEthernet0/1.4<br>> ip address 192.168.4.1 255.255.255.0<br>> !<br><br>Verify the following information in the output of the command:<br><br>- Status. Make sure the status of the primary interface (in this case FastEthernet0/1) is not shutdown. In this example, the main interface is shutdown.<br>- Subinterface. The number of the sub interface (in this case FastEthernet0/1.2 and .4) should correspond with the VLAN numbers being forwarded.<br>- IP address. This is the IP address of the subinterface. An IP address and subnet mask must be assigned to the interface before interVLAN routing can occur.<br>- Encapsulation. The router-on-a-stick must be running a trunking protocol (typically 802.1Q). Make sure an encapsulation protocol is being used and the proper VLAN number is configured.|
|show interfaces trunk|Displays information about currently configured trunks. The following is sample output from the show interfaces trunk command on a switch:<br><br>> Switch#**show interfaces trunk**<br>>                         <br>> Port        Mode         Encapsulation     Status     Native vlan<br>> Gi0/1       on           802.1q            trunking   1<br>> <br>> Port        Vlans allowed on trunk<br>> Gi0/1       1-4094<br>>                         <br>> Port        Vlans allowed and active in management domain<br>> Gi0/1       1-2,4 <br>> <br>> Port        Vlans in spanning tree forwarding state and not pruned<br>> Gi0/1       1-2,4<br><br>The output of the command displays three lists of VLANs:<br><br>- VLANs allowed.<br>- VLANs allowed and active.<br>- VLANs in spanning tree forwarding state and not pruned.|





---
# References

- [[InterVLAN Routing Config Facts]]
- [[Layer 3 Switch InterVLAN Routing Facts]]
- [[VLAN Trunking Protocol]]
- [[Trunking Advanced Config]]
- [[Trunking Command List]]