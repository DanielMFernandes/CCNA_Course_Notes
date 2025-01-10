# 50. DHCP SNOOPING (LAYER 2)

WHAT IS DHCP SNOOPING?

- DHCP SNOOPING is a security feature of switches that is used to filter DHCP messages received on untrusted ports
- DHCP snooping only filters DHCP messages.
    - Non-DHCP messages are not affected
- All ports are untrusted, by default
    - Usually uplink ports are configured as trusted ports, and downlink ports remain untrusted
    

![image](https://github.com/psaumur/CCNA/assets/106411237/9ed71d09-d94c-4fc9-ad87-1b31acfdd132)

![image](https://github.com/psaumur/CCNA/assets/106411237/9d7d23a6-9d54-4234-a07e-a5caea136c94)

---

ATTACKS ON DHCP

DHCP STARVATION

- An example of a DHCP-based attack is a DHCP STARVATION ATTACK (DHCP EXHAUSTION)
- An attacker uses spoofed MAC addresses to flood DHCP discover messages
- The target server’s DHCP pool becomes full, resulting in a DoS to other devices

![image](https://github.com/psaumur/CCNA/assets/106411237/33dfbb8b-2b78-4700-b4ab-0dd95fc03eed)

DHCP POISONING (Man-in-the-Middle)

- Similar to ARP poisoning, DHCP POISONING can be used to perform a Man-in-the-Middle attack
- A *spurious DHCP server* replies to clients’ DHCP discover messages and assigns them IP addresses but makes the clients use the *spurious server’s IP* as a default gateway

** clients usually accept the first DHCP offer message they receive

- This will cause the client to send traffic to the attacker instead of the legitimate default gateway
- The attacker can then examine / modify the traffic before forwarding it to the legitimate default gateway

![image](https://github.com/psaumur/CCNA/assets/106411237/d0cd7a5c-9ff4-4ab7-bec6-4edec4ea2646)

![image](https://github.com/psaumur/CCNA/assets/106411237/1573bcb7-6fa8-46d7-8cb8-46e30bac559d)

---

DHCP MESSAGES

- When DHCP snooping filters messages, it differentiates between DHCP server messages and DHCP client messages

- Messages sent by DHCP servers:
    - OFFER
    - ACK
    - NAK = Opposite of ACK - used to decline a client’s request
- Messages sent by DHCP clients:
    - DISCOVER
    - REQUEST
    - RELEASE = Used to tell the server that the client no longer needs its IP address
    - DECLINE = Used to decline the IP address offered by a DHCP server

---

HOW DOES IT WORK?

- If a DHCP message is received on a trusted port, forward it as normal without inspection
- If a DHCP message is received on an untrusted port, inspect it and act as follows:
    - If it is a DHCP server message, discard it
    - If it as a DHCP client message, perform the following checks:
        - DISCOVER / REQUEST messages :
            - Check if the frame’s source MAC address and the DHCP message’s CHADDR fields match.
                - MATCH = forward
                - MISMATCH = discard
        - RELEASE / DECLINE messages:
            - Check if the packet’s source IP address and the receiving interface match the entry in the *DHCP SNOOPING BINDING TABLE*
                - MATCH = forward
                - MISMATCH = discard
    
- When a client successfully leases an IP address from a server, create a new entry in the *DHCP snooping binding table*

---

DHCP SNOOPING CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/729466dc-9432-47d2-8799-652fa064b058)

SWITCH 2’s CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/8d6cacb8-ffd8-4cf0-bd96-fe9978377989)

SWITCH 1’s CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/bb11e4fd-a340-4dd3-a6f5-3cd280fc5a13)

DHCP SNOOPING RATE-LIMITING

- DHCP snooping can limit the RATE at which DHCP messages are allowed to enter an interface
- If the RATE of DHCP messages crosses the configured LIMIT, the interface is `err-disabled`
- Like with port security, the interface can be manually re-enabled, or automatically re-enabled with `errdisable recovery`

![image](https://github.com/psaumur/CCNA/assets/106411237/6586df19-5a58-4ca3-a316-bd0aeb2ce67c)

- You wouldn’t set the limit rate to 1 since it’s so low, it would shut the port immediately but this shows how rate-limiting works

`errdisable recovery cause dhcp-rate-limit`

![image](https://github.com/psaumur/CCNA/assets/106411237/83c324aa-baa0-4ae1-82ac-157e503e048a)

DHCP OPTION 82 (INFORMATION OPTION)

- Option 82, also known as a ‘DHCP RELAY AGENT INFORMATION OPTION’ is one of many DHCP options
- It provides additional information about which DHCP relay agent received the client’s message, on which interface, in which VLAN, etc.
- DHCP relay agents can add option 82 to message they forward to the remote DHCP server
- With DHCP snooping enabled, by default Cisco switches will add option 82 to DHCP messages they receive from clients, even if the switch isn’t acting as a DHCP relay agent
- By default, Cisco switches will drop DHCP messages with option 82 that are received on an untrusted port

![image](https://github.com/psaumur/CCNA/assets/106411237/2efc6edd-21fd-4c1a-bb11-9c1f761e1d32)

THIS command disables OPTION 82 for SW1 but not SW2 

![image](https://github.com/psaumur/CCNA/assets/106411237/84f1c3f2-9ad1-4367-97f3-95dab053b30c)

traffic gets passed to R1 and is dropped because of “inconsistent relay information” (packet contains option 82 but wasn’t dropped by SW2)

![image](https://github.com/psaumur/CCNA/assets/106411237/5c4b547e-c588-4d62-8098-76902199a131)

By ENABLING option 82 on both switches…

![image](https://github.com/psaumur/CCNA/assets/106411237/dda50cf6-ae86-47ec-9b4f-104669697f64)

PC1’s DHCP discover message gets passed, through SW1 and SW2, to R1.
R1 responds with an DHCP offer message, as normal

![image](https://github.com/psaumur/CCNA/assets/106411237/7e59cc5a-bf8e-482d-848d-5bfa0540c74b)

---

COMMAND SUMMARY

![image](https://github.com/psaumur/CCNA/assets/106411237/308e32fa-52bd-4ee4-9356-f14e65416e17)
