# TryHackMe: Linux CLI Basics

**Platform:** TryHackMe  
**Module:** Linux CLI Basics  
**Pathway:** Pre-Security  
**Focus:** Linux CLI | Filesystem Navigation | File Discovery | System Enumeration

---

## 1. Overview

Completed the Linux CLI Basics TryHackMe room as an introductory IT Support Engineer on the Cyber Operations Support Team. The exercise involved navigating a Linux environment, locating hidden files, retrieving mission instructions, and collecting basic system information using command-line utilities.

---

## 2. Filesystem Navigation and Investigation

Practiced navigating the Linux filesystem and identifying files using the following commands:

| Command | Purpose |
|---|---|
| `pwd` | Display the current working directory |
| `ls` | List files and directories |
| `ls -la` | Display hidden files and detailed directory information |
| `cd` | Navigate between directories |
| `find` | Search for files by name or location |
| `cat` | Read file contents |

### Practical Exercise: Locating Mission Instructions

Used the `find` command to locate a file named `mission_brief.txt` within the home directory:

```bash
find ~ -name mission_brief.txt
```

The search identified the following path:

```text
/home/ubuntu/Documents/.research/archive/mission_brief.txt
```

Navigated to the directory and inspected the file:

```bash
cd /home/ubuntu/Documents/.research/archive/
cat mission_brief.txt
```

This exercise demonstrated how to locate files within nested directories, including hidden directories such as `.research`, and retrieve information from their contents.

---

## 3. Linux System Enumeration

Collected basic system information using built-in Linux utilities to understand the environment and its configuration.

| Command | Information Retrieved |
|---|---|
| `whoami` | Current logged-in username |
| `uname -a` | Kernel version and system architecture |
| `df -h` | Disk usage and available storage |
| `cat /etc/os-release` | Linux distribution and version |

### System Information Gathered

- **Username:** `ubuntu`
- **Kernel version:** `6.14.0-1018-aws`
- **Available disk space:** `58G`
- **Linux distribution:** Ubuntu

These commands introduced host-level enumeration and basic system diagnostics.

---

## 4. Independent File Discovery Challenge

Applied the commands learned throughout the room to locate a second file, `day1_report.txt`, within the home directory.

Used `find` to identify its location, `cd` to navigate to the directory, and `cat` to retrieve its contents.


---

## 5. Key Takeaways

- Navigated Linux directories and explored hidden files.
- Used `find` to locate files within nested filesystem structures.
- Retrieved mission instructions and information using `cat`.
- Used `whoami`, `uname`, and `df` for basic host enumeration.
- Inspected `/etc/os-release` to identify the Linux distribution
---

## Lessons
These foundational skills support Linux system administration, host enumeration, security investigations, and incident response. They provide a starting point for more advanced activities such as examining file permissions, reviewing system logs, monitoring processes, and investigating suspicious files.
