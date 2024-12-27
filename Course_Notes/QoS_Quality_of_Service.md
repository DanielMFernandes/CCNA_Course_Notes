# 47. QoS (Quality of Service) : PART 2

CLASSIFICATION / MARKING

- The purpose of QoS is to give certain kinds of network traffic priority over others during congestion
- CLASSIFICATION organizes network traffic (packets) into TRAFFIC CLASSES (CATEGORIES)
- Classification is fundamental to QoS.
    - To give priority to certain types of traffic, you have to identify which types of traffic to give priority to.
- There are many methods of classifying traffic
    - An ACL : traffic which is permitted by the ACL will be given certain treatment, other traffic will not
    - NBAR (Network Based Application Recognition) performs a *DEEP PACKET INSPECTION*, looking beyond the Layer 3 and Layer 4 information up to Layer 7 to identify the specific kinds of traffic
    - In the Layer 2 and Layer 3 headers there are specific fields used for this purpose
- The PCP (PRIORITY CODE POINT) field of the 802.1Q Tag (in the Ethernet header) can be used to identify HIGH / LOW PRIORITY traffic
    - Only when there is a dot1q tag!
- The DSCP (DIFFERENTIATED SERVICES CODE POINT) field of the IP header can also be used to identify HIGH / LOW PRIORITY traffic

---

PCP / CoS

