2023/09/06 09:04
Status: #definition
Tags: [[Linux]]

# Dev Directory - Device File Representation

The `/dev` directory contains device nodes that represent devices attached to the system. These nodes facilitate interaction with hardware devices, allowing programs and users to communicate with them through file operations. Notably, it can be used to establish socket connections and interact with devices directly, serving as a bridge between the system's hardware and software components.

---
## Special Properties 
- **Socket Connections**: Enables the creation of socket connections for inter-process communication. 
- **Device Interaction**: Allows direct interaction with hardware devices through specific device files.

---
## See Also
- [[Linux - File System]]

---
# References
