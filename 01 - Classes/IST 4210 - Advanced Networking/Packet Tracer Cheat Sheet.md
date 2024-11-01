2024/10/03 13:25
Status: #idea
Tags:

# Packet Tracer Cheat Sheet

configure terminal  
hostname SWFloor1
no ip domain lookup
no service call-home
no call-home
service password-encryption  
enable secret IST4210class
line con 0  
password IST4210cisco
login  
logging synchronous  
exit  
line vty 0 15  
password IST4210cisco
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
vlan 60  
name Guest
vlan 99 
name NTAdmin 
exit  
crypto key generate rsa general-keys modulus 1024  
interface gi1/1/1
switchport mode trunk
switchport trunk encapsulation dot1q
switchport trunk native vlan 5  
switchport trunk allowed vlan 5,10,20,30,40,60,99  
no shutdown  
interface range gi1/0/1-4
no shut
switchport mode access  
switchport access vlan 10
interface range gi1/0/5-7
no shut
switchport mode access  
switchport access vlan 20  
interface range gi1/0/8-9
no shut
switchport mode access  
switchport access vlan 30  
interface range gi1/0/10
no shut
switchport mode access  
switchport access vlan 40
interface gi1/0/11
no shut
switchport mode access  
switchport access vlan 60
interface gi1/0/12  
no shut
switchport mode access  
switchport access vlan 99  
exit  
interface vlan 10  
no shut
description Vlan for Finance department
ip address 10.10.10.1 255.255.255.192  
interface vlan 20
no shut
description Vlan for Sales department  
ip address 10.10.10.65 255.255.255.192  
interface vlan 30
no shut
description Vlan for HR department  
ip address 10.10.10.129 255.255.255.192  
interface vlan 40
no shut
description Vlan for Management department  
ip address 10.10.10.193 255.255.255.224
interface vlan 60
no shut
description Vlan for Guests  
ip address 10.10.10.241 255.255.255.248
interface vlan 99
no shut
description Vlan for NTAdmin department  
ip address 10.10.10.225 255.255.255.240

service dhcp
ip dhcp excluded-address 10.10.10.1 10.10.10.5
ip dhcp excluded-address 10.10.10.65 10.10.10.70
ip dhcp excluded-address 10.10.10.129 10.10.10.134
ip dhcp excluded-address 10.10.10.193 10.10.10.197
ip dhcp excluded-address 10.10.10.225 10.10.10.226
ip dhcp excluded-address 10.10.10.241 10.10.10.242
ip dhcp pool Finance-VLAN10
network 10.10.10.0 255.255.255.192
default-router 10.10.10.1
ip dhcp pool Sales-VLAN20
network 10.10.10.64 255.255.255.192
default-router 10.10.65.65
ip dhcp pool HR-VLAN30
network 10.10.10.128 255.255.255.192
default-router 10.10.10.129
ip dhcp pool Management-VLAN40
network 10.10.10.192 255.255.255.224
default-router 10.10.10.193
ip dhcp pool NTAD
network 10.10.10.224 255.255.255.240
default-router 10.10.10.225
ip dhcp pool Guest
network 10.10.10.240 255.255.255.248
default-router 10.10.10.241
end  
copy run start






---
# References

- [[Bill Herbert Cheat Sheet]]