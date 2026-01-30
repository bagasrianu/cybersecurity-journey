# Windows Fundamentals 1 - Writeup

* **Room:** [Windows Fundamentals 1](https://tryhackme.com/room/windowsfundamentals1)
* **Category:** Pre-Security
* **Module:** Module 5 "Windows Fundamentals."
* **Date:** 30 Jan 2026

---

## 1. Objectives
This module serves as a foundational introduction to the Windows Operating System, establishing the essential vocabulary and navigation skills for security professionals. The key objectives included:
* **Windows Editions**: Understanding the differences between Home, Pro, and Enterprise editions (specifically BitLocker).
* **Desktop Navigation**: Mastering the Graphical User Interface (GUI), including the Start Menu, Taskbar, and Notification Area.
* **File System Architecture**: Understanding NTFS features, file permissions, and critical directories like System32.
* **User Management**: Auditing local user accounts, groups, and understanding User Account Control (UAC).
* **System Monitoring**: Utilizing the Task Manager and Control Panel to monitor system resources.

---

## 2. Windows Editions & GUI
I explored the history of Windows versions and customized the desktop interface for a cleaner workflow.
* **Editions**: I identified that **BitLocker** (full disk encryption) is a key feature available on Pro/Enterprise editions but restricted on Home editions.
* **Desktop Configuration**: I practiced configuring the Taskbar by setting the Search Box to **Hidden**, ensuring the **Task View button** was visible, and identifying the **Action Center** in the Notification Area.
* **Flag Found (Encryption)**: **`BitLocker`**

---

## 3. File System & Permissions
Understanding where data lives and how it is protected is vital for forensics.
* **NTFS**: I verified that the system uses **NTFS** (New Technology File System), which supports journaling and granular permissions.
* **Permissions**: I inspected file security settings to understand access levels like Read, Modify, and Full Control.
* **System Variables**: I confirmed that the environment variable **`%windir%`** points to the Windows installation directory.
* **System32**: Navigated to **C:\Windows\System32** and noted that this directory contains critical OS files where deletion could render the system inoperable.

---

## 4. User Account Management
I performed a security audit on the local user accounts to identify potential vulnerabilities.
* **Audit Tools**: Used `lusrmgr.msc` to inspect Local Users and Groups.
* **Findings**: I discovered a user named **`tryhackmebilly`** who was a member of both the **Remote Desktop Users** and **Users** groups.
* **Hidden Flag**: While inspecting the account description for `tryhackmebilly`, I found a hidden string.
* **UAC**: Observed the **User Account Control** shield icon, which indicates that an application requires administrative approval to run.
* **Flag Found (Account Desc)**: **`window$Fun1!`**

---

## 5. System Configuration & Monitoring
Professional administration requires mastering tools to configure settings and monitor active processes.
* **Control Panel**: I switched the view to "Small Icons" and identified **Windows Defender Firewall** as the final configuration item in the list.
* **Task Manager**: Used the shortcut **`Ctrl+Shift+Esc`** to launch the Task Manager. I monitored real-time resources (CPU and RAM) and identified active background processes.

---

## 6. Final Conclusion
Completing **Windows Fundamentals 1** has bridged my knowledge from Linux to the Windows ecosystem. I am now proficient in:
1. **Desktop Navigation** and environment optimization.
2. **File System Auditing** using NTFS permissions.
3. **User Account Security** and Group management.
4. **Process Monitoring** and System Configuration.
