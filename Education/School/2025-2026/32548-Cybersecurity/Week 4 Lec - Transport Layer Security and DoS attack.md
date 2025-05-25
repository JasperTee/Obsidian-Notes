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

---
## 2. **Record and Application Data Protocols**
After the handshake, this layer handles **secure transmission of actual data** (e.g., HTTP content, emails, files).

 Common vulnerabilities:
	- **BEAST, POODLE, CRIME**: Exploit flaws in block cipher modes, compression, or padding
	- **Padding Oracle Attacks**: Exploit incorrect handling of padding in encrypted messages
	- **Heartbleed**: A bug in OpenSSL that leaks memory content, including private keys and passwords

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

