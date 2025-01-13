# 51. DYNAMIC ARP INSPECTION

WHAT IS DYNAMIC ARP INSPECTION (DAI) ?

ARP REVIEW

- ARP is used to learn the MAC address of another device with a known IP address
    - For example, a PC will use ARP to learn the MAC address of its default gateway to communicate with external networks
- Typically, it is a two message exchange :  ARP request and ARP reply

GRATUITOUS ARP

- A GRATUITOUS ARP message is an ARP reply that is sent without receiving an ARP request
- It is sent to the broadcast MAC address
- It allows other devices to learn the MAC address of the sending device without having to send ARP requests.
- Some devices automatically send GARP messages when an interface is enabled, IP address is changed, MAC address is changed, etc.

DYNAMIC ARP INSPECTION

- DAI is a security feature of switches that is used to filter ARP messages received on  *untrusted ports*
- DAI only filters ARP messages. Non-ARP messages are not affected
- All ports are *untrusted*, by default
    - Typically, all ports connected to other network devices (switches, routers) should be configured as trusted, while interfaces connected to end hosts should remain untrusted

![image](https://github.com/psaumur/CCNA/assets/106411237/02da32ef-654c-4755-abcd-ea8230df4029)

![image](https://github.com/psaumur/CCNA/assets/106411237/29744383-746e-47be-8220-ba1a641a7a11)

![image](https://github.com/psaumur/CCNA/assets/106411237/6848c2b5-e866-4023-9ad9-c18f63aa6bb5)

---

ARP POISONING (MAN IN THE MIDDLE)

- Similar to DHCP poisoning, ARP snooping involved an attacker manipulating target’s ARP tables so traffic is sent to the attacker
- To do this, the attacker can send GRATUITOUS ARP messages using another device’s IP address
- Other devices in the network will receive the GARP and update their ARP tables, causing them to send traffic to the attacker instead of the legitimate destination

![image](https://github.com/psaumur/CCNA/assets/106411237/aae80c8f-2673-4c04-a206-9b646f5c1f08)

DYNAMIC ARP INSPECTION OPERATIONS

- DAI inspects the sender MAC and sender IP fields of ARP messages received on untrusted ports and checks that there is a matching entry in the DHCP snooping binding table
    - If there is a match, the ARP message is forwarded
    - If there is no match, the ARP message is discarded

![image](https://github.com/psaumur/CCNA/assets/106411237/060f3d3a-b2fd-46a1-8b3c-7a6839985c87)

- DAI doesn’t inspect messages received on trusted ports. They are forwarded as normal.

- ARP ACLs can be manually configured to map IP addresses / MAC addresses for DAI to check
    - Useful for hosts that don’t use DHCP
    
- DAI can be configured to perform more in-depth checks also - but these are optional

- Like DHCP snooping, DAI also supports rate-limiting to prevent attackers from overwhelming the switch with ARP messages
    - DHCP snooping and DAI both require work from the switch’s CPU
    - Even if the attacker’s messages are blocked, they can overload the switch CPU with ARP messages

---

DYNAMIC ARP INSPECTION CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/4a91bd7b-626a-4d64-b69a-308d65bbdda4)

![image](https://github.com/psaumur/CCNA/assets/106411237/774765fa-4918-4cd9-bb64-57130968c359)

Command : `show ip arp inspection interfaces`

![image](https://github.com/psaumur/CCNA/assets/106411237/e64a568e-e5c6-442b-98f7-4fe829ff7519)

DAI RATE LIMITING

![image](https://github.com/psaumur/CCNA/assets/106411237/6400e059-2c8c-4369-827d-7774fddd57eb)

DAI OPTIONAL CHECKS

![image](https://github.com/psaumur/CCNA/assets/106411237/0e6b780a-16ef-466a-bfd3-8dd2cdace4ad)

![image](https://github.com/psaumur/CCNA/assets/106411237/1f109b81-9c9b-4acd-9557-0b652ba29b8d)

![image](https://github.com/psaumur/CCNA/assets/106411237/dd78740a-4f41-43aa-8ed2-3fa574acc0f9)

ARP ACLs (Beyond Scope of CCNA)

Create an ARP ACL for SRV1

![image](https://github.com/psaumur/CCNA/assets/106411237/cf121a75-45b2-4e2d-a35f-320e3f5491fa)

After applying it to switch 2, SRV1 is able to send ARP request to R1

![image](https://github.com/psaumur/CCNA/assets/106411237/582feed0-1915-4f59-b3b9-9db37854c6e1)

Command: `show ip arp inspection`

Shows a summary of the DAI configuration and statistics

![image](https://github.com/psaumur/CCNA/assets/106411237/684e694a-5b0a-4f85-b135-b288a8c4c6ec)

---

COMMAND REVIEW

![image](https://github.com/psaumur/CCNA/assets/106411237/4cb7dc28-b09d-4a98-8d43-aca2cdf6180b)
