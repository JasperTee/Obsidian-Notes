## What is Cryptography?**
**Cryptography** is the science of protecting information by converting it into a form that only authorised people can read and understand.
### Main Goals of Cryptography:
1. **Confidentiality** – Keep data secret from unauthorised users.
2. **Integrity** – Ensure the data hasn't been changed.
3. **Authentication** – Verify who is sending or receiving the data.
4. **Non-repudiation** – Prevent someone from denying they sent a message.
### Types of Cryptography
#### Symmetric Cryptography
![[Symmetric Cryptography.png]]
**Symmetric cryptography** is a method of encryption where the same secret key is used to both encrypt (lock) and decrypt (unlock) a message.
##### How It Works
1. **One Key for Everything:**  
    Both the sender and receiver share one common key. This key must be kept secret. If someone else obtains it, they can read all the messages.
2. **Encryption Process:**
    - The sender starts with a plain message (plaintext).
    - Using the shared secret key, an algorithm transforms this plaintext into a scrambled version called ciphertext.
    - Even if someone intercepts the ciphertext, without the secret key, it appears as gibberish.
3. **Decryption Process:**
    - The receiver, who also has the secret key, uses it to convert the ciphertext back into the original plain message.
    - This ensures that only someone with the correct key can see the message as it was intended.
##### Real-World Examples
- **File Encryption:** When you password-protect a file or folder using software like BitLocker or FileVault, the same key is used to lock and unlock it.
- **Secure Communication:** Many messaging apps use symmetric encryption for speed and efficiency, especially after the initial handshake process in a secure connection is established.
##### Advantages of Symmetric Cryptography
- **Efficiency:** Encryption and decryption can be done quickly, which is useful for encrypting large amounts of data.
- **Simplicity:** Since only one key is involved, the process is straightforward.
##### Disadvantages
- **Key Distribution:** The secret key must be securely shared between the sender and receiver before any encrypted communication can occur. If the key is intercepted during this exchange, security is compromised.
    
- **Scalability:** In environments with many users, managing a unique secret key for every pair of users can become complex.
##### Types of Symmetric Cryptography 
1. **AES (Advanced Encryption Standard)**
- **Key sizes:** 128, 192, or 256 bits
- **Use:** Most widely used today (e.g., Wi-Fi encryption, file encryption)
- **Strength:** Fast, secure, standardised by the US government
---
 2. **DES (Data Encryption Standard)**
- **Key size:** 56 bits
- **Use:** Was widely used in the past (e.g., ATM encryption)
- **Weakness:** Now considered insecure due to short key length
---
 3. **3DES (Triple DES)**
- **Key size:** 112 or 168 bits
- **Use:** Encrypts data three times with DES
- **Strength:** More secure than DES, but slower and now outdated
---
 4. **Blowfish**
- **Key size:** Variable (32 to 448 bits)
- **Use:** Used in some file and disk encryption systems
- **Strength:** Fast and flexible, but newer algorithms (like AES) are preferred
---
5. **RC4, RC5, RC6**
- **RC4:** Was used in SSL and WEP; no longer secure
- **RC5/RC6:** Improved versions; RC6 was a finalist for AES
#### Asymmetric Cryptography
![[Asymmetric Cryptography.png]]
 **Asymmetric encryption** is a method of encrypting data using **two different keys**:
- A **public key** (shared with others)
- A **private key** (kept secret)
The public key **encrypts** the message, and only the private key can **decrypt** it.
##### **How It Works – Step by Step**
1. **Key Pair Generation**
    - A user creates two keys:
        - **Public key** (shared with others) 
        - **Private key** (kept secret)
2. **Encryption**
    - Anyone who wants to send a message uses the **recipient’s public key** to encrypt it.
    - This turns the message into scrambled code called **ciphertext**.
3. **Transmission**
    - The encrypted message (ciphertext) is sent over the internet or stored.
4. **Decryption**
    - Only the person with the **matching private key** can decrypt the ciphertext and read the original message (plaintext).
---
 **Why It’s Secure**
- Even if a hacker gets the public key and the encrypted message, they **cannot decrypt** it without the private key.
    
- The math involved (like factoring huge prime numbers in RSA) is **too hard to solve** without the private key.
---
##### **Real-World Uses**
- **HTTPS websites**: When you see a lock in your browser, it means asymmetric encryption was used to set up a secure connection.
- **Email encryption**: Tools like PGP use it to send private messages.
- **Digital signatures**: Prove that a message was really sent by a person (not fake).
##### **Advantages**
- **No need to share a secret key** beforehand
- Supports **digital signatures** and secure identity verification
##### **Disadvantages**
- **Slower** than symmetric encryption
- Not ideal for encrypting large data (often used to encrypt symmetric session keys instead)
##### Type of Asymmetric Cryptography
**1. RSA (Rivest–Shamir–Adleman)**
- **Most widely used** asymmetric algorithm.
- Based on the difficulty of factoring large prime numbers    
- **Use cases:** Digital signatures, SSL/TLS (HTTPS), secure emails.
- **Key sizes:** 1024, 2048, or 4096 bits.
- **Strengths:** Well-understood, secure with long key sizes.
- **Limitations:** Slower than newer methods; large key sizes.
- **Algorithm:**
	**1. Key Generation**
	- Choose two **prime numbers**: p, q
	- Compute n = p×q
	- Compute z = (p−1) (q−1)
	- Choose a number k such that gcd⁡(k,z) = 1 
	    → This is the **public exponent**
	- Find j such that:  
	    k × j≡ 1 mod  z
	    → This is the **private exponent**
	✅ **Public key** = (n, k)
	✅ **Private key** = (n, j)

