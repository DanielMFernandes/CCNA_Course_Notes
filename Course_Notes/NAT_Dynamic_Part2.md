# 45. NAT (DYNAMIC): PART 2

MORE ABOUT STATIC NAT

- STATIC NAT involves statically configuring one-to-one mappings of PRIVATE IP ADDRESSES to PUBLIC IP ADDRESSES
- When traffic from the internal host is sent to the outside network, the router will translate the source address

![image](https://github.com/psaumur/CCNA/assets/106411237/60ba15dd-ee70-4bd9-b9a7-febf3ebbcd10)

- HOWEVER, this one-to-one mapping also allows external hosts to access the internal host via inside global address

![image](https://github.com/psaumur/CCNA/assets/106411237/09de8e06-249c-4185-9d09-ca5fc1435f5a)

---

DYNAMIC NAT

- In DYNAMIC NAT, the router DYNAMICALLY maps inside local addresses to inside global addresses, as needed
- An ACL is used to identify which traffic should be translated
    - If the source IP is permitted; the source IP will be translated
    - If the source IP is denied; the source IP will NOT be translated
        
        💡 However, Packet Traffic will NOT be dropped
        
        
- A NAT POOL is used to define the available inside global addresses

![image](https://github.com/psaumur/CCNA/assets/106411237/98fe2d7d-345c-4d6b-9772-4b152f9bd7a3)

  

- Although they are dynamically assigned, the mappings are still one-to-one (one inside local IP address per inside global IP address)
- If there are NOT enough inside global IP addresses available (=all are being used), it is called ‘NAT POOL EXHAUSTION’
    - If a packet from another inside host arrives and needs NAT but there are no available addresses, the router will drop the packet
    - The host will be unable to access outside networks until one of the inside global IP addresses becomes available
    - DYNAMIC NAT entries will time out automatically if not used, or you can clear them manually

NAT POOL EXHAUSTION

![image](https://github.com/psaumur/CCNA/assets/106411237/59c01575-b42f-475b-9502-2f9ed490ca8d)

192.168.0.167 TIMES OUT and 192.168.0.98 is assigned it’s TRANSLATED SOURCE IP

![image](https://github.com/psaumur/CCNA/assets/106411237/59e68f3b-8acc-4d7e-8d8e-f930dec3be5f)

DYNAMIC NAT CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/6694689a-4880-497c-a1f6-838003810f0c)

`show ip nat translations`

![image](https://github.com/psaumur/CCNA/assets/106411237/5b656147-f61c-4313-9a7e-34bec3ae6fbf)

![image](https://github.com/psaumur/CCNA/assets/106411237/04951fde-f130-43f8-b2ce-05eba6382329)

![image](https://github.com/psaumur/CCNA/assets/106411237/99bb39f3-2ea7-44d2-929e-223755726882)

---

DYNAMIC PAT (NAT OVERLOAD)

- PAT (NAT OVERLOAD) translates BOTH the IP address and the port number (if necessary)
- By using a unique port number for each communication flow, a single public IP address can be used by many different internal hosts
    - port numbers are 16 bits = over 65,000 available port numbers
- The router will keep track of which inside local address is using which inside global address and port

![image](https://github.com/psaumur/CCNA/assets/106411237/8f720b58-9700-4908-bd8d-a1846191854b)

PAT CONFIGURATION (POOL)

![image](https://github.com/psaumur/CCNA/assets/106411237/2a1acc30-658c-4479-9984-9c620b5e6ce3)

`show ip nat translations`

![image](https://github.com/psaumur/CCNA/assets/106411237/088db6f4-a695-4765-b435-2f20a5e16c9e)

PAT CONFIGURATION (INTERFACE)

![image](https://github.com/psaumur/CCNA/assets/106411237/8a3990ff-c58e-44a9-928d-e534f0cff690)

![image](https://github.com/psaumur/CCNA/assets/106411237/557d0217-80d2-4423-ba6a-041703568e13)

`show ip nat translations`

![image](https://github.com/psaumur/CCNA/assets/106411237/cae56ec7-38b5-4053-beda-ff670083718e)

---

COMMAND REVIEW

![image](https://github.com/psaumur/CCNA/assets/106411237/fe0655bb-4020-4ddc-bec4-b2fb198e2314)
