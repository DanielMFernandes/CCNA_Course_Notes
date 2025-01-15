# 54. VIRTUALIZATION AND CLOUD: PART 1

VIRTUAL SERVERS

- Although Cisco is more known for their networking devices (routers, SWITCHES, FIREWALLS), they also offer hardware servers such as UCS (Unified Computing System)
- The largest vendors of hardware servers include Dell, EMC, HPE, and IBM

---

SERVERS BEFORE VIRTUALIZATION

![image](https://github.com/psaumur/CCNA/assets/106411237/365cde17-88c6-4149-91f2-d67c79590aec)

- Before VIRTUALIZATION, there was a one-to-one relationship between a PHYSICAL server and OPERATION SYSTEM
- In that OPERATING SYSTEM, apps providing services (such as a WEB server, EMAIL server, etc) would run
- One PHYSICAL server would be used for the WEB server, one for the EMAIL server, one for the DATABASE server, etc.
- This is inefficient for multiple reasons:
    - Each PHYSICAL server is expensive and takes up space, power, etc.
    - The RESOURCES on each PHYSICAL server (CPU, RAM, STORAGE, NIC) are typically under-utilized

---

VIRTUALIZATION (TYPE 1 HYPERVISOR)

![image](https://github.com/psaumur/CCNA/assets/106411237/62a40737-7451-4b38-a5bd-abd9367cbd40)

- VIRTUALIZATION allows us to break the one-to-one relationships of hardware to OS, allowing multiple OS’s to run on a single PHYSICAL server
- Each INSTANCE is called a VM (Virtual Machine)
- A HYPERVISOR is used to manage and allocate the hardware RESOURCES (CPU, RAM, etc.) to each VM
- Another name for a HYPERVISOR is VMM (Virtual Machine Monitor)
- The type of HYPERVISOR which runs directly on top of hardware is called a TYPE 1 HYPERVISOR
    - Examples include : VMware ESXi, Microsoft Hyper-V, etc.
- TYPE 1 HYPERVISORS are also called *bare-metal hypervisors* because they run directly on the hardware (metal).
    - Another term is *native hypervisor*
- This is the type of HYPERVISOR used in data center environments

---

VIRTUALIZATION (TYPE 2 HYPERVISOR)

![image](https://github.com/psaumur/CCNA/assets/106411237/25a29935-a56d-4ffe-b9e4-15c5c50bca46)

- TYPE 2 HYPERVISORS run as a program on an OS like a regular computer program
    - Examples: VMware Workstation, Oracle Virtualbox, etc
- The OS running directly on the hardware is called the HOST OS
- The OS running in a VM is called a GUEST OS
- Another name for a TYPE 2 HYPERVISOR is *hosted hypervisor*
- Although TYPE 2 HYPERVISORS are rarely used in data center environments, they are common on personal-use devices (for example, if a MAC/Linux user needs to run an app that is only supported on Windows, or vice-versa)

---

WHY VIRTUALIZATION?

- PARTITIONING :
    - Run multiple OS’s on ONE PHYSICAL MACHINE
    - Divide system resources between VIRTUAL MACHINES
    
- ISOLATION :
    - Provide FAULT and SECURITY ISOLATION at the hardware level
    - Preserve performance with advanced resource controls
- ENCAPSULATION :
    - Save the entire state of a virtual machine to files
    - Move and copy virtual machines as easily as moving and copying files

- HARDWARE INDEPENDENCE :
    - Provision or migrate any virtual machine to any physical server

![image](https://github.com/psaumur/CCNA/assets/106411237/f0f5f886-7924-46fc-addf-6916f0d2b2c9)

---

VIRTUAL NETWORKS

![image](https://github.com/psaumur/CCNA/assets/106411237/7bf3f22c-a7b8-41bf-bc1e-8c128a41f20f)

- VMs are connected to each other and the external network via a VIRTUAL SWITCH running on the HYPERVISOR
- Just like a regular PHYSICAL SWITCH, the vSWITCH’s interfaces can operate as ACCESS ports or TRUNK ports and use VLANs to separate the VMs at LAYER 2
- Interfaces on the vSWITCH connect to the physical NIC (or NICs) of the server to communicate with the external network

---

INTRO TO CLOUD COMPUTING

- Traditional IT infrastructure deployments were some combination of the following:
    - ON-PREMISES
        - All servers, network devices, and other infrastructure are located on company property
        - All equipment is purchased and owned by the company using it
        - The company is responsible for the necessary space, power, and cooling
    
    - CO-LOCATION
        - Data centers that rent out space for customers to put their infrastructure (servers, network devices)
        - The data center provides the space, electricity, and cooling
        - The servers, network devices, etc are still the responsibility of the end customer, although they are not located on the customer’s premises
- Cloud SERVICE provide an alternative that is hugely popular and is continuing to grow
    - Most people associate “cloud” with PUBLIC cloud PROVIDERS such as AWS
        - Although this is the most common USE of cloud services, it’s not the only one

---

CLOUD SERVICES

- The American NIST (National Institute of Standards and Technology) defined cloud computing in SP (Special Publication) 800-145

![image](https://github.com/psaumur/CCNA/assets/106411237/746a4f38-01b9-49cf-8dd9-5522b4cabf7b)

- To understand what the cloud is, let’s look at the following outlined in SP 800-145:
    - FIVE ESSENTIAL CHARACTERISTICS
    - THREE service models
    - FOUR DEPLOYMENT models

---

THE FIVE ESSENTIAL CHARACTERISTICS OF CLOUD

- ON-DEMAND SELF-SERVICE
    - The CUSTOMER is able to use the service (or stop the service) freely (via a web portal) without direct communication to the service PROVIDER

- BROAD NETWORK ACCESS
    - The service is available through standard network connections (ie: the Internet or PRIVATE WAN) and can be access through many kinds of devices
- RESOURCE POOLING
    - A POOL of RESOURCES is provided by the service PROVIDER and when a CUSTOMER requests a service (for example creates a new VM), the RESOURCES to fulfill that request are allocated from the shared POOL
- RAPID ELASTICITY
    - CUSTOMERS can quickly expand the service they use in the cloud (for example: add new VMs, expand STORAGE, etc) from a POOL of RESOURCES that appear to be infinite. Likewise, they can quickly reduce their services when not needed
- MEASURED SERVICE
    - The cloud service PROVIDER measures the CUSTOMER’s usage of cloud RESOURCES and the CUSTOMER can measure their own use as well. CUSTOMERS are charged based on usage (for example: X Dollars per Gigabyte of STORAGE per day)

---

THE THREE SERVICE MODELS OF THE CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/a3f0e08a-3207-4a69-aa81-d4142d6735a3)

- In cloud COMPUTING, everything is provided on a “service” model
- For example: rather than the END USER buying a PHYSICAL server, mounting it on a rack, installing the hypervisor, creating the VM, etc. the service PROVIDER offers all of this as a service
- There are a variety of services referred to as “___________ as a service” or “__aaS”
- The THREE service models of cloud COMPUTING are:
    
    Software as a service (SaaS) - Example : MS Office 365
    
![image](https://github.com/psaumur/CCNA/assets/106411237/5bcfedb7-3ab6-462a-a089-09884d220ab7)
    
    PLATFORM as a service (PaaS) - Examples : AWS Lambda and Google App Engine 
    
![image](https://github.com/psaumur/CCNA/assets/106411237/e3886b6b-4ed8-4358-ba47-e2f50378c53d)
    
    INFRASTRUCTURE as a service (Iaas) - Examples: Amazon EC2 and Google Compute Engine
    
![image](https://github.com/psaumur/CCNA/assets/106411237/f8144a61-0d7f-4928-9e47-73fb969e0b4a)
    

---

DEPLOYMENT MODELS

- Most people assume that “cloud” means PUBLIC cloud PROVIDERS like AWS, AZURE, and GCP
- Although “PUBLIC cloud” is the most common deployment model, it’s not the ONLY one
- The FOUR DEPLOYMENT models of cloud COMPUTING are:

- PRIVATE CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/b8953a31-3861-41ef-99df-62a49b97610a)

- PRIVATE cloud are generally only used by large enterprises
- Although the cloud is PRIVATE, it may be owned by a THIRD PARTY
    - For example: AWS provides PRIVATE cloud services for the American DoD
- PRIVATE clouds may be ON or OFF PREMISES
    - Many people assume “cloud” and “ON-PREM” are two different things but that is not always the case
- The same kind of services offered are the same as in PUBLIC clouds (SaaS, PaaS, IaaS) but the infrastructure is reserved for a SINGLE ORGANIZATION

- COMMUNITY CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/1c9008e9-205b-4ca8-8236-fc0b02c3addc)

- Least common CLOUD deployment
- Similar to PRIVATE cloud, but the INFRASTRUCTURE is reserved for use by a SPECIFIC GROUP or ORGANIZATION

- PUBLIC CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/94e9c895-9538-4664-93db-085f013ee9fb)

- The most common cloud deployment
- Popular PUBLIC cloud service providers include:
    - AWS
    - MS AZURE
    - GCP (Google Cloud Platform)
    - OCI (Oracle Cloud Infrastructure)
    - IBM Cloud
    - Alibaba Cloud

- HYBRID CLOUD
    
![image](https://github.com/psaumur/CCNA/assets/106411237/14f910cf-b6e2-4f75-8959-4589d2592e1c)
    
    - Basically ANY combination of the preview THREE DEPLOYMENT TYPES
    - Example: A PRIVATE cloud which can offload to a PUBLIC cloud when necessary

---

BENEFITS OF CLOUD COMPUTING

- COST
    - CapEx (Capital Expense) of buying hardware and software, setting up DATA CENTERS, etc. are reduced or eliminated
- GLOBAL SCALE
    - cloud services can scale GLOBALLY at a rapid pace. services can be set up and offered to CUSTOMERS from a geographic location close to them

- SPEED / AGILITY
    - Services are provide ON DEMAND and vast amounts of RESOURCES can be provisioned within minutes

- PRODUCTIVITY
    - cloud services remove the need for many time-consuming tasks such as procuring physical servers, racking them, cabling, installing and updating equipment, etc.
- RELIABILITY
    - Backups in the cloud are very easy to perform. Data can be mirrored at multiple sites in different geographic locations to support disaster recovery

---

CONNECTION TO PUBLIC CLOUDS

![image](https://github.com/psaumur/CCNA/assets/106411237/671747bb-6908-47bb-b9c8-47f2df82c821)
