---
title: 'Introduction'
description: 'An introduction to web exploitation'
category: 'Web Exploitation'
order: 1
---

Web Exploitation is identifying vulnerabilities in web applications, websites and APIs to gain unauthorized access, steal sensitive data or disrupt services.

## Pre-requisites

- **How the web works (HTTP/S, Clients, Servers):** Before breaking things, you must know how they work. The web relies on a simple request-response cycle. A **Client** (your web browser) sends an **HTTP Request** asking for data or performing an action. The **Server** (where the website lives) processes it and sends an **HTTP Response** back. You will spend most of your time intercepting, reading, and tampering with these HTTP requests before they reach the server! You'll also need to know a bit of JavaScript and HTML.
- Resources:
    - [Mozilla Web Docs](https://developer.mozilla.org/en-US/docs/Web) [Gold standard]
    - [Web Security Academy](https://portswigger.net/web-security) [Highly Recommended]
    - [MDN - How the web works](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_web_works)

## Some Common Vulnerabilities

- SQL Injection (SQLi)
- Cross-Site Scripting (XSS)
    - Reflected
    - Stored
    - DOM-based
- CSRF (Cross-Site Request Forgery)
- SSRF (Server-Side Request Forgery)
- File Upload Vulnerabilities
- Authentication Vulnerabilities
- Race Conditions
- XXE (XML External Entity)

## SQL Injection

SQL Injection (SQLi) is a vulnerability that occurs when an attacker is able to manipulate a web application's database queries using malicious SQL code. This malicious SQL code can be injected into text fields, URL parameters, or any other input that is processed by the application. This allows the attacker to access or modify data in the database, potentially leading to unauthorized access, data theft, or system compromise.

**Example:** Imagine a login page. When you type your username and password, the server builds a database query like this:

```sql
SELECT * FROM users WHERE username = 'your_input' AND password = 'your_password';
```

Now, what if instead of a real username, you type: `' OR 1=1 --`

Now the query looks like:

```sql
SELECT * FROM users WHERE username = '' OR 1=1 --' AND password = 'whatever';
```

`OR 1=1` is always true, and `--` comments out the rest of the query (including the password check). The database happily returns every user in the table, and the application logs you in as the first user, often the admin.


#### Types of SQL Injection

- **Error-Based SQLi:** Attacker exploits database errors to extract information.
- **Union-Based SQLi:** Uses SQL UNION operator to extract data from other tables.
- **Blind SQLi:** No error messages are returned. Attacker infers data based on boolean responses or time delays.


#### Prevention
Use **prepared statements** (also called parameterized queries). Instead of gluing user input directly into the SQL string, you use placeholders. The database treats the input as data, never as code. That's pretty much it, and if every app did this, SQLi would be dead.

## Cross-Site Scripting (XSS)


This type of attack happens when a website allows users to inject code into the website ( HTML, Javascript ) which then gets executed on the other user's browsers, potentially stealing their data or hijacking their sessions.

### Types of XSS

- **Reflected:** Your payload is part of the URL or request. The server bounces it right back in the response. You trick someone into clicking your crafted link, and the script fires in their browser.
- **Stored:** Your payload gets saved on the server (in a database, a forum post, a profile bio, etc.). Every time someone loads that page, your script runs. More dangerous.
- **DOM-based:** The page's own JavaScript takes your input and unsafely writes it into the page. The server never even sees the payload, it all happens client-side.


Prevention of XSS:
- **Output Encoding:** Whenever user input is rendered on a page, encode special characters like `<`, `>`, `"`, `'` so the browser treats them as text, not code.
- **Content Security Policy (CSP):** A header you set on your server that tells the browser which scripts are allowed to run. Even if someone injects a `<script>` tag, the browser will refuse to execute it if it's not on the whitelist.
- **Input Sanitization:** Strip or escape dangerous characters before storing user input.

## CSRF (Cross-Site Request Forgery)

Let's say you're logged into your bank. You visit some random forum, and hidden in the page is an image tag like `<img src="https://bank.com/transfer?to=attacker&amount=10000">`. Your browser sees a URL, it sends the request along with your session cookies. The bank thinks it's you. Money might be gone.

That's CSRF. The attacker tricks your browser into making authenticated requests on your behalf without you knowing.

**Prevention:** Use anti-CSRF tokens, a unique, random value tied to your session that must be included in every state-changing request. If the token doesn't match, the server rejects it.

## SSRF (Server-Side Request Forgery)

Some apps let you provide a URL, maybe to fetch a profile picture, preview a link, or import data. SSRF is when you give it an internal URL like `http://localhost:6379` or `http://169.254.169.254/latest/meta-data/` (AWS metadata endpoint) and the server fetches it for you. You're essentially using the server as a proxy to access things you shouldn't be able to reach from the outside.

This is how people steal cloud credentials, access internal admin panels, and pivot into private networks.

## File Upload Vulnerabilities

A website lets you upload a profile picture. What if you upload a `.php` file instead of a `.jpg`? If the server doesn't validate properly, your PHP code gets saved to the web directory and you can execute it by visiting its URL.

Bypasses often involve:
- Changing the file extension (`.php` → `.php.jpg`, `.pHp`, `.php%00.jpg`)
- Spoofing the `Content-Type` header
- Embedding code in image metadata

## XXE (XML External Entity)

If an application parses XML input (and many do like SOAP APIs, file uploads, SVG images), you can define an external entity that reads local files:

```xml
<?xml version="1.0"?>
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<data>&xxe;</data>
```

The server processes this and replaces `&xxe;` with the contents of `/etc/passwd`. You're reading arbitrary files off the server through XML.

## Race Conditions

Sometimes the bug isn't in the logic, it's in the *timing*. If a website checks your balance and then deducts it in two separate steps, what happens if you fire off 10 requests at the exact same time? All 10 might pass the balance check before any deduction happens.

Race conditions are tricky to find and exploit, but they show up more often than you'd think, especially in coupon redemption, voting systems, and file operations.

## Authentication Vulnerabilities

This is a broad category, but here are the greatest hits:
- **Weak passwords / default credentials:** Admin panels with `admin:admin` are more common than you'd hope.
- **Broken session management:** Session tokens that are predictable, don't expire, or aren't invalidated on logout.
- **JWT attacks:** Forging tokens by changing the algorithm to `none`, or cracking weak signing secrets.
- **Password reset flaws:** Tokens sent in URLs, leaked in referrer headers, or not properly validated.

---

## Tools

You'll need these in your toolkit:

- **Burp Suite**: The Swiss army knife of web hacking. It intercepts HTTP requests between your browser and the server, lets you modify them, replay them, and automate attacks. [Download the Community Edition](https://portswigger.net/burp/communitydownload) - it's free.
- **Browser DevTools (F12)**: Inspect the DOM, monitor network requests, read cookies and local storage. You already have this.
- **curl**: Make HTTP requests from the command line.
- **SQLMap**: Automated SQL injection tool. Feed it a URL with a parameter and it'll test, exploit, and dump the database for you. [GitHub](https://github.com/sqlmapproject/sqlmap)
- **ffuf / gobuster**: Directory and file fuzzing. Find hidden endpoints, admin panels, backup files. [ffuf](https://github.com/ffuf/ffuf)

## Where to Practice

- [PortSwigger Web Security Academy](https://portswigger.net/web-security/all-labs): Free labs for every vulnerability type. Start with Apprentice-level. This is the single best free resource.
- [PicoCTF: Web Exploitation](https://play.picoctf.org/practice?category=1&page=1): Beginner-friendly CTF challenges.
- [OverTheWire: Natas](https://overthewire.org/wargames/natas/): A wargame focused entirely on web security. Progressive difficulty.
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/): An intentionally vulnerable web app you can run locally and hack to your heart's content.
- [TryHackMe](https://tryhackme.com/): Guided rooms with step-by-step walkthroughs.
- [HackTheBox](https://www.hackthebox.com/): More advanced, less hand-holding.

## Further Reading

- [OWASP Top 10](https://owasp.org/www-project-top-ten/): The industry-standard list of the most critical web security risks.
- [CTF101: Web Exploitation](https://ctf101.org/web-exploitation/overview/): Quick overview of common web CTF challenges.
- [LiveOverflow: Web Hacking Playlist](https://www.youtube.com/playlist?list=PLhixgUqwRTjx2BmNF5-GddyqZcizwLLGP)
- [Bug Bounty Bootcamp](https://nostarch.com/bug-bounty-bootcamp) by Vickie Li: A solid book if you want to get into bug bounties.
