## What is Cryptography?
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
###### 1. **AES (Advanced Encryption Standard)**
- **Key sizes:** 128, 192, or 256 bits
- **Use:** Most widely used today (e.g., Wi-Fi encryption, file encryption)
- **Strength:** Fast, secure, standardised by the US government
---
 ###### 2. **DES (Data Encryption Standard)**
- **Key size:** 56 bits
- **Use:** Was widely used in the past (e.g., ATM encryption)
- **Weakness:** Now considered insecure due to short key length
---
 ###### 3. **3DES (Triple DES)**
- **Key size:** 112 or 168 bits
- **Use:** Encrypts data three times with DES
- **Strength:** More secure than DES, but slower and now outdated
---
 ###### 4. **Blowfish**
- **Key size:** Variable (32 to 448 bits)
- **Use:** Used in some file and disk encryption systems
- **Strength:** Fast and flexible, but newer algorithms (like AES) are preferred
---
###### 5. **RC4, RC5, RC6**
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
###### **1. RSA (Rivest–Shamir–Adleman)**
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
###### **2. ECC (Elliptic Curve Cryptography)**
- Based on the mathematics of **elliptic curves**.
- Provides **strong security with shorter keys** (e.g., ECC-256 ≈ RSA-3072).
- **Use cases:** Mobile apps, IoT devices, cryptocurrency wallets.    
- **Strengths:** Fast, lightweight, uses less power and memory.
- **Limitations:** More complex math, harder to implement correctly.
---
 ###### **3. ElGamal**
- Based on the Diffie–Hellman key exchange concept.
- Supports both **encryption** and **digital signatures**.
- **Use cases:** Secure data transfer, GPG/PGP systems.
- **Strengths:** High security, adaptable.
- **Limitations:** Produces longer ciphertext; slower than RSA.
---
###### **4. Diffie–Hellman (DH)**
- Not for encryption itself, but used for **secure key exchange**.
- Allows two parties to create a **shared secret** over an insecure channel.
- **Use cases:** TLS handshakes, VPNs.
- **Strengths:** Foundational algorithm for secure key setup.    
- **Limitations:** Vulnerable to man-in-the-middle if not authenticated.
---
###### **5. DSA (Digital Signature Algorithm)**
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
A **Certificate Authority** is a **trusted organisation** that is responsible for:
- Verifying identities
- Issuing digital certificates
- Helping build trust online
Think of a CA like a **passport office**. It checks your identity and gives you a passport (certificate), which others trust because it comes from a known authority.
---
##### **Core Functions of a CA**

 ###### 1. **Verify the Subject**
- Before issuing a certificate, the CA checks whether:
    - You own the domain
    - Or you represent the person or company in the certificate
- This step ensures that the certificate is not issued to someone pretending to be someone else
---
 ###### 2. **Signing Digital Certificates**
- Once verified, the CA **digitally signs** the certificate
- It uses its **private key** to create a digital signature on the certificate
- This signature:
    - Confirms that the certificate came from the CA
    - **Cannot be modified** once applied
- Anyone (like a browser) can verify this signature using the **CA’s public key**
---
 ###### 3. **Being a Certificate Authority**
A CA must:
- **Issue certificates**: After validation, it generates a certificate and signs it
- **Provide a way to request certificates**: Often done through a Certificate Signing Request (CSR)
- **Support setup**: Users install the certificate on their web servers to enable HTTPS
##### **Real World CAs**
![[Real World CAs.png]]
###### **1. Root CA (Top Level)**
- This is the **most trusted authority**.
- It is pre-installed in operating systems and browsers (e.g., Mozilla, Chrome, Windows).
- **Signs and authorises intermediate CAs**.
- Root CA signs its own certificate — called a **self-signed certificate**.
---
###### **2. Intermediate CAs (Middle Level)**
- These are **issued and trusted by the Root CA**.
- They **sign and issue certificates** to:
    - Domain owners
    - Other lower-level CAs (sub-CAs)
- Help reduce the risk to the Root CA (the Root CA can remain offline for extra security).
---
###### **3. Sub CAs**
- Optional lower-level authorities that are authorised by an intermediate CA.
- Further delegate certificate issuance.
- Still follow strict policies and trace back to the Root CA through the chain.
---
###### **4. Domain Owners (End Entities)**
- These are the people or companies that **request and receive digital certificates**.
- Examples:
    - Website owners (e.g., `example.com`)
    - Email servers
- The certificate they get is signed by a **Sub CA or Intermediate CA**, not directly by the Root CA
#### 2. **Digital Certificate**
- A file that proves a **public key belongs to a specific person, website, or organisation**
- Includes:
    - Owner's name (domain/organisation)
    - Public key
    - Expiration date
    - CA’s name
    - Digital signature from CA
##### **How Digital Certificates Works**
**1. Signing the Message (Sender’s side)**
Let’s say **Alice** wants to send a message to **Bob**.
1. Alice writes the message (M).
2. She uses a **hash function** (like SHA-256) to create a **message digest** (a fixed-size summary of M).
3. Alice **encrypts the digest** with her **private key** → this is the **digital signature**.
4. Alice sends both the message and the signature to Bob.
---
 **2. Verifying the Signature (Receiver’s side)**
1. Bob receives the message and the signature.
2. Bob uses **Alice’s public key** to **decrypt the signature**, revealing the original message digest.
3. Bob hashes the received message himself.
4. If the two digests match, then:
    - The message was **not changed**
    - The message was **definitely from Alice**
    ---
