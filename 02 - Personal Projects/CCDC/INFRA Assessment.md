2024/12/26 17:25
Status: #idea
Tags:

# INFRA Assessment

## System Profile

Machine Name:  *macaroni*
Primary Role: *Web Server/Database*  
IP Address:  *192.168.220.84*
Operating System:  *Ubuntu 20.04.6 LTS*
Team Member:  *Jaylon*
Assessment Time: *uh now*

## Required Services Overview

### Critical Scoring Services

1. *Jupyter Notebooks*
    
    - Current Status: *UP*
        
    - Port: *8888*
        
    - Authentication Method: *there is none lol*
        
    - Known Issues: *unauthenticated root shell through gui...*
        
    - Hardening Applied: *Edit configs to add password based auth.*
        
    - Screenshot of service:
        
2. [Service Name]  
    - ![[Pasted image 20241226173805.png]]
    

### Supporting Services

1. *mysql*
    
    - Required By: *jupyter notebook*
        
    - Current Status: *up*
        
    - Dependencies: *Uhhh*
        
    - Hardening Applied: *Removed extra admin accounts and applied password*
        

## Network Exposure

### Listening Services

|      |         |           |                 |                    |
| ---- | ------- | --------- | --------------- | ------------------ |
| Port | Process | Required? | Service         | Hardening Status   |
| 8888 | 761     | yes       | jupyter-noteboo | hardened?          |
| 1433 | 1402    | yes       | sqlservr        | yes                |
| 22   | 850     | yes       | ssh             | copy pasted config |

### Internal Connections

- Database Links:
    
- Domain Services:
    
- Mail Flow:
    
- File Shares:
    

### Suspicious Traffic

- Unexpected Connections:
    
- Investigation Status:
    
- Monitoring Plan:
    

## Vulnerabilities and Hardening

### Known Issues

1. [Issue Name]
    
    - Affected Service: *Jupyter*
        
    - Current Risk: *High*
        
    - Scoring Impact: *Medium (depends cuz the red team would decide to keep the service up to establish persistence and then maybe bring it down)*
        
    - Fix Priority: *High*
        
    - Hardening Steps: 
	    - edit config file
		```
		cd .jupyter
		vim jupyter_notebook_config.py
		```
		- Add password based auth (password is password123)
		```
		c.ServerApp.password = 'argon2:$argon2id$v=19$m=10240,t=10,p=8$spZoSqbkraU1a5yj2oe98Q$CH09U8s6Sn2Sm/h42pxpJIfQE7adg5e0z+MMEPFTJhc' 
		c.ServerApp.password_required = True c.IdentityProvider.token = ''
		```

		- Add ssl
	```
	c.ServerApp.allow_root = False
	c.ServerApp.certfile = 'mycert.pem' 
	c.ServerApp.keyfile = 'mykey.pem'
	
	# maybe do this to restrict ips 
	c.ServerApp.ip = 'your.ip.address'
	```
	- Generate self signed certs
	```
	openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout mykey.pem -out mycert.pem
	```

    - Testing Method:
	    - restart the service 
		```
		jupyter notebook --certfile=mycert.pem --keyfile=mykey.pem --port=8888
		```
	    - visit the website in your browser
        
2. [Issue Name]  
    [Same structure as above]
    

### Applied Hardening

1. [Hardening Step]
    
    - Target:
        
    - Changes Made:
        
    - Tested Working:
        
    - Before/After Evidence:
        
2. [Hardening Step]  
    [Same structure as above]
    

## Defense Strategy (What would you do in competition?)

### Immediate Actions (Next 30 min)

1. [Action]
    
    - Purpose:
        
    - Steps:
        
    - Testing Method:
        
    - Success Criteria:
        
    - Rollback Plan:
        

### Short-term Actions (Next 2 hours)

1. [Action]  
    [Same structure as above]





---
# References
