# TryHackMe: Operating Systems Introduction

## Overview

This room introduced the fundamentals of operating systems, including how they manage hardware, applications, system resources, and security. I learned how operating systems maintain system stability, enforce access controls, and provide different interfaces for interacting with a computer.

The hands-on exercise involved exploring a Linux desktop environment, reviewing system information, navigating user directories, and locating files.

**Platform:** TryHackMe  
**Room:** Operating Systems Introduction  
**Topics:** Operating System Fundamentals, Linux, System Enumeration, File Systems, Access Control

## 1. Operating System Fundamentals

An operating system (OS) acts as an intermediary between users, applications, and computer hardware. It coordinates system resources and provides the services applications need to operate.

Key concepts learned:

- **Kernel:** The core component responsible for managing hardware and system resources.
- **Kernel Space:** A privileged execution environment where the operating system kernel performs critical operations.
- **User Space:** A restricted environment where standard applications run.
- **System Calls:** Mechanisms that allow applications to request services from the kernel.

I learned how privilege separation helps protect critical system resources and reduces the risk of applications interfering with one another.

## 2. Core Operating System Responsibilities

Operating systems perform several essential functions to maintain system performance, stability, and security.

- **Process Management:** Controls the creation, execution, scheduling, and termination of processes.
- **Memory Management:** Allocates RAM to processes, isolates memory, and manages virtual memory.
- **File System Management:** Organizes files and directories while maintaining metadata and access permissions.
- **User Management:** Maintains user accounts, authentication, and access privileges.
- **Device Management:** Uses device drivers and hardware abstraction to facilitate communication between applications and hardware.

Understanding these responsibilities helped me recognize how operating systems coordinate different components while maintaining a functional computing environment.

## 3. Operating System Security

I learned that operating systems provide foundational security controls before additional security tools are installed.

Important mechanisms include:

- **Authentication:** Verifies the identity of users.
- **Access Control:** Restricts access to files, applications, and system resources according to permissions.
- **Process Isolation:** Helps prevent processes from accessing protected memory belonging to other processes.
- **Privilege Separation:** Limits ordinary applications from performing privileged operations directly.
- **System Protection:** Helps safeguard critical files and settings against unauthorized modifications.

These concepts are relevant to endpoint security, access control reviews, and investigating suspicious system activity.

## 4. Graphical User Interface vs. Command-Line Interface

I explored two primary methods of interacting with an operating system.

### Graphical User Interface (GUI)

A GUI provides visual elements such as windows, icons, menus, and file managers. It allows users to inspect system information, manage files, and configure settings through graphical controls.

### Command-Line Interface (CLI)

A CLI allows users to interact with the operating system through text-based commands. It provides a precise and repeatable way to inspect system resources, navigate directories, and perform administrative tasks.

Examples of Linux commands to practise include:

```bash
# Identify the current user
whoami

# Display the current working directory
pwd

# List files, including hidden files
ls -la

# Display kernel and system information
uname -a

# Check memory usage
free -h

# Check disk space
df -h
```

I learned that both interfaces provide access to system functionality, while command-line tools are especially useful for efficient system administration and technical investigations.

## 5. Operating System Types and Use Cases

I explored how different operating systems are designed for different environments.

- **Desktop Operating Systems:** Support personal computing, productivity, and everyday applications.
- **Server Operating Systems:** Prioritize reliability, availability, and the ability to support network services and multiple users.
- **Mobile Operating Systems:** Support touch interfaces, application sandboxing, and power-efficient operation.
- **Embedded Operating Systems:** Run on specialized devices with limited resources or dedicated functions.
- **Virtual and Cloud Environments:** Support scalable computing workloads through virtual machines and container-oriented platforms.

This helped me understand why operating systems vary according to hardware constraints, security requirements, and intended workloads.

## 6. Hands-On Linux System Exploration

The practical exercise involved exploring a Linux desktop environment and gathering basic information about the system.

Activities performed:

- Opened the system information utility to examine operating system details.
- Reviewed hardware and resource information.
- Investigated available storage.
- Navigated the Home directory and explored user directories.
- Accessed a user's Documents directory.
- Located and inspected a text file.

This exercise provided practical exposure to system enumeration, directory navigation, and basic file discovery within a Linux environment.

## 7. Cybersecurity Applications

The concepts covered in this room provide a foundation for several cybersecurity activities.

- **Security Operations (SOC):** Understanding users, processes, and system behavior supports endpoint alert triage and investigation.
- **Incident Response:** Navigating file systems and inspecting system information helps establish context during investigations.
- **Vulnerability Management:** Identifying operating system versions supports asset inventory and vulnerability assessment workflows.
- **Access Control:** Understanding accounts and permissions helps analysts recognize potential access-control weaknesses.
- **Endpoint Security:** Knowledge of operating system architecture helps explain how security controls isolate applications and protect system resources.

## 8. Key Takeaways

Through this room, I developed a foundational understanding of operating system architecture, resource management, privilege separation, and security controls.

I also practised navigating a Linux desktop, reviewing system information, exploring user directories, and locating files.

These skills establish a starting point for further hands-on learning in Linux and Windows administration, command-line operations, endpoint investigation, and defensive cybersecurity.

### Next Steps

- Practise Linux CLI commands and file system navigation.
- Learn file ownership, permissions, users, and groups.
- Explore Windows system administration and command-line tools.
- Practise process inspection, log analysis, and endpoint enumeration.
