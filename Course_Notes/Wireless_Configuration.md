# 58. WIRELESS CONFIGURATION

TOPOLOGY INTRODUCTION

![image](https://github.com/psaumur/CCNA/assets/106411237/1e8ed6b8-1183-42e7-9584-d5504c52987a)

Internal PC (VLAN 100) accessing default gateway via Internal CAPWAP tunnel

![image](https://github.com/psaumur/CCNA/assets/106411237/4dec4c60-945e-4f2c-b7db-3028269ec441)

Reaching External guest PC  via default gateway + Internal and External CAPWAP tunnels

![image](https://github.com/psaumur/CCNA/assets/106411237/3b1c79a6-f8c5-496b-a0b8-d561ff87880f)

---

LAYER 3 SWITCH CONFIGURATION (SW1)

![image](https://github.com/psaumur/CCNA/assets/106411237/eae43f12-aa95-41a3-8a5d-26ffc5e83262)

PART 2 of configuration

Note DHCP “Option 43”

![image](https://github.com/psaumur/CCNA/assets/106411237/ade4dc29-3017-4d79-99d2-d895968bf741)

WLC SETUP

This helps set up the WLC to allow GUI configuration

![image](https://github.com/psaumur/CCNA/assets/106411237/3a2c00c0-eda3-4b72-af07-b07e820365c5)

![image](https://github.com/psaumur/CCNA/assets/106411237/313e030b-add3-4384-bdf0-96306e3663b1)

Why Jeremy chose France for Country Code (has to do with regulatory domain of equipment)

![image](https://github.com/psaumur/CCNA/assets/106411237/c3a21043-c4fc-47fb-9294-953700fbd8ed)

![image](https://github.com/psaumur/CCNA/assets/106411237/80dce78b-3a7e-4c93-a5f1-47eefb6e28b0)

---

ACCESSING THE WLC GUI

![image](https://github.com/psaumur/CCNA/assets/106411237/a5b44611-af07-4bf6-94b3-957ee342bb24)

![image](https://github.com/psaumur/CCNA/assets/106411237/7924d814-35f2-40d0-ac3c-a2f8022df2bc)

![image](https://github.com/psaumur/CCNA/assets/106411237/45432356-9b45-43dd-99c7-701984d541c1)

![image](https://github.com/psaumur/CCNA/assets/106411237/f097e29c-c7f6-4045-9451-9fdd5035b4b4)

![image](https://github.com/psaumur/CCNA/assets/106411237/b6ec70b7-d628-422b-b693-d9f0af9d1e78)

---

WLC CONFIGURATION

![image](https://github.com/psaumur/CCNA/assets/106411237/fbc3b9fd-c0db-48f3-9ce8-270812e00008)

WLC PORTS

- WLC ports are the physical ports that cables connect to
- WLC interfaces are the logical interfaces within the WLC (ie: SVIs on a switch)
- WLCs have a few different ports:
    - SERVICE PORT
        - A dedicated management port
        - Used for out-of-band management
        - Must connected to a switch access port because it only supports one VLAN
        - This port can be used to connect to the device while it is booting, performing system recovery, etc.
    - DISTRIBUTION SYSTEM PORT
        - These are the standard network ports that connect to the “distribution system” (wired network) and are used for data traffic.
        - These ports usually connect to switch trunk ports, and if multiple distribution ports are used they can form a LAG
    - CONSOLE PORT
        - This is a standard console port, either RJ45 or USB
    - REDUNDANCY PORT
        - This port is used to connect to another WLC to form a high availability (HA) pair

![image](https://github.com/psaumur/CCNA/assets/106411237/cec94d93-d58b-43b1-8e5e-f4c07ee430fd)

---

WLC INTERFACES

- MANAGEMENT INTERFACES
    - Used for management traffic such as telnet, SSH, HTTP, HTTPS, RADIUS authentication, NTP, syslog, etc.
    - CAPWAP tunnels are also formed to / from the WLC’s management interface
- REDUNDANCY MANAGEMENT INTERFACE
    - When two WLCs are connected by their redundancy ports, one WLC is “active” and the other is “standby”
    - This interface can be used to connect to and manage the “standby” WLC

- VIRTUAL INTERFACE
    - This interface is used when communicating with Wireless clients to relay DHCP requests, perform client web authentication, etc.

- SERVICE PORT INTERFACE
    - If the service port is used, this interface is bound to it and used for out-of-band management

- DYNAMIC INTERFACE
    - These are the interfaces used to map a WLAN to a VLAN
    - For example :
        - Traffic from the “internal” WLAN will be sent to the wired network from the WLCs “internal” dynamic interface

---

WLAN CONFIGURATION

Click “NEW”

![image](https://github.com/psaumur/CCNA/assets/106411237/b20dbb39-fac6-4cf3-926b-869e75c04e15)

Fill in details of the interface and click “apply”

![image](https://github.com/psaumur/CCNA/assets/106411237/48a4810d-a56c-4aef-8cfd-d2474d42cbb1)

Fill out details (IP, Netmask, Gateway…) and then click “apply”

![image](https://github.com/psaumur/CCNA/assets/106411237/6d11036b-3d82-4c2f-a20a-4367eb18ca8a)

Internal interface has now been created

![image](https://github.com/psaumur/CCNA/assets/106411237/80a91b22-c4fa-43e2-b035-05ac6199c6f3)

Now, repeat the above steps for the guest interface

![image](https://github.com/psaumur/CCNA/assets/106411237/80d5a300-a3ef-4e46-ae1a-7b7afb6a5078)

Fill out details (IP, Netmask, Gateway, etc) and then click “apply”

![image](https://github.com/psaumur/CCNA/assets/106411237/43f70936-4b10-4647-8f57-a086e3f0b7bc)

![image](https://github.com/psaumur/CCNA/assets/106411237/3a98ae1c-13a4-4bde-ab8c-398f8d16da43)

Now that all the interfaces are created, we can start WLAN configuration

![image](https://github.com/psaumur/CCNA/assets/106411237/d80eff95-41c7-43c6-a31e-0ebde3a7cd81)

![image](https://github.com/psaumur/CCNA/assets/106411237/960f24e5-efb9-4a15-9f5f-2a8e45b2d425)

Internal WLAN is set to “management”, it needs to be changed to “internal”

![image](https://github.com/psaumur/CCNA/assets/106411237/a3cb544c-3ce4-43b5-b054-e52e8388ab83)

SECURITY will also need to be changed from [WPA2] to [WPA2 PSK]

![image](https://github.com/psaumur/CCNA/assets/106411237/4cb2783e-26db-4584-8daa-feba124e9966)

(Need to check the PSK “Enable” box at the bottom)

Change the PSK format to “ASCII” and enter a password (at least 8 chars in length)

![image](https://github.com/psaumur/CCNA/assets/106411237/220202e1-222f-4966-81a6-aafa81727c33)

![image](https://github.com/psaumur/CCNA/assets/106411237/8cd2c63a-aa10-48c3-b826-fe107d04666d)

- WEB AUTHENTICATION
    - After the Wireless clients gets an IP address and tries to access a web page, they will have to enter a username and password to authenticate

- WEB PASSTHROUGH
    - Similar to the above, but no username or password are required
    - A warning or statement is displayed and the client simply has to agree to gain access to the internet
    
- Conditional and splash page web redirect options are similar but additionally require 802.1x LAYER 2 authentication

---

QoS

![image](https://github.com/psaumur/CCNA/assets/106411237/957336a3-d81c-4914-b35f-99925a316ad3)

Default QoS setting is “silver” (Best Effort). This can be changed depending on the class of traffic being sent through the WLAN

---

ADVANCED SETTINGS

![image](https://github.com/psaumur/CCNA/assets/106411237/ed70b1b9-b0b6-4b37-b4a5-4492a0cb9120)

![image](https://github.com/psaumur/CCNA/assets/106411237/12bcb065-78af-47b9-810c-fbe7ad739260)

---

CONFIGURING A NEW WLAN (GUEST)

![image](https://github.com/psaumur/CCNA/assets/106411237/4782e82e-4545-458e-917c-42d40e08748d)

Change status to “enabled” and interface group to “guest”

![image](https://github.com/psaumur/CCNA/assets/106411237/7a84ce73-0250-404b-896c-695ac5b9d05a)

![image](https://github.com/psaumur/CCNA/assets/106411237/2ca8357b-7564-4ef9-8f36-cb730a4b415f)

Now, we need to change the security policy to [WPA2][Auth(PSK)]

Returning to monitoring, we can see the changes we made to the configuration

![image](https://github.com/psaumur/CCNA/assets/106411237/5a06ae8b-cad0-46ec-bf34-adab0960fc41)

Current number of clients is now 0. By connecting to the WLANS, these numbers should change.
To see a list of the clients connected, click the left-hand side “clients” tab

![image](https://github.com/psaumur/CCNA/assets/106411237/b6eefbd8-f79e-4dc6-90e6-95a8c0c17849)

![image](https://github.com/psaumur/CCNA/assets/106411237/75d359fe-dc41-4d87-9351-e1da0ebbb8c7)

---

ADDTIONAL WLC FEATURES

Wireless tab showing a list of the APs currently in the network

![image](https://github.com/psaumur/CCNA/assets/106411237/29f5608e-9edb-4c6e-9382-998deedd4c72)

Clicking on an AP shows information and configuration settings for it

![image](https://github.com/psaumur/CCNA/assets/106411237/7d87bbcc-ed95-47b6-b966-fb95f5bb7f29)

---

Management tab allows you change the ways you can manage the WLC

Clicking “Mgmt Via Wireless” allows you change if you can access management via Wi-Fi

![image](https://github.com/psaumur/CCNA/assets/106411237/605361a0-c8da-47fc-bca3-af09751838dd)

![image](https://github.com/psaumur/CCNA/assets/106411237/e13bdcea-cb87-4e38-9dd4-711079761987)

---

Security tab can allow us to create access lists

![image](https://github.com/psaumur/CCNA/assets/106411237/7eddccfb-07cd-4ba9-914e-54161a4b10f3)

First, name the ACL and what kind of IP address it’s for

![image](https://github.com/psaumur/CCNA/assets/106411237/e9f303bc-9078-4ff2-be86-f63fb9877008)

Click “Add New Rule” to specify the ACL Rules (What traffic can pass)

![image](https://github.com/psaumur/CCNA/assets/106411237/4637053c-042d-4afc-acf8-27e914698c00)

![image](https://github.com/psaumur/CCNA/assets/106411237/c9d26aa3-c277-45ac-8f74-1dbd11e1bda5)

![image](https://github.com/psaumur/CCNA/assets/106411237/afbdb580-5383-4f32-9713-708f0a4ebb7e)

We now need to apply the ACL (just like applying it to an interface on a router)

Click “CPU ACL” from the left-hand menu

![image](https://github.com/psaumur/CCNA/assets/106411237/3eeee534-2071-47df-97f6-639e46d54b94)

Select the new ACL from the pull-down list and then click “apply”

![image](https://github.com/psaumur/CCNA/assets/106411237/7c18a89c-cad3-4f54-b6e5-6d5956edbd37)

![image](https://github.com/psaumur/CCNA/assets/106411237/6319e0ad-4c65-418d-920b-3c1f43ae4b55)
