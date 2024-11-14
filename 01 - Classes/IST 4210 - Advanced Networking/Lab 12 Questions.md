2024/11/12 14:06
Status: #idea
Tags:

# 

We went to access restrictions -> internet access policy. We then added the two urls https://netflix.com and https://pornhub.com

We blocked the following services:

NNTP
Telnet

Security:

WPA2 Personal

Passphrase: IST4210@cisco

Firmware: 4.30.18

Printer IP: 10.10.60.5

Printer ip should be shown in dhcp pool leases. show ip dhcp pool

Alternatively you could nmap the network like this

nmap -T5 10.10.xx.0/24

You could even limit it to the subnet of the finance VLAN

nmap -T5 10.10.xx.0/26








---
# References
