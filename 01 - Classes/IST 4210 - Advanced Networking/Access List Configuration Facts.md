2024/11/29 14:15
Status: #idea
Tags:

# Access List Configuration Facts

Creating access control lists (ACLs) requires an understanding of the matching logic used and the commands to the implement matching logic.

The two general steps for configuring ACLs are:

1. Create the list and list entries with the access-list or IP access-list commands.
2. Apply the list to a specific interface or line:

- Use the ip access-group command to apply the list to an interface.
- Use the access-class command to apply the list to a line.

When constructing access list statements, keep in mind the following:

- The access list statement includes the access ID number.
- A single access list can include multiple access list statements. The access list number groups all statements into the same access list.
- List statements include an action of either permit or deny.
- To identify a host address in the access list statement, use the following formats:

> n.n.n.n
> n.n.n.n 0.0.0.0
> 
> or
> 
> host n.n.n.n
> 
> Where n.n.n.n is the IP address of the host.

- To identify a network address, use the format:

> n.n.n.n w.w.w.w
> 
> Where n.n.n.n is the subnet address and w.w.w.w is the wildcard mask.

- You should enter access list statements in order, with the most restrictive statements at the top. Traffic is matched to access list statements in the order they appear in the list. If the traffic matches a statement high in the list, subsequent statements will not be applied to the traffic.
- Each access list has an implicit deny any statement at the end of the access list. Your access list must contain at least one allow statement or no traffic will be allowed.
- When you remove an access list statement, the entire access list is deleted. Use Notepad or another text editor to construct and modify access lists, and then paste the list into the router console.
- A single access list can be applied to multiple interfaces.

Newer routers process ACLs differently. For example, when you remove an access list statement, only that statement, not the entire access list is removed. On newer computers, you must first enter the command prompt mode before you can create ACLs. The following table describes the commands you use to enter into command prompt mode.

|Command|Description|
|---|---|
|Router> **enable**|This command logs you into the enable mode, also known as the privileged mode.|
|Router# **configure terminal**|This command logs you into configuration mode.|
|Router(config)#|This is the prompt from which you can start creating access lists.|

In addition to numbering ACLs, you can use a specific sequence number to identify the order of the access list statement being created. The access list statements are processed in sequence by these numbers. The following table gives an example:

|Command|Description|
|---|---|
|Router(config)# **ip access-list standard 1**|Creates or edits a standard access list using an ID number of 1.|
|Router(config)# **10 deny 192.168.0.0 0.255.255.255**|Assigns the sequence number of 10 to the deny statement.|

The following commands create a standard IP access list that permits all outgoing traffic, except the traffic from network 10.0.0.0, and applies the list to the Fast Ethernet 0/0 interface:

> Router>**enable**
> Router#**configure terminal**
> Enter configuration commands, one per line. End with CNTL/Z.
> Router(config)#**access-list 1 deny 10.0.0.0 0.255.255.255**
> Router(config)#**access-list 1 permit any**
> Router(config)#**interface fa0/0**
> Router(config-if)#**ip access-group 1 out**
> Router(config-if)#**end**
> Router#

The following commands create a standard named IP access list named block-network that permits all outgoing traffic, except the traffic from network 172.16.20.0, It applies the list to the Fast Ethernet 0/0 interface. :

> Router>**enable**
> Router#**configure terminal**
> Enter configuration commands, one per line. End with CNTL/Z.
> Router(config)#**ip access-list standard block-network**
> Router(config-std-nacl)#**deny 172.16.20.0 0.0.0.255**
> Router(config-std-nacl)#**permit any**
> Router(config)#**interface fa0/0**
> Router(config-if)#**ip access-group block-network out**
> Router(config-std-nacl)#**end**

The following commands create a standard IP access list that rejects all traffic, except traffic from host 10.12.12.16. It applies the list to the Serial0 interface:

> Router>**enable**
> Router#**configure terminal**
> Enter configuration commands, one per line. End with CNTL/Z.
> Router(config)#**access-list 2 permit 10.12.12.16**
> Router(config)#**interface s0**
> Router(config-if)#**ip access-group 2 in**
> Router(config-if)#**end**

The following commands create a standard access list that allows VTY lines 0–4 access only from the internal network of 192.168.1.0/24:

> Router>**enable**
> Router#**configure terminal**
> Enter configuration commands, one per line. End with CNTL/Z.
> Router(config)#**access-list 12 permit 192.168.1.0 0.0.0.255**
> Router(config)#**line vty 0 4**
> Router(config-line)#**access-class 12 in**





---
# References