##### **Type of Digital Certificates**
![[Type of Digital Certificates.png]]
**1. Domain Validated (DV) Certificates**
 **What it is:**
- The **most common and basic** type of certificate.
- Used mainly for **small websites**, blogs, or personal pages.
 **What is verified:**
- The Certificate Authority (CA) only checks **if the applicant controls the domain name**.
 **How it’s verified:**
- Through **Domain Control Validation (DCV)**:
    - Using the **WHOIS database** (checks domain ownership info)
    - CA may send a confirmation email to the domain owner
    - Or ask the applicant to upload a file to the website
    - Or check a DNS record (TXT or CNAME)
 **Pros:**
- Fast and cheap
- Easy to issue (automated)
 **Cons:**
- **No business information is shown**
- Less trustworthy for e-commerce or financial services
---
 **2. Organisational Validated (OV) Certificates**
 **What it is:**
- A **moderate-level** certificate that includes organisation identity.
- Used by **small to medium-sized companies**.
 **What is verified:**
Before issuing, the CA checks:
- Domain control (same as DV)
- The applicant’s **legal identity and address**
- Proof that the person is **linked to the organisation**
- Organisation’s address and WHOIS record
- Phone callback to a **verified company phone number**
 **Pros:**
- More **trustworthy than DV**
- **Displays company information** in the certificate details
**Cons:**
- Not as commonly used as DV
- Requires more manual verification steps (takes longer)
---
 **3. Extended Validation (EV) Certificates**
 **What it is:**
- The **highest level** of digital certificate.
- Used by **banks, government websites, large businesses**.
 **What is verified:**
CA performs very strict checks, including:
- Domain control
- The **identity, authority, and signature** of the individual requesting it
- The organisation’s **physical address and phone number**
- Proof of **legal existence** (e.g. business registration)
- Proof of **operational status**
- Check that the company is in **good legal standing**
 **Pros:**
- **Displays company name in browser address bar** (some browsers)
- Offers the **strongest trust** and customer confidence
- Ideal for sites handling sensitive data
 **Cons:**
- Takes more time and documents to issue
- More expensive than DV or OV
---
#### 3. **Registration Authority (RA)**
- Helps CA verify identities before issuing certificates (like an assistant to the CA)
#### 4. **Certificate Revocation Mechanisms**
- **CRL (Certificate Revocation List):** A list of certificates that were revoked
- **OCSP (Online Certificate Status Protocol):** A fast way to check if a certificate is still valid
---
### **How PKI Works**
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
 ####**Why Attack PKI?**
PKI is the trust backbone of the internet. If attackers compromise it, they can:
- Impersonate trusted websites
- Decrypt secure traffic
- Launch man-in-the-middle (MITM) attacks
---
### **Real Case-Study: Attacks on PKI**
#### **Attacks on PKI and CAs**
a. **DigiNotar Breach (2011)**
- Several CA servers of DigiNotar (including government-related) were hacked.
- The attacker **stole DigiNotar’s private key**.
- **531 fake certificates** were issued (e.g., for Google domains).
- Enabled MITM attacks: attackers could intercept Gmail traffic.
- Result: DigiNotar collapsed and lost trust globally.
---
 b. **Comodo Attack (2011)**
- A regional partner of Comodo was compromised.
- **9 fraudulent certificates** were issued for major websites (e.g., `addons.mozilla.org`).
- This attack bypassed normal certificate validation.
- Affected **trust in browsers like Firefox**.
---
 c. **ANSSI Hack (2013)**
- A French government CA (ANSSI) issued **unauthorised certificates**.
- Fake certificates were used to **intercept Google users’ traffic**.
- Google and Mozilla blocked the certs immediately.
---
 d. **Let’s Encrypt Phishing (2021)**
- Attackers exploited validation to obtain certificates for lookalike domains.
- Example: domains like `xn--pple-43d.com` looked like `apple.com` using Unicode.
- Used in phishing attacks where the **browser displayed a valid lock**, misleading users.
---
#### **Attacks on Algorithms**
Digital certificates rely on **hash functions** and **signatures**. If those break, so does PKI.
a. **SHA-1 Collision Attacks**
- In 2017, Google’s SHAttered attack showed that **two files could have the same SHA-1 hash**.
- Certificates using SHA-1 could be **forged**.
- Fix: Use SHA-256 or stronger hash functions.
b. **MD5 Attacks**
- Earlier CAs used MD5. Attackers could **generate two certificates with the same hash**.
- Some fake CAs were created this way before it was banned.
---
#### **User Confirmation Attacks**
Sometimes the problem is **not technical**, but how software verifies certificates:
a. **Common Name Mismatch**
- Some apps don’t check if the **domain in the certificate matches the actual website**.
- Leads to **MITM success** if users accept any certificate blindly.
b. **Unicode Domain Attacks**
- Example: `xn--80ak6aa92e.com` (Cyrillic letters) appears as `apple.com` in some browsers.
- Attacker gets a valid certificate for it → tricks users into thinking it’s the real Apple site.
---
#### **MITM via Proxy Certificate**
- A proxy installs its **own CA certificate** in the user's trusted store.
- It then intercepts HTTPS traffic and generates **fake but trusted certificates** for every site.
- This is how **some corporate firewalls** or malware inspect encrypted traffic.