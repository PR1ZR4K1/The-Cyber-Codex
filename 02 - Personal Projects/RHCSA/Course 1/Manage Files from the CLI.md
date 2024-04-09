2024/01/31 18:48
Status: #idea
Tags:

# Module 3

## Make Links Between Files

There are two types of links: *hard link and symbolic link (soft link)*
## Hard Link

**Every file starts with a single hard link which is from its initial name to the data on the file system**

You create a name that points to data. So, when you create a hard link to a file that already exists you are mapping a new name to the same set of data.

### How to identify file with multiple hard links?

`ls -l`

A file with a hard link attached to it has a value higher than one: 

![[Pasted image 20240305183159.png]]

*grade1 has another hard link associated with it*

### How to create hard link

```
ln {existing file} {new link}

ln file.txt new_link.txt
```

### Determine if two files are hard linked 

```
ls -il {file1} {file2}

ls -il file.txt new_link.txt
```

The `-i` flag will display the inode number for each file. If they are the same then you know these two files are linked. Everything from file permissions, ownership, timestamp, and size will be the same for this type of link because they point to the same data. 

Result: 
![[Pasted image 20240305184054.png]]

#### Good to Know

Even if original file is deleted the contents of the file will still be accessible from the other file because the link still exists. Only when the file has no remaining links will it be unreachable.

## Symbolic (Soft) Link

A symbolic link is not a regular file, but a special type of file that points to an existing file or directory.

### Advantages over hard links

- Symbolic links can link two files on different file systems.
- Symbolic links can point to a directory or special file, not just to a regular file.

### Creating a sym link

`ln -s {existing file} {sym_link.txt}`

Example: 

![[Pasted image 20240305193712.png]]

*In the preceding example, the first character of the long listing for the `/tmp/newfile-symlink.txt` file is `l` (letter l) instead of `-`. This character indicates that the file is a symbolic link and not a regular file.*

**When creating a sym link to a directory you must provide complete file path. Don't use ../ within path**
### Dangling Symbolic link

When the file that a symbolic link points to is deleted the link becomes a dangling symbolic link. If you create a new file with the same name as the previously deleted file the symbolic link will no longer be dangling and will point to the new file

## Hard vs. Sym Link

- hard link points a name to data on a storage device
- sym link points a name to another name, which points to data on a storage device
- sym links can point to a directory where a hard link can only point to files.


## Quiz 1 Notes

Which directory contains non-persistent process runtime data?

- /tmp
- /etc
- /run
- /var

*Answer: /run* 

Which directory contains installed software programs and libraries?

- /etc
- /lib
- /usr
- /var

*Answer: /usr*




---
# References
