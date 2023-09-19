2023/09/06 09:08
Status: #definition
Tags: [[Linux]]

# Proc Directory - Process Information Viewer

The `/proc` directory is a virtual filesystem that provides a detailed, real-time view of the system's state, including kernel, processes, and system memory. It doesn't contain real files but runtime system information, such as system memory, devices mounted, hardware configuration, etc.

---
## Special Properties 
- **Process Information (PID)**: Each running process is assigned a unique process ID (PID), and you can view detailed information about each process in directories named with their PID. For instance, to view the command that started a process with PID 123, you could use `cat /proc/123/cmdline`. 
- **System Insights**: Offers insights into various system attributes, including CPU, memory, and device status. For example, to view the system's memory information, you could use `cat /proc/meminfo` to get a detailed report.

---
## See Also
- [[Linux - File System]]

---
# References