---
	 **2. Encryption**
![[RSA Algorithm 1.png]]
	→ Encrypt plaintext P using the **public key**

---
	**3. Decryption**
![[RSA Algorithm 2.png]]
	→ Decrypt ciphertext EE using the **private key**

---
**2. ECC (Elliptic Curve Cryptography)**
- Based on the mathematics of **elliptic curves**.
- Provides **strong security with shorter keys** (e.g., ECC-256 ≈ RSA-3072).
- **Use cases:** Mobile apps, IoT devices, cryptocurrency wallets.    
- **Strengths:** Fast, lightweight, uses less power and memory.
- **Limitations:** More complex math, harder to implement correctly.
---
 **3. ElGamal**
- Based on the Diffie–Hellman key exchange concept.
- Supports both **encryption** and **digital signatures**.
- **Use cases:** Secure data transfer, GPG/PGP systems.
- **Strengths:** High security, adaptable.
- **Limitations:** Produces longer ciphertext; slower than RSA.
---
**4. Diffie–Hellman (DH)**
- Not for encryption itself, but used for **secure key exchange**.
- Allows two parties to create a **shared secret** over an insecure channel.
- **Use cases:** TLS handshakes, VPNs.
- **Strengths:** Foundational algorithm for secure key setup.    
- **Limitations:** Vulnerable to man-in-the-middle if not authenticated.
---
**5. DSA (Digital Signature Algorithm)**
- Designed for **digital signatures**, not encryption.
- Standardised by the U.S. government.
- **Use cases:** Verifying sender identity, secure software updates.
- **Strengths:** Good for authentication.
- **Limitations:** Slower signature verification than RSA or ECC.
## **Vulnerabilities in public key cryptography**
### 1. **Man-in-the-Middle (MITM) Attack**
- **What it is:** An attacker secretly intercepts and possibly alters communication between two parties.
- **Example:** Alice thinks she's sending her encrypted message to Bob, but it's intercepted by an attacker who reads or modifies it before forwarding.
- **Defence:** Use digital certificates, HTTPS, and certificate authorities (CA).
---
### 2. **Side-Channel Attack**
- **What it is:** Instead of breaking the encryption itself, attackers observe physical signals (like timing, power usage, or electromagnetic leaks) from the device to deduce private keys.
- **Example:** Measuring how long it takes your device to perform encryption to guess the private key.
- **Defence:** Use constant-time algorithms and hardware protections.
---
### 3. **Chosen-Ciphertext Attack**
- **What it is:** The attacker tricks the system into decrypting selected ciphertexts and uses the results to gain information about the private key.
- **Example:** Sending modified encrypted messages and observing how the system responds to infer the original data.
- **Defence:** Use secure padding schemes (e.g., OAEP in RSA).
---
### 4. **Key Management Attack**
- **What it is:** Attackers exploit weaknesses in how cryptographic keys are generated, stored, distributed, or destroyed.
- **Example:** A weak random number generator produces predictable keys.
- **Defence:** Use secure key storage and strong key management protocols.
---
### 5. **Brute Force Attack**
- **What it is:** The attacker tries all possible keys until the correct one is found.
- **Example:** Trying billions of key combinations to decrypt a message.
- **Defence:** Use long and complex keys (e.g., RSA-2048 or ECC-256).
## **Public Key Infrastructure (PKI)?**
**PKI** is a system that **manages, issues, and verifies digital certificates** to help people, websites, and devices **trust each other** when exchanging information securely over the internet.
   X.509 standard is used for specifying format of Public Key Certificates
![[Public Key Infrastructure.png]]
---
### **Key Components of PKI**
#### 1. **Certificate Authority (CA)**
a trusted party, responsible for verifying the identity of users, and then bind the verified identity to a public keys.
#### 2. **Digital Certificate**
- A file that proves a **public key belongs to a specific person, website, or organisation**
- Includes:
    - Owner's name (domain/organisation)
    - Public key
    - Expiration date
    - CA’s name
    - Digital signature from CA

#### 3. **Registration Authority (RA)**
- Helps CA verify identities before issuing certificates (like an assistant to the CA)
#### 4. **Certificate Revocation Mechanisms**
- **CRL (Certificate Revocation List):** A list of certificates that were revoked
- **OCSP (Online Certificate Status Protocol):** A fast way to check if a certificate is still valid
---
### **How PKI Works – Step-by-Step Example**
1. A website owner (e.g., example.com) creates a **key pair**: public key + private key
2. They send a **CSR (Certificate Signing Request)** to a CA, including their public key
3. The CA **verifies** the owner’s identity
4. If valid, the CA **issues a digital certificate**, signed with the CA’s private key
5. The certificate is installed on the website
6. When a user visits `https://example.com`:
    - Their browser checks if the certificate is **signed by a trusted CA**
    - If it’s valid, a **secure (HTTPS) connection** is established
---
### **Why is PKI Important?**
- **Protects online communication:** Used in HTTPS, email, VPN, etc.
- **Prevents identity spoofing:** Confirms the real owner of a website or public key
- **Enables trust:** Browsers and users trust the identity because it’s verified by a CA
- **Supports encryption + authentication**