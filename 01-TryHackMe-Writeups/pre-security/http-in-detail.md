# HTTP in Detail - Writeup

* **Room:** [HTTP in Detail](https://tryhackme.com/room/httpindetail)
* **Category:** Pre-Security
* **Module:** Module 3 "How The Web Works."
* **Date:** 22 Jan 2026
---

## 1. Objective
This room provides a deep dive into the HyperText Transfer Protocol (HTTP), the foundational language of the web. The objective is to understand how browsers and servers communicate, analyze the structure of requests/responses, differentiate between HTTP methods, and grasp the importance of headers, cookies, and secure connections (HTTPS).

---

## 2. Core Concepts: The Web's Language

### A. HTTP vs. HTTPS
* **HTTP:** A protocol developed by Tim Berners-Lee (1989-1991) for transmitting web data (HTML, images, etc.). It sends data in clear text, which is insecure.
* **HTTPS (Secure):** The encrypted version of HTTP. It ensures Confidentiality (stopping eavesdroppers) and Authentication (verifying the server's identity).

### B. Anatomy of a URL
A URL (Uniform Resource Locator) is an instruction to access a resource. It consists of specific parts:
* **Scheme:** Protocol (`http://` or `https://`).
* **Host:** Domain name or IP address.
* **Port:** Connection gate (Default: 80 for HTTP, 443 for HTTPS).
* **Path:** The file location on the server (`/view-room`).
* **Query String:** Parameters sent to the server (`?id=1`).

---

## 3. Technical Breakdown

### A. HTTP Methods (The Verbs)
Methods define the *action* the client wants to perform:
* **GET:** Retrieve information (e.g., loading a page).
* **POST:** Submit new data (e.g., login form).
* **PUT:** Update existing data.
* **DELETE:** Remove data/records.

### B. Status Codes (The Signals)
Servers respond with 3-digit codes to indicate the request outcome:
* **200 OK:** Success.
* **301/302:** Redirection (Moved Permanently/Found).
* **400 Bad Request:** Client error (Typo or malformed request).
* **401/403:** Authentication error (Unauthorized/Forbidden).
* **404 Not Found:** Resource does not exist.
* **500/503:** Server error (Internal Error/Service Unavailable).

### C. Headers & Cookies (State Management)
HTTP is **stateless**, meaning the server forgets the user after every request. Cookies solve this problem.
* **The Cookie Flow:**
    1.  User logs in.
    2.  Server sends a `Set-Cookie` header (Response) to save a token on the user's computer.
    3.  Browser automatically sends the `Cookie` header (Request) in all future requests to identify the user.
* **Inspection:** Cookies can be inspected using the browser's Developer Tools under the "Network" or "Application" tab.

---

## 4. Practical

In the final task, I utilized a Request Simulator to manipulate HTTP requests and bypass simple controls to retrieve hidden flags.

**1. Basic Navigation (GET):**
* **Action:** Request the `/room` page using GET.
* **Flag:** `THM{YOU'RE_IN_THE_ROOM}`.

<img width="790" height="431" alt="room" src="https://github.com/user-attachments/assets/8957ad1a-4c6a-46b7-9da4-3a9f671ae6b7" />

**2. Parameter Manipulation (Query String):**
* **Action:** Request `/blog` and add the parameter `id=1`.
* **Flag:** `THM{YOU_FOUND_THE_BLOG}`.
* 
<img width="782" height="413" alt="blog1" src="https://github.com/user-attachments/assets/88c8827b-b82c-4f8e-80a7-523bce93f349" />

<img width="792" height="403" alt="blog2" src="https://github.com/user-attachments/assets/3c5d5474-f89c-428f-a495-e407728dda12" />

**3. Data Modification (PUT & DELETE):**
* **Action:** `DELETE` the resource at `/user/1`.
* **Flag:** `THM{USER_IS_DELETED}`.
* **Action:** `PUT` (Update) `/user/2` with body parameter `username=admin`.
* **Flag:** `THM{USER_HAS_UPDATED}`.

<img width="777" height="408" alt="delete" src="https://github.com/user-attachments/assets/235d521f-eb0f-4b3c-a3e4-0864400113bf" />


**4. Authentication Bypass (POST):**
* **Action:** `POST` credentials to `/login` (`username=thm`, `password=letmein`).
* **Flag:** `THM{HTTP_REQUEST_MASTER}`.

<img width="782" height="440" alt="post" src="https://github.com/user-attachments/assets/02d0acaa-ad6e-4eac-80a6-b5f6b0f44d28" />

---

## 5. Conclusion
Understanding the raw structure of HTTP is essential for Web Security. Tools like Browser Developer Tools allow us to inspect these invisible exchanges—viewing headers, modifying cookies, and analyzing status codes—which is the first step in identifying vulnerabilities like Broken Access Control or Insecure Direct Object References (IDOR).
