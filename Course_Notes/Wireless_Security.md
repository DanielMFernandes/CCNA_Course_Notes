# 57. WIRELESS SECURITY

INTRO TO WIRELESS NETWORK SECURITY

- Although security is important in all networks, it is even more essential in wireless networks
- Because wireless signals are not contained within a wire, any device within range of the signal can receive traffic
- In wired networks, traffic is often only encrypted when sent over an untrusted network such as the internet
- In wireless networks, it is very important to encrypt traffic sent between the wireless clients and the AP

- We will cover three MAIN CONCEPTS:
    - Authentication
    - Encryption
    - INTEGRITY

---

AUTHENTICATION

- All clients must be authenticated before they can associate with an AP
- In a corporate setting, only TRUSTED users / devices should be given access to the network
    - In corporate settings, a separate SSID which doesn’t have access to the corporate network can be provided for GUEST users
- Ideally, clients should also AUTHENTICATE the AP to avoid associating with a malicious AP
- There are MULTIPLE WAYS to AUTHENTICATE:
    - password
    - username / password
    - CERTIFICATES

![image](https://github.com/psaumur/CCNA/assets/106411237/00d34740-8da7-428d-8b36-f8998ec2f0cd)

---

ENCRYPTION

- Traffic sent between clients and APs should be encrypted so that it can’t be read by anyone except the AP and the client
- There are many possible PROTOCOLS that can be used to encrypt traffic
- All devices on the WLAN will use the same PROTOCOL, however each client will use a unique encryption / DECRYPTION KEY so that other devices can’t read its traffic
- A “GROUP KEY” is used by the AP to encrypt traffic that it wants to send to all of its clients
    - All of the clients associated with the AP keep that key so they can DECRYPT the traffic
    

---

INTEGRITY

- As explained in the “security FUNDAMENTALS” video of the course, INTEGRITY ensures that the message is not modified by a third-party
- The message that is sent by the SOURCE HOST should be the same as the message that is received by the DESTINATION HOST
- A MIC (Message Integrity Check) is added to the message to help protect their INTEGRITY.

![image](https://github.com/psaumur/CCNA/assets/106411237/b632c321-36e5-4a03-b08c-d0a2c2e215da)

---

AUTHENTICATION METHODS

The original 802.11 STANDARD included TWO OPTIONS for authentication:

- OPEN AUTHENTICATION
    - The client sends an authentication REQUEST and the AP just accepts it
    - The is clearly not a secure authentication method
    - After the client is authenticated and associated with the AP, it’s possible to require the user to authenticate via other methods before access to the network is granted (ie: Starbucks Wi-Fi)
- WEP (Wired Equivalent Privacy)
    - WEP is used to provide both authentication and encryption of wireless traffic
    - For encryption, WEP uses the RC4 ALGORITHM
    - WEP is a “SHARED-KEY” PROTOCOL, requiring the SENDER and RECEIVER to have the same KEY
    - WEP KEYS can be 40 bits or 104 bits in length
    - The above KEYS are combined with a 24-bit “IV” (INITIALIZATION VECTOR) to bring the total length to 64 bits or 128 bits
    - WEP encryption is not secure and can easily be cracked
    - WEP can be used for authentication like this:
    

![image](https://github.com/psaumur/CCNA/assets/106411237/86e4f243-1692-41a6-9b15-6b2e99942e50)

---

EAP (Extensible Authentication Protocol)

- EAP is an authentication FRAMEWORK
- It defines a STANDARD SET of authentication FUNCTIONS that are used by the various *EAP METHODS*
- We will look at FOUR EAP METHODS:
    - LEAP
    - EAP-FAST
    - PEAP
    - EAP-TLS
- EAP is integrated with **802.1X** which provides *PORT-BASED network access CONTROL*

**802.1X** is used to limit network access for clients connected to a LAN or WLAN until they AUTHENTICATE

There are **three MAIN ENTITIES** in 802.1X:

- SUPPLICANT : The device that wants to connect to the network
- AUTHENTICATOR : The device that provides access to the network
- Authentication Server (AS) : The device that receives client credentials and PERMITS / DENIES access

![image](https://github.com/psaumur/CCNA/assets/106411237/5565e646-696f-4245-b1e5-d728fe0e3380)

- LEAP (Lightweight EAP)
    - LEAP was developed by Cisco an an improvement over WEP
    - Clients must provide a username and password to AUTHENTICATE
    - In addition, *MUTUAL authentication* is provided by both the client and server sending a CHALLENGE PHRASE to each other.
    - DYNAMIC WEP KEYS are used, meaning that the WEP KEYS are changed frequently
    - Like WEP, LEAP is considered vulnerable and should not be used anymore

![image](https://github.com/psaumur/CCNA/assets/106411237/0b9ecce2-4219-42d0-8275-086b92134cda)

- EAP-FAST (EAP FLEXIBLE Authentication via Secure Tunneling)
    - EAP-FAST was also developed by Cisco
    - Consists of three PHASES:
        - A PAC (PROTECTED Access CREDENTIAL) is generated and passed from server to client
        - A secure TLS tunnel is established between the client and authentication server
        - Inside of the secure (encrypted) TLS tunnel, the client and server communicated further to AUTHENTICATE / AUTHORIZE the client
    

![image](https://github.com/psaumur/CCNA/assets/106411237/f17d6f7b-9f87-4cb2-be24-5d8c95dc0cfc)

- PEAP (PROTECTED EAP)
    - Like EAP-FAST, PEAP involves establishing a secure TLS tunnel between the client and server
    - Instead of a PAC, the server has a DIGITAL CERTIFICATE
    - The client uses this DIGITAL CERTIFICATE to AUTHENTICATE the server
    - The CERTIFICATE is also used to establish a TLS tunnel
    - Because only the server provides a CERTIFICATE for authentication, the client must still be authenticated within the secure tunnel
        - Example: MS-CHAP (Microsoft Challenge-Handshake Authentication Protocol)

![image](https://github.com/psaumur/CCNA/assets/106411237/0f9babe7-d86f-49c8-b732-20f31ea26437)

- EAP-TLS (EAP TRANSPORT LAYER Security)
    - Whereas PEAP only requires the AS to have a CERTIFICATE, EAP-TLS requires a CERTIFICATE on the AS and on every single client
    - EAP-TLS is the most secure wireless authentication method, but it is more difficult to implement than PEAP because every client device needs a CERTIFICATE
    - Because the client and server AUTHENTICATE each other with DIGITAL CERTIFICATES, there is no need to AUTHENTICATE the client within the TLS tunnel
    - The TLS tunnel is still used to exchange encryption KEY information (encryption methods will be discussed next)

![image](https://github.com/psaumur/CCNA/assets/106411237/c6c57595-fd75-4761-8760-29fab8dbf698)

---

ENCRYPTION / INTEGRITY METHODS

- TKIP (Temporal Key Integrity Protocol)
    - WEP was found to be vulnerable, but wireless hardware at the time was built to use WEP
    - A temporary solution was needed until a new STANDARD was created and a new HARDWARE was built
    - TKIP adds various security FEATURES:
        - A MIC (Message Integrity Check) is added to protect the integrity of messages
        - A KEY MIXING ALGORITHM is used to create a unique WEP key for every frame
        - The INITIALIZATION VECTOR is doubled in length from 24 bits to 48 bits, making BRUTE-FORCE attacks much more difficult
        - The MIC includes the SENDER MAC ADDRESS to identify the FRAME’s SENDER
        - A TIMESTAMP is added to the MIC to prevent replay attacks. Replay attacks involved re-resending a FRAME that has already been transmitted
        - A TKIP SEQUENCE NUMBER is used to keep track of FRAMES sent from each SOURCE MAC ADDRESS. This also protects against REPLAY ATTACKS

** You probably don’t need to memorize all of the above features

** TKIP is used in WPA version 1, which will be discussed in the next section

- CCMP (Counter / CBC-MAC Protocol)
    - CCMP was developed after TKIP and is more secure
    - It is used in WPA2
    - To use CCMP, it must be supported by the device’s hardware.
    - Old hardware built only to use WEP / TKIP cannot use CCMP
    - CCMP consists of TWO DIFFERENT ALGORITHMS to provide encryption and MIC :
        - AES (Advanced Encryption Standard) COUNTER Mode encryption
            - AES is the most secure encryption PROTOCOL currently available.
            - Widely used all over the world
            - There are multiple modes of operation for AES.
            - CCMP uses “COUNTER Mode”
        - CBC-MAC (CIPHER BLOCK CHAINING MESSAGE Authentication CODE)
            - Used as a MIC to ENSURE the INTEGRITY of MESSAGES

- GCMP (GALOIS / COUNTER MODE PROTOCOL)
    - GCMP is more secure and EFFICIENT than CCMP
    - Its increased efficiency allows higher data throughput than CCMP
    - It is used in WPA3
    - GCMP consists of TWO ALGORITHMS:
        - AES COUNTER Mode encryption
        - GMAC (GALOIS MESSAGE Authentication CODE)
            - Used as a MIC to ENSURE the INTEGRITY of MESSAGE

---

WI-FI PROTECTED ACCESS (WPA)

- The Wi-Fi Alliance has developed three WPA CERTIFICATIONS for wireless devices:
    - WPA
    - WPA2
    - WPA3
- To be WPA-CERTIFIED, EQUIPMENT must be TESTED in authorized testing labs
- All of the above support TWO Authentication modes:
    - PERSONAL MODE :
        - A PRE-SHARED KEY (PSK) is used for AUTHENTICATOIN
        - When you connect to a home Wi-Fi network, enter the password and are authenticated, that is PERSONAL Mode
        - This is common in small networks
        - The PSK itself is not sent over the air
        - A FOUR-WAY HANDSHAKE is used for authentication and the PSK is used to GENERATE encryption KEYS
    - ENTERPRISE MODE :
        - 802.1X is used with an authentication server (RADIUS server)
        - No specific EAP METHOD is specified, so all are supported (PEAP, EAP-TLS, etc)
    
    WPA
    
    - The WPA CERTIFICATION was developed after WEP was proven to be vulnerable and includes the following PROTOCOLS:
        - TKIP (based on WEP) provides encryption / MIC
        - 802.1X authentication (ENTERPRISE Mode) or PSK (PERSONAL Mode)
    
    WPA2
    
    - Was released in 2004 and includes the following PROTOCOLS:
        - CCMP provides encryption / MIC
        - 802.1X authentication (ENTERPRISE Mode) or PSK (PERSONAL Mode)
    
    WPA3
    
    - Was released in 2018 and includes the following PROTOCOLS:
        - GCMP provides encryption / MIC
        - 802.1X authentication (ENTERPRISE mode) or PSK (PERSONAL mode)
        
        - WPA3 also provides several additional security features:
            - PMF (PROTECTED MANAGEMENT FRAMES)
                - Protecting 802.11 MANAGEMENT FRAMES from eavesdropping / forging
            - SAE (SIMULTANEOUS Authentication OF EQUALS)
                - Protects the four-way handshake when using PERSONAL mode authentication
            - FORWARD SECRECY
                - Prevents DATA from being DECRYPTED after it has been transmitted over the air so an attacker can’t capture wireless FRAMES and then try to DECRYPT them later
