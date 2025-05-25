# TLS (Transport Layer Security) / SSL (Secure Sockets Layer)
##  What is TLS/SSL?
**TLS (Transport Layer Security)**, previously known as **SSL (Secure Sockets Layer)**, is a **security protocol** that protects data transmitted over the internet.
TLS ensures:
1. **Confidentiality** – Data is encrypted so others can’t read it.
2. **Authentication** – You know you're communicating with the correct server.
3. **Integrity** – The data hasn’t been changed during transmission.
Whenever you visit a website that starts with `https://`, it means TLS is being used to protect your connection.
---
## How Does TLS Work?
To establish a **shared session key** between the client (e.g., your browser) and the server, which will be used to encrypt actual communication data.

---
## TLS Handshake
This is how **a client (e.g., browser)** and **a server (e.g., website)** securely agree on encryption settings and keys **before actual data is exchanged**.
![](https://miro.medium.com/v2/1*yAvvDe7IqsSw8DafUgitew.png)
### **Phase 0: TCP Connection Setup**
This is the standard **TCP 3-way handshake** before TLS begins.
1. **SYN** → Client initiates connection
2. **SYN/ACK** → Server acknowledges
3. **ACK** → Client acknowledges back
4. **ESTABLISHED** → TCP connection is ready
This is **not yet encrypted**, it's just basic TCP setup.
---
###  **Phase 1: Hello Messages**
5. **Client Hello**
Client sends:
- TLS/SSL version it supports
- Random value (used for key generation)
- List of supported **cipher suites** (encryption algorithms)
- Optional extensions (like SNI – server name indication)

6. **Server Hello**
Server replies with:
- Chosen TLS version
- Chosen cipher suite
- Another random value
- **Server's digital certificate** (contains public key)
- Optionally: a request for the **client certificate**
---
### **Phase 2: Key Exchange**
![[Key Generation and Exchange.png]]
 7. **Client sends Pre-Master Secret**
- Client generates a **pre-master secret**
- Encrypts it using the **server’s public key** from the certificate
- Sends it to the server
**(If the server requested client authentication: client also sends its certificate here)**

8. **Session Key Creation**
- Both client and server now **derive a master secret** from:
    - The pre-master secret
    - The two random values exchanged earlier
- Then, from the master secret → **they generate symmetric session keys**:
    - Encryption keys
    - MAC keys (for integrity)
    - IVs (if needed)
---
###  **Phase 3: Finish and Start Encrypted Communication**
![[Network Traffics During TLS Handshake.png]]
9. **Client Finished**
- Client sends a “Finished” message encrypted with the session key
- Contains a hash of all handshake messages for integrity check    

10. **Server Finished**
- Server replies with its “Finished” message, also encrypted
![[TLS Data Transmission.png]]
11. **Exchange Encrypted Application Data**
- Now, both sides can start exchanging actual data (e.g., HTTP requests/responses)
- All communication is now encrypted and secure
---
### Optional Authentication
If the **server requires client authentication**:
- It requests the client certificate during **Server Hello**
- Client sends its certificate along with the pre-master secret
- Server **verifies the client’s certificate**
This is used in **mutual TLS (mTLS)** – common in APIs and enterprise systems.
---
## Why Use So Many Keys?

 **Asymmetric encryption (public/private key)**
	- Used **only during the handshake**
	- Secure but **slow and resource-intensive**
	
**Symmetric encryption (session keys)**
	- Used for the actual data transfer
	- **Fast and efficient**
	
So, TLS uses **public/private keys to securely agree on a shared secret**, then switches to **session keys** for efficient encryption.

## What Does TLS Do in Each Protocol?
![[What Does TLS Do in Each Protocol?.png]]

 1. **HTTPS (Secure Web Browsing)**
TLS protects:
- HTTP requests: URLs, methods (GET/POST), parameters
- Form data: usernames, passwords, credit card numbers
- Cookies (e.g., login session)
- Server responses (HTML, images, scripts, etc.)

 How it works:
- When you visit a website starting with `https://`, the browser **establishes a TLS connection first**
- Only after that, the encrypted HTTP data is sent
- Without TLS, this sensitive data could be read or modified by attackers (e.g., in a public Wi-Fi)
---
 2. **SMTPS (Secure Email Sending)**
 TLS protects:
- Login credentials (username and password)
- Email content
- Sender and recipient information
- SMTP commands: `MAIL FROM`, `RCPT TO`, `DATA`

 How it works:
- **Implicit TLS (port 465)**: TLS starts immediately after the TCP connection
- **Explicit TLS (port 587)**: Client connects in plain text, then sends `STARTTLS` to upgrade the connection
- After the TLS handshake, all data is encrypte
---
3. **POP3S (Secure Email Downloading)**
TLS protects:
- Login credentials
- List of messages
- Email contents
- POP3 commands: `USER`, `PASS`, `RETR`, etc.

 How it works:
- TLS handshake occurs right after connecting to port **995**
- The email client and server then communicate securely, downloading emails over the encrypted channel
---
 4. **IMAPS (Secure Email Access)**
 TLS protects:
- Usernames and passwords
- Mailbox folder structure
- Message metadata and contents
- IMAP commands: `LOGIN`, `SELECT`, `FETCH`, `SEARCH`

 How it works:
- When connecting to port **993**, TLS starts immediately (implicit)
- All access to emails, even when syncing across multiple devices, is encrypted
---
5. **FTPS (Secure File Transfer Protocol)**
TLS protects:
- Login credentials
- File and folder names
- File contents
- FTP commands: `LIST`, `RETR`, `STOR`, etc.

How it works:
- **Implicit FTPS (port 990):** TLS handshake begins immediately
- **Explicit FTPS (port 21):** FTP connection starts plain, then client sends `AUTH TLS` to begin encryption
- After TLS is established, all command and file transfers are encrypted
---
 6. **SIPS (Secure SIP – Voice/Video Calls Setup)**
 TLS protects:
- Call setup and teardown messages
- IP addresses, phone numbers, session control data
- SIP commands: `INVITE`, `ACK`, `BYE`, etc.

How it works:
- TLS is used to **encrypt the SIP signaling messages** over port **5061**
- It does **not encrypt audio or video data** (that’s handled by SRTP)
- It prevents attackers from spoofing or intercepting call setup
# SSL/TLS Vulnerabilities
![[TLS Vulnerabilities.png]]
Although SSL/TLS is designed to secure communications, **it can still be vulnerable** due to weaknesses in different parts of its design or implementation.
## 1. **Handshake Protocol**
This is the initial phase where:
- Client and server agree on the encryption algorithms (cipher suites)
- Exchange keys
- Authenticate each other

 Common vulnerabilities:
	- **Downgrade attacks**: An attacker forces the client/server to use an older, less secure TLS/SSL version (e.g., SSL 3.0)
	- **Man-in-the-Middle (MITM)**: Attacker intercepts the handshake to impersonate the server
	- **Version rollback**: The protocol is tricked into using SSL 2.0/3.0, which are vulnerable

### Man-in-the-Middle (MITM) Attack
![[Man-in-the-Middle (MITM) Attack.png]]
#### 1. What is a MITM attack?
A **Man-in-the-Middle (MITM)** attack happens when an attacker **secretly intercepts, reads, or alters communication**between two parties (such as a user and a website) **without either side knowing**.
- The **user thinks they are talking to the website**.
- The **website thinks it’s talking to the real user**.
- In reality, the **attacker sits silently in the middle**.

---
#### 2. Goal of MITM
- **Eavesdrop** on sensitive data (cookies, passwords, login tokens)
    
- **Impersonate** the user or the server
    
- **Modify** the communication content
    
- **Hijack** the session or connection

---
#### 3. Three common types of MITM attacks

##### SSL/TLS Renegotiation Attack
**Objective:**
	To **inject malicious data** into a secure TLS session by abusing the **renegotiation feature** of TLS.

---
**How it works**:

1. The attacker first **establishes a TLS connection with the server** as if they were the legitimate client.
    
2. Then, the attacker **captures the real client’s TLS handshake request**.
    
3. Instead of starting a new session, the attacker **injects this handshake as a renegotiation** within the already-established session.
    
4. The server thinks the original client is **renegotiating the session**, and assumes that all data (from both attacker and client) belongs to the same entity.
    
5. As a result:
    
    - The attacker’s data and the client’s data are **combined into the same session**.
        
    - The server accepts commands or input **that were actually injected by the attacker**.
---
 **Consequences**:
- The attacker can **send unauthorized requests**, such as placing fake orders or altering transactions.
    
- This can occur even though the session appears encrypted and authenticated.
    
---
 **Mitigation**:

- **Disable renegotiation** on the server if not needed.
    
- Or enforce **RFC 5746**, which ensures that renegotiation is cryptographically linked to the original session.
---
#####  SSLstrip Attack
**Objective**:
To trick the user into communicating over **unsecured HTTP** instead of **secure HTTPS**, and steal their sensitive data.

 **How it works**:
1. The user types a website address, such as `http://example.com`.
    
2. Normally, the website would **redirect to `https://example.com`** for security.
    
3. The attacker, acting as a MITM, **intercepts this redirect** and **blocks or strips the HTTPS upgrade**.
    
4. The attacker **sends the user a fake version of the website over HTTP**, which looks exactly like the real site.
    
5. The user sees no warning, types in their **username and password**, and submits them.
    
6. The attacker captures the credentials and can **immediately log in as the victim**.
    
7. The attacker may then forward the user to the real HTTPS version of the site, so the user **does not suspect anything went wrong**.
---

 **Consequences**:
- The user believes they are using HTTPS but actually **sends login information in plain text**.
- The attacker **silently captures sensitive data** without being detected.
---

 **Mitigation**:
- The website should use **HSTS (HTTP Strict Transport Security)** to force browsers to only use HTTPS.
- Modern browsers should show **clear warnings when login forms are served over HTTP**.
- Users should **always check for the `https://` and the padlock icon** in the address bar.
---

#####  Version Rollback Attack
![[Version Rollback Attack.png]]
 **Objective**:
To **downgrade the TLS version** used by the client and server to an older, **weaker version**, and then exploit known vulnerabilities in that version.

---
 **How it works**:
1. The client sends a **ClientHello** message offering support for the latest TLS version (e.g., TLS 1.3).
    
2. The attacker, acting as a MITM, **intercepts this message** and **modifies it** to indicate that the client only supports TLS 1.0.
    
3. The server receives this altered handshake and **agrees to use TLS 1.0** instead of a newer, more secure version.
    
4. The handshake completes, and both sides communicate using **TLS 1.0**.
    
5. Now that the communication is protected with a **weaker, outdated protocol**, the attacker can:
    
    - Use a **BEAST attack** to recover encrypted cookies
        
    - Use **known exploits** against TLS 1.0 or SSL 3.0
---

 **Consequences**:
- Even though both the client and server support strong encryption, the attacker **forces them to fall back** to weak security.
- The attacker can then **break encryption, steal data, or manipulate traffic**.

---
 **Mitigation**:
- Servers and clients should be configured to **refuse old versions of TLS**.
- Use **TLS 1.2 or TLS 1.3 only**.
- Implement **version negotiation protection** to detect and block downgrade attempts.

---

#### 4. Can SSL/TLS stop MITM?
Yes — **if properly configured**, SSL/TLS can prevent MITM by:

- **Encrypting all traffic** between client and server
    
- **Authenticating server identity** using certificates
    
- **Verifying data integrity**
    

But SSL/TLS can fail if:

- Outdated protocols like TLS 1.0 are used
    
- The client doesn't verify the server certificate
    
- HTTPS is stripped or downgraded

---
## 2. **Record and Application Data Protocols**
After the handshake, this layer handles **secure transmission of actual data** (e.g., HTTP content, emails, files).

 Common vulnerabilities:
	- **BEAST, POODLE, CRIME**: Exploit flaws in block cipher modes, compression, or padding
	- **Padding Oracle Attacks**: Exploit incorrect handling of padding in encrypted messages
	- **Heartbleed**: A bug in OpenSSL that leaks memory content, including private keys and passwords

### **BEAST Attack (Browser Exploit Against SSL/TLS)**
![[BEAST Attack.png]]
#### I.  **What is BEAST?**
**BEAST** stands for **Browser Exploit Against SSL/TLS**  
It is a **real-world attack discovered in 2011 (CVE-2011-3389)** that:
- Targets **TLS 1.0 and SSL 3.0**
- Allows attackers to **decrypt HTTPS traffic**
- Specifically focuses on **breaking cookies, login tokens, or private user data**
---
#### II.  **Why is it possible? (The root problem)**
The BEAST attack exploits a flaw in how **TLS 1.0 uses CBC (Cipher Block Chaining)** for encryption.

CBC encryption works like this:
`Cipher[0] = Encrypt(Plain[0] XOR IV) Cipher[1] = Encrypt(Plain[1] XOR Cipher[0]) Cipher[2] = Encrypt(Plain[2] XOR Cipher[1]) ...`

- Each plaintext block is **XORed with the previous ciphertext block**
- The first block uses a public **IV (Initialization Vector)**
**The issue:** In TLS 1.0, the IV is **not secret** → attacker knows it.
---
#### III.  **How does the BEAST attack work?**
**Goal:**
To decrypt something sensitive (like a session cookie) that the browser is sending encrypted via HTTPS.

 **Setup:**
The attacker must:
- Control JavaScript or applet code in the victim’s browser (via injected script)
- Be in a position to **capture encrypted HTTPS traffic** (MITM = Man-in-the-Middle)

**Step-by-step Attack:**
Let’s say the cookie being sent is:
`Cookie = "Secret"`
That gets encrypted like this:
`C1 = Encrypt("S" XOR IV)`
1. Attacker sees C1 and IV (both are visible)

2. Attacker guesses the first byte of the cookie
He tries:
- Guess = "A" → Encrypt("A" XOR IV) = G1
- If G1 == C1 → Cookie[0] = "A" (correct!)
- Otherwise, try "B", "C", ..., until it matches
👉 This might take **up to 256 tries per byte**

2. Repeat for the next byte
Attacker shifts the plaintext block position and guesses byte 2, then 3...
Eventually, attacker **decrypts the whole cookie**.

---
#### IV. **Example:**

|Guess|XORed with IV|Result (Encrypted)|Match with C1?|
|---|---|---|---|
|"A"|"A" XOR IV|Encrypted result|❌|
|"B"|"B" XOR IV|Encrypted result|❌|
|"S"|"S" XOR IV|Encrypted result|✅ Match!|

→ First byte of cookie = `"S"`

Repeat the same to get `"e"`, `"c"`, `"r"`, etc.

---
#### V. **How to defend against BEAST**

| Defense                                                  | Explanation                                         |
| -------------------------------------------------------- | --------------------------------------------------- |
| **Upgrade to TLS 1.2 or 1.3**                            | These do not use predictable CBC IVs                |
| **Use AES-GCM instead of CBC**                           | GCM mode is not vulnerable to this attack           |
| **Block Java/JavaScript applets from untrusted sources** | Prevent attacker from injecting guess attempts      |
| **Disable TLS 1.0 and SSL 3.0 on servers**               | Prevent vulnerable clients from connecting this way |

---
## 3. **Crypto using PKI (Public Key Infrastructure)**
TLS uses PKI to validate digital certificates and verify the identity of servers (and sometimes clients).

 Common vulnerabilities:
- **Fake or forged certificates**
- **Compromised Certificate Authorities (CA)**
- **Clients not properly verifying server identity** (e.g., not checking hostname)

---
## 4. **Other Application-Specific Vulnerabilities**
These occur when **TLS is used incorrectly or poorly configured** in the application.

 Examples:
- Applications that **don’t validate certificates** properly.
- Transmitting sensitive data **before the handshake is completed**
- **Weak or outdated cipher suites** being used
- **Misconfigured TLS settings** (e.g., not enabling certificate validation)

