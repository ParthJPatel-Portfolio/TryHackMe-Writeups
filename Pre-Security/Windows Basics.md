# TryHackMe: Windows Basics

## Overview

This room introduces the fundamentals of the Windows operating system through a hands-on Windows Server 2019 environment. Topics include user authentication, desktop navigation, file management, application installation and updates, system configuration, process monitoring, and built-in security features.

## 1. Windows Evolution

Windows evolved from MS-DOS, which relied on typed commands, to a graphical user interface (GUI) introduced with Windows 1.0 in 1985. Over time, Windows developed into a full operating system with integrated applications, system management tools, and security capabilities.

## 2. Authentication and User Permissions

Windows requires users to authenticate before accessing the desktop. Authentication verifies a user's identity, while account permissions determine which files, settings, and system functions they can access.

Common account types include:

- **Guest:** Restricted access intended for temporary users.
- **Standard User:** Supports everyday tasks without unrestricted system-wide privileges.
- **Administrator:** Provides elevated permissions for system configuration, software installation, and user management.

Understanding account privileges is important because excessive permissions can increase the impact of a compromised account.

## 3. Windows Desktop and Built-in Tools

The Windows desktop provides access to applications, files, folders, and system functions.

Key components include:

- **Desktop:** Main workspace for files, folders, and shortcuts.
- **Taskbar:** Provides access to applications, system tools, and notifications.
- **Start Menu and Search:** Used to locate applications, files, and settings.
- **Task View:** Displays open windows and supports switching between tasks.
- **File Explorer:** Used to navigate directories, locate files, and manage folders.
- **Settings and Control Panel:** Provide access to system configuration and administrative options.

Windows also includes built-in utilities such as Notepad and Calculator for everyday tasks.

## 4. System Information and File Management

The **About your PC** section in Windows Settings provides information about the operating system, device specifications, and related system details.

Windows organizes files using a hierarchical directory structure, where folders contain files and subfolders. Common locations include Desktop, Documents, and Downloads.

File Explorer supports browsing directories, searching for files, and viewing folder paths. For example:

`C:\Users\Administrator\Desktop\TryHatMe Onboarding`

Understanding file paths and directory structures helps with system administration, troubleshooting, and locating potentially suspicious files.

## 5. Application Management

Windows supports installing, updating, and uninstalling applications.

- **Updating applications:** Windows Update delivers operating system and supported component updates, while third-party applications may use built-in updaters or manually downloaded installers.
- **Installing applications:** Software can be installed through the Microsoft Store, where available, or through trusted vendor installers such as `.exe` and `.msi` files.
- **Uninstalling applications:** Programs can be removed through Settings, Control Panel, the Microsoft Store, or an application's uninstaller.

Keeping software updated is important because updates frequently address security vulnerabilities, bugs, and performance issues. Applications should be downloaded from trusted sources to reduce the risk of installing malicious software.

## 6. Windows Settings and Control Panel

**Windows Settings** provides a centralized interface for managing system preferences, devices, applications, accounts, networks, accessibility, and security.

**Control Panel** is a legacy management interface that continues to provide access to certain configuration and administrative functions.

Both tools are useful for troubleshooting system issues and reviewing configuration settings.

## 7. Task Manager and System Monitoring

Task Manager provides real-time visibility into running applications, background processes, system resource consumption, and Windows services.

Its main tabs include:

- **Processes:** Displays running applications and background processes with their resource usage.
- **Performance:** Shows CPU, memory, disk, and network utilization.
- **Users:** Displays logged-in users and their resource usage.
- **Details:** Provides technical process information, including process IDs (PIDs).
- **Services:** Displays Windows services and their current states.

Task Manager helps identify resource-intensive applications, investigate unusual processes, and troubleshoot performance issues. In security investigations, process information can also help analysts identify activity that warrants further examination.

## 8. Native Windows Security

Windows includes built-in security features to help protect against malware, unsafe applications, and unauthorized network access.

### Windows Security

Windows Security provides access to several protection features:

- **Virus & threat protection:** Detects and helps remove malicious software through real-time protection and scans.
- **Firewall & network protection:** Provides access to firewall status and network protection settings.
- **App & browser control:** Helps protect against potentially unsafe applications, files, and websites.
- **Device security:** Provides access to supported hardware-based security features.

During the room, a custom scan was performed on the `TryHatMe Onboarding` folder. The scan demonstrated how Windows can inspect a selected location and identify a test file flagged by its security engine.

This exercise highlights the importance of investigating scan results and reviewing detected threats rather than assuming every file is safe.

## 9. Windows Defender Firewall

Windows Defender Firewall monitors network traffic and applies rules to allow or block connections based on configured policies.

Windows uses three primary network profiles:

- **Domain:** For systems connected to an organization's domain network.
- **Private:** For trusted networks, such as a home or lab network.
- **Public:** For untrusted networks, such as public Wi-Fi.

The firewall's Advanced settings provide access to inbound rules, outbound rules, and connection security rules. Users can review rule names, enabled status, network profiles, and configured actions, as well as create or modify rules where permissions allow.

Reviewing firewall rules helps identify potentially excessive network access and understand how a Windows system controls inbound and outbound communications.

## Key Takeaways

This room provided foundational knowledge of Windows system operation and security, including:

- Authentication, account types, and user permissions.
- Desktop navigation, system information, and file-system paths.
- Application installation, updates, and removal.
- Monitoring processes, system resources, and services with Task Manager.
- Using Windows Security to scan files for potential malware.
- Understanding firewall profiles, traffic rules, and network access controls.

These skills provide a foundation for Windows administration and defensive security tasks, including endpoint monitoring, basic troubleshooting, malware investigation, and security configuration reviews.
