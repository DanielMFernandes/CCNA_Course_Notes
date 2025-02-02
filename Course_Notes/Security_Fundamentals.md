# 48. SECURITY FUNDAMENTALS

KEY SECURITY CONCEPTS

WHY SECURITY?

What is the purpose / goal of security in an enterprise ?

- The principles of the CIA TRIAD form the foundation of security:
    - CONFIDENTIALITY
        - Only authorized users should be able to access data
        - Some information / data is public and can be accessed by anyone
        - Some information / data is secret and should be only be accessed by specific people
    - INTEGRITY
        - Data should not be tampered with (modified) by unauthorized users
        - Data should be correct and authentic
    - AVAILABILITY
        - The network / security should be operational and accessible to authorized users

Attackers can threaten the CONFIDENTIALITY, INTEGRITY, and AVAILBILITY of an enterprise’s systems and information

---

VULNERABILITY, EXPLOIT, THREAT, MITIGATION

- A VULNERABILITY is any potential weakness that can compromise the CIA of a system
    - A potential weakness isn’t a problem in its own
- An EXPLOIT is something that can potentially be used to exploit the vulnerability
    - Something than can *potentially* be used as an exploit isn’t a problem on it’s own.

- A THREAT is the potential of a VULNERABILITY to be EXPLOITED
    - A hacker EXPLOITING a VULNERABILITY in your system is a THREAT

- A MITIGATION TECHNIQUE is something that can protect against threats
    - Should be implemented everywhere a VULNERABILITY can be EXPLOITED:
        - Client Devices
        - Servers, Switches, Routers, Firewalls
        - etc.

💡 NO SYSTEM IS PERFECTLY SECURE!


---

COMMON ATTACKS

- DoS (Denial of Service) Attacks
- Spoofing Attacks
- Reflection / Amplification Attacks
- Man-in-the-Middle Attacks
- Reconnaissance Attacks
- Malware
- Social Engineering Attacks
- Password-Related Attacks

DoS (Denial of Service) Attacks

- DoS attacks threaten the AVAILABILITY of the system
- One common DoS attack is the TCP SYN Flood
    - TCP Three-Way Handshake : SYN | SYN-ACK | ACK
    - The ATTACKER sends countless TCP SYN messages to the TARGET
    - The TARGET sends a SYN-ACK message in response to each SYN it receives
    - The ATTACKER never replies with the final ACK of the TCP Three-Way Handshake
    - The incomplete connections fill up the TARGET’S TCP connection table
    - The ATTACKER continues sending SYN messages
    - The TARGET is no longer able to make legitimate TCP connections

