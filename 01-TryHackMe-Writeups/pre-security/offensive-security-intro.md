# Offensive Security Intro - Writeup

* **Room:** [Offensive Security Intro](https://tryhackme.com/room/offensivesecurityintrokK).
* **Category:** Pre-Security
* **Module:** Module 1 "Introduction to Cyber Security."
* **Date:** 19 Jan 2026

---

## 1. Objective
In this room, I simulated the role of an attacker to breach a fictional bank site called FakeBank.
The goal was to discover unprotected hidden pages to transfer money into my account illegally. This lab demonstrated the concept of "Security through Obscurity" (attempting to secure a system simply by hiding it), proving it to be a very weak defense mechanism.

---

## 2. Key Concepts Learned
* **Offensive Security:** The process of breaking into systems to identify vulnerabilities and loopholes before malicious actors do.
* **Directory Busting:** The technique of discovering hidden pages on a website that are not listed in the visible navigation menu.
* **Command Line Interface (CLI):** Using the terminal to execute hacking tools and commands.

---

## 3. Task Walkthrough

### Task 1: The Story
I assumed the role of an Ethical Hacker hired to test the security of FakeBank. My objective was to transfer money from a target account to my own to prove the existence of a vulnerability.

<img width="2559" height="1439" alt="fakebank account" src="https://github.com/user-attachments/assets/611104a2-9a2a-4787-928b-00a82b97a37b" />


### Task 2: Hacking the Website
Here, I utilized the AttackBox (Virtual Machine) provided by the room and the dirb tool to perform directory brute-forcing (guessing hidden folder names).

**Steps taken:**
1.  Opened the terminal on the Virtual Machine.
2.  Executed the command to scan the website:
    ```bash
    dirb http://fakebank.thm
    ```
3.  **Findings:**
    Based on the scan results, the tool identified two interesting directories:
    * `/images` (CODE:301) - Likely just an image asset folder.
    * `/bank-deposit` (CODE:200) - Critical finding. Status 200 indicates this page is fully accessible.
      
   <img width="2560" height="1440" alt="dirb" src="https://github.com/user-attachments/assets/4fe99d21-63b5-4eae-8f45-067f8a2842dd" />

4.  **Exploitation:**
    I accessed the URL `http://fakebank.thm/bank-deposit` in the browser. It turned out to be a fund transfer portal that was open without any login requirement. I successfully transferred $30,000 to my account, proving that this page is vulnerable to Broken Access Control.
   
    <img width="2560" height="1440" alt="admin portal" src="https://github.com/user-attachments/assets/c9a26d11-7ace-40cf-be7d-b855e96906d9" />
    <img width="2560" height="1440" alt="result" src="https://github.com/user-attachments/assets/440a50db-7ccc-408a-9a74-9d7e9f43545f" />
---

## 4. Conclusion
Although my goal is to become a Blue Teamer, this lab taught me that Security through Obscurity (hiding pages without password protection) is not a viable defense strategy. An attacker can easily discover them using automated tools. 
As a future Security Engineer, I learned that every administrative page must be protected with strong authentication, not just hidden from the menu.
