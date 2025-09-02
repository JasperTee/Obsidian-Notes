## 1. Security and Privacy Requirement
### 1.1. CIA Triad

#### a. Confidentiality

- **Definition**: Ensures that information is only accessible to **authorized individuals** and protected from unauthorized access.
    
- **Risks if violated**:
    
    - Credit card or banking information leaks.
        
    - Exposure of personal data such as phone numbers, medical records, or email.
        
- **How it is implemented**:
    
    - **Authentication**: usernames/passwords, OTPs, Multi-Factor Authentication (MFA).
        
    - **Authorization**: Access Control Lists (ACLs), Role-Based Access Control (RBAC).
        
    - **Encryption**:
        
        - Symmetric (AES).
            
        - Asymmetric (RSA).
            
        - Secure protocols like HTTPS (TLS/SSL).
            
- **Real-world example**:
    
    - When you log into Gmail, only you can access your emails. Google enforces confidentiality with passwords + MFA.
        

---

#### b. Integrity

- **Definition**: Ensures that information is **accurate and unaltered**, protecting it from unauthorized modification or tampering.
    
- **Risks if violated**:
    
    - Hackers changing a $500 transfer to $5000.
        
    - Attackers modifying system logs to erase evidence.
        
- **How it is implemented**:
    
    - **Hashing**: algorithms like SHA-256, SHA-3, MD5 (to verify data hasn’t been altered).
        
    - **Digital Signatures**: ensure authenticity and integrity of the sender’s data.
        
    - **Checksums**: used when downloading files to confirm they are intact.
        
- **Real-world example**:
    
    - Software vendors provide a SHA-256 checksum for downloads. If the downloaded file’s hash doesn’t match, integrity has been compromised.
        

---

#### c. Availability

- **Definition**: Ensures that systems, services, and data are **accessible when needed** by authorized users.
    
- **Risks if violated**:
    
    - A DDoS attack makes a banking website unavailable.
        
    - Company email servers go down, halting communication.
        
- **How it is implemented**:
    
    - **Redundancy**: backup servers, failover systems.
        
    - **Load Balancing**: distribute workload across servers.
        
    - **Backup & Disaster Recovery**: frequent data backups and recovery plans.
        
    - **Regular maintenance and patching** to fix vulnerabilities.
        
- **Real-world example**:
    
    - Facebook and YouTube run multiple data centers worldwide so users can always access services, even if one center fails.
### 1.2. Regulatory Requirements and International Standards

#### a. GDPR (General Data Protection Regulation – European Union)

-  **Scope**: Applies to any organization (worldwide) that processes personal data of **EU residents**.
    
-  **Key Principles**:
    
    - **Privacy by design & by default** – data protection must be built into systems from the start.
        
    - **Consent** – personal data can only be processed with **clear and informed consent**.
        
    - **Breach notification** – organizations must report a data breach within **72 hours**.
        
    - **Data subject rights** – individuals have the right to:
        
        - Access their personal data.
            
        - Request correction or deletion.
            
        - Restrict or object to processing.
            
- **Example**: In 2021, Amazon was fined €746 million for violating GDPR.
    

---

#### b. NIST Cybersecurity Framework (United States)

- **Purpose**: A flexible framework for improving **cybersecurity risk management**.
    
- **Five Core Functions**:
    
    1. **Identify** – asset management, risk assessment.
        
    2. **Protect** – access control, encryption, employee training.
        
    3. **Detect** – continuous monitoring, intrusion detection systems (IDS).
        
    4. **Respond** – incident response planning, communication strategy.
        
    5. **Recover** – disaster recovery, system restoration, lessons learned.
        
- **Example**: A US bank may adopt NIST CSF to protect against cyberattacks and report compliance to regulators.
    

---

#### c. ISO/IEC 27001 (International Standard)

- **Definition**: An **international standard** for establishing an **Information Security Management System (ISMS)**.
    
- **Key Requirements**:
    
    - Build a **framework (ISMS)** to manage security across the organization.
        
    - **Risk assessment** – identify and prioritize threats.
        
    - **Implement security controls** – physical, technical, and organizational safeguards.
        
    - **Continuous improvement** – audit and update security practices regularly.
        
- **Benefits**:
    
    - Provides credibility to customers/partners.
        
    - Helps organizations reduce security incidents.
        
- **Example**: A cloud provider like AWS or Azure is ISO/IEC 27001 certified to prove their security governance.
    

---

#### d. COPPA (Children’s Online Privacy Protection Act – United States)