![image](https://github.com/psaumur/CCNA/assets/106411237/5b04eea4-c53a-48b7-9683-952c9b27c9db)

- In a DDoS (Distributed Denial of Service) Attack, the attacker infects many computers with MALWARE and uses them to initiate a Denial-of-Service Attack.
- This group of infected computers is called a BOTNET

Example : A TCP SYN Flood Attack

![image](https://github.com/psaumur/CCNA/assets/106411237/fc394c8d-33f4-4fd4-84a0-3e49caa9c158)

---

SPOOFING ATTACKS

- To SPOOF an address is to use a fake source address (IP or MAC)
- Numerous attacks involve spoofing; it’s not a single kind of attack
- An example is a DHCP EXHAUSTION attack
- An attacker uses spoofed MAC addresses to flood DHCP Discover messages
- The target server’s DHCP POOL becomes full, resulting in a Denial-of-Service to other devices

![image](https://github.com/psaumur/CCNA/assets/106411237/c539c50b-1be0-42f9-8ce3-fbeb47ea2034)

---

REFLECTION / AMPLIFICATION ATTACKS

- In a REFLECTION attack, the attacker sends traffic to a *reflector*, and spoofs the source of the packet using the TARGET’S IP ADDRESS
- The *reflector* (ie: a DNS Server) sends the reply to the target’s IP address
- If the amount of traffic sent to the target is large enough, this can result in a Denial-of-Service

- A REFLECTION attack becomes an AMPLIFICATION attack when the amount of traffic sent by the ATTACKER is small but it triggers a LARGE amount of traffic to be sent from the *reflector* to the target

![image](https://github.com/psaumur/CCNA/assets/106411237/34ca977d-9884-4aeb-b99a-9f3677ba17fa)

---

MAN-IN-THE-MIDDLE ATTACKS

- In a MAN-IN-THE-MIDDLE attack, the attacker places himself between the source and destination to eavesdrop on communications, or to modify traffic before it reaches the destination
- A common example is ARP SPOOFING, also known as ARP POISONING
- A host sends an ARP request, asking for the MAC address of another device
- The target of the request sends an ARP reply, informing the requester of it’s MAC address
- The attacker waits and sends another ARP reply after it’s legitimate replier

![image](https://github.com/psaumur/CCNA/assets/106411237/86cee6cd-845a-4732-bfec-4cfe18101322)

- In PC1’s ARP table, the entry for 10.0.0.1 will have the attacker’s MAC address
- When PC1 tries to send traffic to SRV1, it will be forwarded to the attacker instead
- The attacker can inspect the messages, and then forward them on to SRV1
- The attacker can also modify the messages before forwarding them to SRV1
- This compromises the CONFIDENTIALITY and INTEGRITY of communication between PC1 and SRV1

![image](https://github.com/psaumur/CCNA/assets/106411237/07ebfebd-0686-436a-8990-853e3fee4377)

---

RECONNAISSANCE ATTACKS

- RECONNAISSANCE ATTACKS are not attacks themselves but they are used to gather information about a target which can be used for a future attack
- This is often publicly available information
- IE: nslookup to learn the IP address of a site

![image](https://github.com/psaumur/CCNA/assets/106411237/6e63b09d-a768-4cb3-ac06-87ad41d45c38)

- Or a WHOIS query to learn email addresses, phone numbers, physical addresses, etc.

https://lookup.icann.org/lookup

---

MALWARE

- MALWARE (MALICIOUS SOFTWARE) refers to a variety of harmful programs that can infect a computer
- VIRUSES infect other software (a ‘host program’)
    - The VIRUS spreads as the software is shared by users. Typically, they corrupt or modify files on the target computer
- WORMS do not require a host program. They are standalone malware and they are able to spread on their own, without user interaction. The spread of WORMS can congest the NETWORK but the ‘payload’ of a WORM can cause additional harm to target devices

- TROJAN HORSES are harmful software that is disguised as legitimate software. They are spread through user interaction such as opening email attachments, downloading a file from the Internet.

The above MALWARE types can exploit various VULNERABILITIES to threaten any of the CIA of a target device

** There are many types of MALWARE

---

SOCIAL ENGINEERING ATTACKS

- SOCIAL ENGINEERING ATTACKS target the most vulnerable part of any system - PEOPLE!
- They involve psychological manipulation to make the target reveal confidential information or perform some action

- PHISHING typically involves fraudulent emails that appear to come from a legitimate business (Amazon, bank, credit card company, etc) and contain links to a fraudulent website that seems legitimate. Users are told to login to the fraudulent website, providing their login credentials to the attacker.
    - SPEAR PHISHING is a more targeted form of phishing, ie: aimed at employees of a certain company
    - WHALING is a phishing targeted at high-profile individuals, ie: a company president
- VISHING (Voice Phishing) is phishing performed over a phone

- SMISHING (SMS Phishing) is phishing using SMS text messages

- WATERING HOLE attacks compromise sites that the target victim frequently visits. If a malicious link is placed on a website the TARGET trusts, they might not hesitate to click it
- TAILGATING attack involves entering restricted, secured areas by simply walking in behind an authorized person as they enter. Often the target will hold the door open for the attacker to be polite, assuming the attacker is also authorized to enter.

---

PASSWORD-RELATED ATTACKS

- Most systems use a USERNAME / PASSWORD combination to AUTHENTICATE users
- The USERNAME is often simple / easy to guess (for example the user’s email address) and the strength and secrecy of the password is relied on to provide the necessary security
- ATTACKERS can learn a user’s passwords via multiple methods:
    - Guessing
    - DICTIONARY ATTACK :
        - A program runs through a ‘dictionary’ or list of common words / passwords to find the target’s password
    - BRUTE FORCE ATTACK :
        - A program tries every possible combination of letters, numbers, and special characters to find the target’s password

- STRONG PASSWORDS should contain:
    - At least 8 characters (preferably more)
    - A mixture of uppercase and lowercase letters
    - A mixture of letters and numbers
    - One of more special characters (# @ ! ? etc.)
    - Should be changed regularly 

---

PASSWORDS / MULTI-FACTOR AUTHENTICATION (MFA)

- MULTI-FACTOR AUTHENTICATION involves providing more than just a USERNAME / PASSWORD to prove your identity
- It usually involves providing two of the following ( = Two-Factor Authentication) :
    - SOMETHING YOU KNOW
        - A username / password combination, a PIN, etc.
        
    - SOMETHING YOU HAVE
        - Pressing a notification that appears on your phone, a badge that is scanned, etc.
    
    - SOMETHING YOU ARE
        - Biometrics such as a face scan, palm scan, fingerprint scan, retina scan, etc.

- Requiring multiple factors of authentication greatly increases the security. Even if the attacker learns the target’s password (SOMETHING YOU KNOW), they won’t be able to login to the target’s account

---

DIGITAL CERTIFICATES

- DIGITAL CERTIFICATES are another form of authentication used to prove the identity of the holder of the certificate
- They are used for websites to verify that the website being accessed is legitimate
- Entities that want a certificate to prove their identity send a CSR (CERTIFICATE SIGNING REQUEST) to a CA (CERTIFICATE AUTHORITY) which will generate and sign the certificate

---

CONTROLLING AND MONITORING USERS WITH AAA

- AAA (Triple-A) stands for AUTHENTICATION, AUTHORIZATION, and ACCOUNTING
- It is a framework for controlling and monitor users of a computer system (ie: a network)

- AUTHENTICATION
    - Process of verifying a user’s identity
    - Logging in = authentication
- AUTHORIZATION
    - Process of granting the user the appropriate access and permissions
    - Granting the user access to some files / services, restricting access to other files / services = AUTHORIZATION

- ACCOUNTING
    - Process of recording the user’s activities on the system
    - Logging when a user makes a change to a file = ACCOUNTING

- Enterprises typically use a AAA server to provide AAA services
    - ISE (Identity Services Engine) is Cisco’s AAA server

- AAA Servers usually support the following two AAA Protocols:
    - RADIUS :  Open Standard Protocol
        - Uses UDP ports 1812 and 1813
        
    - TACACS+ : Cisco Proprietary Protocol
        - Uses TCP port 49

💡 FOR THE CCNA, KNOW THE DIFFERENCES BETWEEN AUTHENTICATION, AUTHORIZATION, and ACCOUNTING


---

SECURITY PROGRAM ELEMENTS

- USER AWARENESS PROGRAMS are designed to make employees aware of potential security threats and risks
- USER TRAINING PROGRAMS are more formal than USER AWARENESS PROGRAMS
- PHYSICAL ACCESS CONTROL protects equipment and data from potential attackers by only allowing authorized users into the protected areas such as NETWORK CLOSETS or DATA CENTER FLOORS
