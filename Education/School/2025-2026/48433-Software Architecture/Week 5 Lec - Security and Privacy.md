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
### 3.3. Tools and Techniques in Threat Modelling
#### 3.3.1. STRIDE Threat Model

**STRIDE** was developed by Microsoft to classify different types of security threats.  
Each letter in STRIDE represents a category of threat, along with the typical **security property it violates**.

---

##### 1. **S – Spoofing Identity**

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

##### 2. **T – Tampering with Data**

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

##### 3. **R – Repudiation**

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

##### 4. **I – Information Disclosure**

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

##### 5. **D – Denial of Service (DoS)**

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

##### 6. **E – Elevation of Privilege**

- **Definition**: Gaining higher access rights than intended.
    
- **Violates**: **Authorization**.
    
- **Examples**:
    
    - A normal user exploits a bug to become an admin.
        
    - Malware running with system-level privileges.
        
- **Mitigations**:
    
    - Principle of Least Privilege (limit permissions).
        
    - Code reviews and patching vulnerabilities.
        
    - Sandboxing applications.
#### 3.3.2. DREAD
##### Definition

**DREAD** is a **quantitative risk assessment model** developed at Microsoft.  
It helps security teams **prioritize threats** by assigning scores based on five criteria. Each criterion is usually scored from **1 to 10**.

The acronym **DREAD** stands for:

- **D – Damage**
    
- **R – Reproducibility**
    
- **E – Exploitability**
    
- **A – Affected Users**
    
- **D – Discoverability**
    

The total score = sum of all five values → higher scores = higher priority to fix.

---

##### Five Criteria in Detail

###### 1. **Damage Potential**

- **Question**: If this threat is exploited, how severe is the damage?
    
- **Low score (1–3)**: Small inconvenience (e.g., logout forced).
    
- **Medium score (4–7)**: Some data lost, service disruption.
    
- **High score (8–10)**: Financial loss, data breach, system-wide compromise.
    
- **Example**: Credit card leak = **10** (severe financial + reputation damage).
    

---

###### 2. **Reproducibility**

- **Question**: How easy is it to reproduce the attack?
    
- **Low score (1–3)**: Attack only works in rare conditions, hard to repeat.
    
- **Medium score (4–7)**: Some effort required but reproducible with skill.
    
- **High score (8–10)**: Works every time with little effort.
    
- **Example**: SQL injection that always works = **9–10**.
    

---

###### 3. **Exploitability**

- **Question**: How easy is it to launch the attack?
    
- **Low score (1–3)**: Requires advanced hardware, specialized access.
    
- **Medium score (4–7)**: Needs some tools and knowledge.
    
- **High score (8–10)**: Can be done with a simple script or widely available tool.
    
- **Example**: Using a free script to brute-force passwords = **8–9**.
    

---

###### 4. **Affected Users**

- **Question**: How many users are impacted if this threat is successful?
    
- **Low score (1–3)**: One or a few users.
    
- **Medium score (4–7)**: A group of users.
    
- **High score (8–10)**: All users of the system.
    
- **Example**: Login vulnerability affecting all customers = **10**.
    

---

###### 5. **Discoverability**

- **Question**: How easy is it for attackers to find the vulnerability?
    
- **Low score (1–3)**: Hidden, very hard to detect.
    
- **Medium score (4–7)**: Needs some scanning and analysis.
    
- **High score (8–10)**: Obvious to anyone (e.g., public form, error messages).
    
- **Example**: A search form vulnerable to SQL injection = **9**.
    

---

##### Example: Online Banking Threat

Threat: **SQL Injection on Login Form**

|Criterion|Score (1–10)|Explanation|
|---|---|---|
|**Damage**|10|Attacker could bypass login and access all accounts.|
|**Reproducibility**|9|The same injection works repeatedly.|
|**Exploitability**|8|Only basic SQL knowledge and a script required.|
|**Affected Users**|10|All bank customers could be affected.|
|**Discoverability**|8|Input fields are public and easily tested.|
|**Total**|**45/50**|Extremely high risk – must fix immediately.|

---

##### Strengths of DREAD

- Gives a **numerical value** → makes prioritization easier.
    
- Helps teams compare different threats objectively.
    
- Easy to explain to non-technical stakeholders (management).
    

##### Limitations

- Scoring can be **subjective** (depends on the assessor).
    
- Microsoft has retired official DREAD use in favor of newer models, but it is still widely used in learning and practice.
#### 3.3.3. Attack Trees

##### Definition

An **Attack Tree** is a diagram that represents different ways an attacker can achieve a malicious goal.