![image](https://github.com/psaumur/CCNA/assets/106411237/2d2037b6-6992-4758-a1cb-5df0f939b153)

- PCP is also known as CoS (CLASS OF SERVICE)
- It’s use is defined by IEEE 802.1p
- 3 bits = 8 possible values (2^3 = 8)

![image](https://github.com/psaumur/CCNA/assets/106411237/af191e31-082d-43c0-ab76-225d4dd2e354)

- PCP VALUE 0:
    - “BEST EFFORT” delivery means there is no guarantee that data is delivered or that it meets any QoS Standard. This is regular traffic - NOT HIGH PRIORITY

- PCP VALUE 3 and 5:
    - IP phones mark "call signaling traffic" (used to establish calls) as PCP3
        - They mark the actual VOICE traffic as PCP5

- Because PCP is found in the dot1q header, it can only be used over the following connections:
    - Trunk links
    - Access links with a voice VLAN
    
- In the diagram below, traffic between R1 and R2, or between R2 and external destinations will not have a dot1q tag. So, traffic over those links PCP cannot be marked with a PCP value.

![image](https://github.com/psaumur/CCNA/assets/106411237/07a1cbb3-d034-4a9b-accc-59e7f738452f)

---

THE IP ToS BYTE

![image](https://github.com/psaumur/CCNA/assets/106411237/3323ff23-96a5-45f4-abde-893d72a4021f)

![image](https://github.com/psaumur/CCNA/assets/106411237/ffec398b-7b0a-47a1-9758-a7a14daf6aa0)

(6 bits for DSCP and 2 bits for ECN)

---

IP PRECEDENCE (OLD)

![image](https://github.com/psaumur/CCNA/assets/106411237/1b0ca3ca-fc8d-4225-9368-64c8ff9587da)

- Standard IPP markings are similar to PCP:
    - 6 and 7 are reserved to ‘network control traffic’ (ie: OSPF Messages between routers)
    - 5 = VOICE
    - 4 = VIDEO
    - 3 = VOICE SIGNALLING
    - 0 = BEST EFFORT
- With 6 and 7 reserved, 6 possible values remain
- Although 6 values is sufficient for many networks, the QoS requirements of some networks demand more flexibility

---

DSCP (CURRENT)

![image](https://github.com/psaumur/CCNA/assets/106411237/48a63948-81b9-43d5-a108-34525a381533)

- RFC 2474 (1998) defines the DSCP field, and other ‘DiffServ’ RFCs elaborate on its use
- With IPP updated to DSCP, new standard markings had to be decided on
    - By having generally agreed upon standard markings for different kinds of traffic:
        - QoS DESIGN and IMPLEMENTATION is simplified.
        - QoS works better between ISPs and Enterprises
        - etc.

- You should be aware of the following standard markings:
    - DEFAULT FORWARDING (DF) - Best Effort traffic
    - EXPEDITED FORWARDING (EF) - Low Loss / Latency / Jitter traffic (usually voice)
    - ASSURED FORWARDING (AF) - A set of 12 standard values
    - CLASS SELECTOR (CS) - A set of 8 standard values, provides backward compatibility with IPP

---

DF / EF

DEFAULT FORWARDING (DF)

![image](https://github.com/psaumur/CCNA/assets/106411237/26f6bc76-6b33-40f0-9327-022b4816d280)

- Used for best effort traffic
- The DSCP marking for DF is 0

EXPEDITED FORWARDING (EF)

![image](https://github.com/psaumur/CCNA/assets/106411237/12cf77c0-f139-494c-ab8b-d765a73a92f4)

- EF is used for traffic that requires Low Loss / Latency / Jitter
- The DSCP marking for EF is 46

---

ASSURED FORWARDING (AF)

- Defines FOUR TRAFFIC CLASSES
- ALL packets in a class have the same priority
- Within each class, there are THREE LEVELS of DROP PRECEDENCE
    - HIGHER DROP PRECEDENCE = More likely to drop the packet during congestion
    

![image](https://github.com/psaumur/CCNA/assets/106411237/407ab29c-678d-4a38-8e8e-2a6f904b4d94)

EXAMPLES:

![image](https://github.com/psaumur/CCNA/assets/106411237/d6b2dac7-fefc-409b-8136-f34df165dd23)

![image](https://github.com/psaumur/CCNA/assets/106411237/6543afb5-9aba-4d91-9d61-233c2c67958d)

![image](https://github.com/psaumur/CCNA/assets/106411237/fae89ed7-7229-4632-b3de-5415a36ad267)

![image](https://github.com/psaumur/CCNA/assets/106411237/a7440ed0-70d8-48c2-b83d-dcb4e169fade)

![image](https://github.com/psaumur/CCNA/assets/106411237/0d2d9ba8-fecc-47a8-9cee-02ae5a7a30e9)

![image](https://github.com/psaumur/CCNA/assets/106411237/05fa1552-e305-4e2d-b6aa-db0c8cbed3f7)

![image](https://github.com/psaumur/CCNA/assets/106411237/be10edd7-a4e3-4df6-a94f-b9e1b1c9e304)

- AF41 gets the BEST TREATMENT (Highest Priority / Lowest Drop)
- AF13 gets the WORST TREATMENT (Lowest Priority / Highest Drop)

---

CLASS SELECTOR (CS)

- Defines EIGHT DSCP values for backward compatibility with IPP
- The THREE BITS that were added for DSCP are set to 0, and the original IPP bits are used to make 8 values

![image](https://github.com/psaumur/CCNA/assets/106411237/d7619e44-1ffd-4613-bbad-f2ff19ff6d2a)

---

RFC 4954

- RFC 4954 was developed with help of Cisco to bring all of these values together and standardize their use

- The RFC offers many specific recommendations, but here are a few key ones:
    - VOICE TRAFFIC : EF
    - INTERACTIVE VIDEO : AF4x
    - STREAMING VIDEO : AF3x
    - HIGH PRIORITY DATA : AF2x
    - BEST EFFORT : DF

---

TRUST BOUNDARIES

- The TRUST BOUNDARY of a network defines where the device trust / don’t trust the QoS markings of received messages
- If the markings are TRUSTED:
    - Device will forward the message without changing the markings
- If the markings are NOT TRUSTED:
    - Device will change the markings according to configured policy

![image](https://github.com/psaumur/CCNA/assets/106411237/cdcdc302-9dbe-4dd8-9184-72d1f501bc1a)

- If an IP phone is connected to the switch port, it is recommended to move the trust boundary to the IP phones
- This is done via configuration on the switch port connected to the IP phone
- If a user marks their PC’s traffic with a HIGH PRIORITY, the marking will be changed (not trusted)

![image](https://github.com/psaumur/CCNA/assets/106411237/606ad681-fad4-4f23-96bf-bd7dde91eaf4)

---

QUEUING / CONGESTION MANAGEMENT

- When a network device receives traffic at a faster pace than it can forward out of the appropriate interface, packets are placed in that interface’s queue as they wait to be forwarded
- When a queue becomes full, packets that don’t fit in the queue are dropped (Tail Drop)
- RED and WRED DROP packets early to avoid TAIL DROP

![image](https://github.com/psaumur/CCNA/assets/106411237/5dbfd417-097c-4107-a5e1-b5476f423b15)

- An essential part of QoS is the use of MULTIPLE QUEUES
    - This is where CLASSIFICATION plays a role.
    - Device can match traffic based on various factors (like DSCP MARKINGS in the IP header) and then place it in the appropriate queue

- However, the device is only able to forward one frame out of an interface at once so a *SCHEDULER*, is used to decide which queue traffic is forwarded from the next
    - *PRIORITZATION* allows the SCHEDULER to give certain queues more PRIORITY than others

![image](https://github.com/psaumur/CCNA/assets/106411237/56bfe184-5bdf-4b8f-8851-756766456bf9)

- A common scheduling method is *WEIGHTED ROUND-ROBIN*
    - ROUND-ROBIN:
        - packets taken from each queue in order, cyclically
    - WEIGHTED:
        - More data taken from HIGH PRORITY queues each time the scheduler reaches that queue

---

- CBWFQ (CLASS BASED WEIGHED FAIR QUEUING)
    - Popular method of scheduling
    - Uses WEIGHTED ROUND-ROBIN SCHEDULER while guaranteeing each queue a certain percentage of the interface’s bandwidth during congestion
    

![image](https://github.com/psaumur/CCNA/assets/106411237/eee24cef-c67a-42de-9fa0-9351cab56354)

- ROUND-ROBIN SCHEDULING is not ideal for voice/video traffic
    - Even if VOICE / VIDEO traffic receives a guaranteed MINIMUM amount of bandwidth, ROUND-ROBIN can add DELAY and JITTER because even the high priority queues have to wait their turn in the scheduler

---

- LLQ (LOW LATENCY QUEUING)
    - Designates one (or more) queues as *strict priority queues*
    - This means that if there is traffic in the queue, the scheduler will always take the next packet from that queue until it is empty
    - This is very effective for reducing the delay and jitter of voice/video traffic
    - However, LLQ has a downside of potentially starving other queues if there is always traffic in the designated *STRICT PRIORITY QUEUE*
        - POLICING can control the amount of traffic allowed in the *STRICT PRIORITY QUEUE* so that it can’t take all of the link’s bandwidth
    

![image](https://github.com/psaumur/CCNA/assets/106411237/2b544243-3a2e-4721-bf1f-4636ec4085a7)

 

---

SHAPING / POLICING

- TRAFFIC SHAPING and POLICING are both used to control the rate of traffic
- SHAPING
    - Buffers traffic in a queue if the traffic rate goes over the configured rate

- POLICING
    - DROPS traffic if the traffic rate goes over the configured rate
        - POLICING also has the option of RE-MARKING the traffic, instead of DROPPING
    - “BURST” traffic over the configured rate is allowed for a short period of time
    - This accommodates data applications which typically are “bursty” in nature (ie: not constant stream)
    - The amount of burst traffic allowed is configurable
    
- In both cases, classification can be used to allow for different rates for different kinds of traffic
- Why would you want to limit the rate that traffic is sent / received?

![image](https://github.com/psaumur/CCNA/assets/106411237/09771d78-4570-4300-97e1-adba77fe28b4)
