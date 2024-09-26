2024/09/26 13:03
Status: #idea
Tags:

# Basic Config Cheat Sheet

en
conf t
hostname S3
banner motd *Unauthorized access prohibited!*
enable secret class
line con 0
password cisco
login
exit
service password-encryption
no ip domain-lookup
ip domain-name ist4210-Lab.com
ip ssh version 2
crypto key generate rsa general-keys modulus 1024
username admin privilege 15 secret sshadmin
line vty 0 15
transport input ssh
password cisco
login local
exit
vlan 10
name Faculty/Staff
vlan 20
name Students
vlan 30 
name Guest(Default)
vlan 99
name NTManagement
end
copy run start



interface range g0/1 - 2
switchport mode trunk
switchport trunk native vlan 5
switchport trunk allowed vlan 5,10,20,30



---
# References
