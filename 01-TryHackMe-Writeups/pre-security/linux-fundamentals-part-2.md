# Linux Fundamentals Part 2 - Writeup

* **Room:** [Linux Fundamentals Part 2](https://tryhackme.com/room/linuxfundamentalspart2)
* **Category:** Pre-Security
* **Module:** Module 4 "Linux Fundamentals."
* **Date:** 28 Jan 2026
---

## 1. Objectives
After mastering basic navigation in Part 1, this module focuses on operating Linux systems in professional and secure environments. The key skills developed include:
* **Remote Management:** Learning to control remote terminals using the SSH protocol.
* **Advanced Command Usage:** Optimizing commands with flags and switches for specific results.
* **Filesystem Manipulation:** Performing advanced actions such as copying (`cp`), moving, and renaming files/directories (`mv`).
* **Access Control & Permissions:** Understanding Linux security through access rights (Read, Write, Execute) and user account management.
* **System Hierarchy:** Identifying critical Linux directories like `/etc`, `/var`, and `/tmp`.

---

## 2. Remote Access via SSH
In cybersecurity, physical access to a server is rare. We use **SSH (Secure Shell)** for secure remote connections.

**A. How SSH Works**
* **Encryption:** SSH encrypts data (such as passwords) during network transit to prevent eavesdropping.
* **Process:** Human input is encrypted by the sender, travels across the internet as ciphertext, and is decrypted upon reaching the server.

**B. Practical Login**
* **Syntax:** `ssh [username]@[IP_Address]`.
* **Terminal Experience:** When typing a password, the terminal provides no visual feedback (characters do not appear) as a security feature.
* **Result:** A successful login is indicated by the prompt changing from `root@attackbox` to `tryhackme@linux2:~$`.

<img width="656" height="330" alt="task2" src="https://github.com/user-attachments/assets/fed8852a-1cce-410d-98d1-092f05c0a727" />

---

## 3. Advanced Commands & Documentation
Linux commands can be expanded using additional arguments called **flags** or **switches**.

<img width="652" height="527" alt="task3 1" src="https://github.com/user-attachments/assets/18b39fca-cfbc-4f88-bd51-35c2a9175d00" />
<img width="649" height="514" alt="task3 2" src="https://github.com/user-attachments/assets/d137fa3c-9e35-42ea-913a-0d0c5ff00f68" />
<img width="655" height="572" alt="task3 3" src="https://github.com/user-attachments/assets/de065713-9940-4e5e-b362-6e5a3afa4311" />

**A. Using Flags (ls -a)**
* **Default:** `ls` only shows standard folders.
* **Flag `-a`:** Displays all files, including **hidden files** (prefixed with a dot) like `.hiddenfolder`.

**B. Manual Pages (man)**
* **Function:** Accessing official command documentation directly in the terminal.
* **Example:** Running `man ls` provides detailed information regarding the synopsis and description of every available flag.

---

## 4. Filesystem Interaction Continued
Practical file management for efficient data organization.

<img width="656" height="419" alt="task4" src="https://github.com/user-attachments/assets/f672b4a4-dc39-4f03-8daa-1233ec3c6f50" />

**A. Basic File Operations**
* **Creating a File:** `touch newnote`.
* **Copying:** `cp -r note note2` (The `-r` flag is used to copy directories recursively).
* **Moving/Renaming:** `mv myfile myfolder` to move, or `mv note2 note3` to rename.
* **Identifying Types:** Using the `file` command to determine the actual content of a file (e.g., `ASCII text`).

**B. Flag Discovery**
* **Steps:** Move to the target directory (`cd myfolder`) and read the file content (`cat myfile`).
* **Flag Found:** **`THM{FILESYSTEM}`**.

---

## 5. Permissions 101
The Linux security system utilizes access rights for the **Owner**, **Group**, and **Others**.

<img width="656" height="134" alt="task5" src="https://github.com/user-attachments/assets/2ed33a3b-0b50-49b0-8999-fe22e9177e71" />

**A. Access Permission Analysis (ls -lh)**
Below are the symbolic-to-numeric conversion results (r=4, w=2, x=1) from my experiments, for examples:

| File/Folder Name | Symbolic Permission | Numeric Calculation | Value | Analysis |
| :--- | :--- | :--- | :--- | :--- |
| `important` | `-rw-r--r--` | (4+2+0), (4+0+0), (4+0+0) | **644** | Owner (user2) can read/write. |
| `myfolder` | `drwxr-xr-x` | (4+2+1), (4+0+1), (4+0+1) | **755** | Directory accessible to all users. |
| `note` | `-rw-rw-r--` | (4+2+0), (4+2+0), (4+0+0) | **664** | Read/write collaboration between Owner & Group. |


**B. Switching Users (su) & Flag Retrieval**
* **Action:** The file `important` is owned by `user2`, requiring a user switch.
* **Command:** `su user2`.
* **Flag Found:** **`THM{SU_USER2}`**.

---

## 6. Common Directories
Understanding the Ubuntu Linux directory hierarchy is essential for rapid system navigation.

* **`/etc`**: Home to crucial system configuration files.
* **`/var/log`**: Where system logs are stored for security investigations.
* **`/root`**: The dedicated home directory for the administrator (root) user.
* **`/tmp`**: A volatile temporary storage directory (data is lost upon restart), similar to RAM.

---

## 7. Conclusion
This module solidified my system administration skills, particularly in secure remote access and data security management. 
* **Key Takeaways:** Proficiency in SSH, numeric permission calculation, root directory navigation, and user-switching principles.
