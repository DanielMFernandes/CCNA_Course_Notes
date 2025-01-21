# 55. WIRELESS FUNDAMENTALS

- Although we will briefly look at other types of wireless networks, in this section of the course we will be focusing on wireless LANs using Wi-Fi
- The standards we use for wireless LANs are defined in IEEE 802.11
- The term Wi-Fi is a trademark of the Wi-Fi Alliance, not directly connected to the IEEE
- The Wi-Fi Alliance tests and certifies equipment for 802.11 standards compliance
- However, Wi-Fi has become the common term that people use to refer to 802.11 wireless LANs and that term will be used through the course videos

WIRELESS NETWORKS

- Wireless networks have some issues that we need to deal with

![image](https://github.com/psaumur/CCNA/assets/106411237/f1adc053-b4e7-4779-b497-d17fb8caa973)

1)  All devices within range receive all frames, like devices connected to an ethernet hub

- Privacy of data within the LAN is a greater concern
- CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance) is used to facilitate half-duplex communications
- CSMA / CD is used in wired networks to detect and recover from collisions
- CSMA / CA is used in wireless networks to avoid collisions

- When using CSMA / CA, a device will wait for other devices to stop transmitting before it transmits data itself.

![image](https://github.com/psaumur/CCNA/assets/106411237/7d266279-5342-478e-8001-0146a016296b)

2)  Wireless communications are regulated by various international and national bodies

3)  Wireless signal coverage area must be considered

- Signal range
- Signal absorption, reflection, refraction, diffraction, and scattering

---

SIGNAL ABSORPTION

- Absorption happens when a wireless signal passes through a material and is converted into heat, weakening the signal

