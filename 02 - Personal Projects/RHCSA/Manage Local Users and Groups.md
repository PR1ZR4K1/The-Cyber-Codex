2024/01/31 19:08
Status: #idea
Tags:
## /etc/passwd

Each line contains information about a user. The file is divided into seven colon-separated fields.

Here is example output:

![[Pasted image 20240306124158.png]]

*Definitions from left to right:*
- **user01:** The username for this user
- **x:** The user's encrypted password was historically stored here; now it is a placeholder.
- **1000:** The UID number for this user
- **1000:** The GID for this user account's primary group
- **User One:** A brief comment, description, or the real name for this user.
- **/home/user01:** The user's home dir, and the initial working directory when the login shell starts.
- **/bin/bash:** The default shell program for this user that runs at login. 
	- *Some accounts user the /sbin/nologin shell to disallow interactive logins with that account.* 

## Groups 

A group is a collection of users that need to share access to files and other system resources. Uniquely identified by the group ID (GID). 

### /etc/group 

Each line contains information about one group. Each entry is divided into four colon-separated fields

Example:

![[Pasted image 20240306124824.png]]

*Definitions from left to right:*

- **group01:** Name for this group
- **x:** used to be group password field now it is a placeholder.
- **10000:** The GID for this group.
- **user01, user02, user03:** A list of users that are members of this group as a supplementary group.

### Primary and Supplementary Groups

**Every user has only one primary group!**

#### Primary Groups

*For local users, this group is listed by GID in /etc/passwd.*

When a regular user is created, a group is created with the same name as the user, to be the primary group for the user. This group is referred to as the *User Private Group*. This distinction simplifies management of file permissions because user groups are separated by default.

#### Supplementary Groups

**Membership in supplementary groups is stored in the /etc/group file**

Users are granted access to files based on whether any of their groups have access.

## /etc/sudoers
# Quiz Notes

Which item represents the program that provides the user's command-line prompt?

- Primary shell
- Home directory
- <mark style="background: #FFF3A3A6;">Login Shell</mark>
- Command Name








---
# References
