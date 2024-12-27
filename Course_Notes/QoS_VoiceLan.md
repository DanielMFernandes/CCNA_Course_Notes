# 46. QoS (Voice VLANs) : PART 1

IP PHONES / VOICE LANS

- Traditional phones operate over the *public switched telephone network* (PSTN)
    - Sometimes, this is called POTS (Plain Old Telephone System)
- IP phones use VoIP (Voice Over IP) technologies to enable phone calls over an IP NETWORK, such as the internet
- IP phones are connected to a switch, just like any other end host

IP PHONES

- Have an internal 3-port switch
    - 1 PORT is the “UPLINK” to the external switch
    - 1 PORT is the “DOWNLINK” to the PC
    - 1 PORT connects internally to the phone itself

![image](https://github.com/psaumur/CCNA/assets/106411237/0bba51c0-af57-49e4-ae29-fca2a1079a34)

- This allows the PC and the IP phone to share a single switch port. Traffic from the PC passes through the IP phone to the switch
- It is recommended to separate “VOICE” traffic (from IP phone) and “DATA" traffic (from the PC) by placing them into SEPARATE VLANS (!)
    - This can be accomplished using a VOICE VLAN
    - Traffic from the PC will be UNTAGGED - but traffic from the phone will be tagged with a VLAN ID

![image](https://github.com/psaumur/CCNA/assets/106411237/12a1bfa5-036a-4eb6-b165-23fc8209a1f8)

![image](https://github.com/psaumur/CCNA/assets/106411237/b7c5b7e6-fa79-4405-b72f-b609ab56f216)

![image](https://github.com/psaumur/CCNA/assets/106411237/fc26e9dd-e19e-43cc-9f2a-4022b47f98b4)

---

POWER OVER ETHERNET (PoE)

- PoE allows Power Sourcing Equipment (PSE) to provide power to Powered Devices (PD) over an ethernet cable
- Typically, the PSE is a switch and the PDs are IP phones, IP cameras, wireless access points, etc.
- The PSE receives AC power from the outlet, converts it to DC power, and supplies that DC power to the PDs

![image](https://github.com/psaumur/CCNA/assets/106411237/4229e398-a50e-487c-adf3-66b235ea9189)

- Too much electrical current can damage electrical devices
- PoE has a process to determine if a connected device needs power and how much it needs.
    - When a device is connected to a PoE-Enabled port, the PSE (switch) sends LOW POWER SIGNALS, monitors the response, and determines how much power the PD needs
    - If the device needs power, the PSE supplies the power to allow the PD to boot
    - The PSE continues to monitor the PD and supply the required amount of power (but not too much!)
- *POWER POLICING* can be configured to prevent a PD from taking too much power
    - 'power inline police' configures power policing with the default settings:  disable the port and send a SYSLOG message if a PD draws too much power
        - Equivalent to 'power inline police action err-disable'
        - The interface will be put in an ‘error-disabled’ state and can be re-enabled with 'shutdown' followed by 'no shutdown'
    
    ![image](https://github.com/psaumur/CCNA/assets/106411237/59914c0d-2c0e-4952-a4af-1f7ada02002d)
    -  'power inline police action log' does NOT shut down the interface if the PD draws too much power. It will restart the interface and send a SYSLOG message
    
    ![image](https://github.com/psaumur/CCNA/assets/106411237/9717fb1e-9129-41f9-90bb-613c2bdee460)
    
    ![image](https://github.com/psaumur/CCNA/assets/106411237/8fe2eb15-49be-4f63-9f6f-79c0d5fe052f)
    

---

INTRO TO QUALITY OF SERVICE (QoS)

- VOICE traffic and DATA traffic used to use entirely separate networks
    - VOICE TRAFFIC used the PSTN
    - DATA TRAFFIC used the IP network (Enterprise WAN, Internet, etc)
- QoS wasn’t necessary as the different kinds of traffic didn’t compete for bandwidth

![image](https://github.com/psaumur/CCNA/assets/106411237/8a21a767-5a93-42bd-a8d4-52453f8a7341)

- Modern networks are typically *converged networks* in which IP phones, video traffic, regular traffic, etc. all share the same IP network
- This enables cost savings as well as more ADVANCED FEATURES for voice and video traffic (Example : Collaboration Software like Cisco WebEx, MS Teams, etc)
- However, the different kinds of traffic now have to compete for bandwidth
- **QoS** is a set of tools used by network devices to apply different treatment to different packets

![image](https://github.com/psaumur/CCNA/assets/106411237/8909efdb-bbbd-4f50-b412-7abe12a3bcef)

QUALITY OF SERVICE (QoS)

- QoS is used to manage the following characteristics of network traffic
    - BANDWIDTH
        - Overall capacity of the link (measured in *bits per second*)
        - QoS tools allow you to RESERVE a certain amount of a link’s bandwidth for specific kinds of traffic
    - DELAY
        - One-Way Delay = Time it takes traffic to go from source to destination
        - Two-Way Delay = Time it takes traffic to go from source to destination and return
        
![image](https://github.com/psaumur/CCNA/assets/106411237/29ed6306-a6aa-46ba-af2f-5ebcd383d1d7)
        
    
    - JITTER
        - The variation in ONE-WAY DELAY between PACKETS SENT by the same application
        - IP phones have a ‘jitter buffer’ to provide a FIXED DELAY to audio packets
    - LOSS
        - The % of PACKETS sent that DO NOT reach their destination
        - Can be caused by faulty cables
        - Can also be caused when a device’s PACKET QUEUES get full and the device starts discarding packets
    
- The following standards are recommended for ACCEPTABLE INTERACTIVE AUDIO quality:
    - ONE-WAY DELAY : 150 milliseconds or less
    - JITTER : 30 milliseconds or less
    - LOSS : 1% or less
    
- If these standards are not met, there could be a noticeable reduction in the quality of the phone call
    
    

QoS QUEUING

- If a network device receives messages faster than it can forward them out of the appropriate interface, the messages are placed in the QUEUE
- By default, the QUEUED MESSAGES will be forwarded in a FIRST IN FIRST OUT (FIFO) manner
    - Message will be sent in the order they are received
- If the queue is full, new packets will be dropped
- The is called *tail drop*

![image](https://github.com/psaumur/CCNA/assets/106411237/15de2fcd-5711-4014-8185-9975b2ce8a0d)

- TAIL DROP is harmful because it can lead to TCP GLOBAL SYNCHRONIZATION

![image](https://github.com/psaumur/CCNA/assets/106411237/1d22afa7-91aa-4e86-9c5f-ad9506dcb44c)

- When the queue fills up and tail drop occurs, all TCP hosts sending traffic will slow down the rate at which they send traffic
- They will ALL then increase the rate at which they send traffic, which rapidly leads to more congestion, dropped packets, and the process repeats…

![image](https://github.com/psaumur/CCNA/assets/106411237/b75c2cac-043c-4df6-a1d6-f26d9110630a)

- A solution to prevent tail drops and TCP global synchronization is RANDOM EARLY DETECTION (RED)

- When the amount of traffic in the queue reaches a certain threshold, the device will start RANDOMLY dropping packets from select TCP FLOWS
- Those TCP flows that dropped packets will reduce the rate at which traffic is sent, but you will avoid TCP global synchronization, in which all TCP flows reduce and then increase the rate of transmission at the same time, in waves.
- In STANDARD RED, all kinds of traffic are treated the same
- WEIGHTED RANDOM EARLY DETECTION (WRED) - an improved version of RED, allows you control which packets are dropped depending on the TRAFFIC CLASS

** TRAFFIC CLASSES and details about how QoS works will be covered in DAY 47 **
