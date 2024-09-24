2024/09/21 23:56
Status: #idea
Tags:

# Useful Cisco Router and Switch Configuration Commands

## Basic Configuration

- `hostname [name]`: Set the device's hostname
- `enable secret [password]`: Set encrypted password for privileged EXEC mode
- `service password-encryption`: Encrypt passwords in the configuration
- `banner motd #[message]#`: Set a message of the day banner

## Interface Configuration

- `interface [type][number]`: Enter interface configuration mode
- `ip address [ip-address] [subnet-mask]`: Assign IP address to an interface
- `no shutdown`: Enable an interface
- `shutdown`: Disable an interface
- `description [text]`: Add a description to an interface

## Routing

- `ip route [destination_network] [subnet_mask] [next_hop_ip/exit_interface]`: Configure a static route
- `router ospf [process-id]`: Enter OSPF routing configuration mode
- `network [network_address] [wildcard_mask] area [area_id]`: Specify networks for OSPF

## Switching

- `vlan [vlan_id]`: Create a VLAN or enter VLAN configuration mode
- `switchport mode access`: Set port to access mode
- `switchport access vlan [vlan_id]`: Assign a port to a VLAN
- `switchport mode trunk`: Set port to trunk mode
- `switchport trunk allowed vlan [vlan_list]`: Specify VLANs allowed on a trunk

## Security

- `access-list [number] {permit|deny} [source] [source-wildcard]`: Create an access list
- `ip access-group [number] {in|out}`: Apply an access list to an interface
- `line vty 0 4`: Enter VTY line configuration mode
- `login local`: Enable local authentication for VTY lines

## DHCP

- `ip dhcp pool [name]`: Create a DHCP pool
- `network [network_address] [subnet_mask]`: Define the address pool
- `default-router [ip_address]`: Specify the default gateway for DHCP clients

## DNS Configuration

- `ip domain-name [domain_name]`: Set the default domain name
- `ip name-server [ip_address1] [ip_address2]`: Specify DNS server(s)
- `ip domain-lookup`: Enable DNS lookup (enabled by default)
- `no ip domain-lookup`: Disable DNS lookup
- `ip host [hostname] [ip_address]`: Create a static host entry
- `show hosts`: Display the DNS host table
- `clear host *`: Clear all host entries from the DNS cache
- `ip dns server`: Enable the router as a DNS server (if supported)
- `dns-server [ip_address]`: Specify DNS server in DHCP configuration

### DNS Troubleshooting

- `nslookup [hostname]`: Perform a DNS lookup (available on some IOS versions)
- `show ip dns view`: Display DNS view information
- `debug ip dns`: Enable DNS debugging

## Management

- `ntp server [ip_address]`: Configure NTP server
- `logging [ip_address]`: Configure a syslog server
- `snmp-server community [string] {ro|rw}`: Configure SNMP

## SSH Configuration

### 1. Set Hostname and Domain Name

- Hostname is required for key generation
- Domain name is used in key generation process

Copy

`hostname SwitchName ip domain-name yourdomain.com`

### 2. Generate RSA Key Pair

- Required for SSH encryption
- Recommended modulus size is 2048 bits or higher

Copy

`crypto key generate rsa modulus 2048`

### 3. Create Local User Account

- Used for SSH authentication
- Use strong passwords

Copy

`username admin privilege 15 secret StrongPassword`

### 4. Enable SSH Version 2

- More secure than SSH version 1

Copy

`ip ssh version 2`

### 5. Configure VTY Lines

- Enables SSH access and local authentication

Copy

`line vty 0 15  transport input ssh login local`

### 6. Optional SSH Settings

- Timeout and authentication retry limits

Copy

`ip ssh time-out 60 ip ssh authentication-retries 3`

## Verification

- Check SSH status: `show ip ssh`
- View current connections: `show ssh`

## Best Practices

1. Use strong, unique passwords for local accounts
2. Regularly update SSH keys
3. Limit SSH access using ACLs if possible
4. Monitor and log SSH access attempts

## Troubleshooting

1. Ensure cryptographic IOS image is installed
2. Verify IP connectivity to the switch
3. Check that RSA keys are generated: `show crypto key mypubkey rsa`
4. Confirm VTY line configuration: `show line vty 0 15`


## Troubleshooting

- `show running-config`: Display the current configuration
- `show interfaces`: Display interface status and configuration
- `show ip route`: Display the routing table
- `show vlan brief`: Display VLAN information (switches only)
- `debug [protocol]`: Enable debugging for a specific protocol

Remember to save your configuration with:
- `copy running-config startup-config` or `write memory`

Note: Always be cautious when applying these commands, especially in a production environment. Test configurations in a lab setting first when possible.







---
# References
