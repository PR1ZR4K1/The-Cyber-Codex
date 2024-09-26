2024/09/24 16:18
Status: #idea
Tags:

# VLAN Trunking Protocol


When connecting multiple switches via trunk links, the VLAN configurations between the switches can become extremely time consuming to manage. If a VLAN is added or removed, that change needs to be configured on each switch in the network that uses the VLAN. Luckily, Cisco switches are able to use a special protocol named the VLAN Trunking Protocol (VTP) that allows VLAN configuration changes to be automatically propagated out to each switch.

This lesson covers the following topics:

- VTP characteristics
- VTP modes
- VTP configuration
- VTP commands

## VTP Characteristics

In order to implement VTP, you need to be aware of the following VTP characteristics:

- VTP uses advertisement messages to maintain VLAN consistency across switches. Advertisement messages are sent using either ISL or 802.1Q frames. They contain the following information:

- VTP domain name
- VTP revision number
- VLAN IDs
- VLAN configurations

- There are two versions of VTP, version 1 (V1) and version 2 (V2). Other than V2 supporting Token Ring VLANs, the two versions are almost identical.

All switches in a VTP domain must use the same version number. Unless you need to support Token Ring VLANs, it is recommended to always use V1.

- VTP can be configured to use a password.

- All switches in the VTP domain must be configured to use the same password.
- If being used, the password is hashed using MD5 and sent with all advertisement messages.

- Extended VLANs (1006–4094) are not advertised by VTP.
- Unless a switch is in VTP transparent mode, extended VLANs cannot be configured on the switch.

## VTP Modes

Switches using VTP operate in one of four VTP modes:

|Mode|Description|
|---|---|
|Server|Server mode is the default VTP mode. A switch in server mode can perform the following actions:<br><br>- Add, remove, and modify VLANs.<br>- Change VTP configuration settings (e.g., change the VTP version number or enable pruning).<br>- Send advertisement messages to propagate changes in the VTP domain.|
|Client|A switch in client mode is able to send and receive VTP advertisement messages but is unable to add, remove, or modify VLAN configurations.|
|Transparent|A switch in transparent mode will not obtain configuration information from VTP. However, it will forward VTP messages it receives.<br><br>In order for a switch in transparent mode to forward VTP messages, it must be configured to be in the same VTP domain as all other switches.|
|Off|A switch in off mode will not participate in VTP and will not forward VTP messages.|

## VTP Configuration

Configuring VTP consists of the following general steps:

1. Establish a trunk link between two switches.

VTP can send only advertisement messages through trunk ports. If you have problems configuring VTP, make sure the switches are connected using a trunk port.

3. For the VTP server switch:

1. Configure the VTP domain name.
2. Specify a VTP password (optional).
3. Set the switch to VTP server mode.

5. For the VTP client switch:

1. Configure the same VTP domain name as the server.
2. Specify the same VTP password as the server (optional).
3. Set the switch to VTP client mode.

7. Use the show vtp status command to verify that VTP is operational.

## VTP Commands

The following table describes the commands used to configure and verify VTP:

|Command|Description|
|---|---|
|Switch(config)# **vtp domain _[name]_**|Configures the VTP domain. The domain name is case sensitive and must be the same for all switches in order for them to send and receive VTP messages.|
|Switch(config)# **vtp password _[password]_**|Configures the password for VTP. The same password must be used for all switches in the VTP domain.<br><br>To display the current VTP password, use the show vtp password command in enabled mode.|
|Switch(config)# **vtp mode {server\|client\|transparent\|off}**|Changes the VTP mode of the switch.|
|Switch(config)# **vtp version 1\|2**|Changes the VTP version for all switches in the VTP domain (the default VTP version is 1). This command is available only if the switch is a VTP server.<br><br>All switches must use the same VTP version or they will be unable to communicate.|
|Switch(config)# **vtp pruning**  <br>  <br>Switch(config)# **no vtp pruning**|Enables/disables VTP pruning. VTP pruning is used to eliminate unnecessary traffic in large networks by forwarding only VLAN broadcast traffic to the necessary VLANs.<br><br>If VTP pruning is enabled/disabled on a VTP server, pruning will be enabled/disabled for all switches in the VTP domain.|
|Switch# **show vtp status**|Displays the following status information about VTP:<br><br>- VTP Version: The highest version the switch is capable of, not the version that the switch is using.<br>- Configuration Revision: The revision number of the VTP database. This number should be the same on all switches in the VTP domain.<br>- VTP Operating Mode: The VTP mode of the switch. Possible values are Server, Client, Transparent, and Off.<br>- VTP Domain Name: The configure domain of the switch. This value should be the same for all switches using VTP.<br>- VTP Pruning Mode: Specifies whether VTP pruning is enabled or disabled.<br>- VTP V2 Mode: Shows the version of VTP being used.<br><br>- Disabled: V1 is being used.<br>- Enabled: V2 is being used.<br><br>The following is an example of the output generated by the command:<br><br>VTP Version                     : 2<br>  Configuration Revision          : 5<br>  Maximum VLANs supported locally : 36<br>  Number of existing VLANs        : 10<br>  VTP Operating Mode              : Server<br>  VTP Domain Name                 : CORP1<br>  VTP Pruning Mode                : Disabled<br>  VTP V2 Mode                     : Disabled<br>  VTP Traps Generation            : Disabled<br>  MD5 digest                      : 0x99 0xE5 0x15 0xDB 0xA0 0x5D 0x6A 0x3F<br>  Configuration last modified by 0.0.0.0 at 3-1-02 00:13:55<br>  Local updater ID is 0.0.0.0 (no valid interface found)|

In the following example, two switches are connected via a trunk link. The commands below configure both switches to use VTP, SwitchA as the server and SwitchB as the client.

> SwitchA#**conf t**
> SwitchA(config)#**vtp domain CORPNET**
> Changing VTP domain name from NULL to CORPNET
> SwitchA(config)#**vtp password secure**
> Setting device VLAN database password to secure
> SwitchA(config)#**vtp mode server**
> Setting device to VTP SERVER mode
> 
> SwitchB#**conf t**
> SwitchB(config)#**vtp domain CORPNET**
> Changing VTP domain name from NULL to CORPNET
> SwitchB(config)#**vtp password secure**
> Setting device VLAN database password to secure
> SwitchB(config)#**vtp mode client**
> Setting device to VTP CLIENT mode

en
conf t
int range g0/1-2
switchport trunk native vlan 10
shut
no shut
end
copy run start


---
# References

- [[VLAN Facts]]
- [[Trunking Command List]]
- [[Trunking Advanced Config]]
- [[InterVLAN Routing Config Facts]]