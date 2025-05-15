## Web Browser as an Attack Point
Your **web browser** is like a doorway to the internet. It's used for:
- Logging into bank accounts
- Shopping online
- Filling out forms

Because of this, **hackers love targeting browsers**. They exploit weak points in:
- JavaScript
- Flash
- ActiveX
Sometimes, the malware is hidden inside scripts and won’t be caught by regular antivirus software.
## Type of Web Based Attacks
![[Type of Web Bassed Attacks.png]]
### DNS Cache Poisoning
**DNS Cache Poisoning**, also called **DNS Spoofing**, is a type of cyberattack where a hacker inserts **false DNS information** into a DNS server’s cache. The goal is to **redirect users to fake or malicious websites** without them knowing.
####  How DNS Works?
![[How DNS Works?.png]]
Suppose you type `www.google.com` into your web browser.
1. *Check Local Cache*
Your computer first checks its local DNS cache to see if it already knows the IP address.
- If yes, it uses the stored IP address.
- If not, it proceeds to the next step.
- ---
1. *Ask the Recursive Resolver (usually from your ISP)*
If your computer doesn’t have the answer, it asks a DNS resolver (usually provided by your internet service provider).
The resolver now takes responsibility for finding the IP address.

---
*The Recursive Resolver Queries Other Servers*
 1. **Root DNS Server**
The resolver asks the root server: “Where can I find the `.com` top-level domain (TLD) server?”
2. **TLD DNS Server**
The root server directs it to the TLD server for `.com`.  
The resolver then asks this server: “Where is the authoritative server for `google.com`?”
3. **Authoritative DNS Server**
This server knows the exact IP address for `www.google.com`.  
It responds with the correct IP address.

---
3. *Return the IP Address*
The resolver sends the IP address back to your computer.  
Your browser uses this IP to connect to the server hosting the website.

