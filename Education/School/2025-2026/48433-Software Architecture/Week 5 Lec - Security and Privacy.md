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