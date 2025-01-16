# 54. VIRTUALIZATION (CONTAINERS): PART 2

REVIEW OF VIRTUAL MACHINES (TYPE 1 AND TYPE2 HYPERVISORS)

![image](https://github.com/psaumur/CCNA/assets/106411237/bfc801ca-a603-4957-a67c-316fb72e25cb)

![image](https://github.com/psaumur/CCNA/assets/106411237/da1b653d-f5f2-42d3-8088-dd3daa430913)

- Virtual Machines (VMs) allow multiple OS’s to run on a single physical server
- A hypervisor is used to manage and allocate hardware resources to each VM
    - Type 1 hypervisors (aka native or bare-metal) run directly on top of hardware
    - Type 2 hypervisors (aka hosted) run on top of a host OS (ie: Windows)
- Type 1 hypervisors are widely used in data center environments
- Type 2 hypervisors are commonly used on personal devices
    - Running a virtual network lab on your PC using Cisco Modeling Labs (CML)

- The OS in each VM can be the same or different (Windows, Linux, MacOS, etc)
- *Bins / Libs* are the software libraries / services needed by the Apps running in each VM
- A VM allows it’s app / apps to run in an isolated environment, separate from the apps in other VMs.
- VMs are easy to create, delete, move, etc.
    - A VM can be easily saved and moved between different physical servers.

![image](https://github.com/psaumur/CCNA/assets/106411237/5ed6704c-f332-49bf-8ff9-ad17a7f74b76)

---

CONTAINERS

![image](https://github.com/psaumur/CCNA/assets/106411237/4f350818-f030-46fe-8850-f2e633d22bfa)

- CONTAINERS are software packages that contain an APP and all dependencies (*Bins/Libs* in the diagram) for the contained app to run.
    - Multiple apps can be run in a single container, but this is not how container are usually used
- Containers run on a CONTAINER ENGINE (ie: Docker Engine)
    - The container engine is run on a host OS (usually Linux)
- Containers are lightweight (small in size) and include only the dependencies required to run the specific app
- A CONTAINER ORCHESTRATOR is a software platform for automating the deployment, management, scaling, etc of containers
    - KUBERNETES (originally design by Google) is the most popular container orchestrator
    - DOCKER SWARM is Docker’s container orchestration tool
- In small numbers, manual operation is possible, but large-scale systems (ie: with Microservices) can require thousands of containers

![image](https://github.com/psaumur/CCNA/assets/106411237/07083826-c7b0-45c1-aefe-e05f63d7acfd)

---

VIRTUAL MACHINES vs. CONTAINERS

![image](https://github.com/psaumur/CCNA/assets/106411237/98a4075d-ab70-4579-ba10-c129e935ca22)

- VMs can take minutes to boot up as each VM runs it’s own OS
- Containers can boot up in milliseconds

- VMs take more disk space (Gigabytes)
- Containers take up very little disk space (Megabytes)

- VMs use more CPU/RAM resources (each VM must run its own OS)
- Containers use fewer CPU/RAM resources (shared OS)

- VMs are portable and can move between physical systems running the same hypervisor
- Containers are more portable; they are smaller, faster to boot up, and Docker containers can be run on nearly any container service

- VMs are more isolated because each VM runs it’s own OS
- Containers are less isolated because they all run on the same OS; if the OS crashes, all containers running on it are effected

![image](https://github.com/psaumur/CCNA/assets/106411237/128a8574-a555-4a3e-9e9c-62f33df2d34d)
