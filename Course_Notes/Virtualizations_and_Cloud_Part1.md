# 54. VIRTUALIZATION AND CLOUD: PART 1

VIRTUAL SERVERS

- Although Cisco is more known for their networking devices (routers, switches, firewalls), they also offer hardware servers such as UCS (Unified Computing System)
- The largest vendors of hardware servers include Dell, EMC, HPE, and IBM

---

SERVERS BEFORE VIRTUALIZATION

![image](https://github.com/psaumur/CCNA/assets/106411237/365cde17-88c6-4149-91f2-d67c79590aec)

- Before virtualization, there was a one-to-one relationship between a physical server and operating system
- In that operating system, apps providing services (such as a web server, email server, etc) would run
- One physical server would be used for the web server, one for the email server, one for the database server, etc.
- This is inefficient for multiple reasons:
    - Each physical server is expensive and takes up space, power, etc.
    - The resources on each physical server (CPU, RAM, storage, NIC) are typically under-utilized

---

VIRTUALIZATION (TYPE 1 HYPERVISOR)

![image](https://github.com/psaumur/CCNA/assets/106411237/62a40737-7451-4b38-a5bd-abd9367cbd40)

- Virtualization allows us to break the one-to-one relationships of hardware to OS, allowing multiple OS’s to run on a single physical server
- Each INSTANCE is called a VM (Virtual Machine)
- A HYPERVISOR is used to manage and allocate the hardware resources (CPU, RAM, etc.) to each VM
- Another name for a hypervisor is VMM (Virtual Machine Monitor)
- The type of hypervisor which runs directly on top of hardware is called a type 1 hypervisor
    - Examples include : VMware ESXi, Microsoft Hyper-V, etc.
- Type 1 hypervisors are also called *bare-metal hypervisors* because they run directly on the hardware (metal).
    - Another term is *native hypervisor*
- This is the type of hypervisor used in data center environments

---

VIRTUALIZATION (TYPE 2 HYPERVISOR)

![image](https://github.com/psaumur/CCNA/assets/106411237/25a29935-a56d-4ffe-b9e4-15c5c50bca46)

- Type 2 hypervisors run as a program on an OS like a regular computer program
    - Examples: VMware Workstation, Oracle Virtualbox, etc
- The OS running directly on the hardware is called the HOST OS
- The OS running in a VM is called a GUEST OS
- Another name for a type 2 hypervisor is *hosted hypervisor*
- Although type 2 hypervisors are rarely used in data center environments, they are common on personal-use devices (for example, if a MAC/Linux user needs to run an app that is only supported on Windows, or vice-versa)

---

WHY VIRTUALIZATION?

- PARTITIONING :
    - Run multiple OS’s on one physical machine
    - Divide system resources between virtual machines
    
- ISOLATION :
    - Provide fault and security isolation at the hardware level
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

- VMs are connected to each other and the external network via a virtual switch running on the hypervisor
- Just like a regular physical switch, the vSwitch’s interfaces can operate as access ports or trunk ports and use VLANs to separate the VMs at layer 2
- Interfaces on the vSwitch connect to the physical NIC (or NICs) of the server to communicate with the external network

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
- Cloud service provide an alternative that is hugely popular and is continuing to grow
    - Most people associate “cloud” with public cloud providers such as AWS
        - Although this is the most common use of cloud services, it’s not the only one

---

CLOUD SERVICES

- The American NIST (National Institute of Standards and Technology) defined cloud computing in SP (Special Publication) 800-145

![image](https://github.com/psaumur/CCNA/assets/106411237/746a4f38-01b9-49cf-8dd9-5522b4cabf7b)

- To understand what the cloud is, let’s look at the following outlined in SP 800-145:
    - Five essential characteristics
    - Three service models
    - Four deployment models

---

THE FIVE ESSENTIAL CHARACTERISTICS OF CLOUD

- ON-DEMAND SELF-SERVICE
    - The customer is able to use the service (or stop the service) freely (via a web portal) without direct communication to the service provider

- BROAD NETWORK ACCESS
    - The service is available through standard network connections (ie: the Internet or private WAN) and can be access through many kinds of devices
- RESOURCE POOLING
    - A pool of resources is provided by the service provider and when a customer requests a service (for example creates a new VM), the resources to fulfill that request are allocated from the shared pool
- RAPID ELASTICITY
    - Customers can quickly expand the service they use in the cloud (for example: add new VMs, expand storage, etc) from a pool of resources that appear to be infinite. Likewise, they can quickly reduce their services when not needed
- MEASURED SERVICE
    - The cloud service provider measures the customer’s usage of cloud resources and the customer can measure their own use as well. customers are charged based on usage (for example: X Dollars per Gigabyte of storage per day)

---

THE THREE SERVICE MODELS OF THE CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/a3f0e08a-3207-4a69-aa81-d4142d6735a3)

- In cloud computing, everything is provided on a “service” model
- For example: rather than the end user buying a physical server, mounting it on a rack, installing the hypervisor, creating the VM, etc. the service provider offers all of this as a service
- There are a variety of services referred to as “___________ as a service” or “__aaS”
- The three service models of cloud computing are:
    
    Software as a Service (SaaS) - Example : MS Office 365
    
![image](https://github.com/psaumur/CCNA/assets/106411237/5bcfedb7-3ab6-462a-a089-09884d220ab7)
    
    Platform as a Service (PaaS) - Examples : AWS Lambda and Google App Engine 
    
![image](https://github.com/psaumur/CCNA/assets/106411237/e3886b6b-4ed8-4358-ba47-e2f50378c53d)
    
    Infrastructure as a Service (IaaS) - Examples: Amazon EC2 and Google Compute Engine
    
![image](https://github.com/psaumur/CCNA/assets/106411237/f8144a61-0d7f-4928-9e47-73fb969e0b4a)
    

---

DEPLOYMENT MODELS

- Most people assume that “cloud” means public cloud providers like AWS, AZURE, and GCP
- Although “public cloud” is the most common deployment model, it’s not the only one
- The four deployment models of cloud computing are:

PRIVATE CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/b8953a31-3861-41ef-99df-62a49b97610a)

- Private cloud are generally only used by large enterprises
- Although the cloud is private, it may be owned by a third party
    - For example: AWS provides private cloud services for the American DoD
- Private clouds may be ON or OFF PREMISES
    - Many people assume “cloud” and “on-prem” are two different things but that is not always the case
- The same kind of services offered are the same as in public clouds (SaaS, PaaS, IaaS) but the infrastructure is reserved for a single organization

COMMUNITY CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/1c9008e9-205b-4ca8-8236-fc0b02c3addc)

- Least common cloud deployment
- Similar to private cloud, but the infrastructure is reserved for use by a specific group or organization

PUBLIC CLOUD

![image](https://github.com/psaumur/CCNA/assets/106411237/94e9c895-9538-4664-93db-085f013ee9fb)

- The most common cloud deployment
- Popular public cloud service providers include:
    - AWS
    - MS AZURE
    - GCP (Google Cloud Platform)
    - OCI (Oracle Cloud Infrastructure)
    - IBM Cloud
    - Alibaba Cloud

HYBRID CLOUD
    
![image](https://github.com/psaumur/CCNA/assets/106411237/14f910cf-b6e2-4f75-8959-4589d2592e1c)
    
    - Basically any combination of the preview three deployment types
    - Example: A private cloud which can offload to a public cloud when necessary

---

BENEFITS OF CLOUD COMPUTING

- COST
    - CapEx (Capital Expense) of buying hardware and software, setting up data centers, etc. are reduced or eliminated
- GLOBAL SCALE
    - Cloud services can scale globally at a rapid pace. services can be set up and offered to customers from a geographic location close to them

- SPEED / AGILITY
    - Services are provide on demand and vast amounts of resources can be provisioned within minutes

- PRODUCTIVITY
    - Cloud services remove the need for many time-consuming tasks such as procuring physical servers, racking them, cabling, installing and updating equipment, etc.
- RELIABILITY
    - Backups in the cloud are very easy to perform. Data can be mirrored at multiple sites in different geographic locations to support disaster recovery

---

CONNECTION TO PUBLIC CLOUDS

![image](https://github.com/psaumur/CCNA/assets/106411237/671747bb-6908-47bb-b9c8-47f2df82c821)
