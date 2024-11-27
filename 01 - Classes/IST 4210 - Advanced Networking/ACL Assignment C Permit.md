2024/11/26 23:02
Status: #MOC
Tags:

# ACL Assignment C Permit


```
conf t
ip access-list 199
permit tcp 10.101.117.32 0.0.0.15 10.101.117.0 0.0.0.31 eq telnet
permit icmp any any
```




---
