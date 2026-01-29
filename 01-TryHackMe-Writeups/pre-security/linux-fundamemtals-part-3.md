# Linux Fundamentals Part 3 - Writeup

* **Room:** [Linux Fundamentals Part 3](https://tryhackme.com/room/linuxfundamentalspart3)
* **Category:** Pre-Security
* **Module:** Module 4 "Linux Fundamentals"
* **Date:** 29 Jan 2026

---

## 1. Objectives
The finale of the Linux Fundamentals series transitions from basic system interaction to professional system administration and "Linux-fu" skills. The key objectives included:
* **Terminal Text Editors**: Mastering **Nano** and **Vim** for direct file modification.
* **General Utilities**: Downloading files with `wget` and hosting lightweight web servers using Python.
* **Process Management**: Monitoring system activity and managing background/foreground tasks.
* **Maintenance & Automation**: Understanding **Crontabs** for task scheduling and Package Management via `apt`.
* **System Logging**: Reviewing application and service logs for troubleshooting and forensic auditing.

---

## 2. Terminal Text Editors (Nano & Vim)
Directly editing configuration files is a daily task for security professionals.
* **Practical Task**: I accessed the target machine via SSH and used `nano task3` to edit the file in the home directory.
* **Activity**: I found the flag and then modified the file with a personal goal: *"Hello my name is Bagas, In 2026 ill be a cybersecurity engineer."*
* **Flag Found**: **`THM{TEXT_EDITORS}`**
  
<img width="651" height="593" alt="task3 1" src="https://github.com/user-attachments/assets/1c35206e-617f-43e9-b075-beb67bbdd325" />

---

## 3. General Utilities & Web Serving
I practiced different methods of data transfer between the target machine and the AttackBox.
* **Python Web Server**: Initialized a quick web server using `python3 -m http.server` on the target machine.
* **Wget**: Used `wget http://10.48.156.171:8000/.flag.txt` in a new terminal to download the file `.flag.txt`.
* **Discovery**: Since it was a hidden file, I used **`ls -a`** to locate it before reading the content.
* **Flag Found**: **`THM{WGET_WEBSERVER}`**
  
<img width="655" height="143" alt="task4 1" src="https://github.com/user-attachments/assets/67d46fb4-3d7f-41d6-b4a2-365f352ea4cc" />

<img width="653" height="350" alt="task4 2" src="https://github.com/user-attachments/assets/75c821b5-3f2b-4703-a215-2e407b0673e1" />

<img width="656" height="371" alt="task4 3" src="https://github.com/user-attachments/assets/474eeb30-84de-4e39-99f4-de69eb15c92c" />

---

## 4. Processes 101
Processes are programs running on a machine, each assigned a unique **Process ID (PID)**.
* **Monitoring**: I used **`ps aux`** to view a comprehensive list of all active processes on the system.
* **Process Control**: Learned to manage lifecycle signals such as SIGTERM (clean exit) and SIGKILL (forced exit) using the `kill` command.
* **Background/Foreground**: Practiced using the `&` operator to run tasks in the background and the `fg` command to bring them back to focus.
* **Flag Found**: **`THM{PROCESSES}`**
  
<img width="653" height="588" alt="task5 1" src="https://github.com/user-attachments/assets/87b5a303-ebb7-4cc7-9c0f-0234c4661619" />

<img width="656" height="593" alt="task5 2" src="https://github.com/user-attachments/assets/8ec3c2db-b72f-4a30-a146-29badffbc502" />

---

## 5. Maintaining Your System: Automation & Logs
Professional Linux management requires automating tasks and auditing system behavior through logs.

**A. Automation (Cron)**
* **Task**: Inspected scheduled tasks on the instance using `crontab -e`.
* **Result**: I discovered that the crontab was configured to run at **`@reboot`**, meaning the command executes every time the system starts up.

<img width="653" height="295" alt="task6 2" src="https://github.com/user-attachments/assets/d445e699-853d-4815-adc0-cc85f250e914" />

**B. Log Auditing (Forensics)**
* **Directory**: Navigated to `/var/log/apache2` to investigate web server activity.
* **Technique**: Inspected the rotated log file **`access.log.1`** using `less`.
* **Findings**:
    * **Visitor IP Address**: `10.9.232.111`
    * **File Accessed**: `catsanddogs.jpg`

<img width="653" height="163" alt="task8 1" src="https://github.com/user-attachments/assets/54779f65-7ab6-495c-869e-e3dd61bc0a17" />

<img width="657" height="194" alt="task8 2" src="https://github.com/user-attachments/assets/9f262b14-7a91-48d3-8e0e-f6ac534a40b4" />

---

## 6. Final Conclusion
Completing the **Linux Fundamentals** series has provided me with a robust toolkit for both system administration and security operations. I am now proficient in:
1. **Remote Management** and secure file transfers.
2. **Process Auditing** and system-wide monitoring.
3. **Task Automation** and software package maintenance.
4. **Log Analysis** for security investigations.
