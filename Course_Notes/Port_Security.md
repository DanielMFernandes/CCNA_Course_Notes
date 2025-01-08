# 49. PORT SECURITY

INTRO TO PORT SECURITY

- PORT SECURITY is a security feature of Cisco switches
- It allows you to control which source MAC address(es) are allowed to enter the switchport
- If an unauthorized source MAC address enters the port, an action will be taken
    - The default action is to place the interface in an “err-disabled” state

![image](https://github.com/psaumur/CCNA/assets/106411237/92f4ce9b-8fb4-4d57-b200-f41c7d5236ee)

- When you enable port security on an interface with the default settings, one MAC address is allowed
    - You can configure the allowed MAC address manually
    - If you do not configure it manually, the switch will allow the first source MAC address that enters the interface
- You can change the maximum number of MAC addresses allowed
- A combination of manually configured MAC addresses and dynamically learned addresses is possible

![image](https://github.com/psaumur/CCNA/assets/106411237/0b6e8053-6819-4e02-ae28-4699a5c9c92d)

---

WHY USE PORT SECURITY?

- Port security allows network admins to control which devices are allowed to access the network
- However, MAC address spoofing is a simple task
    - It is easy to configure a device to send frames with a different source MAC address
- Rather than manually specifying the MAC addresses allowed on each port, port security’s ability to limit the number of MAC addresses allowed on an interface is more useful
- Think of the DHCP STARVATION ATTACK (DAY 48 LAB video)
    - The attacker spoofed thousands of fake MAC addresses
    - The DHCP server assigned IP addresses to these fake MAC addresses, exhausting the DHCP pool
    - The switch’s MAC address table can also become full due to such an attack
- Limiting the number of MAC addresses on an interface can protect against those attacks

ENABLING PORT SECURITY

![image](https://github.com/psaumur/CCNA/assets/106411237/b00765c2-f3a1-45be-8ed4-0a8dab68e43e)

![image](https://github.com/psaumur/CCNA/assets/106411237/787959b1-ffad-451d-ac65-11ea9a99db2d)

![image](https://github.com/psaumur/CCNA/assets/106411237/9a6dd39d-130e-411b-be46-ecfe93420813)

![image](https://github.com/psaumur/CCNA/assets/106411237/f071f447-a6ef-4ee6-8a40-2bde94030993)

RE-ENABLING AN INTERFACE (MANUALLY)

![image](https://github.com/psaumur/CCNA/assets/106411237/706736d4-ee7c-42b2-b424-6cc30eb50905)

RE-ENABLING AN INTERFACE (ERR-DISABLE RECOVERY)

![image](https://github.com/psaumur/CCNA/assets/106411237/6eb0d808-a989-4261-9b39-1ac9e1bf1460)

![image](https://github.com/psaumur/CCNA/assets/106411237/41d54ef0-7391-473e-9b51-87f44b9e3f3c)

---

VIOLATION MODES

- There are three different violation modes that determine what the switch will do if an unauthorized frame enters an interface configured with port security
    - SHUTDOWN
        - Effectively shuts down the port by placing it in an ‘err-disabled` state
        - Generates a Syslog and / or SNMP message when the interface is ‘disabled’
        - The violation counter is set to 1 when the interface is ‘disabled’
    - RESTRICT
        - The switch discards traffic from unauthorized MAC addresses
        - The interface is NOT disabled
        - Generates a Syslog and / or SNMP message each time an unauthorized MAC is detected
        - The violation counter is incremented by 1 for each unauthorized frame
    
    - PROTECT
        - The switch discards traffic from unauthorized MAC addresses
        - The interface is NOT disabled
        - It does NOT generate a Syslog / SNMP message for unauthorized traffic
        - It does NOT increment the violation counter
    
---

VIOLATION MODE - RESTRICT

![image](https://github.com/psaumur/CCNA/assets/106411237/819f00b9-9694-442d-8459-8018f4277e45)


VIOLATION MODE - PROTECT

![image](https://github.com/psaumur/CCNA/assets/106411237/20d17f97-056e-4e76-8566-bb49c10bb9e1)

---

SECURE MAC ADDRESS AGING

![image](https://github.com/psaumur/CCNA/assets/106411237/4454fedf-f942-4b0d-9b6f-074765de653d)

- By default, secure MAC addresses will not ‘age out’ (Aging Time : 0 mins)
    - Can be configured with `switchport port-security aging time *minutes*`

- The default Aging Type is absolute
    - ABSOLUTE
        - After the secure MAC address is learned, the aging timer starts and the MAC is removed after the timer expires, even if the switch continues receiving frames from that source MAC address.
    - INACTIVITY
        - After the secure MAC address is learned, the aging timer starts but is reset every time a frame from that source MAC address is received on the interface
            - Aging type is configured with:  `switchport port-security aging type {absolute | inactivity}`
- Secure static MAC aging (address configured with `switchport port-security mac-address x.x.x`) is disabled by default

![image](https://github.com/psaumur/CCNA/assets/106411237/93f11517-9d97-4e52-89ad-a0e590bca702)

---

STICKY SECURE MAC ADDRESSES 

- ‘STICKY’ secure MAC address learning can be enabled with the following command:
    - `SW(config-if)# switchport port-security mac-address sticky`

- When enabled, dynamically-learned secure MAC addresses will be added to the running configuration, like this:
    - `switchport port-security mac-address sticky *mac-address*`

- The ‘STICKY’ secure MAC addresses will NEVER age out
    - You need to save the `running-config` to `startup-config` to make them truly permanent (or else they will not be kept if the switch restarts)
- When you issue the `switchport port-security mac-address sticky` command, all current dynamically-learned secure MAC addresses will be converted to sticky secure MAC addresses
- If you issue the `no switchport port-security mac-address sticky` command, all current sticky secure MAC addresses will be converted to regular dynamically-learned secure MAC addresses

![image](https://github.com/psaumur/CCNA/assets/106411237/10d591f9-334c-4e3b-889e-16030c36c445)

---

MAC ADDRESS TABLE

- Secure MAC addresses will be added to the MAC address table like any other MAC address
    - Sticky and static secure MAC addresses will have a type of STATIC
    - Dynamically-Learned secure MAC addresses will have a type of DYNAMIC
    - You can view all secure MAC addresses with `show mac address-table secure`
    

![image](https://github.com/psaumur/CCNA/assets/106411237/c9123729-541c-4363-ba19-d8e49f75c6c5)

---

COMMAND REVIEW

![image](https://github.com/psaumur/CCNA/assets/106411237/716ce91d-d1bb-4f12-a8fd-226b65f22569)
