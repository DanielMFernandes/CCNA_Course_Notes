# 56. WIRELESS ARCHITECTURES

802.11 MESSAGE / FRAME FORMAT

![image](https://github.com/psaumur/CCNA/assets/106411237/7b459483-7156-44cf-9ee7-f9391e476636)

- 802.11 frames have a different format than 802.3 ethernet frames
- For the CCNA, you don’t have to learn it in as much detail as the Ethernet and IP headers
- Depending on the 802.11 version and the message type, some of the fields might not be present in the frame
    - For example: Not all messages use all 4 address fields
- Frame Control
    - Provides information such as message type and subtype
    - Indicates if the frame is a management frame
- Duration / ID
    - Depending on the message type, this field can indicate:
        - The time (in microseconds) the channel will be dedicated to transmission of the frame
        - Identifier for the association (the connection)
    
- Addresses
    - Up to four addresses can be present in an 802.11 frame.
    - Which addresses are present, and their order, depends on the message type
        - Destination Address (DA) : final recipient of the frame
        - Source Address (SA) : original sender of the frame
        - Receiver Address (RA) : immediate recipient of the frame
        - Transmitter Address (TA) : immediate sender of the frame
    
- Sequence Control
    - Used to reassemble fragments and eliminate duplicate frames

- QoS Control
    - Used in QoS to prioritize certain traffic
- HT (High Throughput) Control
    - Added in 802.11n to enable High Throughput operations
    - 802.11n is also known as “High Throughput” (HT) Wi-Fi
    - 802.11ac is also know as “Very High Throughput” (VHT) Wi-Fi

- FCS (Frame Check Sequence)
    - Same as in an ethernet frame, used to check for errors

---

802.11 ASSOCIATION PROCESS

- Access points bridge traffic between wireless stations and other devices
- For a station to send traffic through the AP, it must be associated with the AP
- There are three 802.11 connection states:
    - Not authenticated, not associated
    - Authenticated, not associated
    - Authenticated and associated

- The station must be authenticated and associated with the AP to send traffic through it

![image](https://github.com/psaumur/CCNA/assets/106411237/568d795d-41ee-4afd-908d-858297e89c6c)

---

802.11 MESSAGE TYPES

- There are three 802.11 message types
    - Management
    - Control
    - Data

- MANAGEMENT
    - Used to manage the BSS
        - Beacon
        - Probe request / Probe response
        - Authentication
        - Association Request / Association response

- CONTROL
    - Used to control access to the medium (Radio Frequency)
    - Assists with delivery of management and data frames
        - RTS (Request To Send)
        - CTS (Clear To Send)
        - ACK

- DATA
    - Used to send actual data packets

 

---

AUTONOMOUS APs

- Autonomous APs are self-contained systems that do not rely on a WLC
- Autonomous APs are configured individually
    - Can be configured by console cable (CLI)
    - Can be configured by telnet (CLI)
    - Can be configured by HTTP / HTTPS Web connection (GUI)
    - An IP address for remote management should be configured
    - The RF parameters must be manually configured (Transmit Power, Channel, etc)
    - Security policies are handled individually by each AP
    - QoS rules etc. are configured individually by each AP

 

- There is no central monitoring or management of APs

![image](https://github.com/psaumur/CCNA/assets/106411237/57faecbb-36a6-424d-b019-52994a5740db)

- Autonomous APs connect to the wired network with a trunk link
- Data traffic from wireless clients have a very direct path to the wired network or to other wireless clients associated with the same AP
- Each VLAN has to stretch across the entire network. This is considered bad practice
    - Large Broadcast Domains
    - Spanning Tree will disable links
    - Adding / Deleting VLANs is very labor-intensive
- Autonomous APs can be used in small networks but they are not viable in medium to large networks
    - Large networks can have thousands of APs

- Autonomous APs can also function in the modes covered in the previous video:
    - Repeater
    - Outdoor Bridge
    - Workgroup Bridge

---

LIGHTWEIGHT APs

- The functions of an AP can be split between the AP and a WIRELESS LAN CONTROLLER (WLC)
- The is what is called SPLIT-MAC ARCHITECTURE

- LIGHTWEIGHT APs handle **“real-time”** operations like:
    - Transmitting / Receiving of traffic
    - Encryption / Decryption of traffic
    - Sending out beacons / probes
    - Packet prioritization
    - Etc…
- WLC Functions (not time dependent)
    - RF management
    - Security / QoS management
    - Client authentication
    - Client association / roaming management
    - Resource allocation
    - Etc…
    
- The WLC is also used to centrally configure the lightweight APs
- The WLC can be located in the same subnet / VLAN as the lightweight APs it manages or in a different subnet / VLAN
- The WLC and the lightweight APs authenticate each other using DIGITAL CERTIFICATES installed on each device ( X.509 Standard Certificates )
    - This ensures that only authorized APs can join the network

![image](https://github.com/psaumur/CCNA/assets/106411237/c154bcad-ae81-4fb8-9acf-56913dffaf04)

- The WLC and lightweight APs use a protocol called CAPWAP (Control And Provisiong of Wireless Access Points) to communicate
    - Based on an older protocol called LWAPP (Lightweight Access Point Protocol)

- Two tunnels are created between each AP and the WLC :
    - Control tunnel (UDP Port 5246)
        - This tunnel is used to configure the APs and control and manage operations
        - All traffic in this tunnel is encrypted, by default
    - Data tunnel (UDP Port 5247)
        - All traffic from wireless clients is sent through this tunnel to the WLC
        - It does not go directly to the wired network!
        - Traffic in this tunnel is not encrypted by default but you can configure it to be encrypted with DTLS (Datagram Transport Layer Security)

- Because all traffic from wireless clients is tunneled to the WLC with CAPWAP, APs connect to the switch access ports - not trunk ports

![image](https://github.com/psaumur/CCNA/assets/106411237/10917a40-468a-4ea6-8253-bf229d612af1)

---

***  (Not necessary to memorize for CCNA) ***

There are some key benefits to split-MAC architecture

- SCALABILITY
    - With a WLC (or multiple) it’s simpler to build and support a network with thousands of APs
- DYNAMIC CHANNEL ASSIGNMENT
    - The WLC can automatically select which channel each AP should use
- TRANSMIT POWER OPTIMIZATION
    - The WLC can automatically set the appropriate transmit power for each AP
- SELF-HEALING WIRELESS COVERAGE
    - When an AP stops functioning, the WLC can increase the transmit power of nearby APs to avoid coverage holes
- SEAMLESS ROAMING
    - Clients can roam between APs with no noticeable delay
- CLIENT LOAD BALANCING
    - If a client is in range of two APs, the WLC can associate the client with the least-used AP, to balance the load among APs
- SECURITY / QoS management
    - Central management of security and QoS policies ensures consistency across the network

---

- Lightweight APs can be configured to operate in various modes:
    - LOCAL
        - This is the default mode where the AP offers a BSS (more multiple BSSs) for clients to associate with
        
    - FLEXCONNECT
        - Like a Lightweight AP in local mode, it offers one or more BSSs for clients to associate with
        - However, FLEXCONNECT allows the AP to locally switch traffic between the wired (trunk) and wireless networks (access) if the tunnels to the WLC go down
    
![image](https://github.com/psaumur/CCNA/assets/106411237/aa2d7d98-2d6f-46b6-ab38-7acc96c8dc52)
    

- SNIFFER
    - The AP does not offer a BSS for clients
    - Dedicated to capturing 802.11 frames and sending them to a device running software such as Wireshark

- MONITOR
    - The AP does not offer a BSS for clients
    - Dedicated to receiving 802.11 frames to detect rogue devices
    - If a client is found to be a rogue device, an AP can send de-authentication messages to disassociate the rogue device from the AP

- ROGUE DETECTOR
    - The AP does not even use its radio
    - It listens to traffic on the wired network only, but it receives a list of suspected rogue clients and AP MAC addresses from the WLC
    - By listening to ARP messages on the wired network and correlating it with the information it receives from the WLC, it can detect rogue devices

- SE-CONNECT (Spectrum Expert Connect)
    - The AP does not offer a BSS for clients
    - Dedicated to RF spectrum analysis on all channels
    - It can send information to software such as Cisco Spectrum Expert on a PC to collect and analyze the data

- BRIDGE / MESH
    - Like the autonomous APs *outdoor bridge* mode, the lightweight AP can be a dedicated bridge between sites (Example:  over long distances)
    - A mesh can be made between the access points

- FLEX PLUS BRIDGE
    - Adds flexconnect functionality to the bridge / mesh mode
    - Allows wireless access points to locally forward traffic even if connectivity to the WLC is lost
    

![image](https://github.com/psaumur/CCNA/assets/106411237/940a414b-208f-408c-a3e2-37e3bfbb0d32)

---

CLOUD-BASED APs

- Cloud-based AP architecture is between autonomous AP and split-MAC architecture
    - Autonomous APs that are centrally managed in the cloud
- CISCO MERAKI is a popular cloud-based Wi-Fi solution
- The Meraki dashboard can be used to configure APs, monitor the network, generate performance reports, etc.
    - Meraki also tells each AP which channel to use, what transmit power, etc.
- However, data traffic is not sent to the cloud. It is sent directly to the wired network like when using autonomous APs
    - Only management / control traffic is sent to the cloud

![image](https://github.com/psaumur/CCNA/assets/106411237/8bd00a94-f965-4257-af46-82be67850feb)

![image](https://github.com/psaumur/CCNA/assets/106411237/93e62771-c2d5-4003-9ade-0d5be855ea66)

---

WIRELESS LAN CONTROLLER (WLC) DEPLOYMENTS

- In a split-MAC architecture, there four main WLC deployment modes:
    - UNIFIED
        - The WLC is a hardware applicance in a central location of the network
    - Cloud-based
        - The WLC is a VM running on a server, usually in a private cloud in a data center
        - This is not the same as the cloud-based AP architecture discussed previously
    - EMBEDDED
        - The WLC is integrated within a switch
    - MOBILITY EXPRESS
        - The WLC is integrated within an AP

---

UNIFIED WLC

- The WLC is a hardware applicance in a central location of the network
- A unified WLC can support up to about 6000 APs
- If more than 6000 APs are needed, additional WLCs can be added to the network

![image](https://github.com/psaumur/CCNA/assets/106411237/922eac1f-6c62-4926-89bb-a447f8be2edd)

---

CLOUD-BASED

- The WLC is a VM running on a server, usually in a private cloud in a data center
- Cloud-based WLCs can typically support up to about 3000 APs
- If more than 3000 APs are needed, more WLC VMs can be deployed

![image](https://github.com/psaumur/CCNA/assets/106411237/9d87546c-6397-48d2-941c-007f5e6440aa)

---

EMBEDDED WLC

- The WLC is embedded within a switch
- An embedded WLC can support up to about 200 APs
- If more than 200 APs are needed, more switches with embedded WLCs can be added

![image](https://github.com/psaumur/CCNA/assets/106411237/fc6a79f2-a7b5-4b5a-99d6-b94238362e8e)

---

CISCO MOBILITY EXPRESS WLC

- The WLC is embedded within an AP
- A MOBILITY EXPRESS WLC can support up to about 100 APs
- If more than 100 APs are needed, more APs with embedded Mobility Express WLCs can be added

![image](https://github.com/psaumur/CCNA/assets/106411237/4ff02aee-83c9-4a56-8a71-a14e20e8bf3c)
