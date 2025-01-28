# 62. SOFTWARE DEFINED NETWORKING (SDN)

SD REVIEW

- Software Defined Networking (SDN) is an approach to networking that centralizes the control plane into an application called a *controller*
- Traditional control planes use a distributed architecture
- A SDN controller centralizes control plane functions like calculating routes
- The controller can interact programmatically with the network devices using APIs
- The SBI (SouthBound Interface) is used for communications between the controller and the network device it controls
- The NBI (NorthBound Interface) is what allows us to interact with the controller with our scripts and applications

SDN ARCHITECTURE

![image](https://github.com/psaumur/CCNA/assets/106411237/9d7e1a89-3537-48cc-a410-cef352b6a2cb)

---

CISCO SD-ACCESS

- Cisco SD-ACCESS is Cisco’s SDN solution for automating campus LANs
- ACI (Application Centric Infrastructure) is their SDN solution for automating data center networks
- SD-WAN is their SDN solution for automating WANs
- Cisco DNA (Digital Network Architecture) Center is the controller at the center of SD-Access

![image](https://github.com/psaumur/CCNA/assets/106411237/4c1662ee-490c-4eee-8970-550ca60feabb)

- The UNDERLAY is the underlying physical network of devices and connections (including wired and wireless) which provide IP connectivity (ie: using IS-IS)
    - Multilayer Switches and their connections

![image](https://github.com/psaumur/CCNA/assets/106411237/41bb11dd-31c9-493e-9fec-af847f0732dc)

- The OVERLAY is the virtual network built on top of the physical underlay network

![image](https://github.com/psaumur/CCNA/assets/106411237/99f48b9e-ed68-4c11-b456-d0f6ccf13fed)

- The FABRIC is the combination of the overlay and underlay; the physical and virtual network as a whole

![image](https://github.com/psaumur/CCNA/assets/106411237/35cf981c-337d-4117-9124-9f210e85bff3)

---

SD-ACCESS UNDERLAY

- The underlay’s purpose is to support the VXLAN tunnels of the overlay
- There are three different roles for switches in SD-Access:
    - EDGE NODES : Connect to end hosts
    - BORDER NODES : Connect to devices outside of the SD-Access Domain ; ie: WAN routers
    - CONTROL NODES : Uses LISP (Locator ID Separation Protocol) to perform various control plane functions
    
- You can add SD-Access on top of the existing network (*brownfield deployment*) if your network hardware and software supports it
    - Google ‘Cisco SD-Access compatibility matrix’ if you are curious
    - In this case DNA Center won’t configure the underlay

- A new deployment (*greenfield deployment)* will be configured by DNA Center to use the optimal SD-Access underlay:
    - All Switches are layer 3 and use IS-IS as their routing protocol
    - All Links between Switches are routed ports. This means STP is not needed
    - Edge nodes (Access switches) act as the the default gateway of end hosts *(Routed Access Layer)*

![image](https://github.com/psaumur/CCNA/assets/106411237/0315f1e5-d9c6-47ce-acf2-1de6f14ac89c)

![image](https://github.com/psaumur/CCNA/assets/106411237/84d48992-30f9-45cf-856a-089ce00d0641)

---

SD-ACCESS OVERLAY

- LISP (Locator ID Separation Protocol) provides the control plane of SD-Access
    - A list of mappings of EIDs (endpoint identifiers) to RLOCs (routing locators) is kept
    - EIDs identify end hosts connected to edge switches
    - RLOCS identify the edge switch which can be used to reach the end host
    - There is a lot more detail to cover about LISP but I think you can see how it differs from traditional control plane
    
- Cisco TrustSec (CTS) provides policy control (QoS, Security Policy, etc.)

- VXLAN provides the DATA PLANE of SD-Access

![image](https://github.com/psaumur/CCNA/assets/106411237/8fd0bb65-31df-4db5-a79c-044c68c37b01)

![image](https://github.com/psaumur/CCNA/assets/106411237/b4c017b1-cc59-4305-9924-f25a5445a36b)

![image](https://github.com/psaumur/CCNA/assets/106411237/5adcaf16-4caf-4de2-9b8f-3e777c841bc6)

---

CISCO DNA CENTER

- Cisco DNA Center has two main roles:
    - The SDN Controller in SD-Access
    - A network manager in a traditional network (non-SD-Access)
- DNA Center is an application installed on Cisco UCS server hardware
- It has a REST API which can be used to interact with DNA Center
- The SBI supports protocols such as NETCONF and RESTCONF (as well as traditional protocols like Telnet, SSH, and SNMP)
- DNA Center enables *Intent-Based Networking* (IBN)
    - The goal is to allow the engineer to communicate their intent for network behavior to DNA Center, and then DNA Center will take care of the details of the actual configurations and policies on devices

- Traditional security policies using ACLs can become very cumbersome
    - ACLs can have thousands of entries
    - The intent of entries is forgotten with time and as engineers leave and new engineers take over

- DNA Center allows the engineer to specify the intent of the policy
    - Examples :
        - This group of users can’t communicate with that group
        - This group can access this server but not that server
    - DNA Center will take care of the exact details of implementing this policy

![image](https://github.com/psaumur/CCNA/assets/106411237/30773f46-3564-4d66-a175-20962d1569dd)

---

>For more details, you can check out [sandboxdnac.cisco.com](http://sandboxdnac.cisco.com) (User: devnetuser, Password: Cisco123!)

---

DNA CENTER NETWORK MANAGEMENT VS. TRADITIONAL

Traditional Management :

- Devices are configured one-by-one via SSH or Console connection
- Devices are manually configured via Console connection before being deployed
- Configurations and polices are managed per-device
- New network deployments can take a long time due to the manual labor required
- Errors and failures are more likely due to increased manual effort

DNA CENTER-based Network Management :

- Devices are centrally managed and monitored from the DNA Center GUI or other applications using it’s REST API
- The Administrator communicates their intended network behavior to DNA Center, which changes those intentions into configurations on the managed network devices
- Configurations and policies are centrally managed
- Software versions are also centrally managed. DNA Center can monitor cloud servers for new versions and then update the managed devices
- New network deployments are much quicker. New devices can automatically receive their configurations from DNA Center without manual configuration

![image](https://github.com/psaumur/CCNA/assets/106411237/cb9e0184-6b45-4dcc-85ae-cef3245c1629)
