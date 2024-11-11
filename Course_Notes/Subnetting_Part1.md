# 13. SUBNETTING : PART 1

![image](https://github.com/psaumur/CCNA/assets/106411237/a475e909-59b8-4615-a0b9-8a3c1fbdc313)


HOWEVER, only Class A, B, C Addresses can be assigned to a device as an IP Address.

CLASS 		PREFIX LENGTH

A 			/8
B 			/16
C 			/24

![image](https://github.com/psaumur/CCNA/assets/106411237/f0836136-c4a9-475b-b6c2-d1c550b8cfdd)


The IANA (Internet Assigned Numbers Authority) assigns IPv4 addresses/networks to companies based on their size.

The problem with 'CLASSFUL' assignment is that it led to IP Address wastefulness.

Example: A company requiring 5000 addresses was assigned a CLASS B IP, leaving 60000+ addresses unused.

---

The IETF (Internet Engineering Task Force) introduce CIDR in 1993 to replace the "classful" addressing system.

CIDR (Classless Inter-Domain Routing) removed the requirements of CLASS A, B, and C regarding size.

- This allowed larger networks to be split into smaller networks, allowing greater efficiency.
- These smaller networks are called "SUB-NETWORKS" or "SUBNETS"

---

HOW MANY USABLE ADDRESSES ARE THERE IN EACH NETWORK?

REMEMBER:

2^n - 2 = Usable Addresses

n = number of host bits

CIDR PRACTICE!

203.0.113.0/25

/25 means the Subnetwork bit is 25 bits

203 . 0 . 113 . 0 is written in binary as :

11001011 . 00000000 . 01110001 . 0 | 0000000

(Subnet prefix is the first 25 bits)

Flipping all the bits to 1’s, we get the SUBNET MASK for /25:

11111111 . 11111111 . 11111111 . 1 | 0000000

which is equal to:

255.255.255.128 (because the last octet is 10000000 = 128 in binary)

Based on previous definition of USABLE ADDRESSES, the number of hosts for
203.0.113.0 /25 is:

2^(7 bits) - 2 = 128 - 2 = 126 hosts.

---

What about /28 ?

203 . 0 . 113 . 0 is written in binary as :

11001011 . 00000000 . 01110001 . 0000 | 0000

(Subnet prefix is the first 28 bits)

flipping all the bits to 1’s, we get the SUBNET MASK for /28:

11111111 . 11111111 . 11111111 . 1111 | 0000

which is equal to:

255.255.255.240 (because the last octet is 11110000) = 128 + 64 + 32 + 16 = 240

The SUBNET MASK for /28 is 255.255.255.240
which has 16 hosts per group (2 * 4 bits = 16) - 2 Reserved IPs for Network and Broadcast 

---

SUBNETTING CHEATSHEET:

| Prefix Length | Mask | Networks | Addresses (subtract 2 to find hosts) |
| ---------- | ---------- | ---------- | ---------- |
| /1    /9    /17    /25 | 128 | 2 | 128 |
| /2    /10    /18    /26 | 192 | 4 | 64 |
| /3    /11    /19    /27 | 224 | 8 | 32 |
| /4    /12    /20    /28 | 240 | 16 | 16 |
| /5    /13    /21    /29 | 248 | 32 | 8 |
| /6    /14    /22    /30 | 252 | 64 | 4 |
| /7    /15    /23    /31 | 254 | 128 | 2 |
| /8    /16    /24    /32 | 255 | 256 | 1 |

---

1. Use a given CIDR/Mask to find column on Cheat Sheet
    
    a) Write down the correct subnet mask for the CIDR.
    
    b) Highlight the correct column in the Prefix Lenght and the CIDR portion that will change in the process. This is usually where you might make mistakes!
    
    c) Write down the network address for that CIDR/Mask (you will have to check the networks AND addreses columns for that). If this is too complex, you might have to divide the CIDR/Number of addresses (find the integer number) to find the correct network. 
    
    d) Find the next subnet address. Add the number of addresses to the highlighted portion of the CIDR to find it. 
    
    Example: 117.190.155.226/18

   a)

   255.255.192.0

   b)

   117.190.**155**.226/18

   255.255.**192**.0

   c)
   
   Integer division: 155/64 = 2
   
   Multiply result per address value: 64 * 2 = 128

   Network in the range: 117.190.128.0
   
   d)
   (Network portion) + (address value) = 128 + 64 = 192
   Next Subnet: 117.190.192.0

   Final Result
   Network: 117.190.128.0
   First Host: 117.190.128.1
   Last Host:117.190.191.254
   Broadcast: 117.190.191.255
   Next Subnet: 117.190.192.0

---
---
Example 2:
```
84 . 75 . 21 .6 /10

Second Octet = Magic

Address Group Size = 64
256 - 64 = 192

Subnet = 255.192.0.0

75 / 64 = 1 + remainder
1 * 64 = 64 (Base Network #)

Network : 84.64.0.0

Broadcast Base # = 64 + 64 -1 = 127

Broacast : 84.127.255.255

Subnets : 2^2 = 4 Subnets
Total Host Size = (2^(32-10))-2 = 4194302
```