- **Scope**: Applies to websites and online services **targeting children under 13** in the US.
    
- **Key Requirements**:
    
    - **Parental consent** before collecting children’s data (name, email, location, etc.).
        
    - **Privacy policy disclosure** – must clearly explain what data is collected and how it is used.
        
    - **Data minimization** – collect only necessary data.
        
    - **Parental rights** – parents can review or delete their child’s data.
        
- **Example**: YouTube was fined $170 million in 2019 for violating COPPA by collecting data on children without parental consent.
    

---

#### Summary (Comparison)

|Standard/Law|Region|Focus|Key Requirements|
|---|---|---|---|
|**GDPR**|EU (global impact)|Personal data & privacy|Consent, breach notification, right to access/delete|
|**NIST CSF**|USA (global reference)|Cybersecurity risk management|Identify, Protect, Detect, Respond, Recover|
|**ISO/IEC 27001**|International|Information Security Management System|ISMS framework, risk assessment, continuous improvement|
|**COPPA**|USA|Child online privacy (<13 yrs)|Parental consent, data minimization, parental rights|
## 2. Security Design Principles (10 Principles)

### 1. Least Privilege

- **Definition**: Every user, process, or system should have the **minimum access rights** needed to perform their job.
    
- **Why**: Reduces damage if an account is compromised.
    
- **Example**:
    
    - A cashier in a bank’s system can only access daily transactions, not customer full database.
        
    - In Linux, a normal user cannot run `sudo` unless explicitly permitted.
        

---

### 2. Separate Responsibilities (Separation of Duties)

- **Definition**: Split critical tasks among multiple people/systems so no single entity has full control.
    
- **Why**: Prevents abuse of power and insider threats.
    
- **Example**:
    
    - In finance, one person requests a payment, another person approves it.
        
    - Developers write code, but a separate QA team reviews and deploys.
        

---

### 3. Trust Cautiously

- **Definition**: Do not blindly trust inputs, external systems, or third-party libraries.
    
- **Why**: Attackers can exploit unvalidated trust.
    
- **Example**:
    
    - Always validate user input in a web form to prevent SQL injection.
        
    - Verify digital signatures of external libraries before using them.
        

---

### 4. Simplest Solution Possible

- **Definition**: Design systems as simple as possible (but no simpler).
    
- **Why**: Complexity creates more potential vulnerabilities.
    
- **Example**:
    
    - Use a simple authentication mechanism instead of a custom, complex one.
        
    - Avoid unnecessary features that expand the attack surface.
        

---

### 5. Audit Sensitive Events

- **Definition**: Log and monitor security-relevant activities.
    
- **Why**: Enables detection and investigation of incidents.
    
- **Example**:
    
    - Logging failed login attempts.
        
    - Monitoring admin account activity.
        

---

### 6. Fail Securely & Use Secure Defaults

- **Definition**: When a system fails, it should fail in a secure state. Default configurations should always be safe.
    
- **Why**: Prevents attackers from exploiting crashes or weak defaults.
    
- **Example**:
    
    - If authentication server is down, system should deny access (fail closed), not grant access (fail open).
        
    - Default firewall setting = block all, only allow what is explicitly permitted.
        

---

### 7. Never Rely on Obscurity

- **Definition**: Security should not depend on keeping implementation details secret.
    
- **Why**: Attackers can eventually discover the hidden details.
    
- **Example**:
    
    - Hiding an admin page at `/secret_admin` is not real security.
        
    - Real security comes from authentication and authorization, not “hiding URLs”.
        

---

### 8. Defence in Depth

- **Definition**: Use **multiple layers of security controls** to protect systems.
    
- **Why**: If one layer is bypassed, others still protect the system.
    
- **Example**:
    
    - A web app uses HTTPS (encryption), input validation (application layer), WAF (network layer), and firewalls (infrastructure).
        
    - Banks use PIN + card + OTP for transactions.
        

---

### 9. Never Invent Security Technology

- **Definition**: Avoid creating your own encryption or security mechanisms. Use well-tested, standard solutions.
    
- **Why**: Custom-made security is often weak and untested.
    
- **Example**:
    
    - Do not invent your own password hashing function. Use bcrypt, scrypt, or Argon2.
        
    - Use TLS/SSL for secure communication instead of building a custom protocol.
        

---

### 10. Secure the Weakest Link

- **Definition**: Attackers will target the easiest, weakest point in your system.
    
