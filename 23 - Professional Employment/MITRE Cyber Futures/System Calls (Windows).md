2024/06/14 10:50
Status: #idea
Tags: [[Windows Internals]]

# System Calls in Windows

**Overview**:

System calls in Windows are low-level functions provided by the operating system kernel (ntoskrnl.exe) that allow applications and system components to request services from the kernel. These system calls are the backbone of the operating system's functionality, enabling various operations like process management, file operations, and memory management.

**Characteristics**:

1. **Low-Level Operations**: System calls provide the interface for performing low-level operations directly with the operating system kernel.
   
2. **Privileged Mode**: System calls operate in kernel mode, allowing access to hardware and critical system resources.

**Mechanism**:

1. **Nt/Zw Prefixes**: System calls are typically exposed through functions prefixed with `Nt` (for internal use) and `Zw` (for external use).
   
2. **System Service Dispatch Table**: Each system call is associated with an entry in the System Service Dispatch Table (SSDT), which maps the system call to its corresponding handler in the kernel.
   
3. **Interrupt 0x2E**: On x86 systems, the `int 0x2E` instruction is used to transition from user mode to kernel mode to execute a system call. On x64 systems, the `syscall` instruction is used.

**System Call Numbers**:

System calls are identified by unique numbers (indexes) that correspond to their entries in the SSDT. These numbers are used by the kernel to locate the appropriate handler for each system call.

**Hex Values and Backwards Compatibility**:

1. **Changing Values**: The specific hex values (indexes) of system calls can change between different versions of Windows. This occurs because the internal implementation and order of system calls in the SSDT may be modified with each new version of Windows.

2. **Backward Compatibility**: To maintain backward compatibility, Windows ensures that older applications continue to work even if the system call numbers change. This is achieved through several mechanisms:
    - **Thunks and Shims**: Windows uses compatibility layers, such as thunks and shims, to translate older system call numbers to their new equivalents.
    - **Function Wrappers**: High-level API functions provided by Windows (e.g., those in Kernel32.dll and User32.dll) act as stable wrappers around the underlying system calls, insulating applications from changes in system call numbers.
   
3. **Versioned SSDTs**: Windows maintains different versions of the SSDT for different versions of the operating system, ensuring that applications targeting a specific version can still use the expected system call numbers.

### Explanation

System calls in Windows provide the essential interface for interacting with the kernel. Although the specific hex values for system calls may change between Windows versions, backward compatibility is maintained through compatibility layers and function wrappers.

### LaTeX Expression

An example of invoking a system call in assembly language can be represented as:
$$
\text{mov eax, 0x25} \\ \text{int 0x2E}
$$

This example assumes that `0x25` is the system call number for a specific function.

#### Key Components

Understanding how system calls work and how their hex values can change is crucial for developing low-level software that interacts with the Windows kernel. Despite these changes, backward compatibility mechanisms ensure that applications continue to function across different Windows versions.






---
# References
