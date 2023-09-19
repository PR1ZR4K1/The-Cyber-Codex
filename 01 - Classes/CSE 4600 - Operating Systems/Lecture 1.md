2023/09/11 10:40
Status: #idea
Tags: [[Operating Systems]]

# Lecture 1


Operating Systems are like ACs. They work well unless you open Windows - Linus Tordivals

**Abstractions**: process, thread (applications that the OS executes), file, socket, memory page
**Policies**: How to use/implement the mechanisms and policies in efficient and fair manner (LFU, LRU)
**Mechanisms**: Create, launch, open, write, allocate operations

**Objectives:**
- Connect to [[Course Goals]]
- Understand operating system operations and design considerations
- Learn about interrupts, system calls, and OS organization

**Main Points:**
1. **Operating System Operations:**
    - **Components:**
        - Hardware interaction
        - User application management
        - Memory and file system management
        - CPU scheduling
        - Process/thread management
        - Disk I/O and networking
    - **Optimization Considerations:**
        - Application and purpose of the OS
        - Machine's primary functions
        - Workload requirements (e.g., storage, image/video analysis)
2. **Design and Implementation Principles:**
    - **Separation of Mechanisms and Policies:**
        - Flexibility to support multiple policies
        - Memory management strategies (LRU, LFU, random)
    - **Computer System Operation:**
        - Concurrent operation of I/O devices and CPU
        - Device controller management and role in data transfer
        - Interrupt-driven OS architecture
3. **Interrupts and Interrupt Handling:**
    - **Interrupt Functions:**
        - Transfer control to appropriate service routine
        - Save address of interrupted instruction
        - Differentiate between hardware and software interrupts (traps)
    - **System Interrupts:**
        - OS preserves CPU state during an interrupt
        - Specific code segments handle different types of interrupts
4. **System Calls:**
    - Interface for OS services
    - Involved in user process execution and kernel mode transitions
5. **Organization of Operating System:**
    - **Monolithic OS:**
        - Includes all services and abstractions
        - Benefits in performance and customization
        - Challenges in memory footprint and manageability
        - **Example**: [[Windows]]
    - **Modular OS:**
        - Allows dynamic module installation
        - Benefits in resource management and maintainability
        - Challenges in optimization and maintenance due to modularity
        - **Example**: [[Linux]]
    - **Microkernel OS:**
        - Smaller size and lower overhead
        - Benefits in code verification and portability
        - Challenges in software development complexity and user/kernel transitions

