# Linux Fundamentals Part 1 - Writeup

* **Room:** [Linux Fundamentals Part 1](https://tryhackme.com/room/linuxfundamentalspart1)
* **Category:** Pre-Security
* **Module:** Module 4 "Linux Fundamentals."
* **Date:** 24 Jan 2026
---

## 1. Objectives
The primary goal of this room is to transition from a Graphical User Interface (GUI) to the Linux Command Line Interface (CLI), which is the industry standard for cybersecurity. By the end of this module, the following skills are established:
* **Understanding Linux Utility:** Recognizing why Linux is the dominant OS for servers, supercomputers, and smart devices.
* **Terminal Proficiency:** Gaining confidence in interacting with a Linux shell and executing fundamental commands.
* **Filesystem Navigation:** Learning to navigate folders and manage files using commands like `ls`, `cd`, and `pwd` instead of a mouse.
* **Data Retrieval:** Mastering search techniques using `find` and `grep` to locate specific data within complex directories.
* **Command Optimization:** Using shell operators (`&`, `&&`, `>`, `>>`) to chain commands and manipulate output efficiently.

---

## 2. First Interaction with the CLI
I learned how to execute basic commands in the terminal and tested them with my own inputs.

**A. echo (Printing Text)**
* *Function:* Prints text to the terminal.
* *My Experiments:*
    * `echo BAGAS` -> Output: **BAGAS**
    * `echo "my nam eis Bagas Martinus Rianu"` -> Output: **my nam eis Bagas Martinus Rianu**
* *Key Learning:* Using quotes (`""`) is best practice when printing long sentences with spaces.

**B. whoami (Check User)**
* *Function:* Displays the current username.
* *Usage:* `whoami` -> Output: `tryhackme`.
  
<img width="708" height="96" alt="echo" src="https://github.com/user-attachments/assets/32f8543a-4249-4e5c-af6b-8921bf5c3505" />

---

## 3. Navigating the Filesystem
In this task, I applied the four essential commands to navigate the filesystem and retrieve a hidden note.

**A. Exploration (ls)**
* *Action:* I ran `ls` to check the current directory.
* *Output:* Found 4 folders (`folder1` to `folder4`) and a log file (`access.log`).
* *Command:* `ls`

**B. Navigation (cd)**
* *Action:* I decided to investigate `folder4`.
* *Command:* `cd folder4`
* *Verification:* I ran `ls` inside the folder and discovered a file named `note.txt`.

**C. Reading Files (cat)**
* *Action:* I read the contents of the hidden text file.
* *Command:* `cat note.txt`
* *Result:* The file contained the text: **"Hello World"**.

**D. Checking Location (pwd)**
* *Action:* I confirmed my exact location in the filesystem.
* *Command:* `pwd`
* *Result:* My current path was `/home/tryhackme/folder4`.

<img width="643" height="125" alt="task4" src="https://github.com/user-attachments/assets/16be6aa6-4465-4865-923a-288209d817f8" />

---

## 4. Efficient Searching & Log Analysis
I performed practical exercises to locate files and extract hidden information using `find` and `grep`.

**A. Locating Specific Files (find)**
* *Action:* I knew a file named `note.txt` existed but needed its location.
* *Command:* `find -name note.txt`
* *Result:* The system located the file at `./folder4/note.txt`.

**B. Using Wildcards**
* *Action:* I searched for all text files using the wildcard operator.
* *Command:* `find -name *.txt`
* *Result:* This confirmed that `note.txt` was the relevant text file available in the scope.

**C. Analyzing File Statistics (wc)**
* *Action:* I counted the number of entries in the server log.
* *Command:* `wc -l access.log`
* *Result:* The file contained **302 lines** of logs.

**D. Extracting the Flag (grep)**
* *Challenge:* Find the flag prefixed with "THM" inside the `access.log` file.
* *Command:* `grep "THM" access.log`
* *Output:*
  `13.127.130.212 - - [04/May/2021:08:35:26 +0000] "GET THM{ACCESS} lang=en HTTP/1.1" 404 360 ...`
* *Flag Found:* **THM{ACCESS}**

**E. Recursive Search**
* *Action:* I tested searching through system directories.
* *Command:* `grep -R "PRETTY_NAME" /etc`
* *Result:* The command successfully searched recursively through the `/etc` directory and returned multiple configuration matches.

<img width="651" height="469" alt="task6" src="https://github.com/user-attachments/assets/1b5ab97b-3da5-454f-8a0d-61753a2c351a" />

---

## 5. Shell Operators & Redirection
I learned to manipulate command output using shell operators to write data into files:

**A. Overwriting Content (`>`)**
* *Goal:* Replace the contents of a file named "passwords" with "password123".
* *Command:* `echo password123 > passwords`
* *Verification:* `cat passwords` showed that the file now contained only **password123**.

**B. Appending Content (`>>`)**
* *Goal:* Add "tryhackme" to the file without deleting the previous password.
* *Command:* `echo tryhackme >> passwords`
* *Verification:* `cat passwords` confirmed the file now contained two lines:
    1. password123
    2. tryhackme
  
<img width="644" height="116" alt="task7" src="https://github.com/user-attachments/assets/52629a7c-0ea8-48af-8a64-b42d4adb7d4f" />

---

## 6. Conclusion
This exercise established the core skills required for cybersecurity. I can now navigate the filesystem, manipulate files, and perform efficient searches using the command line.
* **Key Takeaways:** Mastery of `ls`, `cd`, `cat`, `find`, `grep`, and shell redirection operators (`>`, `>>`).

I am now ready to progress to **Linux Fundamentals Part 2** to learn about SSH and File Permissions.
