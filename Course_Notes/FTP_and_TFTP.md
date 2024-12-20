# 43. FTP and TFTP

THE PURPOSE OF FTP / TFTP

- FTP (File Transfer Protocol) and TFTP (Trivial File Transfer Protocol) are industry standard protocols used to TRANSFER FILES over a network
- They both use a CLIENT-SERVER model
    - clients can use FTP / TFTP to copy files from a server
    - clients can use FTP / TFTP to copy files to a server
- As a network engineer, the most common use for FTP / TFTP is in the process of UPGRADING the OS of a network device
- You can use FTP / TFTP to download the newer version of IOS from a server and then reboot the device with the new IOS image

![image](https://github.com/psaumur/CCNA/assets/106411237/c3f8288f-cc21-476b-ab36-685fa843f947)

---

TFTP and FTP FUNCTIONS AND DIFFERENCES

TFTP

- TFTP first standardized in 1981
- Named “Trivial” because it’s simple and has only basic features compared to FTP
    - Only allows a client to COPY FILES to/from a server
- Was released after FTP, but not a replacement for FTP.
    - It’s another tool to use when lightweight SIMPLICITY is more important than FUNCTIONALITY
- NO AUTHENTICATION (Username/Password) so servers will respond to ALL FTP REQUESTS
- NO ENCRYPTION. All data is sent PLAIN TEXT
- Best used in a CONTROLLED environment to transfer SMALL FILES quickly
- TFTP SERVERS listen on UDP port 69
- UDP is CONNECTIONLESS and doesn’t provided reliability with retransmissions
- However, TFTP has similar built-in features within the protocol itself

TFTP RELIABILITY

- Every TFTP data message is ACKNOWLEDGED
    - If the client is transferring a file to the server, the server will send ACK messages
    - If the server is transferring a file to the client, the client will send ACK messages
- Timers are used, and if an expected message isn’t received in time, the waiting device will resend its previous message.

![image](https://github.com/psaumur/CCNA/assets/106411237/6b8f914e-0d8f-4cfd-bbbb-3552b5cebb3e)

TFTP “CONNECTIONS”

![image](https://github.com/psaumur/CCNA/assets/106411237/d6634813-5132-4fd8-a712-7bc7b4ea21db)

TFTP TID (Not in the CCNA exam)

- When the client sends the first message to the server, the DESTINATION PORT is UDP 69 and the SOURCE PORT is a random EPHEMERAL PORT
- This “random port” is called a “TRANSFER IDENTIFIER” (TID) and identifies the DATA TRANSFER
- The SERVER then also selects a RANDOM TID to use as a SOURCE PORT when it replies, NOT UDP 69
- When the client sends the next message, the destination port will be the SERVER’S TID, NOT UDP 69

UDP PORT 69 (TFTP) is only used at the initial request message

![image](https://github.com/psaumur/CCNA/assets/106411237/5976c631-4cba-4449-a2b4-912f90cb66e1)

--- 

FTP

- FTP was first standardized in 1971
- FTP uses TCP PORTS 20 and 21
- Usernames and passwords are used for AUTHENTICATION, however there is NO ENCRYPTION
- For greater security, FTPS (FTP over SSL / TLS) can be used (Upgrade to FTP)
- SSH File Transfer Protocol (SFTP) can also be used for greater security (New Protocol)
- FTP is more complex than TFTP and allows not only file transfers but clients can also:
    - Navigate file directories
    - Add/remove files
    - List files
    - etc...
- The client sends FTP *commands* to the server to perform these functions

FTP CONTROL CONNECTIONS

- FTP uses TWO types of connections:
    - An FTP CONTROL connection (TCP 21) is established and used to send FTP commands and replies
    - When FILES or DATA are to be transferred, separate FTP DATA (TCP 20) connections are established and terminated as needed

![image](https://github.com/psaumur/CCNA/assets/106411237/8ff1d9a5-785b-4fb4-86a4-766c1107812f)

ACTIVE MODE FTP DATA CONNECTIONS

- The default method of establishing FTP DATA connections is ACTIVE MODE in which the server initiates the TCP connection.

![image](https://github.com/psaumur/CCNA/assets/106411237/49909dbc-1ed5-425b-8958-03fcaf5b9eab)

- In FTP PASSIVE MODE, the client initiates the data connection.
    - This is often necessary when the client is behind a firewall, which could block the incoming connection from the server

![image](https://github.com/psaumur/CCNA/assets/106411237/5872df1c-b97f-4f61-b0da-6a06e7f69f1a)

FTP VERSUS TFTP

![image](https://github.com/psaumur/CCNA/assets/106411237/e7c11655-61be-40f0-943c-8c51998dc2e2)

---

IOS FILE SYSTEMS

- A file system is a way of controlling how data is stored and retrieved
- You can view the file system of a Cisco IOS device with `show file systems`

![image](https://github.com/psaumur/CCNA/assets/106411237/eb6e12b6-3c34-4e05-93cb-e4368764da74)

---

USING FTP / TFTP IN IOS

- You can view the current version of IOS with `show version`

![image](https://github.com/psaumur/CCNA/assets/106411237/746859c5-d89d-42f5-b198-d0cba7f3682d)

- You can view the contents of flash with `show flash`

![image](https://github.com/psaumur/CCNA/assets/106411237/d131b08c-572d-46b3-8910-0d423b85dc94)

---

COPYING files WITH TFTP

STEP 1

![image](https://github.com/psaumur/CCNA/assets/106411237/f0ce7ea9-115e-4db8-9baf-55ee1bf0d548)

STEP 2

![image](https://github.com/psaumur/CCNA/assets/106411237/9be3610d-3e22-476f-ab90-117ba7d93cf0)

STEP 3

![image](https://github.com/psaumur/CCNA/assets/106411237/604528f7-af5d-44a4-a877-c9d82d7910d1)

---

COPYING files with FTP

STEP 1

![image](https://github.com/psaumur/CCNA/assets/106411237/0e9c1dc5-0dce-4cbb-b584-0509c2119f63)

STEP 2 and 3 identical to TFTP above

---

COMMAND SUMMARY

![image](https://github.com/psaumur/CCNA/assets/106411237/e5f525cd-6e98-4501-9e7c-1c1f4af1d23e)
