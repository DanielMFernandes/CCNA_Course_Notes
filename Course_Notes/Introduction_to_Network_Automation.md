# 59. INTRODUCTION TO NETWORK AUTOMATION

WHY NETWORK AUTOMATION

- Previous versions of the CCNA focused on the traditional model of managing / controlling networks
- The current version focuses on the traditional model as well, but CCNA candidates are expected to have a basic understanding of various topics related to network automation
- In the traditional model, engineers manage devices one at a time by connecting to their CLI via SSH

---

DOWNSIDES OF CONFIGURING DEVICES ONE-BY-ONE

- Typos and other small mistakes are common
- It is time-consuming and very inefficient in large-scale networks
- It is difficult to ensure that all devices adhre to the organization’s standard configuration

---

BENEFITS OF NETWORK AUTOMATION

- Human Error (Typos, etc) is reduced
- Networks become much more scalable and implemented in a fraction of the time
    - New deployments
    - Network-wide changes
    - Troubleshooting
- Network-wide policy compliance can be assured
    - Standard configurations
    - Software versioning

- The improved efficiency of network operations reduces the OP-EX (operating expenses) of the network. Each task requires fewer man-hours

```
There are various tools / methods that can be used to automate tasks in the network

- SDN (Software-Defined Networking)
- Ansible
- Puppet
- Python scripts
- etc…
```

---

LOGICAL “PLANES” OF NETWORK FUNCTIONS

**What does a router do?**

- It forwards messages between networks by examining information in the Layer 3 header
- It uses a routing protocol like OSPF to share route information with other routers and build a routing table
- It uses ARP to build an ARP table, mapping IP addresses to MAC addresses
- It uses Syslog to keep logs of events that occur
- and much more…

**What does a switch do?**

- It forwards messages within a LAN by examining information in the Layer 2 header
- It uses STP to ensure there are no Layer 2 loops in the network
- It builds a MAC address table by examining the Source MAC address of frames
- It uses Syslog to keep logs of events that occur
- It allows a user to connect to it via SSH and manage it

---

The various functions of network devices can be logically divided up (categorized) into *PLANES*

```
- DATA PLANE
- CONTROL PLANE
- MANAGEMENT PLANE
```


- The operations of the management plane and the control plane are usually managed by the CPU
- However, this is not desirable for data plane operations because CPU processing is slow (relatively speaking)
- Instead, a specialized hardware ASIC (Application-Specific Integrated Circuit) is used.
    - ASICs are chips built for a specific purpose
- Using a switch, as an example:
    - When a frame is received, the ASIC (not the CPU) is responsible for the switching logic
    - The MAC address table is stored in a kind of memory called TCAM (Ternary Content-Addressable Memory)
        - Another common name for the MAC Address table is CAM table
    - The ASIC feeds the destination MAC address of the frame into the TCAM which returns the matching MAC address table entry
    - The frame is then forwarded out of the appropriate device
- Modern routers also use a similar hardware data plane: An ASIC designed for forwarding logic, and tables store in TCAM

---

A SIMPLE SUMMARY:

>- When a device receives control / management traffic (destined for itself), it will be processed in the CPU
>- When a device receives data traffic which should pass through the device, it is processed by the ASIC for maximum speed

---

DATA PLANE

- All tasks involved in forwarding user data / traffic from one interface to another are part of the data plane
- A router receives a message, looks for the most specific matching router in its routing table, and forwards it out of the appropriate interface to the next hop
    - It also de-encapsulates the original layer 2 header, and re-encapsulates with a new header destined for the next hop’s MAC address
- A switch receives a message, looks at the destination MAC address, and forwards it out of the appropriate interface (or floods it)
    - This includes functions like adding / removing 802.1q VLAN tags
- NAT (changing the source / destination addresses before forwarding) is part of the data plane
- Deciding to forward / discard messages due to ACL’s, port-security, etc. is part of the data plane
- The data plane is also called the ‘forwarding plane’

