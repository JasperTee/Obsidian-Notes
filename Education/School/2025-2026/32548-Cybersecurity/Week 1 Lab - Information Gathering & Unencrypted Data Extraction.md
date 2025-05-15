In this lab, you will **learn how attackers can collect sensitive information** from unprotected websites — and how cybersecurity professionals use tools like **Wireshark** and **Zenmap** to spot and understand these vulnerabilities.

---

### **Task 1 – Sniffing Login Details from HTTP Traffic**

#### Concept:

- Websites using **HTTP** (not HTTPS) send data without encryption.
    
- That means **anyone listening** on the network can see the data — including **usernames and passwords**.
    

> Tool: **Wireshark** (a free tool that captures and analyses network traffic)

#### What you do:

- Visit an insecure website: `http://testphp.vulnweb.com/login.php`
    
- Login with any name and password.
    
- Use Wireshark to **find the packet** that contains your login info (look for **POST** request).
    
- Extract the **username and password** from the packet.
    

#### Why this matters:

This shows how easy it is to **steal data from insecure websites** — and why HTTPS is essential.

---

### **Task 2 – Extracting an Image from HTTP Traffic**

#### Concept:

- Just like passwords, **images and files** sent over HTTP can also be intercepted.
    

#### What you do:

- In the same Wireshark capture, look for a packet with the image `logo.gif`.
    
- Export that image from the captured packets.
    

#### Why this matters:

Attackers can steal **visual and media files** from unencrypted traffic, including confidential images.

---

### 🌐 **Task 3 – Information Gathering**

#### Concept:

**Ethical hackers** (good hackers) collect data about a website to find weaknesses.

#### Types of Info Gathering:

- **Passive**: Without interacting with the target (e.g. using public info, like Netcraft)
    
- **Active**: Direct interaction (e.g. scanning servers using Zenmap/Nmap)
    

> Tools:

- **Zenmap/Nmap**: Used to scan a website and find:
    - IP address
    - Server type
    - Operating system
    - Scripting technologies
    - Hosting provider
- **Netcraft**: Web tool to gather similar information about a website’s infrastructure.
    

#### What you do:

Scan `www.uts.edu.au` using Zenmap or Netcraft and answer questions like:

- What is the website’s IP address?
    
- What server is used?
    
- Who owns the IP?
    
- Where is it hosted?
    
- Is the email of the admin exposed?