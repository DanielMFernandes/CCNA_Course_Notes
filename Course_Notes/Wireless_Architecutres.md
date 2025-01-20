# 56. WIRELESS ARCHITECTURES

802.11 MESSAGE / FRAME FORMAT

![image](https://github.com/psaumur/CCNA/assets/106411237/7b459483-7156-44cf-9ee7-f9391e476636)

- 802.11 frames have a different format than 802.3 ethernet frames
- For the CCNA, you don’t have to learn it in as much detail as the ethernet and IP headers
- Depending on the 802.11 VERSION and the message type, some of the fields might not be present in the frame
    - For example: Not ALL messages use all 4 ADDRESS FIELDS
- Frame CONTROL
    - Provides information such as message type and subtype
    - Indicates if the frame is a management frame
- DURATION / ID
    - Depending on the message type, this field can indicate:
        - The TIME (in microseconds) the CHANNEL will be dedicated to transmission of the frame
        - Identifier for the ASSOCIATION (the connection)
    
- ADDRESSES
    - Up to FOUR ADDRESSES can be present in an 802.11 frame.
    - Which ADDRESSES are present, and their ORDER, depends on the message type
        - DESTINATION ADDRESS (DA) : Final RECIPIENT of the frame
        - SOURCE ADDRESS (SA) : Original SENDER of the frame
        - RECEIVER ADDRESS (RA) : Immediate RECIPIENT of the frame
        - TRANSMITTER ADDRESS (TA) : Immediate SENDER of the frame
    
- SEQUENCE CONTROL
    - Used to reassemble FRAGMENTS and eliminate DUPLICATE frames

- QoS CONTROL
    - Used in QoS to PRIORITIZE certain traffic
- HT (High Throughput) CONTROL
    - Added in 802.11n to ENABLE High Throughput operations
    - 802.11n is also known as “HIGH THROUGHPUT” (HT) WI-FI
    - 802.11ac is also know as “VERY HIGH THROUGHPUT” (VHT) WI-FI

- FCS (FRAME CHECK SEQUENCE)
    - Same as in an ethernet frame, used to check for errors

---

802.11 ASSOCIATION PROCESS

- ACCESS POINTS bridge traffic between wireless stations and other devices
- For a STATION to send traffic through the AP, it must be associated with the AP
- There are three 802.11 CONNECTION STATES:
    - Not authenticated, not associated
    - Authenticated, not associated
    - Authenticated and associated

- The STATION must be authenticated and associated with the AP to send traffic through it

![image](https://github.com/psaumur/CCNA/assets/106411237/568d795d-41ee-4afd-908d-858297e89c6c)

---

802.11 MESSAGE TYPES

- There are three 802.11 message types
    - Management
    - Control
    - Data

- MANAGEMENT
    - Used to manage the BSS
        - BEACON
        - PROBE REQUEST / PROBE RESPONSE
        - AUTHENTICATION
        - ASSOCIATION REQUEST / ASSOCIATION RESPONSE

- CONTROL
    - Used to control access to the medium (RADIO FREQUENCY)
    - Assists with delivery of management and data frames
        - RTS (REQUEST TO SEND)
        - CTS (CLEAR TO SEND)
        - ACK

- DATA
    - Used to send actual data packets

 

---

AUTONOMOUS APs

- Autonomous APs are self-contained systems that do not rely on a WLC
- Autonomous APs are configured individually
    - Can be configured by CONSOLE cable (CLI)
    - Can be configured by TELNET (CLI)
    - Can be configured by HTTP / HTTPS Web connection (GUI)
    - An IP ADDRESS for REMOTE management should be configured
    - The RF PARAMETERS must be manually configured (Transmit Power, Channel, etc)
    - SECURITY POLICIES are handled individually by each AP
    - QoS RULES etc. are configured individually by each AP

 

- There is NO CENTRAL MONITORING or management of APs

![image](https://github.com/psaumur/CCNA/assets/106411237/57faecbb-36a6-424d-b019-52994a5740db)

- Autonomous APs connect to the WIRED network with a trunk link
- Data traffic from wireless clients have a very direct PATH to the WIRED network or to other wireless clients associated with the same AP
- Each VLAN has to STRETCH across the entire network. This is considered bad practice
    - Large Broadcast Domains
    - Spanning Tree will disable links
    - Adding / Deleting VLANs is very labor-intensive
- Autonomous APs can be used in small networks but they are not viable in medium to large networks
    - Large networks can have thousands of APs

- Autonomous APs can also function in the modes covered in the previous video:
    - REPEATER
    - OUTDOOR BRIDGE
    - WORKGROUP BRIDGE

---

LIGHTWEIGHT APs

- The functions of an AP can be split between the AP and a WIRELESS LAN CONTROLLER (WLC)
- The is what is called SPLIT-MAC ARCHITECTURE

- LIGHTWEIGHT APs handle **“real-time”** operations like:
    - TRANSMITTING / RECEIVING RF traffic
    - Encryption / decryption OF traffic
    - SENDING OUT BEACONS / PROBES
    - Packet prioritization
    - Etc…
- WLC Functions (not time dependent)
    - RF management
    - SECURITY / QoS management
    - CLIENT AUTHENTICATION
    - CLIENT ASSOCIATION / ROAMING management
    - RESOURCE ALLOCATION
    - Etc…
    
- The WLC is also used to centrally configured the lightweight APs
- The WLC can be located in the same subnet / VLAN as the lightweight APs it manages OR in a different subnet / VLAN
- The WLC and the lightweight APs authenticate each other using DIGITAL CERTIFICATES installed on each device ( X.509 STANDARD CERTIFICATES )
    - This ensures that only authorized APs can join the network

![image](https://github.com/psaumur/CCNA/assets/106411237/c154bcad-ae81-4fb8-9acf-56913dffaf04)

- THE WLC and lightweight APs use a protocol called CAPWAP (Control AND PROVISIONING OF Wireless ACCESS POINTS) to communicate
    - Based on an older protocol called LWAPP (LIGHTWEIGHT ACCESS POINT PROTOCOL)

- TWO tunnels are created between each AP and the WLC :
    - Control tunnel (UDP Port 5246)
        - This tunnel is used to configure the APs and control and manage operations
        - All traffic in this tunnel is encrypted, by default
    - Data tunnel (UDP Port 5247)
        - All traffic from wireless clients is sent through this tunnel to the WLC
        - IT DOES not GO DIRECTLY TO THE WIRED network!

- Traffic in this tunnel is not encrypted by default but you can configure it to be encrypted with DTLS (DATAGRAM TRANSPORT LAYER SECURITY)

- Because ALL traffic from WIRELSS clients is tunneled to the WLC with CAPWAP, APs connect to the SWITCH ACCESS PORTS - not trunk PORTS

![image](https://github.com/psaumur/CCNA/assets/106411237/10917a40-468a-4ea6-8253-bf229d612af1)

---

***  (Not necessary to MEMORIZE for CCNA) ***

There are some KEY BENEFITS to SPLIT-MAC ARCHITECTURE

- SCALABILITY
    - With a WLC (or multiple) it’s SIMPLER to build and support a network with thousands of APs
- DYNAMIC CHANNEL ASSIGNMENT
    - The WLC can automatically select which channel each AP should use
- TRANSMIT POWER OPTIMIZATION
    - The WLC can automatically set the appropriate transmit power for each AP
- SELF-HEALING WIRELESS COVERAGE
    - When an AP stops functioning, the WLC can increase the transmit power of nearby APs to avoid coverage holes
- SEAMLESS ROAMING
    - Clients can roam between APs with no noticeable delay
- CLIENT LOAD BALANCING
    - If a CLIENT is in range of TWO APs, the WLC can associate the CLIENT with the least-used AP, to balance the load among APs
- SECURITY / QoS management
    - Central management of SECURITY and QoS policies ensures consistency across the network

---

- LIGHTWEIGHT APs can be configured to operate in VARIOUS MODES:
    - LOCAL
        - This is the DEFAULT mode where the AP offers a BSS (more multiple BSSs) for clients to associate with
        
    - FLEXCONNECT
        - Like a LIGHTWEIGHT AP in LOCAL mode, it offers ONE or MORE BSSs for clients to associate with
        - HOWEVER, FLEXCONNECT allows the AP to locally SWITCH traffic between the WIRED (trunk) and wireless networks (ACCESS) if the tunnels to the WLC go down
    
![image](https://github.com/psaumur/CCNA/assets/106411237/aa2d7d98-2d6f-46b6-ab38-7acc96c8dc52)
    

- SNIFFER
    - The AP does not OFFER a BSS for clients
    - Dedicated to CAPTURING 802.11 frames and SENDING them to a device running software such as WIRESHARK

- MONITOR
    - The AP does not OFFER a BSS for clients
    - Dedicated to RECEIVING 802.11 frames to detect rogue devices
    - If a CLIENT is found to be a rogue device, an AP can send DE-AUTHENTICATION messages to disassociate the rogue device from the AP

- ROGUE DETECTOR
    - The AP does not even USE its RADIO
    - It LISTENS to traffic on the WIRED network only, but it receives a list of SUSPECTED rogue clients and AP MAC ADDRESSES from the WLC
    - By LISTENING to ARP messages on the WIRED network and correlating it with the information it receives from the WLC, it can DETECT rogue devices

- SE-CONNECT (SPECTRUM EXPERT CONNECT)
    - The AP does not OFFER a BSS for clients
    - Dedicated to RF SPECTRUM ANALYSIS on ALL CHANNELS
    - It can send information to software such as Cisco Spectrum Expert on a PC to COLLECT and ANALYZE the data

- BRIDGE / MESH
    - Like the autonomous APs *OUTDOOR BRIDGE* mode, the LIGHTWEIGHT AP can be a DEDICATED BRIDGE between SITES (Example:  over LONG distances)
    - A MESH can be made between the ACCESS POINTS

- FLEX PLUS BRIDGE
    - Adds FLEXCONNECT functionality to the BRIDGE / MESH mode
    - Allows wireless ACCESS POINTS to locally forward traffic even if connectivity to the WLC is lost
    

![image](https://github.com/psaumur/CCNA/assets/106411237/940a414b-208f-408c-a3e2-37e3bfbb0d32)

---

CLOUD-BASED APs

- Cloud-based AP architecture is between autonomous AP and SPLIT-MAC ARCHITECTURE
    - Autonomous APs that are centrally managed in the cloud
- CISCO MERAKI is a popular cloud-based WI-FI solution
- The MERAKI dashboard can be used to configure APs, monitor the network, generate performance reports, etc.
    - MERAKI also tells each AP which CHANNEL to use, what transmit power, etc.
- However, data traffic is not sent to the cloud. It is sent directly to the WIRED network like when using autonomous APs
    - Only management / control traffic is sent to the cloud

![image](https://github.com/psaumur/CCNA/assets/106411237/8bd00a94-f965-4257-af46-82be67850feb)

![image](https://github.com/psaumur/CCNA/assets/106411237/93e62771-c2d5-4003-9ade-0d5be855ea66)

---

WIRELESS LAN CONTROLLER (WLC) DEPLOYMENTS

- In a SPLIT-MAC ARCHITECTURE, there FOUR MAIN WLC DEPLOYMENT MODES:
    - UNIFIED
        - THE WLC is a HARDWARE APPLICANCE in a central location of the network
    - Cloud-based
        - The WLC is a VM running on a SERVER, usually in a PRIVATE cloud in a data CENTER
        - This is not the same as the cloud-based AP ARCHITECTURE discussed previously
    - EMBEDDED
        - The WLC is integrated within a SWITCH
    - MOBILITY EXPRESS
        - THE WLC is integrated within an AP

---

UNIFIED WLC

- THE WLC is a HARDWARE APPLICANCE in a central location of the network
- A UNIFIED WLC can support up to about 6000 APs
- If more than 6000 APs are needed, additional WLCs can be added to the network

![image](https://github.com/psaumur/CCNA/assets/106411237/922eac1f-6c62-4926-89bb-a447f8be2edd)

---

CLOUD-BASED

- The WLC is a VM running on a SERVER, usually in a PRIVATE cloud in a data CENTER
- Cloud-based WLCs can typically support up to about 3000 APs
- If more than 3000 APs are needed, more WLC VMs can be deployed

![image](https://github.com/psaumur/CCNA/assets/106411237/9d87546c-6397-48d2-941c-007f5e6440aa)

---

EMBEDDED WLC

- The WLC is embedded within a SWITCH
- An EMBEDDED WLC can support up to about 200 APs
- If more than 200 APs are needed, more SWITCHES with EMBEDDED WLCs can be added

![image](https://github.com/psaumur/CCNA/assets/106411237/fc6a79f2-a7b5-4b5a-99d6-b94238362e8e)

---

CISCO MOBILITY EXPRESS WLC

- The WLC is embedded within an AP
- A MOBILITY EXPRESS WLC can support up to about 100 APs
- If more than 100 APs are needed, more APs with EMBEDDED MOBILITY  EXPRESS WLCs can be added

![image](https://github.com/psaumur/CCNA/assets/106411237/4ff02aee-83c9-4a56-8a71-a14e20e8bf3c)
