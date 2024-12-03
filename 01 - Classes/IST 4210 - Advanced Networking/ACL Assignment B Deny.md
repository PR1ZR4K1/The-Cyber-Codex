2024/11/26 23:00
Status: #MOC
Tags:

# ACL Assignment B

ACL

  

ip access-list extended ACL

  

# http and https deny from pc1

deny tcp host 172.31.1.101 64.101.255.254 0.0.0.0 eq www

deny tcp host 172.31.1.101 64.101.255.254 0.0.0.0 eq 443

  

deny tcp host 172.31.1.101 64.103.255.254 0.0.0.0 eq www

deny tcp host 172.31.1.101 64.103.255.254 0.0.0.0 eq 443

  
  

# ftp deny from pc2 to s1 and s2

  

deny tcp host 172.31.1.102 64.101.255.254 0.0.0.0 eq ftp

deny tcp host 172.31.1.102 64.103.255.254 0.0.0.0 eq ftp

  

# icmp deny from pc3 to s1 and s2

  

deny icmp host 172.31.1.103 64.101.255.254 0.0.0.0

deny icmp host 172.31.1.103 64.103.255.254 0.0.0.0

  

permit ip any any





---

## References

- [[ACL Assignment C Permit]]