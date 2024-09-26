2024/09/24 17:16
Status: #idea
Tags: [[Vlans]]

# SVI InterVLAN Troubleshooting Facts


When implementing interVLAN routing in a router-on-a-stick or SVI configuration, there are several key parameters that must be configured correctly.

This lesson covers the following topics:

- SVI configuration
- Commands to verify and troubleshoot

## SVI Configuration

When problems arise, verify the configuration by checking the following:

- Connectivity at the Physical layer:
    - Ensure cables are connected to the correct router and switch ports.
    - Ensure cross-over UTP cables are used where required. For example, connecting two switches together requires either a cross-over cable or one of the switch ports itself to be crossed-over.
    - Ensure straight-through UTP cables are used where required. Typically, straight-through cables are used to connect hosts to switches and switches to routers.
- IP settings on network hosts and routers. Frequently, routing issues are caused by misconfigured IP protocol settings. Verify that the following are appropriate for the VLAN:
    - IP address.
    - Subnet mask.
    - Default router address.
- Appropriate subinterface has been created and configured on the router for each VLAN:
    - Verify that a unique VLAN subinterface has been created using the interface _[type]_ _[number.subinterface]_ command.
    - Verify that 802.1Q has been enabled and that a VLAN has been associated with the subinterface using the encapsulation dot1q _[vlan_id]_ command.
    - Verify that the correct IP address and mask has been assigned to the subinterface using the ip address _[address]_ _[mask]_ command.
- Native option is used with the encapsulation command on the router (encapsulation dot1q _[vlan_id]_ native) for the native VLAN.
- Trunking is enabled correctly on the switch:
    
    - Verify that the switchport mode trunk command has been issued for the interface.
    - Verify that the native VLAN on the switch matches the native VLAN on the router. This is done using the switchport trunk native vlan _[vlan_id]_ subcommand on the interface.
    
    You can use the ping command to determine if you can access the gateway routers and hosts on different subnets.
    

## Commands to Verify and Troubleshoot

The following commands can be used to display interVLAN routing configuration settings for verification and troubleshooting:

|Command|Action|
|---|---|
|**show vlan brief**|Displays which VLANs are in the VLAN database and the VLAN membership of each port. The following output is generated from the show vlan brief command:<br><br>VLAN Name                  Status    Ports<br>  ---- --------------------- --------- -------------------------------<br>  1    default               active    Fa0/3, Fa0/4, Fa0/5, Fa0/6,<br>                                       Fa0/7, Fa0/8, Fa0/9, Fa0/10,<br>                                       Fa0/11, Fa0/12, Gi0/1, Gi0/2<br>  2    VLAN0002              active    Fa0/2  1002 fddi-default          active<br>  1003 token-ring-default    active<br>  1004 fddinet-default       active<br>  1005 trnet-default         active<br><br>When using SVIs for interVLAN routing, the VLAN must exist in the VLAN database.|
|**show ip route**|Displays route information. The following is output generated from the show ip route command and a table describing the associated fields relating to interVLAN routing on a Layer 3 switch:<br><br>L3Switch#sh ip route<br>  Codes: C - connected, S - static, R - RIP, M - mobile, B - BGP<br>         D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area<br>         N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2<br>         E1 - OSPF external type 1, E2 - OSPF external type 2<br>         i - IS-IS, su - IS-IS summary, L1 - IS-IS level-1, L2 - IS-IS level-2<br>         ia - IS-IS intr area, * - candidate default, U - per-user static route<br>         o - ODR, P - periodic downloaded static route<br>  <br>  Gateway of last resort is not set<br>  C    192.168.1.0/24 is directly connected, Vlan1<br>  C    192.168.2.0/24 is directly connected, Vlan2<br><br>The command output contains the following information:<br><br>- The first characters of a routing table entry identifies the source or type of the route:<br>    - C is for directly connected networks. All SVIs are shown as directly connected, because the switch treats each interface as a physical link through which it can route traffic.<br>    - S is for static routes.<br>    - R is for routes learned through RIP.<br>    - Additional codes indicate routes learned through other routing protocols.<br>- Following the route type is the network address and subnet mask. This identifies the specific subnet address for the route.<br>- The VLAN ID indicates which VLAN interface is associated with the IP route. In the example above, VLAN 1 and VLAN 2 are configured with SVIs.<br><br>Routes for SVIs are shown only if:<br><br>- The interface has been assigned an IP address.<br>- The interface is enabled.<br>- The interface line protocol is up.<br>- The VLAN exists in the VLAN database.|
|**show run**|Displays interVLAN routing information on a Layer 3 switch. The following is a portion of the output generated from the show run command relating to interVLAN routing:<br><br>output omitted<br>  !<br>  interface Vlan10<br>  ip address 192.168.10.1 255.255.255.0<br>  !<br>  interface Vlan20<br>  ip address 192.168.20.1 255.255.255.0<br>  shutdown<br>  !<br><br>Verify the following information in the output of the command:<br><br>- VLAN Interface ID. This is the VLAN ID found in the VLAN database.<br>- IP address. This is the IP address of the Switch Virtual Interface (SVI). An IP address and subnet mask must be assigned to the interface before interVLAN routing can occur.<br>- Status. The shutdown and no shutdown commands enable the interface. In the example above, the omission of the shutdown command on the VLAN 10 interface indicates that the SVI is enabled and routing may occur through the SVI.|
|**show interfaces trunk**|Displays information about currently configured trunks. The following is sample output from the show interfaces trunk command on a switch:<br><br>Switch# **show interfaces trunk**<br>                        <br>  Port        Mode         Encapsulation     Status     Native vlan<br>  Fa0/1       desirable    802.1q            trunking   1<br>  <br>  Port        Vlans allowed on trunk<br>  Fa0/1       1-2,4-4094<br>                          <br>  Port        Vlans allowed and active in management domain<br>  Fa0/1       1,4 <br>  <br>  Port        Vlans in spanning tree forwarding state and not pruned<br>  Fa0/1       1,4,4<br><br>The output of the command displays three lists of VLANs:<br><br>- VLANs allowed.<br>- VLANs allowed and active.<br>- VLANs in spanning tree forwarding state and not pruned.|




---
# References

- [[Layer 3 Switch InterVLAN Routing Facts]]
- [[InterVLAN Routing Trouble Shooting Facts]]
- [[VLAN Trunking Protocol]]