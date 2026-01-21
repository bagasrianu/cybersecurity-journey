# OSI Model - Writeup

* **Room:** [OSI Model](https://tryhackme.com/room/osimodel)
* **Category:** Pre-Security
* **Module:** Module 2 "Network Fundamentals."
* **Date:** 21 Jan 2026

---

## 1. Objective
The OSI (Open Systems Interconnection) Model is a conceptual framework that standardizes how different computer systems communicate. The objective of this room is to understand the 7 Layers of the model and how data is transformed through a process called Encapsulation as it travels from the user application down to the physical cables.

---

## 2. Key Concepts Learned

### A. The Foundation: Addressing & Routing (Layers 1-3)
The bottom three layers are responsible for the physical and logical movement of data across networks.

* **Layer 1 (Physical):** The lowest layer representing the physical components (cables, connectors). It deals with electrical signals and binary streams (`1`s and `0`s).
* **Layer 2 (Data Link):** Focuses on physical addressing. It uses the NIC (Network Interface Card) and MAC Addresses (burned into the hardware) to ensure data reaches the correct device on a local network.
* **Layer 3 (Network):** Handles Routing and logical addressing. It uses **IP Addresses** (e.g., `192.168.1.100`) and protocols like **OSPF** to determine the optimal path for data to travel across the internet.

### B. Transport & Reliability (Layer 4)
Layer 4 is responsible for delivering data efficiently. I learned the critical distinction between the two main protocols:

1.  **TCP (Transmission Control Protocol):** Connection-oriented and reliable. It performs error checking to guarantee data accuracy (used for Email, File Transfers).
2.  **UDP (User Datagram Protocol):** Connectionless and fast. It uses a "fire and forget" method without guaranteeing delivery (used for Video Streaming, Gaming).

### C. Session Management (Layer 5)
This layer manages the conversation between computers.
* **Session Control:** It establishes, maintains, and terminates unique sessions for different connections (e.g., separating browser tabs).
* **Checkpoints:** It can save progress during data transfer. If a connection drops, data transfer can resume from the last checkpoint instead of restarting from zero.

### D. Data Presentation & Interface (Layers 6-7)
The top layers handle how data is formatted and presented to the human user.

* **Layer 6 (Presentation):** Acts as a Translator. It standardizes data formats (e.g., converting binary to JPEG) and handles Encryption (like HTTPS) for security.
* **Layer 7 (Application):** The interface users interact with directly. It involves protocols like DNS (translating names to IPs), FTP (file sharing), and HTTP (web browsing) via graphical interfaces like web browsers.

### E. Encapsulation
A fundamental concept where specific information (headers/footers) is added to the data as it moves down the layers.
* *Application:* Data
* *Transport:* Segments
* *Network:* Packets
* *Data Link:* Frames
* *Physical:* Bits

---

## 3. Conclusion
By completing the tasks in this room (Layer 1 to Layer 7), I have traced the complete journey of data transmission.
I learned that networking is a structured process that starts from tangible hardware like cables and electrical signals (Layer 1), moves up to logical IP routing (Layer 3), handles data reliability through TCP/UDP (Layer 4), and finally translates everything into a user-friendly GUI (Layer 7).
Mastering this stack is crucial because it helps in pinpointing exactly where a connection fails—whether it's a physical break, a routing error, or an encryption mismatch—and understanding which specific layer is being targeted during a cyber attack.
