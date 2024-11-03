2024/10/31 13:36
Status: #idea
Tags:

# Untitled

configure terminal
no service call-home
no call-home
hostname SWFloor1
no ip domain-lookup
service password-encryption
enable secret ist4210class
line con 0
password ist4210cisco
login
logging synchronous
exit
line vty 0 15
password ist4210cisco
login
logging synchronous
exit
ip domain name ist4210-Lab.com
banner motd #unauthorized access is prohibited#
username admin privilege 15 secret sshadmin
line vty 0 15
transport input ssh
login local
exit
vlan 10
name Finance
vlan 20
name Sales
vlan 30
name HR
vlan 40
name Management
vlan 99
name NTAdmin
vlan 60
name Guest
exit
crypto key generate rsa general-keys modulus 1024
interface range g0/1
switchport mode trunk
encapsulation dot1q 
switchport trunk native vlan 5
switchport trunk allowed vlan 5,99,10,20,30,40,60
no shutdown
interface range Gi1/0/1-4
switchport mode access
switchport access vlan 10
interface range Gi1/0/5-7
switchport mode access
switchport access vlan 20
interface range Gi1/0/8-9
switchport mode access
switchport access vlan 30
interface range Gi1/0/10
switchport mode access
switchport access vlan 40
interface Gi1/0/12
switchport mode access
switchport access vlan 99
interface Gi1/0/11
switchport mode access
switchport access vlan 60
interface vlan 10
description Vlan Finance
ip address 10.10.10.2 255.255.255.192
interface vlan 20
description Vlan for Sales
ip address 10.10.10.66 255.255.255.192
interface vlan 30
description Vlan for HR
ip address 10.10.10.130 255.255.255.192
interface vlan 40
description Vlan for Management
ip address 10.10.10.194 255.255.255.224
interface vlan 99
description Vlan for NTAdmin
ip address 10.10.10.226 255.255.255.240
interface vlan 60
description Vlan for Guest
ip address 10.10.10.242 255.255.255.248
end
copy run start
service dhcp
no ip dhcp conflict logging
ip dhcp excluded-address 10.10.10.2 10.10.10.3
ip dhcp excluded-address 10.10.10.65 10.10.10.66
ip dhcp excluded-address 10.10.10.129 10.10.10.130
ip dhcp excluded-address 10.10.10.193 10.10.10.194
ip dhcp excluded-address 10.10.10.225 10.10.10.226
ip dhcp excluded-address 10.10.10.241 10.10.10.242
ip dhcp pool Finance

network 10.10.10.2 255.255.255.192
default-router 10.10.10.2
ip dhcp pool Sales
network 10.10.10.64 255.255.255.192
default-router 10.10.10.66
ip dhcp pool HR
network 10.10.10.129 255.255.255.192
default-router 10.10.10.130
ip dhcp pool Management
network 10.10.10.193 255.255.255.224
default-router 10.10.10.194
ip dhcp pool NTadmin 
network 10.10.10.225 255.255.255.248
default-router 10.10.10.226
ip dhcp pool Guest
network 10.10.10.241 255.255.255.248
default-router 10.10.10.242





---
# References
