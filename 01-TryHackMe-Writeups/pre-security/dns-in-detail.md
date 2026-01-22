# DNS in Detail - Writeup

* **Room:** [DNS in Detail](https://tryhackme.com/room/dnsindetail)
* **Category:** Pre-Security
* **Module:** Module 3 "How The Web Works."
* **Date:** 22 Jan 2026
---

## 1. Objective
This report explores the Domain Name System (DNS), a fundamental system often described as the "Phonebook of the Internet." The primary objective of this module is to understand how the Internet translates domain names into IP addresses, dissect the domain hierarchy structure, analyze various DNS Record types, and practice Information Gathering techniques using DNS protocols.

---

## 2. Core Concepts: Anatomy of DNS

### A. The Phonebook Analogy
Computers communicate using precise numbers called IP Addresses (e.g., `104.26.10.229`), whereas humans find it easier to remember words (e.g., `tryhackme.com`). DNS bridges this gap by mapping user-friendly domain names to the corresponding server IP addresses, enabling accessible web browsing.

### B. Domain Structure & Hierarchy
A domain name is actually processed by the system from right to left, resembling an Inverted Tree structure:
1.  **Root Domain:** The hidden dot (`.`) at the very end of the address.
2.  **Top-Level Domain (TLD):** The rightmost extension, divided into *Generic* (`.com`, `.org`) and *Country Code* (`.id`, `.uk`).
3.  **Second-Level Domain:** The unique name of the organization or website (e.g., `tryhackme`).
4.  **Subdomain:** The prefix to the left of the main domain (e.g., `blog` or `admin`) used to separate specific services.

### C. The Request Journey
When a user requests a website, a Recursive Query process occurs:
* The computer first checks its Local Cache (short-term memory).
* If not found, the request is sent to the Recursive DNS Server(ISP).
* If the ISP doesn't know, it queries the Root Server, which redirects to the TLD Server, and finally to the Authoritative Server that holds the actual IP data.

---

## 3. DNS Record Analysis
DNS stores information in various types of *records*, each serving a specific function:

| Record Type | Primary Function | Usage Example |
| :--- | :--- | :--- |
| **A Record** | Maps a hostname to an IPv4 Address. | `google.com` -> `142.250.x.x` |
| **AAAA Record** | Maps a hostname to an IPv6 Address. | Newer hex-format IP addresses. |
| **CNAME** | **Alias/Canonical Name**. Points a domain to another domain. | `shop.site.com` -> `shops.shopify.com` |
| **MX Record** | Specifies the Email server. | Directs office mail to Google/Outlook. |
| **TXT Record** | Arbitrary text notes. | Domain ownership verification & email security (SPF). |

---
## 4. Practical

To demonstrate a practical understanding of the theory, I conducted two stages of DNS investigation: a lab simulation and a real-world case study.

### A. Lab Simulation: `website.thm`
In the TryHackMe simulation environment, I interrogated the target domain to map its infrastructure:

* **E-Commerce Platform:** I discovered that the subdomain `shop.website.thm` has a CNAME pointing to `shops.myshopify.com`. This reveals that the target uses a third-party platform (Shopify) for their online store.
  
<img width="797" height="262" alt="cname" src="https://github.com/user-attachments/assets/cf73e61e-d985-497f-90d0-a0ddc2e6af3e" />

* **Hidden Info:** Querying the TXT Record revealed hidden information in the form of a Flag: `THM{7012BBA60997F35A9516C2E16D2944FF}`.

<img width="796" height="266" alt="txt" src="https://github.com/user-attachments/assets/8dd89c9d-92b1-4c2c-b737-60e94ba08622" />

* **Mail Server:** The MX Record showed the email server priority was set to `30`.

<img width="798" height="260" alt="mx" src="https://github.com/user-attachments/assets/9c1d7d3c-c001-4b65-a281-ac55b2f46e2c" />

* **Web Server IP (A Record):** Querying the A record for `www.website.thm` revealed that the site resolves to the IP address `10.10.10.10`. This identifies the actual location of the main web server.

<img width="797" height="273" alt="ip" src="https://github.com/user-attachments/assets/613b79b0-9c11-4f20-8629-62c2b0c66962" />

### B. Real World Case Study: `unmer.ac.id`
I applied Passive Reconnaissance techniques using the `nslookup` tool against a real-world target, Universitas Merdeka Malang (`unmer.ac.id`), and uncovered the following infrastructure data:

1.  **Security & CDN:**
    The A Record query revealed the Nameserver `dion.ns.cloudflare.com`. This indicates the university protects its website using Cloudflare services (WAF & DDoS Protection).
2.  **Email Infrastructure:**
    The MX Record query displayed `aspmx.l.google.com`. This confirms that the university utilizes Google Workspace (Gmail) for its official email system.
3.  **Security Verification:**
    The TXT Record query revealed advanced security configurations:
    * `google-site-verification`: Proof of domain ownership validation in Google Search Console.
    * `v=spf1 include:_spf.google.com -all`: A strict SPF (Sender Policy Framework) implementation, which blocks any server other than Google from sending emails on behalf of the university (preventing *Email Spoofing*).
---

## 5. Conclusion
Understanding DNS is crucial in cybersecurity. It is not just an addressing system, but a rich source of Open Source Intelligence (OSINT).

By investigating records such as CNAME, MX, and TXT, a Security Analyst can map out the technologies used by a target (such as Email providers or Cloudflare) and evaluate their security posture (such as SPF configurations) without needing to perform active attacks on the server.
