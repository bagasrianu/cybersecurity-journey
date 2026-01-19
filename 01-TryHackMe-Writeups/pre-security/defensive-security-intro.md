# Defensive Security Intro - Writeup

* **Room:** [Defensive Security Intro](https://tryhackme.com/room/defensivesecurityintro).
* **Category:** Pre-Security
* **Module:** Module 1 "Introduction to Cyber Security."
* **Date:** 19 Jan 2026

---

## 1. Objective
This room introduces the world of Defensive Security (also known as Blue Teaming).
The objective is to understand how security teams protect organizations from cyber attacks, recognize the various roles within a SOC team, and perform a practical defense simulation using SIEM to detect a "Web Discovery" attack on FakeBank.

---
## 2. Key Concepts Learned

### A. What is Defensive Security?
Defensive Security focuses on two main tasks: preventing intrusions and detecting problems when they occur. If the defense fails, the impact can be fatal for a company, resulting in heavy fines and the leakage of sensitive data (e.g., the British Airways & Marriott cases).

### B. Areas of Defensive Security
There are several main pillars of defense:
* **Monitoring and Detecting:** The command center where teams monitor the network 24/7.
* **Incident Response:** Responding to and restoring systems when an attack is confirmed.
* **Threat Intelligence:** Gathering information about adversaries and their tactics.
* **Vulnerability Management:** Fixing security gaps (patching) before they are exploited.

### C. The Blue Team Roles
* **SOC Analyst:** The frontline defense who monitors alerts and investigates anomalies.
* **Incident Responder:** Investigates and responds to ongoing security incidents within the organization, monitors and prevents attackers in real-time, and shares lessons learned in order to avoid future incidents.
* **Security Engineer:** Develops and maintains essential tools and systems that support the defensive security team.
* **Digital Forensics:** Collects, preserves, and analyzes evidence from networks and systems to uncover vital information about attackers and their methods.

---

## 3. Technology Stack

### Defence in Depth (Layered Defense)
Defensive measures include:
1. **Employee Training:** Preventing human error (e.g., Phishing).
2. **IDS (Intrusion Detection Systems):** "CCTV" cameras that record suspicious activity.
3. **Firewalls:** Controlling the network traffic allowed to enter or exit.
4. **Security Policies:** Policies that help organizations ensure their systems are used correctly.

### Exploring the Security Operations Centre (SOC)
The SOC acts as the defensive security center for an organization's technology and operates around the clock.
A typical day in a SOC involves:
1. Reviewing alerts triggered by security tooling.
2. Investigating anomalies.
3. Responding to incidents.

### SIEM (Security Information and Event Management)
SIEM is described as the **"Defensive Radar"**. This tool collects data (logs) from various sources into a centralized view, making it easier for analysts to see what is happening across the network in *real-time*.

---

## 4. Case Study: Defending FakeBank

**Scenario:**
The FakeBank SIEM system detected suspicious activity. As an analyst, I was tasked with investigating the alert.

### A. Detection
On the SOC dashboard, a MEDIUM severity alert appeared named "Web Discovery Attack".
Alert Description: *"Automated directory enumeration detected on admin endpoints."*

This indicates that someone is using a tool like `dirb` to scan for hidden admin pages (exactly as I did in the previous Offensive lab).

<img width="796" height="594" alt="SOC Dashboard1" src="https://github.com/user-attachments/assets/054148e1-5bb4-4c28-95c3-fc1e3f0fbba3" />

### B. Response & Mitigation (Respon)
I performed 3-phased mitigation actions to stop this attack:

#### 1. Block Source IP Address
The first step was to cut off the attacker's access.
* **Attacker IP:** `32.122.195.63`
* **Action:** Block the IP for 72 Hours.
* **Reason:** To prevent the attacker from continuing scanning or further exploitation.

<img width="799" height="595" alt="SOC Dashboard2" src="https://github.com/user-attachments/assets/0bdbbbdc-93b9-415e-b6e2-4fc8a475d3b2" />

<img width="797" height="596" alt="SOC Dashboard3" src="https://github.com/user-attachments/assets/a270d038-90a5-4f95-ba7d-eafa560dcdbc" />

#### 2. Implement Rate Limiting
To prevent brute-force or Fuzzing attacks in the future, I limited the number of allowed incoming requests.
* **Rule:** Max 50 Requests within 60 Seconds.
* **Impact:** Automated attacker tools will fail due to sending requests too fast, while normal users remain unaffected.

<img width="797" height="592" alt="SOC Dashboard4" src="https://github.com/user-attachments/assets/804eb8ce-2ff5-40db-8339-4eef53c6945c" />

#### 3. Update WAF Rules (Firewall)
As a long-term defense, I updated the Web Application Firewall (WAF) rules.
* **Action:** Create a new rule to "Block suspicious enumeration attempts".
* **Goal:** To ensure the system can automatically block similar attack patterns in the future without manual intervention.

<img width="797" height="596" alt="SOC Dashboard5" src="https://github.com/user-attachments/assets/d97fcde7-8929-4b60-9577-1cf962998465" />

<img width="799" height="596" alt="SOC Dashboard6" src="https://github.com/user-attachments/assets/49fda897-15db-4fc1-9d12-73b6e01c1749" />

---

## 5. Conclusion
This room provided a real-world overview of a Security Analyst's job.
I learned that "attacks" which look cool on the Red Team side (like `dirb` scanning) appear very "noisy" and easy to detect on the Blue Team dashboard if the SIEM is configured correctly. The best defense is a combination of rapid detection (SIEM) and automated response (Firewall/WAF).
