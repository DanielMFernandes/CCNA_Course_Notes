# 54. VIRTUALIZATION (VRF): PART 3

INTRO TO VRF

![image](https://github.com/psaumur/CCNA/assets/106411237/e122f3c6-290f-4f33-a31d-f308f12140a3)

- VIRTUAL ROUTING AND FORWARDING (VRF) is used to divide a single router into multiple virtual routers
    - Similar to how VLANs are used to divide a single switch (LAN) into multiple virtual switches (VLANs)
- It does this by allowing a router to build multiple separate routing tables
    - Interfaces (LAYER 3 only) and routers are configured to be in a specific VRF (aka *VRF INSTANCE*)
    - Router interfaces, SVIs and routed ports on multilayer switches can be configured in a VRF
- Traffic in one VRF cannot be forwarded out of an interface in another VRF
    - As an exception, VRF LEAKING can be configured to allow traffic to pass between VRFs
- VRF is commonly used to facilitate MPLS (Multiple Protocol Label Switching)
    - The kind of VRF we are talking about is VRF-Lite (VRF without MPLS)
- VRF is commonly used by service providers to allow one device to carry traffic from multiple customers
    - Each CUSTOMER’S traffic is isolated from the outside
    - CUSTOMER IP ADDRESSES can overlap without issue

VRF CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/fec7669b-8868-4529-81fa-6f52e07ff6e4)

Creation and Configuration of VRFs

![image](https://github.com/psaumur/CCNA/assets/106411237/624ebfc0-c7c0-498d-a00b-c19e2738585a)

How to `show ip route` for VRFs

![image](https://github.com/psaumur/CCNA/assets/106411237/cbe724be-4497-4976-9927-18ff5c71a4c7)

`ping` other VRFs

![image](https://github.com/psaumur/CCNA/assets/106411237/f29dd935-0ec7-4756-b24a-fc44391254c0)
