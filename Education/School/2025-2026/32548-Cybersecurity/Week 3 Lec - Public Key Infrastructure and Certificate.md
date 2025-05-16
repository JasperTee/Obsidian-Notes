## What is Cryptography?**
**Cryptography** is the science of protecting information by converting it into a form that only authorised people can read and understand.
### Main Goals of Cryptography:
1. **Confidentiality** – Keep data secret from unauthorised users.
2. **Integrity** – Ensure the data hasn't been changed.
3. **Authentication** – Verify who is sending or receiving the data.
4. **Non-repudiation** – Prevent someone from denying they sent a message.
### Types of Cryptography
#### Symmetric cryptography
![[Symmetric Cryptography.png]]
**Symmetric cryptography** is a method of encryption where the same secret key is used to both encrypt (lock) and decrypt (unlock) a message.
### How It Works:
1. **One Key for Everything:**  
    Both the sender and receiver share one common key. This key must be kept secret. If someone else obtains it, they can read all the messages.
    
2. **Encryption Process:**
    
    - The sender starts with a plain message (plaintext).
        
    - Using the shared secret key, an algorithm transforms this plaintext into a scrambled version called ciphertext.
        
    - Even if someone intercepts the ciphertext, without the secret key, it appears as gibberish.
        
3. **Decryption Process:**
    
    - The receiver, who also has the secret key, uses it to convert the ciphertext back into the original plain message.
        
    - This ensures that only someone with the correct key can see the message as it was intended.
        

### Real-World Examples:

- **File Encryption:** When you password-protect a file or folder using software like BitLocker or FileVault, the same key is used to lock and unlock it.
    
- **Secure Communication:** Many messaging apps use symmetric encryption for speed and efficiency, especially after the initial handshake process in a secure connection is established.
    

### Advantages of Symmetric Cryptography:

- **Efficiency:** Encryption and decryption can be done quickly, which is useful for encrypting large amounts of data.
    
- **Simplicity:** Since only one key is involved, the process is straightforward.
    

### Disadvantages:

- **Key Distribution:** The secret key must be securely shared between the sender and receiver before any encrypted communication can occur. If the key is intercepted during this exchange, security is compromised.
    
- **Scalability:** In environments with many users, managing a unique secret key for every pair of users can become complex.