- **Why**: A chain is only as strong as its weakest link.
    
- **Example**:
    
    - If your cloud is well-secured but employees use weak passwords → system is still vulnerable.
        
    - Attackers often target third-party vendors with weaker security to reach the main company.
## 3. Threat Modelling (Mô hình hóa mối đe dọa)

### 3.1. Definition

- **Threat Modelling** is a structured process to **identify, analyze, and mitigate potential security threats** in a system.
    
- It helps answer:
    
    1. **What are you building?** – Understand the system, data flows, components.
        
    2. **What can go wrong?** – Identify threats, vulnerabilities.
        
    3. **What should you do about it?** – Propose mitigation strategies.
        
    4. **Did you do a good job?** – Review and refine.
### 3.2. Key Concepts

#### a. Entry Points

- Places where external users or systems interact with your system.
    
- **Examples**: Login form, API endpoint, admin dashboard.
    

#### b. Trust Boundaries

- Boundaries where data changes ownership or privilege level.
    
- **Examples**:
    
    - From user → web application.
        
    - From application → database.
        
    - From internal system → third-party API.
        

#### c. Data Flow

- Understanding how information moves between components.
    
- **Example**: User login → Web app → Database → Authentication result returned.
    

#### d. Attack Surface

- All possible points where attackers can attempt to exploit the system.
    
- **Examples**: Open ports, API calls, user input fields, forgotten admin pages.
### 3.3. STRIDE Threat Model

**STRIDE** was developed by Microsoft to classify different types of security threats.  
Each letter in STRIDE represents a category of threat, along with the typical **security property it violates**.

---

#### 1. **S – Spoofing Identity**

- **Definition**: Pretending to be someone/something else to gain access.
    
- **Violates**: **Authentication**.
    
- **Examples**:
    
    - Logging in with stolen usernames and passwords.
        
    - Attacker forges an IP address to impersonate a trusted machine.
        
    - Fake email (phishing) pretending to be from a bank.
        
- **Mitigations**:
    
    - Strong authentication (MFA, biometrics).
        
    - Unique session tokens.
        
    - Certificates and digital signatures.
        

---

#### 2. **T – Tampering with Data**

- **Definition**: Unauthorized modification of data, either in storage or during transmission.
    
- **Violates**: **Integrity**.
    
- **Examples**:
    
    - Changing the amount in a bank transfer request from $500 to $5000.
        
    - Altering a configuration file on the server.
        
- **Mitigations**:
    
    - Hashing and checksums to verify integrity.
        
    - Encryption (so modified data becomes invalid).
        
    - Write protection and access controls.
        

---

#### 3. **R – Repudiation**

- **Definition**: Denying having performed an action, when there’s no way to prove otherwise.
    
- **Violates**: **Non-repudiation** (accountability).
    
- **Examples**:
    
    - A customer claims they never authorized a money transfer.
        
    - A system admin deletes logs and denies doing it.
        
- **Mitigations**:
    
    - Digital signatures.
        
    - Secure, tamper-proof logging.
        
    - Audit trails that cannot be erased.
        

---

#### 4. **I – Information Disclosure**

- **Definition**: Exposing information to people who are not authorized to see it.
    
- **Violates**: **Confidentiality**.
    
- **Examples**:
    
    - A web app error message showing database structure.
        
    - Unencrypted credit card numbers stored in logs.
        
    - Data breach exposing personal information.
        
- **Mitigations**:
    
    - Data encryption (at rest and in transit).
        
    - Access control and permissions.
        
    - Masking sensitive information in error messages.
        

---

#### 5. **D – Denial of Service (DoS)**

- **Definition**: Making a system or service unavailable to legitimate users.
    
- **Violates**: **Availability**.
    
- **Examples**:
    
    - Flooding a website with fake traffic (DDoS).
        
    - Locking user accounts by entering wrong passwords repeatedly.
        
- **Mitigations**:
    
    - Rate limiting and throttling.
        
    - Load balancing, failover servers.
        
    - DDoS protection services (e.g., Cloudflare, AWS Shield).
        

---

#### 6. **E – Elevation of Privilege**

- **Definition**: Gaining higher access rights than intended.
    
- **Violates**: **Authorization**.
    
- **Examples**:
    
    - A normal user exploits a bug to become an admin.
        
    - Malware running with system-level privileges.
        
- **Mitigations**:
    
    - Principle of Least Privilege (limit permissions).
        
    - Code reviews and patching vulnerabilities.
        
    - Sandboxing applications.