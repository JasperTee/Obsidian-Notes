1. **Domain Name System (DNS)**
- DNS translates domain names (like `www.google.com`) into IP addresses.
- DNS is essentially the "phonebook" of the internet.
 2. **DNS Pharming**
- A type of cyber attack where attackers manipulate DNS resolution to redirect users to fake websites, typically to steal information like usernames and passwords.
> **Example:**  
> A user attempts to access a bank’s website but gets redirected to a fraudulent site, resulting in the theft of sensitive data.
# Task 1: Attack by Modifying HOSTS File
### **Purpose**
- Redirect the user (Client VM) to a fake IP address by changing local DNS settings manually.
### **Why it Works**
- The system first checks local configurations before sending DNS queries.
- By modifying local DNS settings, attackers force the system to resolve domain names incorrectly.
### **Steps clearly explained**
1. **Check current DNS settings (Before attack):**
    - On Client VM, run:
    `dig www.netsec-week3.com`
    - This shows correct DNS resolution
2. **Modify local DNS configuration:**
    - Open a terminal on Client VM and edit the interfaces file:
    `sudo nano /etc/network/interfaces`
    - Change the line:
    `dns-nameservers 10.0.2.6`
    to
    `dns-nameservers 10.0.2.7`
    (This points DNS queries to the attacker VM.)
    - Save changes (Ctrl + X, press `Y`, then Enter).
3. **Reboot and re-check DNS resolution:**
    - Reboot Client VM to apply changes.
    - Run again:
    `dig www.netsec-week3.com`
    - You should see a fake IP resolution now.
### **Outcome**
- DNS queries are redirected to the attacker’s IP, causing the client to access the attacker's site instead of the legitimate one.
---
# Task 2: Attack by Spoofing DNS Response
### **Purpose**
- The attacker intercepts DNS queries from a user and sends back fake DNS responses, redirecting users without changing local configurations.
### **How this Attack Works**
- When Client VM sends DNS queries, attacker listens (sniffs) for queries.
- Attacker quickly sends a spoofed response before the legitimate DNS server can reply.
### **Detailed Steps**
1. **Start Wireshark on Client VM:**
    - Open terminal and run:
    `sudo wireshark`
    - Select interface `eth0` and start capturing packets.
2. **Send DNS Query from Client:**
    - Open terminal on Client VM, run:
    `dig www.netsec-week3.com`
    - Capture screenshot of Wireshark showing DNS packets.
3. **Attacker VM Setup (Spoofing using Netwag):**
    - Open terminal on Attacker VM, run:
    `sudo netwag`
    - Select tool:
        `105 Sniff and Send DNS Answers`
    - Configure fields using details from Client's original DNS request (captured by Wireshark).
4. **Perform Spoofing:**
    - Start the spoofing attack from Attacker VM.
    - Immediately run again on Client VM:
        `dig www.netsec-week3.com`
    - Capture Wireshark screenshot showing spoofed DNS response.
5. **Confirming the Attack:**
    - Check Wireshark packets for a fake DNS response from the attacker’s IP.
    - Screenshot packet details clearly showing spoofed DNS reply.
### **Outcome**
- User’s DNS query is answered by attacker first, causing redirection without any configuration changes on Client VM.
---
# Task 3: **DNS Server Cache Poisoning**
### **Purpose**
- Insert fake DNS data directly into the DNS server’s cache, causing long-term redirection.
### **How this Attack Works**
- Normally, a DNS server caches responses. Attackers spoof a fake DNS reply, tricking the server into caching incorrect information.
### **Detailed Steps**
1. **Flush Cache on DNS Server:**
    - On DNS Server VM, run:
    `sudo rndc flush`
2. **Configure Spoofing Attack on Attacker VM (Netwag tool):**
    - Open `Netwag` tool (`sudo netwag`).
    - Select option:
        `105 Sniff and Send DNS Answers`
    - Configure fields:
        - `hostname IP`: Attacker’s IP (`10.0.2.7`)
        - `authns`: Create a fake authoritative DNS (example: `ns.yourname.com`)
        - `authnsip`: `10.0.2.10` (given in instruction)
        - Select correct interface (eth0).
    - Start spoofing attack.
3. **Trigger and Verify Cache Poisoning:**
    - On Client VM, repeatedly execute:
    `dig www.uts.edu.au`
    - Continue until you see the spoofed reply in the ANSWER, AUTHORITY, and ADDITIONAL sections.
    - Capture screenshot clearly showing the cache poisoned response.
### **Outcome**
- DNS Server caches the fake response, misleading all future clients querying the poisoned domain until cache expires.