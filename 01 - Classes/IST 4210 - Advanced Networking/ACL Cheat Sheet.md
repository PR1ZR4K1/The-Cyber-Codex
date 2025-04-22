2024/12/01 18:51
Status: #idea
Tags:

# ACL Cheat Sheet

*Inbound rule set to permit the following:*

- [x] Finance team access to finance team all floors.
- [x] The Sales team needs access to the sales team on all floors. 
- [x] HR team access to HR team all floors 
- [x] Management team access to Management team all floors.
- [x] NetAdmin team access to NetAdmin team all floors. 
- [x] The Finance team and Sales team need to be able to share recourses over the network. (Hint Permit) 
- [x] The Management team needs to be able to Access the FTP file share on the Finance department network. (Hint FTP and FTP-Data) 
- [x] The Human Resource department needs to be able to print to the Managements Printer. (Hint Port 9100) 
- [x] Guests will be restricted to their floors (remember that your are allowing bridges and need to allow access to the floor you are working with. See Hands-on lab 13)

**Create access list**

```pt
conf t
ip access-list extended 100 
```

**Finance and Sales Access**

```pt

remark block individual host
deny ip host 10.10.80.6 10.10.10.0 0.0.0.127
remark finance and sales access
permit ip 10.10.15.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.20.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.25.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.30.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.40.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.50.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.55.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.60.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.65.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.70.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.75.0 0.0.0.127 10.10.10.0 0.0.0.127 
permit ip 10.10.80.0 0.0.0.127 10.10.10.0 0.0.0.127 

```

**HR Team Access**

```pt

remark HR team access
permit ip 10.10.15.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.20.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.25.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.30.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.40.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.50.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.55.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.60.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.65.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.70.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.75.128 0.0.0.63 10.10.10.128 0.0.0.63
permit ip 10.10.80.128 0.0.0.63 10.10.10.128 0.0.0.63

```

**Management Access**

```pt

remark management access
permit ip 10.10.15.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.20.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.25.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.30.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.40.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.50.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.55.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.60.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.65.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.70.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.75.192 0.0.0.31 10.10.10.192 0.0.0.31
permit ip 10.10.80.192 0.0.0.31 10.10.10.192 0.0.0.31

```

**Net Admin Access**

```pt

remark net admin access
permit ip 10.10.15.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.20.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.25.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.30.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.40.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.50.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.55.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.60.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.65.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.70.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.75.224 0.0.0.15 10.10.10.224 0.0.0.15
permit ip 10.10.80.224 0.0.0.15 10.10.10.224 0.0.0.15

```

**Management to Finance FTP access!**

```pt

remark management to finance ftp access
permit tcp 10.10.15.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.15.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.20.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.20.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.25.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.25.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.30.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.30.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.40.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.40.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.50.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.50.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.55.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.55.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.60.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.60.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.65.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.65.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.70.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.70.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.75.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.75.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21
permit tcp 10.10.80.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 20
permit tcp 10.10.80.192 0.0.0.31 10.10.10.0 0.0.0.63 eq 21

```

**HR to Management Printer access**

```pt

remark HR to management printer access
permit tcp 10.10.15.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.20.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.25.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.30.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.40.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.50.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.55.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.60.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.65.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.70.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.75.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100
permit tcp 10.10.80.128 0.0.0.63 10.10.10.192 0.0.0.31 eq 9100

```

**Guest to Guest Access?**

```pt

remark guest to guest access
permit ip 10.10.15.240 0.0.0.7 10.10.10.240 0.0.0.7

```

---
# References
