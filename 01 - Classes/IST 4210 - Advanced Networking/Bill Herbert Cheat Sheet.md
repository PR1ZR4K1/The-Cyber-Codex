2024/10/03 13:25
Status: #idea
Tags:

# Bill Herbert Cheat Sheet

configure terminal  
hostname SWFloor1  
no ip domain-lookup  
service password-encryption  
enable secret class  
line con 0  
password cisco  
login  
logging synchronous  
exit  
line vty 0 15  
password cisco  
login  
logging synchronous  
exit  
ip domain-name ist4210-Lab.com 
banner motd #unauthorized access is prohibited#  
username admin privilege 15 secret sshadmin21
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
vlan 50  
name Guest
vlan 99 
name NTAdmin 
exit  
crypto key generate rsa general-keys  modulus 1024  
interface range fa1/0/48  
switchport mode trunk  
switchport trunk native vlan 5  
switchport trunk allowed vlan 5,10,20,30,40,50,99  
no shutdown  
interface range f1/0/1-6
no shut
switchport mode access  
switchport access vlan 10
interface range fa1/0/7-11
no shut
switchport mode access  
switchport access vlan 20  
interface range fa1/0/12-15
no shut
switchport mode access  
switchport access vlan 30  
interface range fa1/0/16-17
no shut
switchport mode access  
switchport access vlan 40
interface range fa1/0/19-22
no shut
switchport mode access  
switchport access vlan 99
interface fa1/0/18  
no shut
switchport mode access  
switchport access vlan 50  
exit  
interface vlan 10  
no shut
description Vlan for Finance department
ip address 10.20.10.2 255.255.255.192  
interface vlan 20
no shut
description Vlan for Sales department  
ip address 10.20.10.66 255.255.255.192  
interface vlan 30
no shut
description Vlan for HR department  
ip address 10.20.10.130 255.255.255.192  
interface vlan 40
no shut
description Vlan for Management department  
ip address 10.20.10.194 255.255.255.224
interface vlan 50
no shut
description Vlan for Guests  
ip address 10.20.10.242 255.255.255.248
interface vlan 99
no shut
description Vlan for NTAdmin department  
ip address 10.20.10.226 255.255.255.240  
end  
copy run start





---
# References
