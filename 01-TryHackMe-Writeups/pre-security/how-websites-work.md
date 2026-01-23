# How Websites Work - Writeup

* **Room:** [How Websites Work](https://tryhackme.com/room/howwebsiteswork)
* **Category:** Pre-Security
* **Module:** Module 3 "How The Web Works."
* **Date:** 23 Jan 2026

---
## 1. Objective
This room deconstructs the fundamental components of a modern website. It explores the Client-Server architecture and distinguishes between Front End (HTML/CSS/JS) and Back End technologies, while introducing basic vulnerabilities like Sensitive Data Exposure and HTML Injection.

---

## 2. Core Concepts: The Web Architecture

### Client vs. Server
The web operates on a request-response cycle:
* **Client (Browser):** Sends a request for a page.
* **Server:** A dedicated computer that processes the request and returns data.

### Front End vs. Back End
* **Front End (Client-Side):** The code that runs in your browser (HTML, CSS, JavaScript). This is what the user sees and interacts with.
* **Back End (Server-Side):** The code that runs on the server (handling databases, authentication, and logic).

---

## 3. Technical Breakdown & Practical Labs

### A. HTML: The Skeleton
HTML (HyperText Markup Language) defines the structure of the page using tags (like `<h1>`, `<p>`, `<img>`).
* **Practical Challenge 1 (Fixing Code):**
    * *Issue:* A cat image was broken because the file extension was missing (`img/cat-2.`).
    * *Fix:* I updated the source to `<img src='img/cat-2.jpg'>`.
    * *Flag Revealed:* HTMLHERO.
      
<img width="822" height="505" alt="1" src="https://github.com/user-attachments/assets/8394238c-15e1-45f1-bc6b-8ed450dc62e9" />

<img width="824" height="459" alt="2" src="https://github.com/user-attachments/assets/ac197513-e19d-4e0c-9198-883fd1880dd4" />

* **Practical Challenge 2 (Adding Content):**
    * *Issue:* I needed to add a dog image to the specific line.
    * *Action:* I inserted the code `<img src='img/dog-1.png'>`.
    * *Flag Revealed:* DOGHTML.

<img width="824" height="442" alt="3" src="https://github.com/user-attachments/assets/eb6745ae-c173-48a8-8d98-22ea189b0d72" />

### B. JavaScript: The Muscle
JavaScript (JS) makes the website interactive, allowing dynamic updates without reloading the page.
* **Practical Challenge 1 (DOM Manipulation):**
    * *Goal:* Change the text "Hi there!" to "Hack the Planet".
    * *Code:* `document.getElementById("demo").innerHTML = "Hack the Planet";`
    * *Flag Revealed:* JSISFUN.

<img width="808" height="280" alt="4" src="https://github.com/user-attachments/assets/b7f52221-3f13-44c3-bf0f-8572e5c26f48" />

<img width="806" height="269" alt="5" src="https://github.com/user-attachments/assets/fffceab0-d406-4682-a3a3-7308efe36873" />

* **Practical Challenge 2 (Event Handling):**
    * *Goal:* Add a button that changes text when clicked.
    * *Code:* `<button onclick='document.getElementById("demo").innerHTML = "Button Clicked";'>Click Me!</button>`
    * *Result:* The button successfully updated the HTML element upon interaction.

<img width="809" height="296" alt="6" src="https://github.com/user-attachments/assets/8357ca60-4147-464e-afdb-d093ee8c23ae" />

<img width="811" height="290" alt="7" src="https://github.com/user-attachments/assets/dc41987b-8209-4ee2-98c9-840987f9c1c9" />

---

## 4. Vulnerability Analysis

### A. Sensitive Data Exposure (Task 4)
This vulnerability occurs when developers leave sensitive information in the Front End code, assuming users won't look at it.
* **Investigation:** I right-clicked and selected "View Page Source" to inspect the raw HTML.
* **Finding:** I discovered an HTML comment (``) containing temporary login credentials.
* **Creds Found:** `admin:password123`
* **Flag/Password:** `testpasswd`.

<img width="1280" height="449" alt="9" src="https://github.com/user-attachments/assets/c1c328f8-2250-4796-a0ea-0ee1a047f84a" />

<img width="1280" height="467" alt="8" src="https://github.com/user-attachments/assets/2d9f46f0-dde0-40d2-9311-5ed2b09cf24e" />

### B. HTML Injection
This vulnerability arises when a website trusts user input blindly and renders it as code instead of plain text.
* **Exploit:** I injected an HTML anchor tag into the "What's your name?" input field to create a malicious link.
* **Payload:** `<a href="http://hacker.com">Click me</a>`
* **Result:** The website rendered the link, proving the vulnerability.
* **Final Flag:** HTML_INJ3CTI0N (Appeared after the injection was successful).
  
<img width="539" height="180" alt="10" src="https://github.com/user-attachments/assets/3f60cc47-634b-4cc6-9424-c5b546aa4a0f" />

<img width="538" height="202" alt="11" src="https://github.com/user-attachments/assets/0ed2553c-5c6b-46ec-b016-55a23a9d577f" />

---

## 5. Conclusion
This room demonstrated that **Front End** code (HTML/JS) is fully accessible to the user and should never be trusted for security.
1.  **Never leave sensitive data** (passwords/comments) in Front End code.
2.  **Always sanitize user input** to prevent attacks like HTML Injection, which can lead to Defacement or Phishing.
