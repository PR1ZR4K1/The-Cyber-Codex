2024/04/08 16:31
Status: #idea
Tags: [[Linux]]

## Keyboard Shortcuts

| G   | Go to end of man page                 |
| --- | ------------------------------------- |
| /   | Begin a search for a word             |
| n   | Move to the next match of a selection |
| q   | quit                                  |

## Sections

**Documentation in man is organized in different sections**

The following sections matter specifically for RHCSA

- 1 - Executable programs or shell commands
- 5 - File formats and conventions 
- 8 - System administration commands

### Complete table of sections and meaning

 
| 1   | Executable programs or shell commands                                                         |
| --- | --------------------------------------------------------------------------------------------- |
| 2   | System calls (functions provided by the kernel)                                               |
| 3   | Library calls (functions within program libraries)                                            |
| 4   | Special files (usually found in /dev)                                                         |
| 5   | File formats and conventions, e.g. /etc/passwd                                                |
| 6   | Games                                                                                         |
| 7   | Miscellaneous (including macro packages and conventions), e.g. man(7), groff(7), man-pages(7) |
| 8   | System administration commands (usually only for root)                                        |
| 9   | Kernel routines [Non standard]                                                                |



*All sections are described in `man man`. Use `man n intro` for and introduction to the topic of a specific section number*

### View all sections for a given command

`man -a passwd`

this allows you to view the different sections of a command like passwd for example.





---
# References
