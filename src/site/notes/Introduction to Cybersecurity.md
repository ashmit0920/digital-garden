---
{"dg-publish":true,"permalink":"/introduction-to-cybersecurity/"}
---

## Unit 4 - OS Security

#### 1. Overview of Operating System Security

- The **operating system (OS)** is the primary controller of all system resources, making it a significant target for attacks.

#### 2. Operating System Structure

- The OS functions as an executive or supervisor for computing hardware, varying in complexity based on the device (e.g., smartphones, tablets, bank servers).
- The OS controls the interaction between users, devices, and applications.

#### 3. Key OS Functions Related to Security

- **Enforced sharing**: Ensures resources are available only to authorized users.
- **Interprocess communication**: Processes need to communicate securely and synchronize access to shared resources.
- **Protection of critical OS data**: Ensures important data is safe from unauthorized access or modification.
- **User authentication**: Verifies users' identities before granting access.
- **Memory protection**: Programs must run in protected memory regions to prevent unauthorized access.

#### 4. History of Operating Systems and Security Evolution

- **Single-user systems**: Originally, there were no OSs. Users would manually enter programs.
- **Multiprogramming**: With multiple users and programs, memory, I/O devices, and networks required protection.
- **Multitasking**: Allowed the OS to switch rapidly between tasks, simulating parallel execution.

#### 5. Multiprogramming and Protection Requirements

- Protection became essential for:
  - Memory, shared I/O devices (disks, networks), reusable I/O devices (printers), shared programs, and data.

#### 6. OS Design for Object Protection

- OS security layers are arranged by criticality:
  - **Security kernel**: Enforces security policies.
  - **OS kernel**: Manages resource allocation.
  - **Other OS functions**: Provide user interfaces for hardware.

#### 7. Authentication Across OS Layers

- **Password authentication** involves several steps, from displaying the input box to verifying the password. The security level increases as operations move from user interaction to altering system tables.

#### 8. OS Modules and Security Challenges

- OS modules come from various sources, requiring careful integration and testing to avoid incompatibility and vulnerabilities.

#### 9. OS Self-Protection

- The OS must protect itself against both user programs and untrusted modules or drivers.
- **Bootstrap loader**: Initiates OS loading upon startup, reading the hard drive's boot sector.

#### 10. OS Security Tools

- **Audit logs**: Record incidents for later analysis to prevent future attacks.
- **Virtualization**: Limits users’ access to resources by simulating hardware (e.g., cloud storage).
- **Hypervisors**: Allow multiple virtual machines (VMs) to run on a single physical machine.
- **Sandboxes**: Provide controlled environments for executing potentially harmful code.
- **Honeypots**: Act as decoys to attract attackers and study their behavior.

#### 11. Memory Protection Techniques

- **Fence registers**: Divide memory into secure regions, keeping user programs from accessing the OS.
- **Base/Bounds registers**: Mark the start and end of memory sections for user programs, ensuring security.
- **Tagged architecture**: Assigns access rights to every word of memory, ensuring only privileged programs can access certain data.

#### 12. Virtual Memory and Security

- **Virtual memory** allows a system to use more memory than its physical capacity by utilizing hard disk space.
- **Segmentation**: Divides programs into segments, offering secure access to memory sections.
- **Paging**: Divides memory into pages for more efficient management while maintaining security.
- **Combined Paging and Segmentation**: Provides both efficient memory management and logical security by segmenting programs and then paging each segment.