- The **root node** = the attacker’s **main objective**.
    
- The **branches** = the possible **steps, methods, or strategies** used to reach that goal.
    
- Each path shows how smaller sub-goals contribute to the overall attack.
    

Attack Trees were first popularized by **Bruce Schneier (1999)** and are still widely used in threat modelling.

---

##### Structure of an Attack Tree

1. **Root Node** – The ultimate target.
    
    - Example: _“Steal money from online banking system”_.
        
2. **Intermediate Nodes** – Sub-goals or strategies.
    
    - Example: _“Gain access to account”_, _“Tamper with transaction data”_.
        
3. **Leaf Nodes** – Specific attack techniques.
    
    - Example: _“Phishing to get credentials”_, _“Exploit SQL injection”_.
        

Each node can be connected with **logic gates**:

- **OR branch** – attacker only needs _one_ of the sub-goals.
    
- **AND branch** – attacker must complete _all_ sub-goals to succeed.
    

---

##### Example: Online Banking Attack Tree

**Root Goal**: Steal money from a customer’s bank account.

- **Branch 1: Account Compromise**
    
    - (OR) Steal password via phishing.
        
    - (OR) Brute-force weak password.
        
    - (OR) Buy leaked credentials on dark web.
        
- **Branch 2: Transaction Tampering**
    
    - (AND) Intercept traffic with MITM attack.
        
    - (AND) Modify amount before sending to server.
        
- **Branch 3: Exploiting System Vulnerabilities**
    
    - (OR) SQL injection to bypass login.
        
    - (OR) Exploit vulnerable API to escalate privileges.
        
- **Branch 4: Insider Attack**
    
    - (OR) Bribe/corrupt a bank employee.
        
    - (OR) Install malware on employee’s machine.
        

---

##### Benefits of Attack Trees

- **Visualization**: Makes it easy to see all possible attack paths.
    
- **Prioritization**: Helps identify the most likely/impactful paths.
    
- **Defense Planning**: You can design countermeasures for each branch.
    
- **Reusability**: Same attack tree can be adapted for different systems.
    

---

##### How Attack Trees Are Used in Practice

1. **Build the tree**: Define the root goal and branches.
    
2. **Annotate nodes**: Add details such as likelihood, cost, or difficulty.
    
3. **Evaluate risks**: Use the tree to see which paths are most dangerous.
    
4. **Mitigate threats**: Apply security controls to break key attack paths.
    

---

##### Example Mitigation from Attack Tree

- If the tree shows phishing → **Mitigation**: Enable MFA to block stolen passwords.
    
- If the tree shows SQL injection → **Mitigation**: Parameterized queries, input validation.
    
- If the tree shows insider threat → **Mitigation**: Monitoring employee actions, strict access control.
#### 3.3.4. Example: Threat Modelling for an Online Payment System

##### 1. STRIDE Table

|Category (STRIDE)|Threat Example|Security Property Broken|Mitigation|
|---|---|---|---|
|**S – Spoofing**|Attacker logs in using a stolen username/password|Authentication|Multi-Factor Authentication (MFA), session tokens|
|**T – Tampering**|Attacker changes the payment amount from $500 to $50,000|Integrity|TLS encryption, digital signatures, checksums|
|**R – Repudiation**|A customer makes a transaction and later denies it|Accountability|Tamper-proof audit logs, digital signatures|
|**I – Information Disclosure**|Credit card numbers accidentally logged in plaintext|Confidentiality|Encryption (at rest & in transit), log sanitization|
|**D – Denial of Service**|Flooding the payment server with requests to crash it|Availability|Load balancing, DDoS protection, rate limiting|
|**E – Elevation of Privilege**|Normal user exploits a flaw to gain admin rights|Authorization|Role-based access control, patching, code reviews|

---

##### 2. DREAD Scoring

Each threat is scored **1–10** for five criteria: **Damage, Reproducibility, Exploitability, Affected Users, Discoverability**.

|Threat|Damage|Reproducibility|Exploitability|Affected Users|Discoverability|Total (50)|Priority|
|---|---|---|---|---|---|---|---|
|**Spoofing (login with stolen password)**|9|8|8|9|7|**41**|High|
|**Tampering (change payment amount)**|10|7|7|9|6|**39**|High|
|**Repudiation (deny transaction)**|6|6|5|7|5|**29**|Medium|
|**Information Disclosure (credit card leak)**|10|8|7|10|8|**43**|Very High|
|**Denial of Service (DDoS attack)**|7|9|9|8|8|**41**|High|
|**Elevation of Privilege (user → admin)**|9|7|8|9|6|**39**|High|

