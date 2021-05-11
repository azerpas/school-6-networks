# Network & Protocols 

## Summary
1. Main concepts
2. [Physical Layer](#physical-layer)
3. Data-link layer
4. Network layer
5. Transport layer

## Main concepts

### Communication network
Set of hardware and software resources that exchange information     
*Internet, mobile network, drones, IoT*     

#### Three categories of networks
- **Telecommunications networks**     
Communication between individuals in:     
    - electromagnetic waves
    - binary information    
Such as GSM networks
- **Computer networks**     
    - Terrastrial wired 
    - Wireless
    - Satellite networks       
- **Broadcast networks**     
Connect computers and exchange binary data
    - Internet
    - Cloud
    - 5G

### Network classification
- Bus Network
- Personal Area Network
- Local Area Network
- Departemental Area Network
- Metropolitan Area Network
- Wide Area Network

### Network topology
- **Physical** : describes how the different nodes are linked together
- **Logical** : describes how information is transmitted from one node to another

### Modes
- Connected mode
    1. Connect
    2. Data transfer
    3. Release connection
- Non connected    
    *A send to B without connection.*     
    Route by:
    - Timing
    - Async

### Switching
Techniques used by nodes to transfer data from A to B
- circuit
- packet
- message

## A network as a system
![img](https://user-images.githubusercontent.com/19282069/116002166-b7429a80-a5f8-11eb-9ecc-e6c85f6aa6a1.png)
### Physical
1. A mean to send signals - **physical medium**
2. Convert information into signal – **encoding**
### Data link
3. Manage the concuren access to the shared medium (avoid collision) – **medium access control**
4. Ensure that the information is sent correctly – **error control**
5. Connect more that 2 machines – **switching**
6. Identify a machine in a network – **physical adress**
### Network
7. Interconnect different networks – **information routing & logical adress**
### Transport
8. Manage the amount of information sent based on receptors and network capacity – **flow control**
9. Deliver the message to the corresponding application – **multiplexing using ports**
10. Maintain an message exchange – **connexion**
11. Ensure message sequencing – **sequence control**
12. Ensure the arrival of the entire message – **retransmission**
### Session
13. Manage the progression of sessions – **session management**
### Presentation
14. Encoding data into a universal language – **presentation**
### Application
15. Manage application rules (depends on the application) - **application**

## Layered structure
- Each layer is based on the previous one
- Each layer pass information to upper layer
### OSI
![OSI Reference](https://user-images.githubusercontent.com/19282069/116220646-292bf880-a74d-11eb-90a2-43466cbe6d82.png)

The model has 7 layers
## Software layers
### Application Layer
#### Many protocols
- HTTP: Web
- FTP: Files
- SMTP: Mails

### Presentation Layer
#### Functions
- Encryption 
- Translation
- Compression

### Session Layer
#### Functions
- Dialogue control
- Recovery points
- Backtracking
- Orchestration

## Transport layer (heart of OSI)
### Transport Layer
Establish connection between to ports to end-to-end delivery.    
#### Functions 
- Segmentation and reassembly 
- Connection Control
- Multiplexing and Demultiplexing
- Flow control
- Error control

# Hardware layers
### Network Layer
- Control the operation of the subnet.     
- Deliver packets from source to destination.     
- On same network communication, the *Network Layer* is almost inexistant.
```c
// Exchanged unit: Packet
```
### Data-link Layer
- Establish, maintain and release data-link connection from entities
- Detect and correct error from *Physical layer*
- Delimit and synchronize data frames
```c
// Exchanged unit: Frame
```
## Physical Layer
- Mechanical, electrical and functional means
- Communicate with bits through signals
```c
// Exchanged unit: bits
```
1. Digital data     
Information bits    
**Example:** LAN     
**Encodings:** NRZ, NRZI, Manchester

2. Anological data  
Voltage    
**Example:** Voice channel

### Cable specifications
- **Speed**:    
Influenced by medium
- **Distance**:     
Influence degradation and attenuation

### Bandwidth
- Amount of information that can be transmitted   
**bit/s**
- **Example:** ADSL

### Ethernet
- Several Ethernet variant exist and differ in: 
    - **Type of support** (UTP, STP, Coax, Fiber)
    - **Topology** (Bus, Star, Tree)
    - **Rate** (1, 5, 10, 100 Mbps, 1 Gbps, 10 Gbps, 100 Gbps)
- **Example:** 100 base F = Optical Fiber   

**Ethernet is the dominant LAN tech**
- Simplicity and ease of maintenance
- Ability to incorporate new techs
- Reliability
- Low cost of installation and upgrate 

### Network transmission parameters
- Propagation time
- Data emission rate 
- Emission time
- Data transfer rate
- Transfer time

## Medium access protocols (Physical & Data-Link Layers)

**2 approaches**     
1. Random allocation: access time **not** limited
2. Deterministic allocation: access time limited

### CSMA

Todo

### Identify a machine in the network

#### Universal Address Mac
- 6 bytes address (48bits)
- Unique to each network card
- = Contructor card + sequence number

### Ethernet frame structure
![Ethernet frame](https://user-images.githubusercontent.com/19282069/116580141-604c0680-a913-11eb-859e-0e817f8482b3.png)

### How does it work?
1. Send 64 bits of synchronization data (*preambule*)
    1. Destination & Source addresses
    2. Type of Protocol **or** Length of data
    3. The payload
    4. Send the FCS (Frame Check Sequence) on the fly
2. On receiving
    1. Check if it match the MAC address
    2. Calculate and check if it match given FCS
    3. If valid, data forwarded to next layer (network)

# Interconnection 
## Level 1 interconnection   
### **o Repeater, Hub:** signal amplification and broadcast
- Allow more hosts
- Can cause **collision** if too much trafic (hosts)
#### Ethernet Switching
- if machines.length increases, the increasing number of collisions can significantly reduce network performance
- to limit the effects collision domains must be created by installing bridges (Bridge) or switches (Switch)

## Level 2 interconnection   
### **o Bridge, switch:** signal amplifier and level 2 processing (frame switching)
#### Bridge 
Create single aggregated network from two network segments  
```
Hosts: A B C  
Ports: 1 2 3
-----
Action: (A -> B)
1. Bridge set address and port of A in table
2. Check for destination in table -> not found
3. Broadcast to all ports
4. Both receive it, C pass, B decode it
```
#### Switch
- Reduce collision to increase the data rate
- Replaces central passive nodes (HUB)
- Low cost Virtual Network (VLAN)

#### Switching modes
1. Cut-through  
Forward as soon as the MAC address is known
2. Store-and-forward    
Wait to receive all data to procede to FCS then reject or send
3. Fragment-free    
Reads first 64 bytes and start transmitting while checking addresses
## Level 3 interconnection   
### **o Router**
- Identification of entities by IP address
- Hide heterogeneity of the supports by federating them
- Provide a network layer protocol suitable for my medias (thanks to **ip protocol**)

## Level 4 to 7 interconnection  
**o Gateway**

# IP Address
Used to identity each machine on a network 
#### Two types of addresses:
1. Physical address (Data-Link)
- Fixed by manufacturer and immutable
- Only works in physical networks (ethernet)
2. Logical address (**IP address**) 

## Format
`<network> <machine>`   
- network prefix: network identifier 
- identifier: machine identifier

![example](https://user-images.githubusercontent.com/19282069/116785192-87801080-aa98-11eb-8fcb-9486ea4d4c01.png)

**One network ID per physical network**
![example](https://user-images.githubusercontent.com/19282069/116785236-b8f8dc00-aa98-11eb-9b61-0c7361680314.png)

## Multiple classes

### A
`0.0.0.0` to `127.255.255.255`
### B 
`128.0.0.0` to `191.255.255.255`
### C 
`192.0.0.0` to `223.255.255.255`
### D (multicast)
`224.0.0.0` to `239.255.255.255`
### E (reserved)
`240.0.0.0` to `255.255.255.255`

## Address mask
The mask indicates the border between the `<network>` part and the `<machine>`  
`255.255.255.0` = `..../24`     
- `1` network
- `0` machine

## IP addresses (example)
![Example](https://user-images.githubusercontent.com/19282069/116785475-0de92200-aa9a-11eb-83e8-e32e777ff340.png)
![1](https://user-images.githubusercontent.com/19282069/116808535-9e2a7400-ab39-11eb-81ce-7740e5a4d915.png)

## Public vs Private address

### Private
Some addresses are used in local **only**
* Class A: `10.0.0.1` to `10.255.255.254`
* Class B: `172.16.0.1` to `172.31.255.254`
* Class C: `192.0.0.1` to `192.168.255.25`

### Public
Used online and known by the routers

## NAT
Map the local address into public address to communicate with the internet.

## Address assignment
Prefixes of IPv4 are assigned by the IANA: *Internet Assigned Numbers Authority*

## Subneting
Multiple physical networks share one IP address
![subnet](https://user-images.githubusercontent.com/19282069/116810398-da62d200-ab43-11eb-8f19-15f603a56acf.png)
3 subnetworks = 2^2, 4 possible subnetworks
![example](https://user-images.githubusercontent.com/19282069/116814301-89110d80-ab58-11eb-8e20-f1bffa1a13b1.png)

## VLSM (Variable Length Subnet Masks)

![VLSM Example](https://user-images.githubusercontent.com/19282069/116814513-a4304d00-ab59-11eb-94d8-2eacec000777.png)

## IP Packet Structure

- Version *(4 bits)*
- Internet Header Length *(4 bits)*
- Total Length
- Time to Live *(8 bits)*
- Protocol 
- Header Checksum

# Fragmentation
Split the packet into smaller fragments to respect *MTU* (Maximum Transfer Unit)
- Splitting by layer 3 entities
- Reassembly done at reception

Works with:
- Identification, common to all fragments
- Flags *(3 bits)*, required for fragmentation
- Offset

![Example](https://user-images.githubusercontent.com/19282069/116815656-d1cbc500-ab5e-11eb-9b44-f37959f6bad4.png)

# Transport Layer (UDP/TCP)

2 protocols: 
## UPD
Connection-less protocol      
Very fast protocol, we use it in all real-time communication (streaming, webcasting, video conference, gaming, VOIP)     
### Port
The transfer is made from source port to destination port.  
- Applications use *Socket API* to connect
- Synchronous with queue
### UDP Datagrams
Consist of UDP Header and UDP Data
1. with data protection
2. without delivery confirmation
## TCP
- Sophisticated and reliable
- Longer than UDP
- Check data on receiption
- Error detection      
### Usage     
- Sending emails
- Exchanging files
- Internet
### Sequencing
- Every byte sent is numbered
	- Number will help the receiver to reassemble data
	- Thus, sending back corrupted or missed data 

## Example
PC1 ---------> SERVER     

Source port is a random generated number.    
Destination port corresponds to the application the client is trying to access.     
We will be using port 25 to access email app.    
### Three-way handshake
1. SYN : Client is asking for sync
2. SYN-ACK : Server is acknowledging
3. ACK : Client is confirming
