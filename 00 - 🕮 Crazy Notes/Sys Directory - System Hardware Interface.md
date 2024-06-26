2023/09/06 09:12
Status: #definition
Tags: [[Linux]]

# Sys Directory - System Hardware Interface

The `/sys` directory, also known as sysfs, is a virtual filesystem in Linux that provides a detailed view of the kernel's view of the system's hardware components. It presents information about hardware and device drivers in a structured manner, allowing users and programs to query hardware attributes and configurations directly from the filesystem.

---
## Special Properties 
- **Hardware Information**: Offers a detailed representation of the system's hardware components, including CPUs, memory modules, and peripheral devices. You can explore various subdirectories to find detailed attributes of these components. 
- **Driver Interaction**: Allows users to interact with device drivers and hardware components directly. For instance, you can query or modify device settings by reading or writing to files in this directory. 
- **Dynamic View**: The contents of the `/sys` directory are dynamically generated by the kernel, providing a real-time view of the system's hardware state.

---
## Usage Examples 
- **View CPU Information**: To view information about the CPU, you can use commands like `cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq` to view the current frequency of CPU 0. 
- **Query Device Attributes**: To query attributes of a specific device, navigate to the appropriate subdirectory and use `cat` to read the attribute files. For example, `cat /sys/class/net/eth0/speed` would show the speed of the `eth0` network interface.

---
## See Also
- [[Linux - File System]]

---
# References
