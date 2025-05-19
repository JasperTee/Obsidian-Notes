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
1. **Client Hello**
    - The client sends a message listing the cryptographic algorithms it supports.
2. **Server Hello + Certificate**
    - The server replies with:
        - A selected algorithm
        - A **digital certificate** containing its **public key**
3. **Certificate Verification**
    - The client checks if the certificate is valid (signed by a trusted Certificate Authority, not expired, domain matches, etc.).
4. **Key Exchange**
    - The client generates a random **pre-master secret**.
    - The client encrypts it using the server’s **public key** and sends it to the server.
5. **Decryption**
    - The server uses its **private key** to decrypt the pre-master secret.
6. **Master Secret**
    - Both client and server now compute the same **master secret** from the pre-master secret.
7. **Session Keys**
    - From the master secret, both sides generate **session keys**:
        - Encryption keys
        - Message Authentication Code (MAC) keys
        - Initialization Vectors (IVs), depending on the algorithm
8. **Finished Messages**
    - Each side sends a final message encrypted with the session key, confirming that future messages will be encrypted.
9. **Secure Communication**
    - Both parties use the session keys to encrypt and decrypt the actual data during the session.
---
## Why Use So Many Keys?

 **Asymmetric encryption (public/private key)**
	- Used **only during the handshake**
	- Secure but **slow and resource-intensive**
	
**Symmetric encryption (session keys)**
	- Used for the actual data transfer
	- **Fast and efficient**
	
So, TLS uses **public/private keys to securely agree on a shared secret**, then switches to **session keys** for efficient encryption.
