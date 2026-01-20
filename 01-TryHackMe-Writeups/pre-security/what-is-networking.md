# What is Networking? - Writeup

* **Room:** [What is Networking?](https://tryhackme.com/room/whatisnetworking)
* **Category:** Pre-Security
* **Module:** Module 2 "Network Fundamentals."
* **Date:** 20 Jan 2026

---

## 1. Objective
This room serves as a foundational introduction to how devices communicate with each other.
The objective is to understand the definition of a network, the structure of the Internet, and how devices are identified using IP Addresses and MAC Addresses.

---

## 2. Key Concepts Learned

### A. What is a Network?
A Network consists of two or more devices connected to share resources. Networks can range from as small as two computers in a home to as large as the Internet, which connects billions of devices worldwide.

### B. The Internet (Public vs. Private)
The Internet is essentially a "Network of Networks."
* **Private Network:** A local network (such as home or office WiFi) that cannot be accessed directly from the outside world.
* **Public Network:** A network accessible to everyone (The Internet). Devices require a *Public IP* from an ISP to browse here.

### C. Device Identification
To ensure data reaches the correct destination, every device possesses two types of identifiers:

1.  **IP Address (Logical Address):**
    * Example: `192.168.1.77`
    * Nature: **Dynamic (Changeable)**. Used to determine the device's *location* on the current network.
    * Format: Exists as IPv4 (decimal numbers) and IPv6 (long hexadecimal strings).

2.  **MAC Address (Physical Address):**
    * Example: `a4:c3:f0:85:ac:2d`
    * Nature: **Permanent (Static)**. Burned into the Network Interface Card (NIC) chip at the factory.
    * Function: Uniquely identifies a device within a local network.
---

## 3. Practical Tasks

### Task A: MAC Spoofing (Impersonation)
In the interactive lab, I simulated a scenario on a Hotel WiFi network.
* **The Problem:** The firewall blocked internet access for "Bob" but allowed access for "Alice."
* **The Solution (Spoofing):** I modified (spoofed) Bob's MAC Address to match Alice's MAC Address exactly.
* **The Result:** The firewall was deceived into identifying Bob as Alice, granting internet access.

This task demonstrated that security filters relying solely on MAC Addresses (MAC Filtering) are easily bypassed.

<img width="796" height="590" alt="MAC Address" src="https://github.com/user-attachments/assets/d6c3a2f7-345f-406b-b6a9-ef091384b277" />

### Task B: Ping (ICMP)
I used the `ping` command to test connectivity between devices. Ping utilizes the ICMP (Internet Control Message Protocol).
* **Target:** `8.8.8.8` (Google DNS).
* **Result:** Received a reply, indicating a stable internet connection.

<img width="796" height="282" alt="Ping" src="https://github.com/user-attachments/assets/16dc3af8-b3d6-4590-8ace-a3090f58ff82" />

---

## 4. Conclusion
In this room, I learned the fundamental difference between IP Addresses and MAC Addresses:
* **IP Address** is logical and changeable, used to locate a device on the internet (like a home address).
* **MAC Address** is physical and permanent, used to identify the specific hardware (like a fingerprint).

Most importantly, the MAC Spoofing task demonstrated that physical identifiers can be faked via software. This teaches a critical security lesson: MAC Filtering alone is a weak security measure because it can be easily bypassed by impersonating a trusted device.
