# Packets and Frames - Writeup

* **Room:** [Packets and Frames](https://tryhackme.com/room/packetsframes)
* **Category:** Pre-Security
* **Module:** Module 2 "Network Fundamentals."
* **Date:** 21 Jan 2026

---

## 1. Objective
This room breaks down the fundamental units of data transmission. The goal is to understand the difference between **Packets and Frames**, how the **TCP** and **UDP** protocols manage data delivery, and how **Ports** ensure traffic reaches the correct application.

---

## 2. Key Concepts Learned

### A. Data Encapsulation: Packets vs. Frames
Data is broken down into small chunks to prevent network bottlenecks. The naming depends on the OSI Layer:
* **Packet (Layer 3 - Network):** Contains the IP Address header.
* **Frame (Layer 2 - Data Link):** Encapsulates the packet and adds the MAC Address header.
* **Key Headers:**
    * **TTL (Time to Live):** An expiry timer to prevent data from looping endlessly.
    * **Checksum:** An integrity check to ensure data hasn't been corrupted.

### B. TCP/IP: The Reliable Connection
TCP (Transmission Control Protocol) is connection-based and ensures data integrity. I learned the Three-Way Handshake process used to establish a connection:
1.  **SYN:** Client asks to connect.
2.  **SYN/ACK:** Server acknowledges and agrees.
3.  **ACK:** Client confirms. Connection established.

**Key TCP Headers:**
* **Source/Destination Port:** Identifies the application.
* **Sequence Number:** Ensures data is reassembled in the correct order.
* **Flags:**
    * `SYN`: Synchronize (Start connection).
    * `FIN`: Finish (Cleanly close connection).
    * `RST`: Reset (Abruptly kill connection).

### C. UDP: Speed Over Reliability
UDP (User Datagram Protocol) is a stateless protocol. Unlike TCP, it does not perform a handshake or check for errors.
* **Process:** "Fire and forget." The sender streams data without waiting for the receiver to say "Ready".
* **Use Case:** Ideal for speed-critical tasks like video streaming, where a few lost packets don't matter.

### D. Ports 101
If an IP address is the building, a Port is the specific room number. Ports ensure data goes to the correct service (e.g., Web vs. Email).

**Common Ports I Analyzed:**
| Port | Protocol | Description |
| :--- | :--- | :--- |
| **21** | FTP | File Transfer Protocol |
| **22** | SSH | Secure Shell (Encrypted Remote Access) |
| **80** | HTTP | Unsecured Web Traffic |
| **443** | HTTPS | Secured Web Traffic |
| **3389** | RDP | Remote Desktop Protocol |

**Practical Challenge:**
I used `netcat` to manually connect to a specific port and retrieve a flag:
```bash
nc 8.8.8.8 1234
# Connection Received: THM{YOU_CONNECTED_TO_A_PORT}
```

<img width="797" height="277" alt="Practical" src="https://github.com/user-attachments/assets/197e76dc-5499-4977-af2f-d673860c1b5c" />

## 3. Conclusion
By completing the tasks in this room, I have mastered the fundamental units of data transmission.
I learned to distinguish between **Packets** (Logical/IP-based) and **Frames** (Physical/MAC-based), and how they work together through encapsulation. I also analyzed the critical difference between the reliable, connection-oriented **TCP** (using the Three-Way Handshake) and the fast, stateless **UDP**.
Finally, I understood the role of **Ports** as the "digital doors" that direct traffic to the correct service (like Web or SSH), and demonstrated this practical knowledge by manually connecting to a specific port to retrieve a flag.