---
4. *Caching for Efficiency*
All steps store the results temporarily (cache) to speed up future requests and reduce traffic.
#### Type of DNS Attacks
###### 1. **DNS Spoofing (DNS Cache Poisoning)**
**What is it?**  
Injecting fake DNS data into a DNS resolver’s cache to redirect users to a malicious IP.
**How it works:**  
The attacker sends fake DNS responses faster than the real ones, tricking the DNS server into caching the wrong IP.
**Who it targets:**
- DNS resolvers
- End users (they're redirected to fake websites)
**Real-world case:**  
🧠 _Kaminsky Attack (2008)_ — exposed a critical flaw in DNS systems, allowing cache poisoning on a large scale.
**How to protect:**
- Enable **DNSSEC** (Domain Name System Security Extensions)
- Use **randomized query IDs and source ports**
- Use **HTTPS/TLS** to validate website identity
---
###### 2.  **DNS Flood Attack**
**What is it?**  
A flood of DNS requests sent to overwhelm a DNS server.
**How it works:**  
Attackers use bots to send massive amounts of traffic to DNS servers, exhausting their resources.
**Who it targets:**
- DNS servers of organisations
- ISPs
- Government/enterprise systems
**Real-world case:**  
🧠 _Dyn DNS Attack (2016)_ — took down major services (Twitter, Netflix, Reddit) by flooding Dyn's DNS servers.
**How to protect:**
- Use **rate limiting** and **traffic filtering**
- Deploy **Anycast DNS** (load balancing across global servers)
- Have **redundant DNS servers**
---
###### 3. **Distributed Reflection DDoS (DRDoS)**
**What is it?**  
An attacker uses DNS servers to **amplify attack traffic** and send it to a victim.
**How it works:**
- The attacker spoofs the victim’s IP in DNS queries.
- DNS servers respond to the victim, overwhelming them with data.
**Who it targets:**
- The **spoofed IP owner** (usually a web service or organisation)
**Real-world case:**  
🧠 _Spamhaus Attack (2013)_ — one of the largest DNS amplification attacks ever (over 300 Gbps).
**How to protect:**
- **Block IP spoofing** on edge routers
- Use **rate-limiting on DNS servers**
- Use **firewalls and DDoS protection services**
---
###### 4. **Domain Lock-Up Attack**
**What is it?**  
Abuse of DNS queries to make a domain unresponsive to legitimate users.
**How it works:**
- Repeated or malformed DNS queries consume server resources.
- DNS server may get stuck, causing **temporary denial of service**.
**Who it targets:**
- Specific websites or DNS zones
**Real-world case:**  
🔍 These are often used in **targeted disruption attacks**, such as during protests or campaigns (less commonly reported but used in cyber warfare scenarios).
**How to protect:**
- Use **timeouts and limits** on recursive queries
- Apply **DNS firewalling and anomaly detection**
---
###### 5. **DNS Tunnelling**
**What is it?**  
Using DNS to **bypass security** and send/receive hidden data (acts like a covert channel).
**How it works:**
- Malware encodes data in DNS queries/responses.
- This data is sent to a remote attacker through allowed DNS traffic.
**Who it targets:**
- Corporate networks
- Government systems with strict firewalls
**Real-world case:**  
🧠 _APT32 (OceanLotus)_ used DNS tunnelling to exfiltrate data during targeted espionage campaigns in Southeast Asia.
**How to protect:**
- Monitor **unusually long or frequent DNS queries**
- Block known **tunnelling domains**
- Use **deep packet inspection (DPI)** and **DNS logging**
---
###  SQL Injection
**SQL Injection (SQLi)** is a **web security vulnerability** that allows an attacker to **interfere with the queries** an application makes to its database. It happens when user input is **incorrectly handled**, allowing malicious SQL code to be injected and executed.
#### Type Example of Injection
###### 1. **UPDATE Injection**
**Scenario**: A site lets users change their password.
**Vulnerable query:**
`UPDATE users SET password = 'newpass' WHERE username = 'input';`
**Malicious input:**
`input = anything' OR '1'='1`
**Final query after injection:**
`UPDATE users SET password = 'newpass' WHERE username = 'anything' OR '1'='1';`
**Effect:** All users' passwords are reset, because `'1'='1'` is always true.

---
###### 2. **UNION-Based Injection**
**Scenario:** The site shows user details by ID.
**Original query:**
`SELECT name, email FROM users WHERE id = 'input';`
**Malicious input:**
`1' UNION SELECT username, password FROM admins --`
**Final query:**
`SELECT name, email FROM users WHERE id = '1' UNION SELECT username, password FROM admins --';`
**Effect:** Returns rows from both `users` and `admins`. The attacker sees admin usernames and passwords.

---
###### 3. **DROP TABLE Injection**
**Scenario:** A form searches for a user by name.
**Vulnerable query:**
`SELECT * FROM users WHERE name = 'input';`
**Malicious input:**
`'; DROP TABLE users; --`
**Final query:**
`SELECT * FROM users WHERE name = ''; DROP TABLE users; --';`
**Effect:** Deletes the entire `users` table from the database.

---
###### 4. **Blind SQL Injection**
**Scenario:** The application doesn't show SQL errors but reacts differently to queries.
**Original query:**
`SELECT * FROM products WHERE id = 'input';`
**Testing inputs:**
- `' AND 1=1 --` returns normal page.
    
- `' AND 1=2 --` returns a blank page.
    
**Use:** Attackers can infer true/false conditions and slowly extract data, one character at a time.
###### 5. **Login Bypass**
**Scenario:** a login form generates this SQL query.
**Vulnerable query:**
`SELECT * FROM users WHERE username = 'user' AND password = 'pass';`
**Malicious input:**
`admin' --`
**Final query:**
`SELECT * FROM users WHERE username = 'admin' --' AND password = '';`
**Effect:** If a user named `admin` exists, the attacker is logged in **without needing a password**.
#### How to protect?
 1. Use **Prepared Statements** (also called **parameterised queries**)
>**Best and most effective method.** 
It separates SQL code from user input.

**Example in Java (JDBC):**
`String sql = "SELECT * FROM users WHERE username = ? AND password = ?"; 

`PreparedStatement stmt = conn.prepareStatement(sql); stmt.setString(1, username);`

`stmt.setString(2, password); ResultSet rs = stmt.executeQuery();`
**Effect:** Even if input contains `' OR 1=1 --`, it’s treated as a string, not SQL code.

---
2. Use **Stored Procedures** (with parameters)
- A **stored procedure** is a **predefined SQL query** saved in the **database**. Instead of building SQL queries in your application code, you call the stored procedure and **pass parameters** to it.
- Stored procedures help **prevent SQL injection** because user input is passed as parameters, not directly injected into SQL strings.

---
3. **Input Validation and Escaping**
- Only allow expected input format (e.g., numbers, emails).
- Reject or sanitise dangerous characters (like `'`, `--`, `;`), especially in rare cases where queries are dynamic.
- Avoid relying solely on escaping — it's not foolproof.

---
4. Apply **Least Privilege** Principle
- The database user used by the application should have only the **minimum required permissions**.
    
- For example, don't give write/delete access if the application only needs to read data.
    

---
5. Use **ORM Frameworks**
- Frameworks like **Hibernate (Java)**, **SQLAlchemy (Python)**, or **Entity Framework (C#)** generate safe queries by default.
- They abstract away raw SQL unless needed.

---
6. Disable Detailed SQL Errors in Production
- Never show raw SQL errors to users.
- Use custom error pages to prevent leaking database structure.
### Cross-Site Request Forgery
**CSRF (Cross-Site Request Forgery)** is a type of attack where a malicious website tricks your browser into making a **request to another site where you're already logged in**, without your permission.
> Also called: _session riding_ or _one-click attack_.

#### How it works?
![[How CSRF Works?.png]]
1. You log into a website (e.g., your bank: `www.bank32.com`) and your browser stores a **session cookie** to keep you logged in.
    
2. You **don’t log out**, and you visit a malicious website created by an attacker.
    
3. That malicious site secretly sends a **forged request** to `www.bank32.com` using your browser.
    
4.  Since your browser is still logged in, the bank **accepts the request**, thinking it came from you.
#### How to prevent CSRF?
 1. **Secret Token (Best Practice)**
- The server includes a hidden token (random string) in each form or request.
- When a request is sent, the server checks the token.
- A forged request won’t have the correct token → request is rejected.

 2. **Same-Site Cookies**
- A cookie setting (`SameSite=Strict` or `Lax`) tells the browser **not to send cookies** on cross-site requests.
- Modern browsers support this and help block CSRF.

3. **Referrer Header (Optional)**
- Server checks if the request came from its own site.
- But this is not always reliable — some browsers or users block referrer headers for privacy.

4. **User Practices**
- Always **log out after using sensitive websites**.
- Don’t click unknown or suspicious links.
---
#### Real-world Case
 1. **Gmail (2007)** – _Email Forwarding via CSRF_
- A CSRF vulnerability in Gmail allowed attackers to **create email filters** that would **forward all incoming emails**to an attacker's email address.
- If a user was logged into Gmail and visited a malicious site, the site could silently send a crafted request to Gmail.
- Google later fixed this by implementing **CSRF tokens**.
---
2. **YouTube (2008)** – _Forced Subscriptions_
- Attackers created web pages that could **make logged-in users automatically subscribe** to specific YouTube channels.
- This was done using CSRF via HTML image or script tags that triggered GET requests to YouTube.
---
3. **Netflix (2006)** – _Account Modification via CSRF_
- Netflix had a vulnerability that allowed an attacker to **change user settings** like email or password via CSRF.
- If the user was logged in and visited a malicious site, their account could be altered without their knowledge.
### Cross-Site Scripting
**Cross-Site Scripting (XSS)** is a web security vulnerability where **an attacker injects malicious scripts (usually JavaScript)** into a website, which are then **executed in the browsers of other users**.

This happens when a website **includes untrusted user input** in a web page **without proper validation or escaping**.
##### How it works?
- The attacker submits code like:
`<script>alert('XSS');</script>`
- The server stores or reflects that input.
- When another user visits the page, their browser **runs the malicious script**, thinking it came from the website.
##### Type of XSS
###### 1. **Reflected XSS (Non-persistent)**
**What is it?**  
Injecting malicious scripts into a URL or form input, which are then immediately reflected by the server and executed in the victim’s browser.

**How it works:**  
![[How Reflected XSS Works?.png]]
The attacker crafts a URL containing a script (e.g., `<script>...</script>`). When the victim clicks the link, the server reflects the input in the response without sanitising it. The browser runs the script as if it came from a trusted source.

**Who it targets:**
- Users who click on untrusted links (phishing emails, forums, etc.)
- Websites that reflect user input without encoding
- 
**Real-world case:**  
_Amazon (2016)_ — A reflected XSS vulnerability was found in the Amazon Seller Central login page, allowing attackers to craft malicious login URLs that executed JavaScript when opened.
**How to protect:**
- Always **encode output** (e.g., convert `<` to `&lt;`)
- **Validate and sanitise user input**
- Avoid reflecting raw user input in responses
- Implement **Content Security Policy (CSP)**
- Use **security libraries** like OWASP ESAPI for encoding
- ---
###### 2. **Stored XSS (Persistent)**
**What is it?**  
An attacker stores malicious scripts in a website's database (e.g., in comments, profiles), which are later delivered and executed in other users’ browsers when they view the page.

**How it works:**  
![[How Stored XSS Works?.png]]
The attacker submits input containing JavaScript (e.g., `<script>...</script>`) into a form field like a comment box. The website stores this input and later displays it to other users without sanitising it. The malicious script runs in every viewer’s browser.

**Who it targets:**
- Users who view content from other users (e.g., forums, blogs, social networks)
- Websites that store user-generated content without sanitisation

**Real-world case:**  
_eBay (2014)_ — Attackers injected malicious JavaScript into product listings. Unsuspecting users who viewed the listings were redirected to phishing sites, putting accounts and financial data at risk.

**How to protect:**
- **Sanitise user input before storing** (e.g., strip scripts and dangerous HTML)
- **Encode output** before displaying data on web pages
- Use **input validation** for all form fields
- Implement a **Content Security Policy (CSP)**
- Store only safe, filtered HTML or plain text
###### 3. **DOM-based XSS**
**What is it?**  
A client-side attack where malicious scripts are executed due to insecure handling of user input in JavaScript, without involving the server.

**How it works:**  
The attacker injects a payload into the URL or input field. The website’s JavaScript reads this input (e.g., from `location.hash`, `document.URL`, or `document.referrer`) and dynamically inserts it into the page’s DOM **without sanitising it**, causing the browser to execute it.

**Who it targets:**
- Web applications using JavaScript to modify the DOM based on user input
- Users who click crafted URLs or interact with untrusted input

**Real-world case:**  
_Google (2012)_ — A DOM-based XSS vulnerability was found in Google Translate. The page’s client-side code mishandled URL parameters, allowing script injection.

**How to protect:**
- Never insert unsanitised user input directly into the DOM (e.g., `innerHTML`)
    
- Use **safe DOM APIs** like `textContent` or `setAttribute`
    
- Validate and **sanitise input on the client side**
    
- Apply a **Content Security Policy (CSP)**
    
- Use libraries like **DOMPurify** to clean dynamic content