# 57. WIRELESS SECURITY

INTRO TO WIRELESS NETWORK SECURITY

- Although security is important in all networks, it is even more essential in wireless networks
- Because wireless signals are not contained within a wire, any device within range of the signal can receive traffic
- In wired networks, traffic is often only encrypted when sent over an untrusted network such as the internet
- In wireless networks, it is very important to encrypt traffic sent between the wireless clients and the AP

- We will cover three main concepts:
    - Authentication
    - Encryption
    - Integrity

---

AUTHENTICATION

- All clients must be authenticated before they can associate with an AP
- In a corporate setting, only trusted users / devices should be given access to the network
    - In corporate settings, a separate SSID which doesn’t have access to the corporate network can be provided for guest users
- Ideally, clients should also authenticate the AP to avoid associating with a malicious AP
- There are multiple ways to authenticate:
    - Password
    - Username / password
    - Certificates

![image](https://github.com/psaumur/CCNA/assets/106411237/00d34740-8da7-428d-8b36-f8998ec2f0cd)

---

ENCRYPTION

- Traffic sent between clients and APs should be encrypted so that it can’t be read by anyone except the AP and the client
- There are many possible protocols that can be used to encrypt traffic
- All devices on the WLAN will use the same protocol, however each client will use a unique encryption / decryption key so that other devices can’t read its traffic
- A “GROUP KEY” is used by the AP to encrypt traffic that it wants to send to all of its clients
    - All of the clients associated with the AP keep that key so they can decrypt the traffic
    

---

INTEGRITY

- As explained in the “Security Fundamentals” video of the course, integrity ensures that the message is not modified by a third-party
- The message that is sent by the source host should be the same as the message that is received by the destination host
- A MIC (Message Integrity Check) is added to the message to help protect their integrity.

![image](https://github.com/psaumur/CCNA/assets/106411237/b632c321-36e5-4a03-b08c-d0a2c2e215da)

---

AUTHENTICATION METHODS

The original 802.11 standard included two options for authentication:

- OPEN AUTHENTICATION
    - The client sends an authentication request and the AP just accepts it
    - The is clearly not a secure authentication method
    - After the client is authenticated and associated with the AP, it’s possible to require the user to authenticate via other methods before access to the network is granted (ie: Starbucks Wi-Fi)
- WEP (Wired Equivalent Privacy)
    - WEP is used to provide both authentication and encryption of wireless traffic
    - For encryption, WEP uses the RC4 ALGORITHM
    - WEP is a “shared-key” protocol, requiring the sender and receiver to have the same key
    - WEP keys can be 40 bits or 104 bits in length
    - The above keys are combined with a 24-bit “IV” (INITIALIZATION VECTOR) to bring the total length to 64 bits or 128 bits
    - WEP encryption is not secure and can easily be cracked
    - WEP can be used for authentication like this:
    

![image](https://github.com/psaumur/CCNA/assets/106411237/86e4f243-1692-41a6-9b15-6b2e99942e50)

---

EAP (Extensible Authentication Protocol)

- EAP is an authentication FRAMEWORK
- It defines a standard SET of authentication functions that are used by the various *EAP methods*
- We will look at four EAP methods:
    - LEAP
    - EAP-FAST
    - PEAP
    - EAP-TLS
- EAP is integrated with **802.1X** which provides *port-based network access control*

**802.1X** is used to limit network access for clients connected to a LAN or WLAN until they authenticate

There are **three main entities** in 802.1X:

- Supplicant : The device that wants to connect to the network
- Authenticator : The device that provides access to the network
- Authentication Server (AS) : The device that receives client credentials and permits / denies access

![image](https://github.com/psaumur/CCNA/assets/106411237/5565e646-696f-4245-b1e5-d728fe0e3380)

- LEAP (Lightweight EAP)
    - LEAP was developed by Cisco an an improvement over WEP
    - Clients must provide a username and password to authenticate
    - In addition, *mutual authentication* is provided by both the client and server sending a CHALLENGE PHRASE to each other.
    - Dynamic WEP keys are used, meaning that the WEP keys are changed frequently
    - Like WEP, LEAP is considered vulnerable and should not be used anymore

![image](https://github.com/psaumur/CCNA/assets/106411237/0b9ecce2-4219-42d0-8275-086b92134cda)

- EAP-FAST (EAP FLEXIBLE Authentication via Secure Tunneling)
    - EAP-FAST was also developed by Cisco
    - Consists of three phases:
        - A PAC (Protected Access Credential) is generated and passed from server to client
        - A secure TLS tunnel is established between the client and authentication server
        - Inside of the secure (encrypted) TLS tunnel, the client and server communicated further to authenticate / authorize the client
    

![image](https://github.com/psaumur/CCNA/assets/106411237/f17d6f7b-9f87-4cb2-be24-5d8c95dc0cfc)

- PEAP (PROTECTED EAP)
    - Like EAP-FAST, PEAP involves establishing a secure TLS tunnel between the client and server
    - Instead of a PAC, the server has a DIGITAL CERTIFICATE
    - The client uses this digital certificate to authenticate the server
    - The certificate is also used to establish a TLS tunnel
    - Because only the server provides a certificate for authentication, the client must still be authenticated within the secure tunnel
        - Example: MS-CHAP (Microsoft Challenge-Handshake Authentication Protocol)

![image](https://github.com/psaumur/CCNA/assets/106411237/0f9babe7-d86f-49c8-b732-20f31ea26437)

- EAP-TLS (EAP TRANSPORT LAYER Security)
    - Whereas PEAP only requires the AS to have a certificate, EAP-TLS requires a certificate on the AS and on every single client
    - EAP-TLS is the most secure wireless authentication method, but it is more difficult to implement than PEAP because every client device needs a certificate
    - Because the client and server authenticate each other with digital certificates, there is no need to authenticate the client within the TLS tunnel
    - The TLS tunnel is still used to exchange encryption key information (encryption methods will be discussed next)

![image](https://github.com/psaumur/CCNA/assets/106411237/c6c57595-fd75-4761-8760-29fab8dbf698)

---

ENCRYPTION / INTEGRITY METHODS

- TKIP (Temporal Key Integrity Protocol)
    - WEP was found to be vulnerable, but wireless hardware at the time was built to use WEP
    - A temporary solution was needed until a new standard was created and a new hardware was built
    - TKIP adds various security features:
        - A MIC (Message Integrity Check) is added to protect the integrity of messages
        - A key mixing algorithm is used to create a unique WEP key for every frame
        - The initialization vector is doubled in length from 24 bits to 48 bits, making brute-force attacks much more difficult
        - The MIC includes the sender MAC address to identify the frame’s sender
        - A timestamp is added to the MIC to prevent replay attacks. Replay attacks involved re-resending a frame that has already been transmitted
        - A TKIP sequence number is used to keep track of frames sent from each source MAC address. This also protects against replay attacks

** You probably don’t need to memorize all of the above features

** TKIP is used in WPA version 1, which will be discussed in the next section

- CCMP (Counter / CBC-MAC Protocol)
    - CCMP was developed after TKIP and is more secure
    - It is used in WPA2
    - To use CCMP, it must be supported by the device’s hardware.
    - Old hardware built only to use WEP / TKIP cannot use CCMP
    - CCMP consists of two different algorithms to provide encryption and MIC :
        - AES (Advanced Encryption Standard) Counter Mode encryption
            - AES is the most secure encryption protocol currently available.
            - Widely used all over the world
            - There are multiple modes of operation for AES.
            - CCMP uses “Counter Mode”
        - CBC-MAC (Cipher Block Chaining Message Authentication Code)
            - Used as a MIC to ensure the integrity of messages

- GCMP (GALOIS / COUNTER MODE PROTOCOL)
    - GCMP is more secure and efficient than CCMP
    - Its increased efficiency allows higher data throughput than CCMP
    - It is used in WPA3
    - GCMP consists of two algorithms:
        - AES Counter Mode encryption
        - GMAC (Galois Message Authentication Code)
            - Used as a MIC to ensure the integrity of message

---

WI-FI PROTECTED ACCESS (WPA)

- The Wi-Fi Alliance has developed three WPA certifications for wireless devices:
    - WPA
    - WPA2
    - WPA3
- To be WPA-certified, equipment must be tested in authorized testing labs
- All of the above support two Authentication modes:
    - PERSONAL MODE :
        - A PRE-SHARED KEY (PSK) is used for authentication
        - When you connect to a home Wi-Fi network, enter the password and are authenticated, that is PERSONAL Mode
        - This is common in small networks
        - The PSK itself is not sent over the air
        - A four-way handshake is used for authentication and the PSK is used to generate encryption keys
    - ENTERPRISE MODE :
        - 802.1X is used with an authentication server (RADIUS server)
        - No specific EAP method is specified, so all are supported (PEAP, EAP-TLS, etc)
    
    WPA
    
    - The WPA certification was developed after WEP was proven to be vulnerable and includes the following protocols:
        - TKIP (based on WEP) provides encryption / MIC
        - 802.1X authentication (Enterprise Mode) or PSK (Personal Mode)
    
    WPA2
    
    - Was released in 2004 and includes the following protocols:
        - CCMP provides encryption / MIC
        - 802.1X authentication (Enterprise Mode) or PSK (Personal Mode)
    
    WPA3
    
    - Was released in 2018 and includes the following protocols:
        - GCMP provides encryption / MIC
        - 802.1X authentication (Enterprise mode) or PSK (Personal mode)
        
        - WPA3 also provides several additional security features:
            - PMF (Protected Management Frames)
                - Protecting 802.11 Management frames from eavesdropping / forging
            - SAE (Simultaneous Authentication of Equals)
                - Protects the four-way handshake when using personal mode authentication
            - FORWARD SECRECY
                - Prevents data from being decrypted after it has been transmitted over the air so an attacker can’t capture wireless frames and then try to decrypt them later
