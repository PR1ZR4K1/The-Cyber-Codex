2024/11/29 15:16
Status: #idea
Tags:

# Extended ACL Facts


Extended ACLs give you far greater detail and control over the security policies that govern your network traffic. Key characteristics of extended access control lists (ACLs) include the following:

- Extended ACLs can filter by:
    - Source IP protocol (IP, TCP, UDP, etc.)
    - Source hostname or host IP address
    - Source or destination socket number
    - Destination hostname or host IP address
    - Precedence or type of service (TOS) values
- Extended ACLs, as a general rule, should be placed as close to the source router as possible. This keeps the packets from being sent throughout the rest of the network.
- Extended ACLs can be identified using either a name or and ID number. When an ID number is used, it must fall in the following ranges:
    - 100–199
    - 2000–2699
- Extended ACLs include a protocol designation (such as IP, TCP, or UDP). Use IP to match any Internet Protocol (including TCP and UDP). Use other keywords to match specific protocols.




---
# References

- [[IPv6 Extended ACL Facts]]