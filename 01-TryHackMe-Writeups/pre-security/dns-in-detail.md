# DNS in Detail - Writeup

* **Room:** [DNS in Detail](https://tryhackme.com/room/dnsindetail)
* **Category:** Pre-Security
* **Module:** Module 3 "How The Web Works."
* **Date:** 22 Jan 2026
---

## 1. Objective
This report explores the Domain Name System (DNS), a fundamental system often described as the "Phonebook of the Internet." The primary objective of this module is to understand how the internet translates domain names into IP addresses, dissect the domain hierarchy structure, analyze various DNS Record types, and practice Information Gathering techniques using DNS protocols.

---

## 2. Core Concepts: Anatomy of DNS

### A. The Phonebook Analogy
Computers communicate using precise numbers called IP Addresses (e.g., `104.26.10.229`), whereas humans find it easier to remember words (e.g., `tryhackme.com`). DNS bridges this gap by mapping user-friendly domain names to the corresponding server IP addresses, enabling accessible web browsing.

### B. Domain Structure & Hierarchy
A domain name is actually processed by the system from right to left, resembling an **Inverted Tree** structure:
1.  **Root Domain:** The hidden dot (`.`) at the very end of the address.
2.  **Top-Level Domain (TLD):** The rightmost extension, divided into *Generic* (`.com`, `.org`) and *Country Code* (`.id`, `.uk`).
3.  **Second-Level Domain:** The unique name of the organization or website (e.g., `tryhackme`).
4.  **Subdomain:** The prefix to the left of the main domain (e.g., `blog` or `admin`) used to separate specific services.

### C. The Request Journey
When a user requests a website, a **Recursive Query** process occurs:
* The computer first checks its **Local Cache** (short-term memory).
* If not found, the request is sent to the **Recursive DNS Server** (ISP).
* If the ISP doesn't know, it queries the **Root Server**, which redirects to the **TLD Server**, and finally to the **Authoritative Server** that holds the actual IP data.

---

## 3. DNS Record Analysis
DNS stores information in various types of *records*, each serving a specific function:

| Record Type | Primary Function | Usage Example |
| :--- | :--- | :--- |
| **A Record** | Maps a hostname to an **IPv4 Address**. | `google.com` -> `142.250.x.x` |
| **AAAA Record** | Maps a hostname to an **IPv6 Address**. | Newer hex-format IP addresses. |
| **CNAME** | **Alias/Canonical Name**. Points a domain to another domain. | `shop.site.com` -> `shops.shopify.com` |
| **MX Record** | Specifies the **Email** server. | Directs office mail to Google/Outlook. |
| **TXT Record** | Arbitrary text notes. | Domain ownership verification & email security (SPF). |

---