👉 **Top priorities**:

1. Information Disclosure (**43**)
    
2. Spoofing (**41**)
    
3. Denial of Service (**41**)
    

---

##### 3. Attack Tree

**Goal (Root):** Steal money from the online payment system.

- **Branch 1: Unauthorized Login (Spoofing)**
    
    - Phish user credentials.
        
    - Log in with stolen password.
        
    - Perform fraudulent transaction.
        
- **Branch 2: Transaction Manipulation (Tampering)**
    
    - Intercept traffic between client and server.
        
    - Modify payment amount or account number.
        
    - Send altered request to the server.
        
- **Branch 3: System Exploitation (Elevation of Privilege)**
    
    - Discover vulnerability in payment API.
        
    - Exploit it to escalate privileges.
        
    - Transfer funds from multiple accounts.
        
- **Branch 4: Service Disruption (Denial of Service)**
    
    - Use botnet to flood the payment gateway.
        
    - Make the system unavailable for customers.
        
    - Launch parallel attack during downtime.
        

---

##### Conclusion

- **STRIDE** classified the main threats (Spoofing, Tampering, Repudiation, Info Disclosure, DoS, Elevation).
    
- **DREAD** quantified risk levels → the most critical threats are **Information Disclosure**, **Spoofing**, and **DoS**.
    
- **Attack Trees** visualized possible attack paths → useful for designing layered defenses.
### 3.4. Risk Response Strategies

Once you know the threats, you must decide **how to respond**. There are four main strategies:

---

#### 1. **Fix / Remove Functionality**

- **Definition**: Eliminate the feature or component that creates the risk.
    
- **When to use**: If the feature is not essential or if securing it is too complex.
    
- **Example**:
    
    - A web app has a file upload function, but it’s too risky to secure properly (attackers could upload malware). → Disable file upload.
        
    - Removing weak encryption algorithms (like MD5 or SHA-1) from a system.
        

---

#### 2. **Accept Risk**

- **Definition**: Acknowledge the risk exists but do nothing about it.
    
- **When to use**: If the risk has **low likelihood or low impact**, or the cost of fixing it is higher than the potential damage.
    
- **Example**:
    
    - A small e-commerce website accepts the risk of short outages during heavy traffic instead of paying for expensive DDoS protection.
        
    - A company accepts that some internal printers may not be encrypted because they pose minimal harm.
        

---

#### 3. **Transfer Risk**

- **Definition**: Shift the responsibility of the risk to a third party.
    
- **When to use**: If another entity can manage the risk more effectively.
    
- **Example**:
    
    - Buy **cybersecurity insurance** to cover financial loss from a data breach.
        
    - Use a **cloud provider (AWS, Azure, GCP)** instead of hosting your own servers, transferring some security responsibility to them.
        
    - Hiring a third-party payment processor (Stripe, PayPal) instead of handling credit card data directly.
        

---

#### 4. **Mitigate Risk**

- **Definition**: Reduce the risk by applying **security controls** to lower either likelihood or impact.
    
- **When to use**: For risks that cannot be fully removed but must be reduced to an acceptable level.
    
- **Example**:
    
    - Use HTTPS/TLS to mitigate the risk of data interception.
        
    - Apply input validation to reduce SQL injection risk.
        
    - Implement firewalls and intrusion detection to lower risk of external attacks.
## 4. Secure Software Development Lifecycle (Secure SDLC)

### Definition

The **Secure Software Development Lifecycle (Secure SDLC)** is a process that ensures **security is built into software from the very beginning** (requirements phase) and maintained throughout its lifecycle (maintenance phase).

It extends the traditional SDLC by embedding **security activities** such as threat modelling, secure coding, security testing, and vulnerability management at every step.
### 4.1. Stages of Secure SDLC

#### 1. **Requirements Analysis**

- **Goal**: Identify both **functional requirements** and **security requirements**.
    
- **Activities**:
    
    - Define compliance requirements (e.g., GDPR, HIPAA, PCI-DSS).
        
    - Specify security needs (encryption, authentication, logging).
        
    - Define privacy considerations (data minimization, user consent).
        
- **Example**: A healthcare app must comply with HIPAA → all patient data must be encrypted at rest and in transit.
    

---

#### 2. **Design**

- **Goal**: Incorporate **security principles** into system architecture.
    
- **Activities**:
    
    - Perform **Threat Modelling (STRIDE, Attack Trees)**.
        
    - Define **trust boundaries** and attack surfaces.
        
    - Apply design principles (Least Privilege, Defense in Depth, Secure Defaults).
        
    - Design secure data flows and error handling.
        
