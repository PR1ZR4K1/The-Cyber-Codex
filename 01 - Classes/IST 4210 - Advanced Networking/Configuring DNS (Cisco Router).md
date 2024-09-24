2024/09/17 09:33
Status: #idea
Tags:[[Domain Name System]]

## Logical Hostname to IP Address Process

The following table describes the difference between a router or switch, and a workstation when resolving a logical hostname to an IP address:

Device Details Router or Switch DNS name resolution looks for information in the following places (in this order):

1. Static DNS entries
2. DNS server query (if enabled)

Workstation DNS name resolution looks for information in the following places (in this order):

1. Local DNS cache
2. HOSTS file
3. DNS server query (Primary)
4. DNS server query (Secondary)
## Configuration Commands

Use the following commands to configure DNS services on a router or switch:

|Command|Description|
|---|---|
|router(config)# **ip host _[name] a.b.c.d_**|Creates static DNS entries.|
|router(config)# **ip domain-name _[name]_**|Configures the router default domain (for DNS).|
|router(config)# **ip name-server _a.b.c.d_**|Sets the default DNS name server.|
|router(config)# **ip domain-lookup**|Enables the router to use DNS to identify IP addresses from hostnames.|
|router(config)# **no ip domain-lookup**|Disables the broadcast name resolution of hostnames.|
|router# **show hosts**|Displays a list of known IP hosts.|





---
# References
