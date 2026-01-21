# Extending Your Network - Writeup

* **Room:** [Extending Your Networks](https://tryhackme.com/room/extendingyournetwork)
* **Category:** Pre-Security
* **Module:** Module 2 "Network Fundamentals."
* **Date:** 21 Jan 2026

---

## 1. Objective
This room focuses on the technologies used to connect local networks to the wider internet and secure them. The goal is to understand how Port Forwarding allows external access, how Firewalls filter traffic, how VPNs create secure tunnels, and the distinct roles of Routers and Switches.

---

## 2. Key Concepts Learned

### A. Accessing Local Services: Port Forwarding
By default, devices on a local network (Intranet) cannot be accessed from the Internet.
* **The Solution:** Port Forwarding is configured on the Router.
* **How it works:** It directs traffic sent to a specific public IP and port (e.g., `82.62.51.70:80`) to a specific internal device (e.g., `192.168.1.10:80`).

### B. Securing the Network: Firewalls (Simulator 1)
A Firewall acts as the border security guard, deciding what traffic is allowed (Permit) or blocked (Deny).

<img width="787" height="353" alt="Firewall" src="https://github.com/user-attachments/assets/b258d400-420e-4a95-9fd6-8d69582260f5" />

**Practical Challenge (Simulator 1):**
I was tasked with stopping a cyber attack against a Web Server.
* **Scenario:** An attacker's computer was sending malicious packets to our server.
* **Rule Configuration:**
    * **Source IP (Attacker):** `198.51.100.34`
    * **Destination IP (Victim):** `203.0.110.1`
    * **Port:** `80` (HTTP)
    * **Action:** `DROP`
* **Result:** With this rule in place, the red (malicious) packets were successfully stopped before reaching the server.

### C. Secure Tunnels: VPN (Virtual Private Network)
A VPN creates a private, encrypted "tunnel" over the public internet.
* **Benefits:**
    1.  **Privacy:** Encrypts data to prevent sniffing on public WiFi.
    2.  **Anonymity:** Hides the user's real IP address.
    3.  **Access:** Allows remote employees to connect to office networks securely.
* **Protocols:** **IPSec** (Strong encryption) vs. PPTP (Fast but weak encryption).

### D. Network Hardware: Router vs. Switch
* **Router:** Operates at Layer 3. Connects *different* networks together (e.g., Home to Internet) and uses IP addresses for routing.
* **Switch:** Operates at Layer 2. Connects devices *within* the same network and uses MAC addresses.
* **Layer 3 Switch:** A hybrid device that can perform routing and supports **VLANs** to virtually separate departments (e.g., Sales vs. Accounting) for security.

---

## 3. Practical Simulator Challenge
In the final task, I simulated sending a TCP packet from `Computer1` to `Computer3` across a routed network.

**The Packet Journey:**
1.  **Routing:** Computer1 recognized Computer3 was on a different network and directed packets to the Gateway (Router).
2.  **ARP:** Address Resolution Protocol was used to resolve the MAC addresses of the Router and the destination.
3.  **Handshake:** A TCP 3-Way Handshake (SYN, SYN/ACK, ACK) was successfully established before data transfer.

<img width="418" height="401" alt="Send Data" src="https://github.com/user-attachments/assets/bab898de-4744-4d0c-8aad-f890ae0ca374" />

**Simulator Results:**
* **Flag Retrieved:** `THM{YOU'VE_GOT_DATA}`
* **Handshake Entries Logged:** `5`

---

## 4. Conclusion
This room bridged the gap between local LAN concepts and the public Internet. I now understand that while Routers and Switches build the infrastructure, Port Forwarding and VPNs manage accessibility, and Firewalls ensure that this access is secure. Mastering these components is critical for designing secure network architectures.
