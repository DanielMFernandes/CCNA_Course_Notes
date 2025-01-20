# 55. WIRELESS FUNDAMENTALS

- Although we will briefly look at other types of wireless networks, in this section of the course we will be focusing on wireless LANs using WI-FI
- The standards we use for wireless LANs are defined in IEEE 802.11
- The term WI-FI is a trademark of the WI-FI Alliance, not directly connected to the IEEE
- The WI-FI Alliance tests and certifies equipment for 802.11 standards compliance
- However, WI-FI has become the common term that people use to refer to 802.11 wireless LANs and that term will be used through the course videos

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

- Signal Range
- Signal absorption, reflection, refraction, diffraction, and scattering

---

SIGNAL ABSORPTION

- Absorption happens when a wireless signal passes through a material and is converted into heat, weakening the signal

![image](https://github.com/psaumur/CCNA/assets/106411237/9ef52c86-66ef-46fb-872e-cb76f0fb8d83)

SIGNAL REFLECTION

- Reflection happens when a signal bounces off a material (like metal)
    - This is why WI-FI reception is usually poor in elevators. The signal bounces off the metal and very little penetrates into the elevator

![image](https://github.com/psaumur/CCNA/assets/106411237/d57a94df-4e82-46f2-8045-de01f7a293f1)

SIGNAL REFRACTION

- Refraction happens when a wave is bent when entering a medium where the signal travels at a different speed
    - For example, glass and water can refract waves

![image](https://github.com/psaumur/CCNA/assets/106411237/9c807832-6feb-40ed-81aa-f9d7337da241)

SIGNAL DIFFRACTION

- Diffraction happens when a wave encounters an OBSTACLE and travels AROUND it
    - This can result in “BLIND SPOTS” behind the obstacle

![image](https://github.com/psaumur/CCNA/assets/106411237/abd44fc3-ec6f-484c-8c81-a2de38c26999)

SIGNAL SCATTERING

- Scattering happens when a material causes a signal to SCATTER in all directions
    - Dust, smog, uneven surfaces, etc. can cause scattering

![image](https://github.com/psaumur/CCNA/assets/106411237/9474adb8-3fc0-44ac-b480-c846cec21e9a)

---

4) Other devices using the SAME CHANNELS can cause INTERFERENCE

- For example, a wireless LAN in your neighbor’s house / apartment

---

RADIO FREQUENCY (RF)

- To send wireless signals, the sender applies an ALTERNATING CURRENT to an antenna
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

- The VISIBLE frequency RANGE is ~400 THz to 790 THz
- The RADIO frequency RANGE is 30 Hz to 300 GHz and is used for many purposes.

![image](https://github.com/psaumur/CCNA/assets/106411237/caf70e36-75b2-4fe5-a2e2-2641fad4d7e0)

---

RADIO FREQUENCY BANDS 

- WI-FI uses two MAIN bands (frequency RANGES)
- 2.4 GHz band
    - Range is 2.400 - 2.4835 GHz
- 5 GHz band
    - Range is 5.150 - 5.825 GHz
    - Divided into FOUR SMALLER bands:
        - 5.150 - 5.250 GHz
        - 5.250 - 5.350 GHz
        - 5.470 - 5.725 GHz
        - 5.725 - 5.825 GHz

- The 2.4 GHz band typically provides FURTHER REACH in open space and BETTER PENETRATION of obstacles such as walls.
    - HOWEVER, more devices tend to use the 2.4 GHz band so INTERFERENCE can be a BIGGER PROBLEM compared to 5GHz

** WI-FI 6 (802.11ax) has EXPANDED the spectrum range to include a band in the 6 GHz RANGE

---

CHANNELS

- Each band is divided up into MULTIPLE “CHANNELS”
    - Devices are configured to transmit and receive traffic on one (or more) of these CHANNELS
- The 2.4 GHz band is divided into several CHANNELS, each with a 22 MHz RANGE
- In a SMALL wireless LAN with only a single ACCESS POINT (AP), you can use ANY channel
- However, in larger WLANs with multiple APs, it’s important that adjacent APs don’t use OVERLAPPING CHANNELS. This helps avoid INTERFERENCE
- In the 2.4 GHz band, it is recommended to use CHANNELS 1, 6 and 11

![image](https://github.com/psaumur/CCNA/assets/106411237/005d246e-d2d2-491e-8d1e-f2fb5afbb664)

- The 5 GHz band consists of NON-OVERLAPPING channels so it’s much EASIER to avoid INTERFERENCE between adjacent APs

- Using CHANNELS 1, 6, 11, you can place APs in a “HONEYCOMB” pattern to provide complete coverage of an area without INTERFERENCE between CHANNELS

![image](https://github.com/psaumur/CCNA/assets/106411237/8bce5d9c-6261-4180-a25c-20007a27f433)

---

WI-FI STANDARDS (802.11)

![image](https://github.com/psaumur/CCNA/assets/106411237/424d3b31-2bbe-454d-973c-fdf1534adfdd)

---

SERVICE SETS

- 802.11 defines different kinds of SERVICE SETS which are groups of wireless network devices
- There are THREE MAIN TYPES:
    - INDEPENDENT
    - INFRASTRUCTURE
    - MESH
- All devices in a SERVICE SET share the same SSID (Service Set Identifier)
- The SSID is a HUMAN-READABLE NAME which identifies the SERVICE SET
- The SSID does NOT have to be UNQUE

SERVICE SETS : IBSS

- An IBSS (INDEPENDENT BASIC SERVICE SET) is a wireless network in which two or MORE wireless devices connect directly without using an AP (ACCESS POINT)
- Also called an AD HOC network
- Can be used for FILE TRANSFER (ie: AirDrop)
- Not scalable beyond a few devices

![image](https://github.com/psaumur/CCNA/assets/106411237/5fe65388-0045-4f35-bd8b-5325e2779ab2)

SERVICE SETS : BSS

- A BSS (BASIC SERVICE SET) is a kind of infrastructure SERVICE SET in which CLIENTS connect to each other via an AP (ACCESS POINT) but not DIRECTLY to each other
- A BSSID (BASIC SERVICE SET ID) is used to uniquely identify the AP
    - Other APs can use the SAME SSID but NOT THE SAME BSSID
    - The BSSID is the MAC ADDRESS of the APs RADIO
- Wireless devices request to *associate* with the BSS
- Wireless devices that have associated with the BSS are called “CLIENTS” or “STATIONS”
- The area around an AP where its signal is usable is called a BSA (BASIC SERVICE AREA)

![image](https://github.com/psaumur/CCNA/assets/106411237/ef259f45-ead1-45f3-8ad3-5f343a763988)

SERVICE SETS: ESS

- To create LARGER wireless LANS beyond the range of a SINGLE AP, we use an ESS (EXTENDED SERVICE SET)
- APs with their own BSSs are connected by a wired network
    - Each BSS uses the SAME SSID
    - Each BSS has a UNIQUE BSSID
    - Each BSS uses a DIFFERENT channel to avoid INTERFERENCE
- CLIENTS can pass between APs without having to RECONNECT, providing a SEAMLESS WI-FI experience when moving between APs
    - This is called ROAMING
- The BSAs should overlap about 10-15%

![image](https://github.com/psaumur/CCNA/assets/106411237/4a2ccc9e-c3c2-43db-b0b2-c704d5da223e)

SERVICE SETS: MBSS

- An MBSS (MESH BASIC SERVICE SET) can be used in situations where it’s difficult to run an ethernet connection to every AP
- MESH APs use two RADIOS:
    - ONE provides BSS to wireless CLIENTS
    - ONE forms a “BACKHAUL NETWORK” which is used to BRIDGE traffic from AP to AP
- At least ONE AP is connected to the wired network and it is called the RAP (ROOT ACCESS POINT)
- The OTHER APs are called MAPs (MESH ACCESS POINTS)
- A PROTOCOL is used to determine the BEST PATH through the MESH (similar to how DYNAMIC ROUTING PROTOCOLS are used to determine the BEST PATH to a DESTINATION)

![image](https://github.com/psaumur/CCNA/assets/106411237/1604f0ea-8a93-4922-a78d-fe55e836ba9a)

---

DISTRIBUTION SYSTEM

- Most wireless networks are not STANDALONE networks
    - Rather, they are a way for wireless CLIENTS to connect to the wired network INFRASTRUCTURE
- In 802.11, the UPSTREAM wired network is called the DS (DISTRIBUTION SYSTEM)
- Each wireless BSS or ESS is mapped to a VLAN in the wired network

![image](https://github.com/psaumur/CCNA/assets/106411237/adf9deae-693c-4f1b-8d6d-c4fbfc356418)

- It is possible for an AP to provide MULTIPLE wireless LANs, each with a unique SSID
- Each WLAN is mapped to a separate VLAN and connected to the wired network via a TRUNK
- Each WLAN uses a UNIQUE BSSID, usually by INCREMENTING the LAST digit of the BBSID by one

![image](https://github.com/psaumur/CCNA/assets/106411237/5667abba-dc3f-4571-a11a-43b3e8cf4304)

---

ADDITIONAL AP OPERATIONAL MODES

- APs can operate in ADDITIONAL MODES beyond the ones we’ve introduced so far

- An AP in REPEATER MODE can be used to EXTEND the RANGE of a BSS

- The REPEATER will re-transmit ANY signal it receives from the AP
    - A REPEATER with a SINGLE RADIO must operate on the SAME CHANNEL as the AP, but this can drastically reduce the overall THROUGHPUT on the CHANNEL
    - A REPEATER with two RADIOS can receive on ONE CHANNEL and then retransmit on ANOTHER CHANNEL

![image](https://github.com/psaumur/CCNA/assets/106411237/7973107f-7f2a-47de-9272-186040b038b5)

- A WORKGROUP BRIDGE (WGB) operates as a wireless CLIENT of another AP and can be used to CONNECT wired devices to the wireless network
- In the example below, PC1 does NOT have wireless CAPABILITIES, and also DOES NOT have ACCESS to wired connections to SW1
- PC1 has a wired connection to the WGB, which has a wireless connection to the AP

![image](https://github.com/psaumur/CCNA/assets/106411237/85cffc3f-3e76-4a55-9810-254135162a82)

- AN OUTDOOR BRIDGE can be used to connect networks over LONG DISTANCES without a PHYSICAL CABLE connecting them
- The APs will use SPECIALIZED ANTENNAS that focus most of the signal POWER in one direction, which allows the wireless connection to be made over LONGER DISTANCES than normally possible
- The connection can be POINT-TO-POINT as in the diagram below, or POINT-TO-MULTIPOINT in which MULTIPLE SITES connect to on CENTRAL SITE

![image](https://github.com/psaumur/CCNA/assets/106411237/36b421fd-ba81-4230-8c67-72b0b88aae8a)

---

REVIEW
![image](https://github.com/psaumur/CCNA/assets/106411237/7bac6988-f3af-4ee3-8046-7d926069934c)

