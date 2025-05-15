###  **Task 1 - Password Cracking with John the Ripper**
#### **Concept:**  
Passwords stored as hashes can be cracked using tools like John the Ripper (JtR), especially if weak or common.
#### **Tool:**  
John the Ripper (already installed in Cybersec-Server)
#### **What you do:**
- Go to the `Documents` folder, open `mypasswd` (contains hashed passwords).
- Run:
    `john mypasswd`
    → Cracks weak passwords using default mode.
- If some remain, use:
    `john --wordlist=password.lst mypasswd`
    → Uses a dictionary file to guess.
- View cracked results:
    `john --show mypasswd`
- Optional: Try to crack Eric’s password (challenge).
#### **Why this matters:**  
Shows how quickly weak passwords can be broken. Emphasises the need for strong, unique passwords.
---
### **Task 2 - SQL Injection**
#### **Concept:**  
Websites that don’t properly validate user input are vulnerable to **SQL Injection**.  
Attackers can enter SQL code into input fields (like username or password) to bypass login or extract sensitive database info.
#### **Tool:**  
Browser + Vulnerable web app running on `Cybersec-Server`  
(Access via: `http://localhost`)
#### **What you do:**
1. **Try basic injection for error discovery:**
    - In username field: `'`
    - Leave password blank
    - Submit and observe error — this tells you the app is using MySQL and is vulnerable.
2. **Bypass login (unauthorised access):**
    - Username: `' OR '1'='1`
    - Password: anything (or blank)
    - This tricks the SQL query to always return true.
3. **Login using SQL in both fields:**
    - Username: `' OR 'a'='a`
    - Password: `' OR 'b'='b`
    - This bypasses authentication again.
4. **Extract table info and credentials (advanced):**
    - Use SQL payloads (from Netsparker cheat sheet or sechow.com) to:
        - List table names
        - Extract usernames and passwords
        - Log in as a real user
#### **Why this matters:**  
This shows how dangerous poorly coded websites can be.  
Without input validation and secure coding practices, attackers can:
- Log in without knowing passwords
- Access or destroy your database
- Steal personal data
---