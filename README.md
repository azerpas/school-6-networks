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

### Network transmission parameters
- Propagation time
- Data emission rate 
- Emission time
- Data transfer rate
- Transfer time

## Medium access protocols (Physical & Data-Link Layers)

1. 