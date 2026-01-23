# Putting it All Together - Writeup

* **Room:** [Putting it All Together](https://tryhackme.com/room/puttingitalltogether)
* **Category:** Pre-Security
* **Module:** Module 3 "How The Web Works."
* **Date:** 23 Jan 2026
---

## 1. Objective
The primary objective of this room is to consolidate the knowledge gained from the entire "How The Web Works" module. It integrates the concepts of DNS resolution, HTTP protocols, and Web Server mechanics to visualize the complete, end-to-end lifecycle of a web request. The goal is to understand not just how a browser talks to a server, but how modern infrastructure (like WAFs, Load Balancers, and Databases) supports secure and efficient web browsing.

---

## 2. Key Concepts Learned

### A. Modern Web Infrastructure
A robust website relies on several critical components beyond just a single server:
* **Load Balancers:** These act as traffic cops, distributing incoming user requests across multiple servers to prevent overloads. They perform "health checks" to ensure traffic is only sent to active servers.
* **CDN (Content Delivery Network):** A global network of servers that hosts static files (images, CSS, JS). This allows users to download content from a server geographically closest to them, reducing latency.
* **WAF (Web Application Firewall):** A security layer sitting between the user and the web server. It inspects traffic to block malicious attempts (like SQL Injection) and prevents Denial of Service (DoS) attacks.
* **Databases:** Specialized systems used to store persistent and organized data, such as user credentials, blog posts, or product inventories.

### B. Web Server Mechanics
At the core of the response is the Web Server software (e.g., Apache, Nginx):
* **Virtual Hosts:** Web servers can host multiple different websites (domains) on a single physical machine by inspecting the `Host` header in the HTTP request to decide which site to serve.
* **Static vs. Dynamic Content:**
    * *Static:* Fixed files (HTML, Images) served directly from the hard drive.
    * *Dynamic:* Content generated in real-time using backend languages (PHP, Python, NodeJS), which often query a database to build the page for the specific user.

---

## 3. The Complete Request Lifecycle (Practical Analysis)
In the final practical challenge, I reconstructed the exact sequence of events that occur when a user visits a website. This sequence validates the understanding of the entire module.

**The Correct Sequence:**

1.  **Request tryhackme.com in your browser:** The user initiates the action.
2.  **Check local cache for IP address:** The computer first checks its own storage to see if it already knows the destination.
3.  **Check your recursive DNS server for address:** If not cached, the query is sent to the ISP's DNS.
4.  **Query root server to find authoritative DNS server:** The search moves up the DNS hierarchy.
5.  **Authoritative DNS server advises the IP address:** The correct IP is found and returned to the browser.
6.  **Request passes through a Web Application Firewall:** The connection is screened for security threats.
7.  **Request passes through a Load Balancer:** Traffic is directed to the most available server.
8.  **Connect to webserver on port 80 or 443:** The browser establishes a TCP connection (HTTP/HTTPS).
9.  **Web server receives the GET request:** The server accepts the command to fetch the page.
10. **Web application talks to database:** The backend logic retrieves necessary data (if dynamic).
11. **Your browser renders the HTML into a viewable website:** The final content is displayed to the user.

---

## 4. Conclusion
This room serves as the final piece of the "How The Web Works" puzzle, effectively bridging the gap between abstract protocols and real-world infrastructure. By visualizing the entire request lifecycle—from the initial DNS lookup to the final browser rendering—we now possess a holistic view of web architecture.

**Why this matters for Security:**
Understanding "normal" behavior is the prerequisite for identifying "abnormal" or malicious activity.
* Knowing how DNS works helps in understanding DNS Spoofing.
* Understanding HTTP Headers and Cookies is crucial for Session Hijacking.
* Recognizing the role of WAFs and Load Balancers is essential for mapping out a target's defense perimeter.

With this foundational knowledge established, the path is now clear to move from *understanding* how the web works to learning how to *exploit* its vulnerabilities.