![image](https://github.com/psaumur/CCNA/assets/106411237/9ef52c86-66ef-46fb-872e-cb76f0fb8d83)

SIGNAL REFLECTION

- Reflection happens when a signal bounces off a material (like metal)
    - This is why Wi-Fi reception is usually poor in elevators. The signal bounces off the metal and very little penetrates into the elevator

![image](https://github.com/psaumur/CCNA/assets/106411237/d57a94df-4e82-46f2-8045-de01f7a293f1)

SIGNAL REFRACTION

- Refraction happens when a wave is bent when entering a medium where the signal travels at a different speed
    - For example, glass and water can refract waves

![image](https://github.com/psaumur/CCNA/assets/106411237/9c807832-6feb-40ed-81aa-f9d7337da241)

SIGNAL DIFFRACTION

- Diffraction happens when a wave encounters an obstacle and travels around it
    - This can result in “blind spots” behind the obstacle

![image](https://github.com/psaumur/CCNA/assets/106411237/abd44fc3-ec6f-484c-8c81-a2de38c26999)

SIGNAL SCATTERING

- Scattering happens when a material causes a signal to scatter in all directions
    - Dust, smog, uneven surfaces, etc. can cause scattering

![image](https://github.com/psaumur/CCNA/assets/106411237/9474adb8-3fc0-44ac-b480-c846cec21e9a)

---

4) Other devices using the same channels can cause interference

- For example, a wireless LAN in your neighbor’s house / apartment

---

RADIO FREQUENCY (RF)

- To send wireless signals, the sender applies an alternating current to an antenna
    - This creates electromagnetic waves which propagate out as waves
- Electromagnetic waves can be measured in multiple ways - for example amplitude and frequency
- AMPLITUDE is the maximum strength of the electric and magnetic fields

![image](https://github.com/psaumur/CCNA/assets/106411237/f7daa2ac-16a7-41f2-8ba4-a7c214c7e96b)

- FREQUENCY measures the number of up / down cycles per a given unit of time
- The most common measurement of frequency is HERTZ
    - Hz (Hertz) = cycles per second
    - kHz (Kilohertz) = 1,000 cycles per second
    - MHz (Megahertz) = 1,000,000 cycles per second
    - GHz (Gigahertz) = 1,000,000,000 cycles per second
    - THz (Terahertz) = 1,000,000,000,000 cycles per second
    

4 cycles per 1 second = 4 Hertz

![image](https://github.com/psaumur/CCNA/assets/106411237/448e6f45-6ef1-4c53-abf7-dd843e8d7a84)

![image](https://github.com/psaumur/CCNA/assets/106411237/28ea49c0-c2ef-40f3-a703-884c612c16f7)

- Another important term is PERIOD, the amount of time of one cycle
    - If the frequency is 4 Hz, the period is 0.25 seconds

![image](https://github.com/psaumur/CCNA/assets/106411237/9ddcffd6-c623-4d75-bee0-d4f01d871085)

- The visible frequency range is ~400 THz to 790 THz
- The radio frequency range is 30 Hz to 300 GHz and is used for many purposes.

![image](https://github.com/psaumur/CCNA/assets/106411237/caf70e36-75b2-4fe5-a2e2-2641fad4d7e0)

---

RADIO FREQUENCY BANDS 

- Wi-Fi uses two main bands (frequency ranges)
- 2.4 GHz band
    - Range is 2.400 - 2.4835 GHz
- 5 GHz band
    - Range is 5.150 - 5.825 GHz
    - Divided into four smaller bands:
        - 5.150 - 5.250 GHz
        - 5.250 - 5.350 GHz
        - 5.470 - 5.725 GHz
        - 5.725 - 5.825 GHz

- The 2.4 GHz band typically provides further reach in open space and better penetration of obstacles such as walls.
    - However, more devices tend to use the 2.4 GHz band so interference can be a bigger problem compared to 5GHz

** Wi-Fi 6 (802.11ax) has expanded the spectrum range to include a band in the 6 GHz range

---

CHANNELS

- Each band is divided up into multiple “CHANNELS”
    - Devices are configured to transmit and receive traffic on one (or more) of these channels
- The 2.4 GHz band is divided into several channels, each with a 22 MHz range
- In a small wireless LAN with only a single ACCESS POINT (AP), you can use any channel
- However, in larger WLANs with multiple APs, it’s important that adjacent APs don’t use overlapping channels. This helps avoid interference
- In the 2.4 GHz band, it is recommended to use channels 1, 6 and 11

![image](https://github.com/psaumur/CCNA/assets/106411237/005d246e-d2d2-491e-8d1e-f2fb5afbb664)

- The 5 GHz band consists of non-overlapping channels so it’s much easier to avoid interference between adjacent APs

- Using channels 1, 6, 11, you can place APs in a “HONEYCOMB” pattern to provide complete coverage of an area without interference between channels

![image](https://github.com/psaumur/CCNA/assets/106411237/8bce5d9c-6261-4180-a25c-20007a27f433)

---

WI-FI STANDARDS (802.11)

![image](https://github.com/psaumur/CCNA/assets/106411237/424d3b31-2bbe-454d-973c-fdf1534adfdd)

---

SERVICE SETS

- 802.11 defines different kinds of SERVICE SETS which are groups of wireless network devices
- There are three main types:
    - INDEPENDENT
    - INFRASTRUCTURE
    - MESH
- All devices in a service set share the same SSID (Service Set Identifier)
- The SSID is a human-readable name which identifies the service set
- The SSID does not have to be unique

SERVICE SETS : IBSS

- An IBSS (Independent Basic Service Set) is a wireless network in which two or more wireless devices connect directly without using an AP (Access Point)
- Also called an AD HOC network
- Can be used for file transfer (ie: AirDrop)
- Not scalable beyond a few devices

![image](https://github.com/psaumur/CCNA/assets/106411237/5fe65388-0045-4f35-bd8b-5325e2779ab2)

SERVICE SETS : BSS

- A BSS (Basic Service Set) is a kind of infrastructure service set in which clients connect to each other via an AP but not directly to each other
- A BSSID (Basic Service Set ID) is used to uniquely identify the AP
    - Other APs can use the same SSID but not the same BSSID
    - The BSSID is the MAC address of the APs radio
- Wireless devices request to *associate* with the BSS
- Wireless devices that have associated with the BSS are called “CLIENTS” or “STATIONS”
- The area around an AP where its signal is usable is called a BSA (Basic Service Area)

![image](https://github.com/psaumur/CCNA/assets/106411237/ef259f45-ead1-45f3-8ad3-5f343a763988)

SERVICE SETS: ESS

- To create larger wireless LANS beyond the range of a single AP, we use an ESS (EXTENDED Service Set)
- APs with their own BSSs are connected by a wired network
    - Each BSS uses the same SSID
    - Each BSS has a unique BSSID
    - Each BSS uses a different channel to avoid interference
- Clients can pass between APs without having to reconnect, providing a seamless Wi-Fi experience when moving between APs
    - This is called ROAMING
- The BSAs should overlap about 10-15%

![image](https://github.com/psaumur/CCNA/assets/106411237/4a2ccc9e-c3c2-43db-b0b2-c704d5da223e)

SERVICE SETS: MBSS

- An MBSS (Mesh Basic Service Set) can be used in situations where it’s difficult to run an ethernet connection to every AP
- MESH APs use two radios:
    - One provides BSS to wireless clients
    - One forms a “BACKHAUL NETWORK” which is used to bridge traffic from AP to AP
- At least one AP is connected to the wired network and it is called the RAP (Root Access Point)
- The other APs are called MAPs (Mesh Access Points)
- A PROTOCOL is used to determine the best path through the MESH (similar to how dynamic routing protocols are used to determine the best path to a destination)

![image](https://github.com/psaumur/CCNA/assets/106411237/1604f0ea-8a93-4922-a78d-fe55e836ba9a)

---

DISTRIBUTION SYSTEM

- Most wireless networks are not standalone networks
    - Rather, they are a way for wireless clients to connect to the wired network infrastructure
- In 802.11, the upstream wired network is called the DS (DISTRIBUTION SYSTEM)
- Each wireless BSS or ESS is mapped to a VLAN in the wired network

![image](https://github.com/psaumur/CCNA/assets/106411237/adf9deae-693c-4f1b-8d6d-c4fbfc356418)

- It is possible for an AP to provide multiple wireless LANs, each with a unique SSID
- Each WLAN is mapped to a separate VLAN and connected to the wired network via a trunk
- Each WLAN uses a unique BSSID, usually by incrementing the last digit of the BBSID by one

![image](https://github.com/psaumur/CCNA/assets/106411237/5667abba-dc3f-4571-a11a-43b3e8cf4304)

---

ADDITIONAL AP OPERATIONAL MODES

- APs can operate in additional modes beyond the ones we’ve introduced so far

- An AP in repeater mode can be used to extend the range of a BSS

- The repeater will re-transmit any signal it receives from the AP
    - A repeater with a single radio must operate on the same channel as the AP, but this can drastically reduce the overall throughput on the channel
    - A repeater with two radios can receive on one channel and then retransmit on another channel

![image](https://github.com/psaumur/CCNA/assets/106411237/7973107f-7f2a-47de-9272-186040b038b5)

- A WORKGROUP BRIDGE (WGB) operates as a wireless client of another AP and can be used to connect wired devices to the wireless network
- In the example below, PC1 does not have wireless capabilities, and also does not have access to wired connections to SW1
- PC1 has a wired connection to the WGB, which has a wireless connection to the AP

![image](https://github.com/psaumur/CCNA/assets/106411237/85cffc3f-3e76-4a55-9810-254135162a82)

- AN OUTDOOR BRIDGE can be used to connect networks over long distances without a physical cable connecting them
- The APs will use specialized antennas that focus most of the signal power in one direction, which allows the wireless connection to be made over longer distances than normally possible
- The connection can be point-to-point as in the diagram below, or point-to-multipoint in which multiple sites connect to on central site

![image](https://github.com/psaumur/CCNA/assets/106411237/36b421fd-ba81-4230-8c67-72b0b88aae8a)

---

REVIEW
![image](https://github.com/psaumur/CCNA/assets/106411237/7bac6988-f3af-4ee3-8046-7d926069934c)

