# Networking
Networking Concepts
1. **TCP vs UDP**

    TCP and UDP are both transport layer protocols. **TCP is a connection orientated protocol** and provides reliable message transfer. **UDP is a connection less protocol** and does not guarantee message delivery.
    
    TCP: **The TCP transport takes care of errors on the link**, and the application can be confident that the data received is error free.
    TCP is used by application protocols that need guaranteed message delivery. HTTP,FTP, SMTP, POP3, IMAP4 and many other common Internet application protocols use TCP.

    UDP: **UDP does not correct or recover errors in the message**. Any error detection and recovery is the responsibility of the receiving application. Because there is no connection setup, UDP is faster than    TCP and results in less network traffic . In addition it doesn’t consume resources on the receiving machine as it doesn’t hold a connection open. Utility applications like DNS, DHCP, RIP and others use UDP.

**The UDP header (8 bytes) is considerably much smaller than the TCP header (20 bytes)**. Both the UDP and TCP header contain 16 bit source and destination Port fields. 

Both TCP and UDP protocols use ports. You can have an application running on a computer using TCP port 80 and another application using UDP port 80.

An application address is effectively:
IP address + protocol (TCP or UDP) + port number

The use of UDP is expected to increase with IOT as sensor type data is ideal for sending via UDP vs TCP.
![image](https://user-images.githubusercontent.com/39849388/111714658-17714e80-888d-11eb-8dd3-e4f6fc8f3573.png)

TCP Handshake:

For example, when an email is sent over TCP, a connection is established and a 3-way handshake is made. First, the source send an SYN “initial request” packet to the target server in order to start the dialogue. Then the target server then sends a SYN-ACK packet to agree to the process. Lastly, the source sends an ACK packet to the target to confirm the process, after which the message contents can be sent. The email message is ultimately broken down into packets before each packet is sent out into the Internet, where it traverses a series of gateways before arriving at the target device where the group of packets are reassembled by TCP into the original contents of the email.


![image](https://user-images.githubusercontent.com/39849388/111714701-3243c300-888d-11eb-9fc2-10173a0e6d9c.png)

2. **TCP/IP vs OSI Model: What's the Difference?**

While TCP/IP is the newer model, the Open Systems Interconnection (OSI) model is still referenced a lot to describe network layers!
**OSI Model Layers:**

1. Physical (e.g. cable, RJ45)
2. Data Link (e.g. MAC, switches)
3. Network (e.g. IP, routers)
4. Transport (e.g. TCP, UDP, port numbers)
5. Session (e.g. Syn/Ack)
6. Presentation (e.g. encryption, ASCII, PNG, MIDI)
7. Application (e.g. SNMP, HTTP, FTP)

The TCP/IP model is a more concise framework, with only 4 layers:

1. Network Access (or Link)
2. Internet
3. Transport (or Host-to-Host)
4. Application (or Process)


![image](https://user-images.githubusercontent.com/39849388/111740452-c3cc2880-88bf-11eb-8ecf-91f752368717.png)




3. **What are the Network Layers and their functions?**


**OSI Model:**
• Layer 7 (Application): Most of what the user actually interacts with is at this layer. Web browsers and other internet-connected applications (like Skype or Outlook) use Layer 7 application protocols.
• Layer 6 (Presentation): This layer converts data to and from the Application layer. In other words, it translates application formatting to network formatting and vice versa. This allows the different layers to understand each other.
• Layer 5 (Session): This layer establishes and terminates connections between devices. It also determines which packets belong to which text and image files.
• Layer 4 (Transport): This layer coordinates data transfer between system and hosts, including error-checking and data recovery.
• Layer 3 (Network): This layer determines how data is sent to the receiving device. It’s responsible for packet forwarding, routing, and addressing.
• Layer 2 (Data Link): Translates binary (or BITs) into signals and allows upper layers to access media.
• Layer 1 (Physical): Actual hardware sits at this layer. It transmits signals over media.

**TCP Model:**
• Layer 1 (Network Access): Also called the Link or Network Interface layer. This layer combines the OSI model’s L1 and L2.
• Layer 2 (Internet): This layer is similar to the OSI model’s L3.
• Layer 3 (Transport): Also called the Host-to-Host layer. This layer is similar to the OSI model’s L4.
• Layer 4 (Application): Also called the Process layer, this layer combines the OSI model’s L5, L6, and L7.


4. **What is Ephemeral port?**

The ephemeral ports are the short-lived transport protocol ports for Internet Protocol (IP) communications. Ephemeral ports are allocated automatically from a predefined range by the IP stack software. An ephemeral port is typically used by the Transmission Control Protocol (TCP), User Datagram Protocol (UDP) or the Stream Control Transmission Protocol (SCTP) as the port assignment for the client end of a client-server communication to a well-known port on a server. 
What that means is, when a client initiates a request it choose a random port from ephemeral port range and it expects the response at that port only. Take note of the below statement:

When we say that the client initiates an HTTPs or HTTP request it actually means that the destination port is 443 or 80. It is NOT the sender port.
**It is the client’s operating system that chooses the sender’s port from the ephemeral port range and this range varies depending on the OS**. For example, many Linux kernels including Amazon Linux kernel use port 32768-61000. Windows OS through Windows Server 2003 use port 1025-5000. While Windows Server 2008 and later use port 49152-65535. Elastic load balancers and NAT gateways use port 1024-65535.
After communication is terminated, the port becomes available for use in another session. However, it is usually reused only after the entire port range is used up![image]

5.  **What is IPSEC?**

IPsec is a group of protocols that are used together to set up encrypted connections between devices. It helps keep data sent over public networks secure. IPsec is often used to set up VPNs, and it works by encrypting IP packets, along with authenticating the source where the packets come from.

Within the term "IPsec," "IP" stands for "Internet Protocol" and "sec" for "secure." The Internet Protocol is the main routing protocol used on the Internet; it designates where data will go using IP addresses. **IPsec is secure because it adds encryption* and authentication to this process**.

6. **What is a VPN? What is an IPsec VPN?**

A virtual private network (VPN) is an encrypted connection between two or more computers. VPN connections take place over public networks, but the data exchanged over the VPN is still private because it is encrypted.

VPNs make it possible to securely access and exchange confidential data over shared network infrastructure, such as the public Internet. For instance, when employees are working remotely instead of in the office, they often use VPNs to access corporate files and applications.

Many VPNs use the IPsec protocol suite to establish and run these encrypted connections. However, not all VPNs use IPsec. Another protocol for VPNs is SSL/TLS, which operates at a different layer in the OSI model than IPsec.

7. **How does IPsec work?**

IPsec connections include the following steps:

**Key exchange:** Keys are necessary for encryption; a key is a string of random characters that can be used to "lock" (encrypt) and "unlock" (decrypt) messages. IPsec sets up keys with a key exchange between the connected devices, so that each device can decrypt the other device's messages.

**Packet headers and trailers:** All data that is sent over a network is broken down into smaller pieces called packets. Packets contain both a payload, or the actual data being sent, and headers, or information about that data so that computers receiving the packets know what to do with them. IPsec adds several headers to data packets containing authentication and encryption information. IPsec also adds trailers, which go after each packet's payload instead of before.

**Authentication:** IPsec provides authentication for each packet, like a stamp of authenticity on a collectible item. This ensures that packets are from a trusted source and not an attacker.

**Encryption:** IPsec encrypts the payloads within each packet and each packet's IP header (unless transport mode is used instead of tunnel mode — see below). This keeps data sent over IPsec secure and private.

**Transmission:** Encrypted IPsec packets travel across one or more networks to their destination using a transport protocol. At this stage, IPsec traffic differs from regular IP traffic in that it most often uses UDP as its transport protocol, rather than TCP. TCP, the Transmission Control Protocol, sets up dedicated connections between devices and ensures that all packets arrive. UDP, the User Datagram Protocol, does not set up these dedicated connections. IPsec uses UDP because this allows IPsec packets to get through firewalls.

**Decryption:** At the other end of the communication, the packets are decrypted, and applications (e.g. a browser) can now use the delivered data.

8. **What is the difference between IPsec tunnel mode and IPsec transport mode?**

**IPsec tunnel mode is used between two dedicated routers**, with each router acting as one end of a virtual "tunnel" through a public network. **In IPsec tunnel mode, the original IP header containing the final destination of the packet is encrypted, in addition to the packet payload.** To tell intermediary routers where to forward the packets, IPsec adds a new IP header. At each end of the tunnel, the routers decrypt the IP headers to deliver the packets to their destinations.

**In transport mode, the payload of each packet is encrypted, but the original IP header is not.** Intermediary routers are thus able to view the final destination of each packet — unless a separate tunneling protocol (such as GRE) is used.

9. **What port does IPsec use?**

A network port is the virtual location where data goes in a computer. Ports are how computers keep track of different processes and connections; if data goes to a certain port, the computer's operating system knows which process it belongs to. **IPsec usually uses port 500.**

10. **How does IPsec impact MSS and MTU?**
MSS and MTU are two measurements of packet size. Packets can only reach a certain size (measured in bytes) before computers, routers, and switches cannot handle them. MSS measures the size of each packet's payload, while MTU measures the entire packet, including headers. Packets that exceed a network's MTU may be fragmented, meaning broken up into smaller packets and then reassembled. Packets that exceed the MSS are simply dropped.

IPsec protocols add several headers and trailers to packets, all of which take up several bytes. For networks that use IPsec, either the MSS and MTU have to be adjusted accordingly, or packets will be fragmented and slightly delayed. Usually, the MTU for a network is 1,500 bytes. A normal IP header is 20 bytes long, and a TCP header is also 20 bytes long, meaning each packet can contain 1,460 bytes of payload. However, IPsec adds an Authentication Header, an ESP header, and associated trailers. These add 50-60 bytes to a packet, or more.

11. **What is an autonomous system?**
The Internet is a network of networks*, and autonomous systems are the big networks that make up the Internet. More specifically, an autonomous system (AS) is a large network or group of networks that has a unified routing policy. Every computer or device that connects to the Internet is connected to an AS.

![image](https://user-images.githubusercontent.com/39849388/111716758-ac764680-8891-11eb-9d70-f8030c27ae1e.png)


Autonomous systems around the world with ASNs
Imagine an AS as being like a town's post office. Mail goes from post office to post office until it reaches the right town, and that town's post office will then deliver the mail within that town. Similarly, data packets cross the Internet by hopping from AS to AS until they reach the AS that contains their destination Internet Protocol (IP) address. Routers within that AS send the packet to the IP address.

Every AS controls a specific set of IP addresses, just as every town's post office is responsible for delivering mail to all the addresses within that town. The range of IP addresses that a given AS has control over is called their "IP address space."

Most ASes connect to several other ASes. If an AS connects to only one other AS and shares the same routing policy, it may instead be considered a subnetwork of the first AS.

Typically, each AS is operated by a single large organization, such as an Internet service provider (ISP), a large enterprise technology company, a university, or a government agency.


12. **What is an AS routing policy?**
An AS routing policy is a list of the IP address space that the AS controls, plus a list of the other ASes to which it connects. This information is necessary for routing packets to the correct networks. ASes announce this information to the Internet using the Border Gateway Protocol (BGP).

13. **What is IP address space?**
A specified group or range of IP addresses is called "IP address space." Each AS controls a certain amount of IP address space. (A group of IP addresses can also be called an IP address "block".)


14. **What is an autonomous system number (ASN)?**
Each AS is assigned an official number, or autonomous system number (ASN), similar to how every business has a business license with an unique, official number. But unlike businesses, external parties often refer to ASes by their number alone.

AS numbers, or ASNs, are unique 16 bit numbers between 1 and 65534 or 32 bit numbers between 131072 and 4294967294. They are presented in this format: AS(number). For instance, Cloudflare's ASN is AS13335. According to some estimates, there are over 90,000 ASNs in use worldwide.

ASNs are only required for external communications with inter-network routers (see "What is BGP?" below). Internal routers and computers within an AS may not need to know that AS's number, since they are only communicating with devices within that AS.

An AS has to meet certain qualifications before the governing bodies that assign ASNs will give it a number. It must have a distinct routing policy, be of a certain size, and have more than one connection to other ASes. There is a limited amount of ASNs available, and if they were given out too freely, the supply would run out and routing would become much more complex.

15. **What is BGP?**
ASes announce their routing policy to other ASes and routers via the Border Gateway Protocol (BGP). **BGP is the protocol for routing data packets between ASes**. Without this routing information, operating the Internet on a large scale would quickly become impractical: data packets would get lost or take too long to reach their destinations.

**Each AS uses BGP to announce which IP addresses they are responsible for and which other ASes they connect to**. BGP routers take all this information from ASes around the world and put it into databases called **routing tables** to determine the fastest paths from AS to AS. When packets arrive, BGP routers refer to their routing tables to determine which AS the packet should go to next.

With so many ASes in the world, BGP routers are constantly updating their routing tables. As networks go offline, new networks come online, and ASes expand or contract their IP address space, all of this information has to be announced via BGP so that BGP routers can adjust their routing tables.

16. **Why is BGP routing necessary? Isn't IP used for routing?**

IP, or the Internet Protocol, is indeed used for routing in that it specifies which destination each packet is going to. BGP is responsible for directing packets on the fastest route to their destination. Without BGP, IP packets would bounce around the Internet randomly from AS to AS, like a driver trying to reach their destination by guessing which roads to take.

17. **How do autonomous systems connect with each other?**
ASes connect with each other and exchange network traffic (data packets) through a process called peering. One way ASes peer with each other is by connecting at physical locations called Internet Exchange Points (IXPs). An IXP is a large local area network (LAN) with lots of routers, switches, and cable connections.

18. **What are the main routing protocols?**
In networking, a protocol is a standardized way of formatting data so that any connected computer can understand the data. A routing protocol is a protocol used for identifying or announcing network paths.

The following protocols help data packets find their way across the Internet:

**IP:** The Internet Protocol (IP) specifies the origin and destination for each data packet. Routers inspect each packet's IP header to identify where to send them.

**BGP:** The Border Gateway Protocol (BGP) routing protocol is used to announce which networks control which IP addresses, and which networks connect to each other. (The large networks that make these BGP announcements are called autonomous systems.) BGP is a dynamic routing protocol.

The below protocols route packets within an AS:

**OSPF:** The Open Shortest Path First (OSPF) protocol is commonly used by network routers to dynamically identify the fastest and shortest available routes for sending packets to their destination.

**RIP:** The Routing Information Protocol (RIP) uses "hop count" to find the shortest path from one network to another, where "hop count" means number of routers a packet must pass through on the way. (When a packet goes from one network to another, this is known as a "hop.")

19. **What is maximum segment size (MSS)?**
MSS (maximum segment size) limits the size of packets, or small chunks of data, that travel across a network, such as the Internet. All data that travels over a network is broken up into packets. Packets have several headers attached to them that contain information about their contents and destination. MSS measures the non-header portion of a packet, which is called the payload.

If a data packet is compared to a transport truck, with the header being the truck itself and the payload being the trailer and cargo, then MSS is like a scale that measures only the trailer. If the trailer weighs too much, then the truck is not allowed to continue to its destination.

More specifically, MSS is the largest TCP (Transport Control Protocol) segment size that a network-connected device can receive. MSS defines "segment" as only the length of the payload, not any attached headers. MSS is measured in bytes.

![image](https://user-images.githubusercontent.com/39849388/111717384-e6941800-8892-11eb-8fa5-cf690d27d56e.png)


Data packet headers and payload - TCP segment and MSS
MSS is determined by another metric that has to do with packet size: MTU, or the maximum transmission unit, which does include the TCP and IP (Internet Protocol) headers. To continue the analogy, MTU measures the total weight of the truck and its trailer and cargo, instead of just the trailer and cargo.

Essentially, the MSS is equal to MTU minus the size of a TCP header and an IP header:

MTU - (TCP header + IP header) = MSS

**One of the key differences between MTU and MSS is that if a packet exceeds a device's MTU, it is broken up into smaller pieces**, or "fragmented." In contrast, if a packet exceeds the MSS, it is dropped and not delivered.

