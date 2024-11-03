2024/09/17 12:47
Status: #idea
Tags: [[Route Summarization]]

# Route Summarization Command List

Route summarization combines a contiguous set of addresses into a single address to reduce network traffic. Route summarization is also referred to as route aggregation. The following table lists the commands used to configure route summarization.

| Command                                                                           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| (config-router)# **no auto-summary**                                              | Turns off automatic route summarization:<br><br>- By default, subnets are summarized based on classful boundaries when advertising routes on networks with a different class boundary.<br>- You must disable automatic summarization if you have a network address (such as 10.0.0.0) subnetted into smaller subnets and separated by a network with a different classful network address (such as 12.0.0.0).<br>- Summarizing routes at classful major network boundaries creates smaller routing tables, causing the routing update process to consume less bandwidth. |
| (config-if)# **ip summary-address  <br>_[routing_protocol]_ _a.b.c.d_ _m.m.m.m_** | Configures a summary address on the specified interface:<br><br>- Use this command on outbound interfaces of the appropriate routers.<br>- The neighboring device will have only a summary route in its routing table.<br>- If the neighboring devices receive a query packet for a network that matches the summary route, it will send a network a.b.c.d/m unreachable message in response and will not extend the query packets any further.<br>- This command will add a summary route to the routing table, with the route's next-hop interface set to null0.       |

The following commands disable auto-summarization and specify a summary address for FastEthernet 0/1:

> Router(config-router)#**no auto-summary**Router(config-router)#**exit**Router(config)#**int fa 0/1**Router(config-if)#**ip summary-address rip 172.16.0.0 255.255.0.0**





---
# References

- [[Route Summarization Facts]]
172.22.70.1
172.22.70.129

172.22.70.00000001
172.22.70.10000001
172.22.70.0/24

172.22.68.1
172.22.69.1
172.22.01000100.
172.22.01000100.
172.22.68.0/23


172.22.64.0 /23
172.22.66.0 /23
01000000
01000010

172.22.64.0/22