- **Example**: In an online banking app, design architecture so that customer data flows only through encrypted channels and cannot bypass authentication checks.
    

---

#### 3. **Development (Implementation)**

- **Goal**: Write code that is **secure by default**.
    
- **Activities**:
    
    - Follow **secure coding standards** (e.g., OWASP Top 10).
        
    - Perform code reviews with security focus.
        
    - Avoid unsafe practices (e.g., string concatenation for SQL queries).
        
    - Use security libraries instead of inventing new cryptography.
        
- **Example**: Use prepared statements or ORM to prevent SQL injection instead of building manual query strings.
    

---

#### 4. **Security Testing**

- **Goal**: Validate the system against security requirements.
    
- **Activities**:
    
    - **Static Application Security Testing (SAST)** – scan source code.
        
    - **Dynamic Application Security Testing (DAST)** – test the running application.
        
    - **Penetration Testing** – simulate real-world attacks.
        
    - Automated tests in CI/CD pipelines.
        
- **Example**: Use automated scanners to detect XSS vulnerabilities in a web app before release.
    

---

#### 5. **Release (Deployment)**

- **Goal**: Ensure the deployed system is hardened and monitored.
    
- **Activities**:
    
    - Harden environments (disable default accounts, enforce secure configs).
        
    - Implement **audit logs** for accountability.
        
    - Create a **rollback plan** in case of deployment failure.
        
    - Use **immutable infrastructure** (no manual changes after deployment).
        
- **Example**: Before deploying an e-commerce app, ensure TLS certificates are installed, and the system logs all admin activities.
    

---

#### 6. **Maintenance (Operations)**

- **Goal**: Keep the system secure after deployment.
    
- **Activities**:
    
    - Monitor logs for anomalies (failed logins, privilege escalations).
        
    - Apply **security patches** and hotfixes regularly.
        
    - Conduct **periodic vulnerability scans** and audits.
        
    - Update threat models as the system evolves.
        
- **Example**: After the Log4j vulnerability was discovered, apply urgent patches to all Java apps in production.
### 4.2. Best Practices in Secure SDLC

- **Shift Left Security** – integrate security checks as early as possible in development (not just before release).
    
- **Automated Security Testing** – embed security tests into CI/CD pipeline.
    
- **Developer Training** – train developers on secure coding techniques.
    
- **Regular Vulnerability Scans** – schedule scanning to catch new risks.
    
- **Third-party/Independent Audits** – verify system with external security experts.
### 4.3. SDLC vs Secure SDLC

#### 1. Traditional SDLC (Software Development Lifecycle)

- **Focus**: Delivering functional features (what the software _does_).
    
- **Approach**:
    
    - Security is often an **afterthought**.
        
    - Teams focus on coding features quickly, then test security near release.
        
- **Drawbacks**:
    
    - Vulnerabilities discovered late → expensive and time-consuming to fix.
        
    - Systems may pass functional testing but still be insecure.
        
- **Example**: A web app is released, then later security testing shows it is vulnerable to SQL injection. Fixing requires redesign of database queries.
    

---

#### 2. Secure SDLC

- **Focus**: Delivering software that is both **functional and secure**.
    
- **Approach**:
    
    - Security integrated at **every stage** (requirements → maintenance).
        
    - Teams use **threat modelling, secure design principles, code reviews, and automated security tests**.
        
- **Benefits**:
    
    - Cheaper to fix issues early (during design or coding).
        
    - Compliance with laws and standards (GDPR, ISO 27001, PCI-DSS).
        
    - Builds customer trust with a secure system.
        
- **Example**: During design, the team identifies SQL injection as a risk and decides to use parameterized queries. This prevents the vulnerability before coding even starts.
    

---

#### 3. Key Differences

|Aspect|Traditional SDLC|Secure SDLC|
|---|---|---|
|**Security timing**|Added at the end, after coding|Embedded from the very beginning|
|**Main focus**|Functionality & delivery speed|Functionality + Security & Privacy|
|**Cost of fixing issues**|High (found late in process)|Lower (caught early)|
|**Testing**|Functional + some security before release|Continuous security testing in every stage|
|**Compliance**|Often reactive (after audit or incident)|Proactive (designed for GDPR, ISO, etc.)|
|**Outcome**|Software works but may have vulnerabilities|Software is secure by design & default|

---

#### 4. Analogy

- **SDLC**: Like building a house and only adding locks after you finish construction. You might realize doors and windows weren’t designed for security.
    
- **Secure SDLC**: Like building a house with locks, cameras, and alarms already included in the blueprint → safer and cheaper than retrofitting later.