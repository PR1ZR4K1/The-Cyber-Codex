2024/11/29 14:20
Status: #idea
Tags:

# ACL Troubleshooting Facts

Troubleshooting and resolving issues with ACLs requires an understanding of the matching logic and detailed analysis. Each line of the ACL must be scrutinized to determine the type of traffic it allows or denies.

This lesson covers the following topics:

- ACL troubleshooting guidelines
- Commands to view ACLs

## ACL Troubleshooting Guidelines

When troubleshooting ACLs, observe the following guidelines:

- Use a text editor, such as Notepad, to build and evaluate ACLs prior to implementing them:

- This allows misconfigurations to be identified and fixed prior to the ACL being brought online in a production environment and potentially causing undesired results.
- You should step through the ACL, line by line, and use the matching logic to identify the traffic it allows or denies. Analyze each address and wildcard mask. Identify the protocols and addresses that will be matched.
- Once done, review the results as a whole and identify whether the ACL meets network design specifications.
- If the matching logic is correct, copy and paste each line into the ACL configuration on the router.

- Verify that the ACL has been configured on the correct interface. The matching logic in the ACL may be perfect, but if it's implemented on the wrong interface, it will not achieve the desired effect.
- Verify that the ACL has been configured in the correct direction. If it's constraining traffic in the wrong direction, it will not achieve the desired effect.
- Do not forget the implicit deny included at the end of every ACL, both standard and extended ACLs:

- The implicit deny is not displayed when viewing the ACL, but it is always there.
- Matching statistics are not displayed for the implicit deny.
- By implementing an ACL, all traffic is locked down by default as a result of the implicit deny.
- If a packet does not match any line in an ACL, then it will be dropped when it hits the implicit deny.
- The ACL should include lines that allow all permitted traffic through. For example, a common strategy is to place all of the deny statements first in the ACL, then set the last line of the ACL to permit any.

- Use the log keyword at the end of access-list commands to create log messages with detailed statistics about matches for a specific line in the ACL:

- For example, the access-list 2 permit 192.168.1.1 log command creates log messages each time this line of the ACL is matched.
- A sample log message for an ACL is as follows:

> Sep 14 13:32:04.071: %SEC-6-IPACCESSLOGNP: list 2 permitted 0 
>     192.168.1.1 -> 172.17.8.1, 1 packet

## Commands to View ACLs

Use the following commands to view ACL information:

|Command|Description|
|---|---|
|**access-list _ACL_ log**|Displays log messages that identify which line in an ACL is being matched.|
|**show run  <br>show access-lists**|Displays all access lists that exist on the router.|
|**show ip int  <br>show run**|Displays all access lists applied to an interface.|
|**show log**|Displays rejected traffic information.|
|**show run  <br>show ip access-lists**|Displays IP access lists configured on the router.|
|**show access-lists _[number]_**|Displays a specific access list.|





---
# References