![image](https://github.com/psaumur/CCNA/assets/106411237/6a72186b-2956-45f6-8643-801caa2cb28e)

---

CONTROL PLANE

- How does a device’s data plane make its forwarding decisions?
    - Routing table
    - MAC address table
    - ARP table
    - STP
    - etc…
    
- Functions that build these tables (and other functions that influence the data plane) are part of the control plane

- The control plane *controls* what the data plane does, for example by building the router’s routing table

- The control plane performs *overhead* work
    - OSPF itself doesn’t forward user data packets, but it informs the data plane about how packets should be forwarded
    - STP itself isn’t directly involved in the process of forwarding frames, but it informs the data plane about which interfaces should and shouldn’t be used to forward frames
    - ARP messages aren’t user data but they are used to build an ARP table which is used in the process of forwarding data

![image](https://github.com/psaumur/CCNA/assets/106411237/4c21b082-5d6e-4388-94c5-bebf33b50c8d)

---

MANAGEMENT PLANE

- Like the control plane, the management plane performs overhead work
    - However, the management plane doesn’t directly affect the forwarding of messages in the data plane
- The management plane consists of protocols that are used to manage devices
    - SSH / TELNET : Used to connect to the CLI of a device to configure / manage it
    - SYSLOG : Used to keep logs of events that occur on the device
    - SNMP : Used to monitor the operations of the device
    - NTP : Used to maintain accurate time on the device

![image](https://github.com/psaumur/CCNA/assets/106411237/3cfffa40-f4cb-4042-8778-139605c2eb26)

---

SOFTWARE-DEFINED NETWORKING (SDN)

- SOFTWARE-DEFINED NETWORKING (SDN) is an approach to networking that centralizes the control plane into an application called a *CONTROLLER*
- SDN is also called SOFTWARE-DEFINED-ARCHITECTURE (SDA) or CONTROLLER-BASED NETWORKING
- Traditional control planes use a distributed architecture
    - For example:
        - Each router in the network runs OSPF and the routers share routing information and then calculate their preferred routes to each destination
- An SDN controller centralized control plane functions like calculation routes
    - That is just an example and how much of the control plane is centralized varies greatly
- The controller can interact programmatically with the network device using APIs (Application Programming Interface)

![image](https://github.com/psaumur/CCNA/assets/106411237/05c4c5d9-5ba4-480c-9c13-72fa1f7937db)

---

SOUTHBOUND INTERFACE (SBI)

- The SBI is used for communications between the controller and the network devices it controls
- It typically consists of a communication protocol and API (Application Programming Interface)

- APIs facilitate data exchanges between programs
    - Data is exchanged between the controller and the network devices
    - An API on the network devices allows the controller to access information on the devices, control their data plane tables, etc.
- Some examples of SBIs :
    - OpenFlow
    - Cisco OpFlex
    - Cisco OnePK (Open Network Environment Platform Kit)
    - NETCONF

---

 NORTHBOUND INTERFACE (NBI)

- Using the SBI, the controller communicates with the managed devices and gathers information about them:
    - The devices in the network
    - The topology (how the devices are connected together)
    - The available interfaces on each device
    - Their configurations
- The Northbound interface (NBI) is what allows us to:
    - Interact with the controller
    - Access the data it gathers about the network
    - Program the network
    - Make changes to the network via the SBI

- A REST API (Representational State Transfer) is used on the controller as an interface for apps to interact with it
- OSGi (Java Open Services Gateway Initiative) - Java based NBI API

- Data is sent in a structured (*serialized*) format such as JSON or XML
    - This makes it easier for programs to use the data

![image](https://github.com/psaumur/CCNA/assets/106411237/d980626f-f731-46a4-ba14-72c3d21f2fd3)

---

AUTOMATION IN TRADITIONAL NETWORKS VS SDN

- Networking tasks can be automated in traditional network architectures too:
    - Scripts can be written (ie: using Python) to push commands to many devices at once
    - Python with good use of regular expressions can parse through “show” commands to gather information about network devices
    
- However, the robust and centralized data collected by SDN controllers greatly facilitates these functions
    - The controller collects information about all devices in the network
    - Northbound APIs allow apps to access information in a format that is easy for programs to understand (ie: JSON and XML)
    - The centralized data facilitates network-wide analytics
- SDN Tools can provide the benefits of automation without the requirement of third-party scripts and apps.
    - You don’t need expertise in automation to make use of SDN Tools
    - However, APIs allow third-party applications to interact with the controller, which can be very powerful


💡 Although SDN and automation aren’t the same thing, the SDN architecture greatly facilitates the automation of various tasks in the network via the SDN controller and APIs
