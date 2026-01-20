# Intro to LAN - Writeup

* **Room:** [Intro to LAN](https://tryhackme.com/room/introtolan)
* **Category:** Pre-Security
* **Module:** Module 2 "Network Fundamentals."
* **Date:** 20 Jan 2026

---

## 1. Objective
This room explores the architecture of Local Area Networks (LAN). The goal is to understand how networks are physically arranged (Topologies) and logically organized (Subnetting & Protocols) to ensure efficient and secure communication.

---

## 2. Key Concepts Learned
### A. Network Topologies & Architecture
Topology refers to the physical layout of the network. I analyzed the evolution from legacy designs to modern standards:
Based on the interactive lab simulations, here is the breakdown of the three major topologies:

### Star Topology (The Modern Standard)
* **Design:** All devices connect individually to a central device (usually a Switch or Hub).
* **Simulation Result:**
    * When I disconnected one computer cable, the others remained unaffected.
    * However, when I destroyed the Central Switch, the entire network went down immediately.
* **Key Takeaway:** Although it is the most reliable and scalable topology used today, its weakness is the reliance on the central hardware. If the switch fails, everything fails.

### Bus Topology (The Old School)
* **Design:** All devices share a single backbone cable. Data travels like a bus on a single-lane road.
* **Simulation Result:**
    * I flooded the network with data packets. Because there is only one cable, the data traffic became "bottlenecked" and slow.
    * Troubleshooting was difficult because it's hard to identify which device is causing the traffic jam.
* **Key Takeaway:** Cheap and easy to set up, but terrible for heavy traffic. It suffers from Data Collisions and high latency.

### Ring Topology ( The Loop)
* **Design:** Devices are connected in a closed loop. Data travels in one direction (unidirectional).
* **Simulation Result:**
    * I cut the cable between two computers.
    * **Result:** The entire data flow stopped completely. Because the loop was broken, data could not reach its destination.
* **Key Takeaway:** Easy to troubleshoot (you can see where the break is), but it has zero redundancy. One cut cable kills the whole network.

I also learned the distinction between critical network devices:
* **Hub:** An older device that blindly broadcasts data to all ports, causing traffic congestion and security risks.
* **Switch:** A smarter device that uses **MAC Addresses** to send data *only* to the intended recipient (Unicast), improving speed and security.
* **Router:** A device that connects different networks (LAN to WAN) and directs traffic using **IP Addresses**.

### B. Subnetting (Network Segmentation)
Subnetting is the practice of splitting a large network into smaller, isolated mini-networks. This is crucial for:
* **Efficiency:** Reducing broadcast traffic.
* **Security:** Isolating sensitive departments (e.g., Finance) from public guests.

In subnetting, an IP address is divided into three parts:
1.  **Network Address:** Identifies the network group.
2.  **Host Address:** Identifies the specific device.
3.  **Default Gateway:** The router's address to access the internet.

### C. Essential Network Protocols (ARP & DHCP)
Two invisible protocols are essential for devices to join and communicate on a network:

**1. ARP (Address Resolution Protocol)**
Devices use IP addresses to find each other, but hardware needs MAC addresses to deliver data. ARP bridges this gap.
* **Mechanism:** It broadcasts a request ("Who has IP X?") and receives a reply containing the MAC address.
* **Security Risk:** It is vulnerable to **ARP Spoofing**, where an attacker impersonates a device to intercept traffic.

**2. DHCP (Dynamic Host Configuration Protocol)**
DHCP automates the assignment of IP addresses, so users don't have to configure them manually.
* **Process (DORA):** Discover -> Offer -> Request -> Acknowledge.
* **Security Risk:** Hackers can deploy **Rogue DHCP Servers** to assign malicious DNS settings to victims.

---

## 3. Conclusion
Understanding LAN fundamentals is the baseline for network security.
* **Topologies** teach us about redundancy and physical failure points.
* **Subnetting** acts as the first line of defense for internal network security through segmentation.
* **ARP & DHCP** are vital for connectivity, but their lack of built-in authentication makes them prime targets for local network attacks (Spoofing/Man-in-the-Middle).
