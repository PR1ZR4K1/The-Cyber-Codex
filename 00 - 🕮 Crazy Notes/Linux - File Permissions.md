2023/09/06 11:12
Status: #definition
Tags: [[Linux]], [[File System]], [[Security]]

# Linux - File Permissions

In the Linux operating system, file permissions are a fundamental mechanism that governs the accessibility and security of files and directories. These permissions dictate who can read, write, or execute files, safeguarding sensitive data and maintaining system integrity. File permissions are defined for three types of users: the file owner, the group (a set of users), and others (everyone else).

#### Key Components:

1. **Read (r)**: This permission allows a user to read the contents of a file or list the contents of a directory.
    
2. **Write (w)**: This permission grants a user the ability to modify a file or directory, including creating, editing, or deleting files.
    
3. **Execute (x)**: This permission enables a user to run a file as a program or script, or access a directory and its contents.

#### Commands:

- **chmod**: A command to change the file permissions. For instance, `chmod 755 filename` sets read, write, and execute permissions for the owner, and read and execute permissions for the group and others.
    
- **chown**: A command to change the ownership of a file or directory. For example, `chown username:groupname filename` would change the owner and group of the specified file.
    
- **ls -l**: A command to list files with detailed information, including file permissions. The permissions are displayed as a string of characters, such as `-rwxr-xr-x`, indicating the permissions for the owner, group, and others, respectively.

---
## See Also
- [[Linux - Introduction]]
- [[Linux - Basic Commands]]
- [[Linux - File System]]

---
# References
