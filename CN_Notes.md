# COMPUTER NETWORKS — Complete Theory Book

> **A Comprehensive Revision Guide for Exams, Placements & Interviews**

---

---

# UNIT 1: INTRODUCTION

---

## 1.1 Networks and Types

### Definition
A **computer network** is a collection of two or more interconnected computing devices (computers, printers, servers, smartphones, etc.) that are linked together to share resources, exchange data, and communicate with each other using a set of rules called protocols.

### Detailed Explanation
A network allows devices to communicate and share resources like files, printers, internet connections, and applications. Networks can be categorized based on their **geographical span**, **ownership**, and **purpose**.

#### Types of Networks

**1. PAN (Personal Area Network)**
- Covers a very small area, typically within a range of a few meters (around 10 meters).
- Used for connecting personal devices like smartphones, tablets, laptops, and wearable devices.
- Technologies: Bluetooth, Zigbee, Infrared.
- Example: Connecting a wireless keyboard to a laptop via Bluetooth.

**2. LAN (Local Area Network)**
- Covers a small geographical area such as a single building, office, school, or campus.
- Typically owned and managed by a single organization.
- Offers high data transfer speeds (10 Mbps to 10 Gbps or more).
- Technologies: Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11).
- Example: A computer lab in a college where all PCs are connected via Ethernet.

**3. MAN (Metropolitan Area Network)**
- Spans a city or a large campus.
- Larger than a LAN but smaller than a WAN.
- Often used by local governments or large corporations to connect multiple LANs within a city.
- Technologies: DQDB (Distributed Queue Dual Bus), Metro Ethernet.
- Example: Cable TV network spread across a city.

**4. WAN (Wide Area Network)**
- Covers a large geographical area such as countries or continents.
- Connects multiple LANs and MANs together.
- Typically uses leased telecommunication lines, satellites, or undersea cables.
- The **Internet** is the largest WAN.
- Technologies: MPLS, Frame Relay, ATM.
- Example: A multinational company connecting its offices in India, the USA, and the UK.

**5. VPN (Virtual Private Network)**
- A secure, encrypted connection over a public network (like the Internet).
- Creates a private tunnel within a public network.
- Used for secure remote access to organizational resources.
- Example: An employee accessing the company's internal network from home using a VPN client.

### Key Points / Highlights
| Type | Span | Speed | Ownership |
|------|------|-------|-----------|
| PAN | Few meters | Low–Medium | Individual |
| LAN | Building/Campus | High | Private |
| MAN | City | Moderate–High | Private/Public |
| WAN | Country/Globe | Lower than LAN | Public/Private |

### MCQ Focus Section
- **LAN** provides the highest speed among all network types.
- **MAN** spans a city; it is between LAN and WAN in size.
- The **Internet** is the best example of a WAN.
- **VPN** provides security over a public network using encryption and tunneling.
- PAN uses technologies like **Bluetooth and Zigbee**, not Ethernet.
- A network within a single room is best described as a **LAN** (or PAN if personal devices).

---

## 1.2 Uses of Computer Networks

### Definition
Computer networks are used to facilitate **communication**, **resource sharing**, **data exchange**, and **collaboration** among users and systems distributed across different locations.

### Detailed Explanation

**1. Resource Sharing**
- Hardware resources (printers, scanners, storage) and software resources (applications, databases) can be shared among multiple users.
- Eliminates the need for every user to have their own dedicated resources.

**2. Communication**
- Networks enable fast and efficient communication through email, instant messaging, video conferencing, and VoIP (Voice over IP).
- Example: Zoom calls, Slack messaging.

**3. Data Sharing and Transfer**
- Files and data can be easily shared between devices connected to the network.
- Example: Shared drives in an office network.

**4. Internet Access**
- Networks provide shared access to the Internet for all connected devices.

**5. Reliability and Redundancy**
- Data can be replicated on multiple machines, so if one fails, others can provide backup.
- Enhances fault tolerance.

**6. Cost Savings**
- Sharing resources reduces overall hardware and software costs.
- Centralized management reduces administrative costs.

**7. E-Commerce and Online Services**
- Networks enable online shopping, banking, ticketing, and various cloud-based services.

**8. Entertainment**
- Streaming services (Netflix, YouTube), online gaming, and social media all rely on networks.

### Key Points / Highlights
- The primary purpose of a computer network is **resource sharing and communication**.
- Networks improve **reliability** through data redundancy.
- **Client-server** and **peer-to-peer** are two fundamental models of network usage.

### MCQ Focus Section
- The most fundamental use of a network is **resource sharing**.
- **VoIP** stands for Voice over Internet Protocol — it uses networks for voice communication.
- **Redundancy** in networks refers to having backup copies of data for fault tolerance.
- Networks reduce cost through **centralized resource management**.

---

## 1.3 Network Software Architecture — Layers and Protocols

### Definition
**Network software architecture** refers to the logical organization of network communication into a set of **layers**, where each layer performs a specific function and communicates with the layers directly above and below it using well-defined **protocols**.

A **protocol** is a set of rules and conventions that govern how data is formatted, transmitted, received, and acknowledged between devices on a network.

### Detailed Explanation

#### Why Layered Architecture?
- **Modularity**: Each layer handles a specific task, making the system easier to design and maintain.
- **Interoperability**: Devices from different manufacturers can communicate if they follow the same protocols.
- **Ease of Modification**: A change in one layer does not affect other layers.
- **Standardization**: Layers provide a standard framework for network communication.

#### Key Concepts

**1. Layers**
- The network communication process is divided into distinct layers (e.g., 7 layers in OSI, 4 or 5 in TCP/IP).
- Each layer provides services to the layer above it and uses services from the layer below it.

**2. Protocols**
- Each layer has its own set of protocols.
- Example: HTTP operates at the Application Layer; TCP operates at the Transport Layer.

**3. Interfaces**
- The boundary between two adjacent layers is called an **interface**.
- It defines which services the lower layer provides to the upper layer.

**4. Peer-to-Peer Communication**
- Logically, each layer on one machine communicates with the same layer on another machine (called **peer communication**).
- Physically, data flows down the layers on the sender side, across the physical medium, and up the layers on the receiver side.

**5. Encapsulation**
- As data moves down the layers, each layer adds its own header (and sometimes a trailer) to the data — this process is called **encapsulation**.
- At the receiving end, each layer removes its respective header — this is called **decapsulation**.

**6. PDU (Protocol Data Unit)**
- The data unit at each layer has a specific name:
  - Application Layer → **Data / Message**
  - Transport Layer → **Segment** (TCP) / **Datagram** (UDP)
  - Network Layer → **Packet**
  - Data Link Layer → **Frame**
  - Physical Layer → **Bits**

### Example
When you browse a website:
1. The browser (Application Layer) creates an HTTP request.
2. TCP (Transport Layer) breaks it into segments and ensures reliable delivery.
3. IP (Network Layer) adds source and destination IP addresses, creating packets.
4. Ethernet (Data Link Layer) creates frames with MAC addresses.
5. The Physical Layer converts frames into electrical/optical signals and transmits them.

### Key Points / Highlights
- Layered architecture provides **modularity, interoperability, and ease of maintenance**.
- Each layer adds a **header** during encapsulation.
- **Protocols** are the rules; **layers** are the logical groupings.
- PDU names: Message → Segment → Packet → Frame → Bits.

### MCQ Focus Section
- **Encapsulation** is the process of adding headers as data moves from upper to lower layers.
- The PDU at the Data Link Layer is called a **Frame**.
- The PDU at the Network Layer is called a **Packet**.
- **Peer communication** is logical (virtual), not physical.
- The difference between a **protocol** and an **interface**: A protocol governs communication between peer layers on different machines; an interface defines services between adjacent layers on the same machine.
- The PDU at the Transport Layer for TCP is **Segment**; for UDP it is **Datagram** (also called User Datagram).

---

## 1.4 Network Hardware Architecture — Topologies

### Definition
**Network topology** refers to the **physical or logical arrangement** of devices (nodes) and connections (links) in a computer network. It defines how devices are interconnected and how data flows between them.

### Detailed Explanation

#### 1. Bus Topology
- All devices are connected to a single central cable called the **bus** or **backbone**.
- Data sent by a device travels in both directions along the bus until it reaches the destination.
- A **terminator** is placed at each end of the bus to absorb signals and prevent signal reflection.
- **Advantages**: Simple to set up, requires less cable, cost-effective for small networks.
- **Disadvantages**: If the backbone cable fails, the entire network goes down. Performance degrades as more devices are added. Difficult to troubleshoot.

#### 2. Star Topology
- All devices are connected to a **central device** (hub or switch).
- All communication passes through the central device.
- **Advantages**: Easy to install and manage. Failure of one cable does not affect others. Easy to add new devices.
- **Disadvantages**: If the central device fails, the entire network goes down. Requires more cable than bus topology.
- **Most commonly used topology** in modern LANs.

#### 3. Ring Topology
- Each device is connected to exactly **two other devices**, forming a circular (ring) path.
- Data travels in **one direction** (unidirectional) or **both directions** (dual ring/bidirectional).
- A **token** is used for access control in Token Ring networks.
- **Advantages**: Equal access for all devices. Predictable performance.
- **Disadvantages**: Failure of one device can disrupt the entire network (unless it's a dual ring). Difficult to add or remove devices.

#### 4. Mesh Topology
- Every device is connected to **every other device** directly.
- **Full Mesh**: Every device is connected to every other device. Number of links = n(n-1)/2.
- **Partial Mesh**: Some devices are connected to all others, some are connected only to those they exchange data with most frequently.
- **Advantages**: Highly reliable and fault-tolerant. Multiple paths for data. No traffic congestion.
- **Disadvantages**: Very expensive due to large number of cables and ports. Complex to install and manage.

#### 5. Tree (Hierarchical) Topology
- A combination of **star and bus** topologies.
- Devices are arranged in a hierarchical structure with a root node and branch nodes.
- **Advantages**: Scalable. Supports hierarchical management.
- **Disadvantages**: If the backbone fails, the entire segment goes down. Complex cabling.

#### 6. Hybrid Topology
- A combination of two or more different topologies.
- Designed to leverage the advantages of different topologies.
- **Example**: A network using star topology in individual departments, connected via a bus backbone.

### Key Points / Highlights
| Topology | Central Device | Fault Tolerance | Cost | Use Case |
|----------|---------------|-----------------|------|----------|
| Bus | None (backbone cable) | Low | Low | Small, temporary networks |
| Star | Hub/Switch | Medium | Medium | Modern LANs |
| Ring | None (circular) | Low (single) | Medium | Token Ring networks |
| Mesh | None | Very High | Very High | Military, critical systems |
| Tree | Root node | Medium | Medium-High | Large organizations |

### MCQ Focus Section
- **Star topology** is the most widely used in modern LANs.
- In **bus topology**, a terminator prevents signal reflection.
- **Mesh topology** provides the highest fault tolerance and redundancy.
- In a **full mesh** network with n devices, the number of links = **n(n-1)/2**.
- **Ring topology** uses a token for controlling access to the network medium.
- **Tree topology** is a combination of Star and Bus topologies.
- The failure of the central hub in a **star topology** brings down the entire network.
- **Hybrid topology** is a combination of two or more basic topologies.

---

## 1.5 Network Devices — Hub, Switch, and Router

### 1.5.1 Hub

#### Definition
A **Hub** is a basic Layer 1 (Physical Layer) networking device that connects multiple devices in a network and broadcasts incoming data to **all ports** regardless of the intended destination.

#### Detailed Explanation
- A hub is a simple, unintelligent device — it does not examine or filter data.
- When a hub receives a data signal on one port, it **floods** (rebroadcasts) the signal to all other ports.
- All devices connected to a hub share the **same collision domain** and **same broadcast domain**.
- Types of Hubs:
  - **Passive Hub**: Simply connects devices; does not amplify or regenerate signals.
  - **Active Hub**: Amplifies and regenerates signals before forwarding (also called a **Repeater Hub** or **Multiport Repeater**).
  - **Intelligent Hub**: Includes some management features like network monitoring.

#### Key Points / Highlights
- Operates at **Layer 1 (Physical Layer)** of the OSI model.
- **Broadcasts** data to all connected devices — no filtering or intelligence.
- Creates a **single collision domain** for all connected devices.
- Leads to **network congestion** as traffic increases.
- Largely **obsolete** — replaced by switches in modern networks.

---

### 1.5.2 Switch

#### Definition
A **Switch** is a Layer 2 (Data Link Layer) networking device that connects multiple devices and uses **MAC addresses** to forward data only to the **specific destination port**, rather than broadcasting to all ports.

#### Detailed Explanation
- A switch is an **intelligent device** — it maintains a **MAC address table** (also called CAM table — Content Addressable Memory table).
- When a switch receives a frame, it reads the **destination MAC address** and forwards the frame only to the port associated with that MAC address.
- If the MAC address is not in the table, the switch **floods** the frame to all ports (except the source port) — this is called **unknown unicast flooding**.
- Each port on a switch is a **separate collision domain**, which significantly reduces collisions.
- All ports share the **same broadcast domain** (unless VLANs are configured).

#### Learning Process:
1. When a device sends a frame, the switch records the **source MAC address** and the **port** it came from in the MAC address table.
2. The switch looks up the **destination MAC address** in the table.
3. If found, it forwards the frame to the specific port. If not, it floods the frame.

#### Key Points / Highlights
- Operates at **Layer 2 (Data Link Layer)** of the OSI model.
- Uses **MAC addresses** for forwarding decisions.
- Creates a **separate collision domain** for each port.
- All ports are in the **same broadcast domain** (unless VLANs are used).
- Much more efficient than a hub — reduces unnecessary traffic and collisions.
- **Full-duplex** communication is supported (devices can send and receive simultaneously).

---

### 1.5.3 Router

#### Definition
A **Router** is a Layer 3 (Network Layer) networking device that forwards data packets between **different networks** based on **IP addresses**. It determines the best path for data to travel using routing tables and routing algorithms.

#### Detailed Explanation
- A router connects two or more **different networks** (e.g., a LAN to the Internet, or two different LANs).
- It reads the **destination IP address** from the packet header and looks up the **routing table** to determine the next hop or the best path.
- Each interface of a router is a **separate broadcast domain** and a **separate collision domain**.
- Routers perform **NAT (Network Address Translation)**, **DHCP**, **firewall** functions, and **packet filtering**.
- Routing can be:
  - **Static**: Routes are manually configured by the network administrator.
  - **Dynamic**: Routes are automatically learned using routing protocols (e.g., RIP, OSPF, BGP).

#### Key Points / Highlights
- Operates at **Layer 3 (Network Layer)** of the OSI model.
- Uses **IP addresses** for forwarding decisions.
- Separates **broadcast domains** — prevents broadcast storms from spreading.
- Connects **different networks** (inter-network communication).
- Uses **routing tables** and **routing algorithms** for path determination.
- More intelligent and expensive than hubs and switches.

---

### Comparison: Hub vs Switch vs Router

| Feature | Hub | Switch | Router |
|---------|-----|--------|--------|
| OSI Layer | Layer 1 (Physical) | Layer 2 (Data Link) | Layer 3 (Network) |
| Address Used | None | MAC Address | IP Address |
| Intelligence | Dumb/None | Moderate | High |
| Collision Domain | Single (shared) | Separate per port | Separate per port |
| Broadcast Domain | Single (shared) | Single (shared) | Separate per interface |
| Data Forwarding | Broadcasts to all | Forwards to specific port | Routes between networks |
| Speed | Slow | Fast | Moderate |
| Cost | Low | Medium | High |

### MCQ Focus Section
- A **Hub** operates at Layer 1; a **Switch** at Layer 2; a **Router** at Layer 3.
- A hub creates a **single collision domain**; a switch creates a **separate collision domain per port**.
- A **Router** separates broadcast domains; a hub and switch do not (without VLANs).
- A switch uses **MAC addresses**; a router uses **IP addresses**.
- **Unknown unicast flooding** occurs when a switch does not have the destination MAC in its table.
- A **Layer 3 Switch** (multilayer switch) can perform both switching (Layer 2) and routing (Layer 3) functions.
- **NAT** (Network Address Translation) is performed by a router.
- A **gateway** is a device that connects two networks using different protocols — a router often acts as a default gateway.
- A **bridge** is similar to a switch but typically has fewer ports — it operates at Layer 2.
- Do not confuse "collision domain" with "broadcast domain" — these are different concepts.

---

---

# UNIT 2: NETWORK MODELS

---

## 2.1 Protocol Layering

### Definition
**Protocol Layering** is the concept of organizing network communication into a hierarchical stack of layers, where each layer is responsible for a specific function and communicates with the layers directly above and below it using defined interfaces and with its peer layer on another machine using protocols.

### Detailed Explanation

#### Why Protocol Layering?
Networks are complex systems. Breaking the communication process into layers makes it:
- **Simpler to design**: Each layer focuses on one aspect of communication.
- **Easier to troubleshoot**: Problems can be isolated to a specific layer.
- **Modular**: One layer can be changed without affecting others.
- **Interoperable**: Different vendors can design products for the same layer as long as they follow the protocol.

#### Principles of Protocol Layering

**Principle 1: Bidirectional Communication**
- Each layer must be able to perform two opposite tasks — one in each direction.
- Example: The encryption layer must be able to both encrypt (at the sender) and decrypt (at the receiver).

**Principle 2: Identical Layer Objects**
- The objects under each layer on both sides (sender and receiver) must be identical.
- Example: If Layer 3 on the sender adds a header, Layer 3 on the receiver must be able to understand and remove that header.

#### Service Types
- **Connection-Oriented Service**: A connection is established before data transfer begins (like a phone call). Example: TCP.
- **Connectionless Service**: No connection is established; each packet is sent independently (like sending a letter). Example: UDP.

### Example
Think of sending a letter:
1. **Writing the letter** — Application Layer (content creation).
2. **Putting it in an envelope and writing the address** — Presentation/Transport Layer (formatting and addressing).
3. **Dropping it at the post office** — Network Layer (routing).
4. **Mail truck delivers it between post offices** — Data Link/Physical Layer (actual transfer).

### Key Points / Highlights
- Protocol layering simplifies complex network communication.
- Two key principles: **bidirectional capability** and **identical objects at peer layers**.
- Services can be **connection-oriented** (TCP) or **connectionless** (UDP).
- Each layer provides **services** to the layer above and uses services from the layer below.

### MCQ Focus Section
- Protocol layering is based on the principle of **divide and conquer**.
- **Connection-oriented** service requires a setup phase before communication (e.g., TCP 3-way handshake).
- **Connectionless** service sends data without establishing a connection (e.g., UDP).
- The key benefit of layering is **modularity** — layers can be modified independently.
- Each layer only communicates with **adjacent layers** (above and below) on the same machine, and with its **peer layer** on the remote machine.

---

## 2.2 OSI Model (Open Systems Interconnection)

### Definition
The **OSI (Open Systems Interconnection) Model** is a **conceptual reference model** developed by the **ISO (International Organization for Standardization)** in 1984. It divides network communication into **7 layers**, each responsible for a specific function, providing a universal framework for understanding and designing network architectures.

### Detailed Explanation

The 7 layers of the OSI model (from bottom to top) are:

#### Layer 1: Physical Layer
- **Function**: Deals with the physical transmission of raw **bits** (0s and 1s) over a communication medium.
- **Responsibilities**: Defines electrical signals, voltages, cable types, connectors, pin configurations, data rates, and physical topologies.
- **Devices**: Hub, Repeater, Cables, Modems.
- **PDU**: **Bits**.
- **Examples**: Ethernet cables (Cat5, Cat6), fiber optic cables, RS-232, USB.

#### Layer 2: Data Link Layer
- **Function**: Provides **node-to-node** (hop-to-hop) reliable data transfer and handles **framing**, **error detection/correction**, **flow control**, and **medium access control**.
- **Sub-layers**:
  - **LLC (Logical Link Control)**: Handles flow control and error detection.
  - **MAC (Media Access Control)**: Handles physical addressing (MAC addresses) and access to the shared medium.
- **Devices**: Switch, Bridge.
- **PDU**: **Frame**.
- **Protocols**: Ethernet (IEEE 802.3), Wi-Fi (IEEE 802.11), PPP, HDLC.

#### Layer 3: Network Layer
- **Function**: Responsible for **logical addressing** (IP addressing), **routing**, and **packet forwarding** from source to destination across multiple networks.
- **Responsibilities**: Path determination, logical addressing, fragmentation and reassembly of packets.
- **Devices**: Router, Layer 3 Switch.
- **PDU**: **Packet**.
- **Protocols**: IP (IPv4, IPv6), ICMP, ARP, RARP, IGMP.

#### Layer 4: Transport Layer
- **Function**: Provides **end-to-end** (process-to-process) communication, ensuring complete data transfer between applications.
- **Responsibilities**: Segmentation and reassembly, flow control, error control, connection management, multiplexing/demultiplexing using **port numbers**.
- **PDU**: **Segment** (TCP) / **Datagram** (UDP).
- **Protocols**: TCP (Transmission Control Protocol), UDP (User Datagram Protocol).

#### Layer 5: Session Layer
- **Function**: Establishes, manages, and terminates **sessions** (dialogues) between applications.
- **Responsibilities**: Session establishment, maintenance, synchronization, and termination. Dialog control (half-duplex or full-duplex).
- **Protocols**: NetBIOS, RPC (Remote Procedure Call), PPTP.

#### Layer 6: Presentation Layer
- **Function**: Handles **data translation**, **encryption/decryption**, and **compression/decompression**.
- **Responsibilities**: Converts data into a format that the application layer can understand. Ensures data from the sender can be read by the receiver's application.
- Also called the **Translation Layer**.
- **Protocols/Standards**: SSL/TLS (encryption), JPEG, MPEG, GIF (data formats), ASCII, EBCDIC, Unicode.

#### Layer 7: Application Layer
- **Function**: Provides the **interface** between the user/application and the network. This is the layer closest to the end-user.
- **Responsibilities**: Network virtual terminal, file access, email, directory services.
- **Protocols**: HTTP, HTTPS, FTP, SMTP, POP3, IMAP, DNS, Telnet, SSH, SNMP, DHCP.

### Mnemonic to Remember (Bottom to Top)
**"Please Do Not Throw Sausage Pizza Away"**
- Physical → Data Link → Network → Transport → Session → Presentation → Application

### Key Points / Highlights
| Layer | Name | PDU | Key Function | Key Device |
|-------|------|-----|--------------|------------|
| 7 | Application | Data/Message | User interface | — |
| 6 | Presentation | Data/Message | Translation, Encryption | — |
| 5 | Session | Data/Message | Session management | — |
| 4 | Transport | Segment/Datagram | End-to-end delivery | — |
| 3 | Network | Packet | Routing, Logical addressing | Router |
| 2 | Data Link | Frame | Framing, MAC addressing | Switch, Bridge |
| 1 | Physical | Bits | Bit transmission | Hub, Repeater |

### MCQ Focus Section
- The OSI Model has **7 layers**; developed by **ISO** in **1984**.
- OSI is a **reference model** (theoretical), not an implementation model.
- **Physical Layer** deals with bits; **Data Link Layer** deals with frames.
- **Transport Layer** is the first end-to-end layer (Layers 1-3 are hop-to-hop).
- **Session Layer** manages dialogues/sessions between applications.
- **Presentation Layer** handles encryption, compression, and data format translation.
- The **Data Link Layer** has two sub-layers: **LLC** and **MAC**.
- **ARP** (Address Resolution Protocol) maps IP address to MAC address — operates between Layer 2 and Layer 3.
- Layers 1-4 are called **Lower Layers** (transport-oriented); Layers 5-7 are called **Upper Layers** (application-oriented).
- **TCP** is connection-oriented and reliable; **UDP** is connectionless and unreliable.
- Remember: The OSI model is **not used in practice** — the TCP/IP model is used. OSI serves as a theoretical reference.

---

## 2.3 TCP/IP Protocol Suite

### Definition
The **TCP/IP (Transmission Control Protocol / Internet Protocol) Protocol Suite** is a **practical, implementation-based** networking model that defines how data is packaged, addressed, transmitted, routed, and received across the Internet. It has **4 layers** (or 5 in the updated version) and is the foundation of the modern Internet.

### Detailed Explanation

#### Layers of the TCP/IP Model

**1. Network Access Layer (Link Layer)** — [Combines OSI Layers 1 & 2]
- Handles the physical transmission of data on a specific network medium.
- Deals with hardware addressing (MAC), framing, and physical medium specifications.
- Protocols: Ethernet, Wi-Fi (802.11), ARP, PPP.

**2. Internet Layer** — [Equivalent to OSI Layer 3]
- Responsible for logical addressing (IP addressing), routing, and packet forwarding.
- Handles the movement of packets from source to destination across multiple networks.
- Key Protocol: **IP (Internet Protocol)** — both IPv4 and IPv6.
- Other Protocols: ICMP (Internet Control Message Protocol), IGMP, ARP (sometimes placed here).

**3. Transport Layer** — [Equivalent to OSI Layer 4]
- Provides end-to-end communication between applications.
- Two main protocols:
  - **TCP (Transmission Control Protocol)**: Connection-oriented, reliable, ordered delivery, flow control, error recovery. Used by HTTP, FTP, SMTP, etc.
  - **UDP (User Datagram Protocol)**: Connectionless, unreliable (best-effort), no flow control or error recovery. Used by DNS, DHCP, VoIP, video streaming.

**4. Application Layer** — [Combines OSI Layers 5, 6, & 7]
- Provides application-level services directly to the user.
- Handles session management, data representation, and application protocols.
- Protocols: HTTP, HTTPS, FTP, SMTP, DNS, Telnet, SSH, SNMP, DHCP, POP3, IMAP.

#### TCP/IP vs OSI Model

| Feature | OSI Model | TCP/IP Model |
|---------|-----------|-------------|
| Layers | 7 | 4 (or 5) |
| Developed by | ISO | DoD (Department of Defense) / DARPA |
| Nature | Theoretical/Reference | Practical/Implementation |
| Approach | Protocol-independent | Protocol-dependent |
| Session & Presentation | Separate layers | Merged into Application |
| Usage | Not used in practice | Used in real-world Internet |
| Reliability | Model first, protocols later | Protocols first, model later |

#### 5-Layer Model (Updated TCP/IP)
Some textbooks use a 5-layer model to provide better alignment with the OSI model:
1. Physical Layer
2. Data Link Layer
3. Network Layer
4. Transport Layer
5. Application Layer

### Example
When you open a webpage (e.g., www.google.com):
1. **Application Layer**: Browser sends an HTTP request.
2. **Transport Layer**: TCP breaks the request into segments, adds port numbers (port 80 for HTTP).
3. **Internet Layer**: IP adds source and destination IP addresses, creating packets.
4. **Network Access Layer**: Ethernet adds MAC addresses and converts data to frames, then to bits for physical transmission.

### Key Points / Highlights
- TCP/IP was developed by **DARPA** (Defense Advanced Research Projects Agency) for the **ARPANET**.
- TCP/IP is a **4-layer model** (Network Access, Internet, Transport, Application).
- TCP/IP is the **actual protocol suite used on the Internet**.
- OSI is a **reference model**; TCP/IP is an **implementation model**.
- TCP/IP was developed **before** the OSI model became a standard.
- The Internet Layer of TCP/IP corresponds to the Network Layer of OSI.

### MCQ Focus Section
- TCP/IP has **4 layers** (original) or **5 layers** (updated version).
- TCP/IP was developed by **DARPA/DoD**, not by ISO.
- The **Internet Layer** of TCP/IP corresponds to the **Network Layer** of OSI.
- **TCP** is reliable and connection-oriented; **UDP** is unreliable and connectionless.
- In TCP/IP, the **Application Layer** combines the functions of OSI's Session, Presentation, and Application layers.
- The **OSI model** came after TCP/IP but is used as a theoretical framework.
- TCP/IP is called a **protocol suite** because it includes a collection of protocols at each layer.
- **ARP** can be placed at either the Network Access Layer or the Internet Layer depending on the textbook.
- Key difference: OSI separates **service, interface, and protocol** clearly; TCP/IP does not.
- **HTTP** uses **TCP** at the Transport Layer; **DNS** can use both **TCP and UDP** (UDP for queries, TCP for zone transfers).


# UNIT 3: PHYSICAL LAYER — Signal & Media

---

## 3.1 Basics of Data Communications

### Definition
**Data Communication** is the process of exchanging data between two or more devices through a transmission medium. It involves a **sender**, a **receiver**, a **message**, a **transmission medium**, and a **protocol**.

### Detailed Explanation

#### Components of a Data Communication System
1. **Message**: The data or information to be communicated.
2. **Sender**: The device that sends the message.
3. **Receiver**: The device that receives the message.
4. **Transmission Medium**: The physical path through which the message travels.
5. **Protocol**: The set of rules governing the communication process.

#### Data Flow (Modes of Communication)

**1. Simplex** — Data flows in **only one direction**. Example: Keyboard to computer, TV broadcast.

**2. Half-Duplex** — Data flows in **both directions**, but **not simultaneously**. Example: Walkie-talkie.

**3. Full-Duplex** — Data flows in **both directions simultaneously**. Example: Telephone conversation.

### Key Points / Highlights
- 5 components: message, sender, receiver, medium, protocol.
- **Simplex** = one-way; **Half-Duplex** = two-way alternating; **Full-Duplex** = two-way simultaneous.

### MCQ Focus Section
- A **keyboard** is **simplex**; a **walkie-talkie** is **half-duplex**; a **telephone** is **full-duplex**.
- Full-duplex provides the **highest efficiency** in communication.
- In simplex mode, communication is **unidirectional**.

---

## 3.2 Analog and Digital Signals

### Definition
- **Analog Signal**: A continuous signal that varies smoothly over time, taking any value within a range.
- **Digital Signal**: A discrete signal representing data as distinct values (typically binary: 0 and 1).

### Detailed Explanation

#### Analog Signals
- Represented as **sine waves** characterized by **Amplitude**, **Frequency**, and **Phase**.
- **Amplitude**: Height/strength of the signal (volts).
- **Frequency**: Cycles per second (Hertz). Period = 1/Frequency.
- **Phase**: Position of waveform relative to time zero (degrees/radians).
- **Wavelength**: Distance traveled in one period = Propagation Speed / Frequency.

#### Digital Signals
- Represented as **square waves** with two levels: high (1) and low (0).
- Characterized by **bit rate** (bits per second — bps).
- **Bit interval** = 1/Bit Rate.
- More robust against noise than analog signals.

#### Bandwidth
- **Analog Bandwidth** = f_max − f_min (Hz).
- Digital signals theoretically have infinite bandwidth.

### Key Points / Highlights
- Analog = continuous; Digital = discrete.
- Digital signals are more **resistant to noise**.
- **Bandwidth** = range of frequencies in a signal.

### MCQ Focus Section
- Frequency is in **Hz**; Period = **1/f**.
- **Bit rate** is in **bps**. **Baud rate** = signal changes/second.
- Bit Rate = Baud Rate × bits per baud.
- A digital signal occupies **more bandwidth** than analog.
- **Fourier analysis** decomposes digital signals into sine waves.

---

## 3.3 Transmission Impairments

### Definition
**Transmission impairments** degrade signal quality during transmission. Three types: **Attenuation**, **Distortion**, and **Noise**.

### Detailed Explanation

**1. Attenuation** — Loss of signal strength over distance. Measured in **dB**. Fixed with amplifiers/repeaters.

**2. Distortion** — Change in signal shape because different frequencies travel at different speeds. Fixed with equalizers.

**3. Noise** — Unwanted signals mixed with the original:
- **Thermal Noise**: Random electron movement. Always present. Cannot be eliminated.
- **Induced Noise**: From external sources (motors, appliances).
- **Crosstalk**: Coupling between adjacent channels.
- **Impulse Noise**: Sudden irregular spikes (lightning, surges). Most harmful for digital data.

**Signal-to-Noise Ratio (SNR)**: Higher SNR = cleaner signal. Measured in dB.

### Key Points / Highlights
- Three impairments: **Attenuation, Distortion, Noise**.
- **Thermal noise** = white noise — affects all frequencies equally.
- **Impulse noise** is most harmful for digital transmission.

### MCQ Focus Section
- **Repeaters** restore digital signals; **Amplifiers** boost analog signals (but also amplify noise).
- **Crosstalk** = hearing another conversation on your phone line.
- High SNR = **high-quality** signal.

---

## 3.4 Performance

### Definition
Network performance is measured using **bandwidth**, **throughput**, **latency**, and **jitter**.

### Detailed Explanation

- **Bandwidth**: Maximum capacity of a link (bps).
- **Throughput**: Actual data rate achieved. Always ≤ Bandwidth.
- **Latency**: Total time from source to destination = Propagation + Transmission + Queuing + Processing delay.
- **Jitter**: Variation in delay between packets. Critical for real-time applications (VoIP, video).

### MCQ Focus Section
- **Throughput ≤ Bandwidth**.
- **Propagation delay** depends on distance and medium speed.
- **Transmission delay** depends on packet size and bandwidth.
- **Jitter** is problematic for real-time applications.

---

## 3.5 Data Rate

### Definition
**Data Rate** (bit rate) is the number of bits transmitted per second (bps).

### Detailed Explanation

- **Nyquist Theorem** (noiseless channel): Max Data Rate = 2 × Bandwidth × log₂(L), where L = signal levels.
- **Shannon's Theorem** (noisy channel): Capacity C = Bandwidth × log₂(1 + SNR). This is the absolute maximum — cannot be exceeded.

### MCQ Focus Section
- **Nyquist** = noiseless; **Shannon** = noisy.
- Shannon gives the **theoretical upper limit** independent of encoding.
- If L = 2, Nyquist gives Max Rate = **2 × Bandwidth**.
- Increasing signal levels (L) increases data rate but also error probability.

---

## 3.6 Transmission Media

### Definition
**Transmission media** are physical pathways for data: **Guided (Wired)** and **Unguided (Wireless)**.

### Detailed Explanation

### Guided Media

**1. Twisted Pair Cable**
- Two insulated copper wires twisted together to reduce EMI and crosstalk.
- **UTP** (Unshielded): Cheaper, used in LANs. Categories: Cat3, Cat5, Cat5e, Cat6, Cat6a, Cat7.
- **STP** (Shielded): Better noise protection, more expensive.

**2. Coaxial Cable**
- Central conductor + insulating layer + metallic shield + outer jacket.
- Better shielding than twisted pair. Uses **BNC connector**.
- Types: Baseband (digital) and Broadband (analog/cable TV).

**3. Fiber Optic Cable**
- Uses **light pulses** through glass/plastic fiber. Uses **Total Internal Reflection**.
- **Single-Mode (SMF)**: Thin core, laser, long distance (100 km), higher bandwidth.
- **Multi-Mode (MMF)**: Thicker core, LED, shorter distance (2 km), lower bandwidth.
- **Advantages**: Highest bandwidth, immune to EMI, very low attenuation, secure.

### Unguided Media

**1. Radio Waves** (3 kHz–1 GHz): Omnidirectional, penetrates walls. Used for Wi-Fi, Bluetooth, radio.

**2. Microwaves** (1 GHz–300 GHz): Unidirectional, line-of-sight. Terrestrial (towers) and Satellite.

**3. Infrared** (300 GHz–400 THz): Short-range, line-of-sight, cannot penetrate walls. Used for TV remotes.

### Key Points / Highlights
| Medium | Bandwidth | Interference Immunity | Cost |
|--------|-----------|----------------------|------|
| UTP | Low-Medium | Low | Low |
| Coaxial | Medium-High | Medium | Medium |
| Fiber Optic | Very High | Very High | High |
| Radio Waves | Medium | Low | Low |
| Microwaves | High | Medium | High |

### MCQ Focus Section
- **Fiber optic** = highest bandwidth, immune to EMI.
- **Twisted pair** cables are twisted to reduce **crosstalk**.
- **Single-mode** fiber supports longer distances than **multi-mode**.
- **Radio waves** = omnidirectional; **Microwaves** = unidirectional, line-of-sight.
- **Infrared** cannot penetrate walls.

---

## 3.7 Cabling Standards

### Definition
Standards ensuring consistency and compatibility of network cabling. Main standard: **TIA/EIA-568**.

### Detailed Explanation

- **T568A** and **T568B**: Two wiring schemes for RJ-45 connectors.
- **Straight-Through Cable**: Both ends same scheme. Connects **different** devices (PC to Switch).
- **Crossover Cable**: Different scheme each end (T568A–T568B). Connects **similar** devices (PC to PC).
- **Rollover Cable**: Reversed wiring. For console/CLI access to routers/switches.
- **Auto-MDI/MDIX**: Modern devices auto-detect cable type.

#### UTP Categories
| Category | Max Speed | Usage |
|----------|-----------|-------|
| Cat5 | 100 Mbps | Fast Ethernet |
| Cat5e | 1 Gbps | Gigabit Ethernet |
| Cat6 | 10 Gbps (short) | 10G Ethernet |

### MCQ Focus Section
- **Straight-through** = different devices; **Crossover** = similar devices.
- **Cat5e** supports up to **1 Gbps**. Max segment = **100 meters**.
- **RJ-45** is the standard connector for UTP Ethernet cables.

---

---

# UNIT 4: PHYSICAL LAYER — Modulation & Multiplexing

---

## 4.1 Digital-to-Digital Conversion (Line Coding)

### Definition
**Line Coding** converts digital data (0s and 1s) into digital signals (voltage pulses) for transmission.

### Detailed Explanation

**1. Unipolar NRZ**: One voltage level + zero. Simple but has DC component and sync problems.

**2. Polar Encoding**:
- **NRZ-L**: Voltage level determines bit value.
- **NRZ-I**: Transition at start = 1; no transition = 0. Better sync for runs of 1s.
- **RZ**: Three voltage levels; returns to zero mid-bit. Self-synchronizing but needs more bandwidth.
- **Manchester**: Transition in middle of every bit for both clock and data. Low-to-high = 0; high-to-low = 1 (IEEE). Used in **Ethernet (802.3)**. Requires **2× bandwidth** of NRZ.
- **Differential Manchester**: Transition in middle always (for clock). Transition at beginning = 0; no transition at beginning = 1. Used in **Token Ring (802.5)**.

**3. Bipolar (AMI)**: Three levels (+V, 0, -V). 0 = zero voltage; 1 = alternating +V/-V. No DC component. Built-in error detection.

### MCQ Focus Section
- **Manchester** = Ethernet (802.3); **Differential Manchester** = Token Ring (802.5).
- Manchester needs **2× bandwidth** of NRZ.
- In **NRZ-I**, transition at start = **1**.
- **AMI**: 1s alternate between +V and -V.

---

## 4.2 Analog-to-Digital Conversion

### Definition
Converting analog signals to digital data. Primary technique: **PCM (Pulse Code Modulation)**.

### Detailed Explanation

**PCM Steps**:
1. **Sampling**: Measure signal at regular intervals. **Nyquist**: Sample rate ≥ 2 × f_max.
2. **Quantization**: Round each sample to nearest discrete level. Difference = quantization error.
3. **Encoding**: Convert each quantized value to binary. L levels → log₂(L) bits/sample.

**Telephone PCM**: 4 kHz signal → 8000 samples/sec × 8 bits = **64 Kbps**.

**Delta Modulation**: Encodes change between consecutive samples. Only **1 bit/sample**. Simpler but less accurate. Suffers **slope overload** for rapidly changing signals.

### MCQ Focus Section
- Nyquist sampling rate = **2 × f_max**.
- Standard telephone PCM = **64 Kbps**.
- PCM stages: **Sampling → Quantization → Encoding** (in order).
- **Delta Modulation** uses **1 bit per sample**.
- Increase quantization levels → reduce quantization error.

---

## 4.3 Analog-to-Analog Conversion

### Definition
Modifying a carrier signal's characteristic based on the modulating (information) signal to shift it to a different frequency band.

### Detailed Explanation

- **AM (Amplitude Modulation)**: Carrier amplitude varies. Bandwidth = 2 × signal bandwidth. Most susceptible to noise.
- **FM (Frequency Modulation)**: Carrier frequency varies. More noise-resistant than AM. Requires more bandwidth.
- **PM (Phase Modulation)**: Carrier phase varies. Similar to FM in noise resistance.

### MCQ Focus Section
- **FM** is more noise-resistant than AM because noise affects amplitude, not frequency.
- AM bandwidth = **2 × modulating signal bandwidth**.
- FM requires **more bandwidth** than AM.

---

## 4.4 Digital-to-Analog Conversion

### Definition
Converting digital data into analog signals using keying techniques.

### Detailed Explanation

- **ASK (Amplitude Shift Keying)**: Amplitude changes for 0/1. Simple but most noise-susceptible.
- **FSK (Frequency Shift Keying)**: Frequency changes for 0/1. Less noise-susceptible than ASK.
- **PSK (Phase Shift Keying)**: Phase changes for 0/1.
  - **BPSK**: 2 phases → 1 bit/symbol.
  - **QPSK**: 4 phases → 2 bits/symbol (dibit).
- **QAM (Quadrature Amplitude Modulation)**: Combines ASK + PSK. **16-QAM** = 4 bits/symbol; **64-QAM** = 6 bits/symbol. Used in Wi-Fi, DSL, 4G/5G.

### MCQ Focus Section
- **ASK** is most noise-susceptible.
- **QPSK**: 4 phases → **2 bits per symbol** (dibit).
- **QAM** = ASK + PSK combined.
- Bits per symbol = **log₂(number of signal elements)**.

---

## 4.5 Multiplexing

### Definition
Combining multiple signals into one channel for simultaneous transmission. Uses **MUX** (sender) and **DEMUX** (receiver).

### Detailed Explanation

**1. FDM (Frequency Division Multiplexing)**: For analog signals. Divides bandwidth into non-overlapping frequency bands. Uses **guard bands** between channels. Example: FM radio, Cable TV.

**2. WDM (Wavelength Division Multiplexing)**: FDM for **fiber optic**. Different wavelengths (colors) of light. **DWDM** can carry 160+ channels.

**3. TDM (Time Division Multiplexing)**: For digital signals. Divides time into slots.
- **Synchronous TDM**: Fixed slots per source — wastes empty slots.
- **Statistical (Asynchronous) TDM**: Dynamic allocation — no wasted slots. More efficient.

**4. CDM/CDMA (Code Division Multiplexing)**: Each sender gets a unique code. All transmit simultaneously on same frequency. Receiver uses the code to extract correct signal. Used in **3G cellular, GPS**.

### Key Points / Highlights
| Technique | Signal Type | Divides By | Example |
|-----------|-------------|------------|---------|
| FDM | Analog | Frequency | FM Radio |
| WDM | Optical | Wavelength | Fiber Optic |
| TDM | Digital | Time | Telephone lines |
| CDM | Digital | Code | 3G, GPS |

### MCQ Focus Section
- **FDM** uses **guard bands**; for **analog** signals.
- **TDM** for **digital** signals. Statistical TDM is more efficient than Synchronous.
- **WDM** = FDM for fiber optic.
- **CDMA**: all users transmit on **same frequency** with unique codes.
- **MUX** combines; **DEMUX** separates.

---

---

# UNIT 5: DATA LINK LAYER

---

## 5.1 Data Link Layer Design Issues

### Definition
The **Data Link Layer** (Layer 2 of OSI) is responsible for **node-to-node** (hop-to-hop) delivery of data. It takes packets from the Network Layer, encapsulates them into **frames**, and ensures reliable transfer between two directly connected nodes.

### Detailed Explanation

#### Key Functions of the Data Link Layer

**1. Framing**
- Divides the stream of bits from the Physical Layer into manageable units called **frames**.
- Methods of framing:
  - **Character Count**: A field in the header specifies the number of characters in the frame. Problem: if the count is corrupted, synchronization is lost.
  - **Flag Bytes with Byte Stuffing**: Special flag bytes mark the start and end of a frame. If the flag pattern appears in the data, a special escape byte is inserted before it (**byte stuffing**).
  - **Flag Bits with Bit Stuffing**: A special bit pattern (e.g., 01111110) marks frame boundaries. If five consecutive 1s appear in the data, a 0 is automatically inserted after them (**bit stuffing**). The receiver removes the stuffed 0s.

**2. Error Control**
- Detects and possibly corrects errors introduced during transmission.
- Error detection techniques: Parity, Checksum, CRC (detailed in 5.3).
- Error correction: Hamming Code, retransmission (ARQ).

**3. Flow Control**
- Ensures the sender does not overwhelm the receiver by sending data faster than it can process.
- Techniques:
  - **Stop-and-Wait**: Sender sends one frame and waits for ACK before sending the next.
  - **Sliding Window**: Sender can send multiple frames before needing an ACK, within a window size.

**4. Access Control**
- Determines which device has control of the link when multiple devices share the same medium.
- Handled by the **MAC sublayer** (covered in Unit 6).

### Key Points / Highlights
- DLL provides **hop-to-hop** delivery (not end-to-end).
- Three main functions: **Framing, Error Control, Flow Control**.
- DLL has two sub-layers: **LLC** (Logical Link Control) and **MAC** (Media Access Control).
- The PDU at the DLL is a **Frame**.

### MCQ Focus Section
- **Bit stuffing**: Insert a 0 after five consecutive 1s in the data.
- **Byte stuffing**: Insert an escape byte before a flag byte that appears in data.
- **Stop-and-Wait** sends one frame at a time; **Sliding Window** sends multiple.
- DLL provides **hop-to-hop** delivery; Transport Layer provides **end-to-end**.
- The DLL adds both a **header and a trailer** to the packet.

---

## 5.2 Elementary Data Link Protocols

### Definition
Elementary data link protocols are basic protocols that define how frames are transmitted between two directly connected nodes with varying levels of error control, flow control, and efficiency.

### Detailed Explanation

#### 1. Unrestricted Simplex Protocol (Utopia)
- Assumes a **perfect, error-free** channel with **infinite buffer** at the receiver.
- Sender sends frames continuously without waiting for any acknowledgment.
- **Not realistic** — used only as a theoretical starting point.

#### 2. Stop-and-Wait Protocol (Simplex Stop-and-Wait)
- Sender sends **one frame** and then waits for an **acknowledgment (ACK)** from the receiver.
- Only after receiving ACK does the sender send the next frame.
- Solves the **flow control** problem but is **very slow** (low utilization of the channel).
- **Problem**: If a frame or ACK is lost, the sender waits forever → **timeout** mechanism is added.

#### 3. Stop-and-Wait ARQ (Automatic Repeat Request)
- Adds **error control** to Stop-and-Wait.
- If a frame is corrupted or lost, the receiver does not send an ACK, and the sender **retransmits** after a timeout.
- Uses **sequence numbers** (0 and 1) to handle duplicate frames caused by retransmissions.
- Issues: Low efficiency because the channel is idle while waiting for ACK.

#### 4. Sliding Window Protocols
- Allow the sender to send **multiple frames** before needing an acknowledgment.
- The sender maintains a **send window** and the receiver maintains a **receive window**.
- Types:
  - **Go-Back-N ARQ**: Sender window size = N; Receiver window size = 1. If an error is detected, the receiver discards all subsequent frames and the sender retransmits from the error frame onward. Less efficient but simpler.
  - **Selective Repeat ARQ**: Sender window size = N; Receiver window size = N. Only the erroneous frame is retransmitted. More efficient but more complex (requires buffer at receiver).

#### Go-Back-N vs Selective Repeat
| Feature | Go-Back-N | Selective Repeat |
|---------|-----------|-----------------|
| Sender Window | N | N |
| Receiver Window | 1 | N |
| Retransmission | All frames from error onward | Only the error frame |
| Efficiency | Lower | Higher |
| Receiver Complexity | Simple | Complex (needs buffering) |
| Max Window Size | 2ⁿ - 1 | 2ⁿ⁻¹ |

### Key Points / Highlights
- **Stop-and-Wait** = sends one frame, waits for ACK. Simple but inefficient.
- **Go-Back-N** = retransmits all frames from the point of error.
- **Selective Repeat** = retransmits only the erroneous frame.
- Sliding Window protocols improve channel utilization significantly.

### MCQ Focus Section
- In **Go-Back-N**, receiver window size = **1**.
- In **Selective Repeat**, receiver window size = **N**.
- Max window size for Go-Back-N with n-bit sequence number = **2ⁿ - 1**.
- Max window size for Selective Repeat = **2ⁿ⁻¹** (half of the sequence number space).
- **Stop-and-Wait** is a special case of Sliding Window with window size = **1**.
- **ARQ** stands for **Automatic Repeat Request**.
- Sequence numbers in Stop-and-Wait ARQ alternate between **0 and 1**.
- **Go-Back-N** wastes bandwidth by retransmitting frames that were received correctly.
- **Selective Repeat** requires more buffer space at the receiver.
- **Piggybacking**: Attaching acknowledgment to an outgoing data frame to improve efficiency.

---

## 5.3 Error Detection and Correction

### Definition
**Error detection** identifies whether errors have occurred during transmission. **Error correction** not only detects but also identifies and fixes the errors without retransmission. Errors can be **single-bit errors** (one bit changed) or **burst errors** (multiple consecutive bits changed).

### Detailed Explanation

### 5.3.1 Parity Check

**Simple (Single) Parity Check**
- Adds one extra bit (parity bit) to the data to make the total number of 1s either **even** (even parity) or **odd** (odd parity).
- **Even Parity**: Total number of 1s (including parity bit) = even.
- **Odd Parity**: Total number of 1s = odd.
- Can detect **single-bit errors** and **odd number of bit errors**.
- **Cannot detect even number of bit errors** (e.g., 2-bit errors).
- Cannot correct errors — only detects them.

**Two-Dimensional Parity Check**
- Data is organized into a matrix (rows and columns).
- Parity bits are calculated for each row and each column.
- Can detect **single-bit, double-bit, and some burst errors**.
- Can also **correct single-bit errors** by identifying the row and column of the error.

### 5.3.2 Checksum

- The data is divided into **fixed-size segments** (e.g., 16-bit words).
- All segments are **added together** using one's complement arithmetic.
- The **one's complement** of the final sum is the **checksum**.
- The sender sends the data + checksum.
- The receiver adds all segments including the checksum. If the result is **all 1s**, no error. If any bit is 0, an error is detected.
- Used in **TCP, UDP, and IP** headers.
- **Limitation**: Cannot detect all errors (e.g., if two segments have equal and opposite errors, they cancel out).

### 5.3.3 CRC (Cyclic Redundancy Check)

- The most powerful and widely used error detection method at the Data Link Layer.
- Based on **polynomial division** (binary division using XOR).
- **How CRC works**:
  1. A **generator polynomial** (divisor) is agreed upon by sender and receiver (e.g., CRC-32, CRC-16).
  2. Sender appends (degree of generator − 1) zeros to the data.
  3. Performs binary division (XOR) of the data by the generator polynomial.
  4. The **remainder** is the CRC (also called FCS — Frame Check Sequence).
  5. Sender replaces the appended zeros with the CRC and sends the frame.
  6. Receiver divides the received frame by the same generator polynomial. If remainder = 0, no error.
- CRC can detect:
  - All **single-bit** errors.
  - All **double-bit** errors (if generator has certain properties).
  - All **odd number of bit** errors (if generator contains factor x+1).
  - All **burst errors** shorter than the degree of the generator polynomial.
- **Standards**: CRC-8, CRC-16, CRC-32 (used in Ethernet, Wi-Fi), CRC-CCITT.

### 5.3.4 Hamming Code (Error Correction)

- An **error-correcting code** that can detect and correct **single-bit errors** and detect (but not correct) **double-bit errors**.
- **How Hamming Code works**:
  1. Parity bits are placed at positions that are powers of 2 (positions 1, 2, 4, 8, 16, ...).
  2. Each parity bit covers a specific set of data bit positions.
  3. Parity bit at position 2ⁱ checks all positions whose binary representation has a 1 in the i-th bit.
  4. At the receiver, parity checks are performed for each parity bit position.
  5. The positions of failed checks form a binary number called the **syndrome**.
  6. If the syndrome = 0, no error. If the syndrome ≠ 0, it points to the position of the erroneous bit.
- **Number of parity bits (r)** required for d data bits: 2ʳ ≥ d + r + 1.
- **Hamming Distance**: The number of bit positions in which two codewords differ. To detect d errors, minimum Hamming distance = d + 1. To correct d errors, minimum Hamming distance = 2d + 1.

### Key Points / Highlights
| Method | Detects | Corrects | Used In |
|--------|---------|----------|---------|
| Parity (Simple) | Single-bit errors | No | Basic checks |
| Parity (2D) | Single, double-bit | Single-bit | — |
| Checksum | Many errors | No | TCP, UDP, IP |
| CRC | Single, double, burst | No (detection only) | Ethernet, Wi-Fi |
| Hamming Code | Single & double-bit | Single-bit | Memory (ECC RAM) |

### MCQ Focus Section
- **CRC** is the most widely used error detection method at the DLL.
- **Hamming Code** can **correct single-bit** errors and **detect double-bit** errors.
- Simple parity **cannot detect even number of bit errors**.
- In CRC, if the remainder is **0**, no error is detected.
- **Hamming distance** to detect d errors = **d + 1**; to correct d errors = **2d + 1**.
- Parity bits in Hamming Code are at positions **1, 2, 4, 8, 16, ...** (powers of 2).
- **Checksum** uses **one's complement addition**.
- CRC uses **XOR-based binary division** (not regular division).
- **FCS** (Frame Check Sequence) is another name for the CRC value appended to the frame.
- CRC-32 is used in **Ethernet** and **Wi-Fi** (produces 32-bit CRC).

---

## 5.4 Switch Working

### Definition
A **network switch** is a Layer 2 device that forwards frames based on **MAC addresses**, using a **MAC address table** to efficiently direct traffic to the correct port.

### Detailed Explanation

#### How a Switch Works

**1. Learning**
- When a frame arrives on a port, the switch reads the **source MAC address** and records it in the **MAC address table** along with the **port number**.
- This process is automatic — the switch builds its MAC table dynamically.

**2. Forwarding**
- The switch reads the **destination MAC address** from the frame.
- It looks up the destination MAC in the MAC address table.
- If found → forwards the frame to the **specific port** only.
- If **not found** → performs **flooding** (sends frame out of all ports except the source port).

**3. Filtering**
- If the source and destination are on the **same port**, the switch does not forward the frame — this is called **filtering**.

**4. Aging**
- Entries in the MAC address table have a **timer**. If no frames are received from a MAC address within the timeout period, the entry is **removed**.
- This ensures the table stays current and doesn't fill up with stale entries.

#### Switch Forwarding Methods

**1. Store-and-Forward**: Receives the **entire frame**, checks CRC for errors, then forwards. Most reliable but has higher latency.

**2. Cut-Through**: Reads only the **destination MAC address** (first 6 bytes of the destination) and immediately forwards. Fastest but does not check for errors.

**3. Fragment-Free**: Reads the first **64 bytes** of the frame before forwarding. Filters out most collision-related errors (runt frames). Compromise between store-and-forward and cut-through.

### Key Points / Highlights
- Switch operations: **Learning, Forwarding, Filtering, Aging**.
- Three forwarding methods: **Store-and-Forward, Cut-Through, Fragment-Free**.
- Each switch port is a **separate collision domain**.
- All switch ports (by default) are in the **same broadcast domain**.

### MCQ Focus Section
- **Store-and-Forward** checks CRC; **Cut-Through** does not.
- **Fragment-Free** reads first **64 bytes** before forwarding.
- **Flooding** occurs when the destination MAC is not in the MAC table.
- **Filtering** occurs when source and destination are on the same port.
- Switch creates a **separate collision domain per port**.
- A switch uses **MAC addresses** (Layer 2); a router uses **IP addresses** (Layer 3).
- **MAC table aging** removes stale entries after a timeout period.
- A **managed switch** supports VLANs, SNMP, and other advanced features.

---

---

# UNIT 6: MAC SUBLAYER

---

## 6.1 Multiple Access Protocols

### Definition
**Multiple Access Protocols** are rules that govern how multiple devices share and access a **shared communication medium** (common channel) to avoid collisions and ensure fair access.

### Detailed Explanation

Multiple access protocols are needed when multiple stations share a single broadcast channel. They are categorized into three types: **Random Access**, **Controlled Access**, and **Channelization**.

---

## 6.2 ALOHA

### Definition
**ALOHA** is one of the earliest random access protocols, developed at the University of Hawaii. It allows stations to transmit whenever they have data, with a mechanism to handle collisions.

### Detailed Explanation

#### Pure ALOHA
- A station transmits a frame **whenever it has data** to send.
- After transmission, it waits for an **acknowledgment (ACK)**.
- If no ACK is received (collision occurred), the station waits a **random time** and retransmits.
- **Vulnerable time** = **2 × Tₓ** (frame transmission time), because a collision can occur if another station transmits within one frame time before or after.
- **Maximum throughput** = **18.4%** (at G = 0.5, where G = average frames per frame time). Throughput formula: S = G × e^(−2G).

#### Slotted ALOHA
- Time is divided into **equal-sized slots** (each slot = one frame transmission time).
- Stations can only begin transmitting at the **start of a time slot**.
- Reduces the vulnerable time to **1 × Tₓ** (half of Pure ALOHA).
- **Maximum throughput** = **36.8%** (at G = 1). Throughput formula: S = G × e^(−G).
- **Doubles** the efficiency of Pure ALOHA.

### Key Points / Highlights
- **Pure ALOHA**: Transmit anytime. Vulnerable time = 2T. Max throughput = 18.4%.
- **Slotted ALOHA**: Transmit at slot boundaries. Vulnerable time = T. Max throughput = 36.8%.
- Slotted ALOHA is **twice** as efficient as Pure ALOHA.

### MCQ Focus Section
- Pure ALOHA max throughput = **18.4%**; Slotted ALOHA = **36.8%**.
- Vulnerable time: Pure = **2T**; Slotted = **T**.
- Pure ALOHA stations can transmit at **any time**; Slotted ALOHA at **slot boundaries only**.
- ALOHA was developed at the **University of Hawaii**.
- **G = 0.5** gives maximum throughput for Pure ALOHA; **G = 1** for Slotted ALOHA.

---

## 6.3 CSMA (Carrier Sense Multiple Access)

### Definition
**CSMA** is an improvement over ALOHA where stations **sense the channel** (listen before transmitting) to reduce collisions. "Carrier Sense" means each station checks whether the channel is idle or busy before transmitting.

### Detailed Explanation

#### Types of CSMA

**1. 1-Persistent CSMA**
- If channel is **idle** → transmit immediately with probability **1**.
- If channel is **busy** → keep listening until idle, then transmit immediately.
- **Problem**: If two stations are waiting and the channel becomes idle, both transmit simultaneously → collision.
- Greedy approach — highest collision probability but lowest delay when traffic is light.

**2. Non-Persistent CSMA**
- If channel is **idle** → transmit immediately.
- If channel is **busy** → wait a **random time**, then sense again.
- Reduces collisions (less greedy) but increases delay.
- Better throughput than 1-Persistent under heavy traffic.

**3. P-Persistent CSMA**
- Used with slotted channels.
- If channel is **idle** → transmit with probability **p**; wait for next slot with probability **(1-p)**.
- If channel is **busy** → wait for next slot and repeat the process.
- Balances between 1-Persistent and Non-Persistent.
- When p = 1, it becomes 1-Persistent.

### Key Points / Highlights
- CSMA = "listen before talk" — reduces collisions compared to ALOHA.
- **1-Persistent**: Most aggressive. Transmit immediately when idle.
- **Non-Persistent**: Most conservative. Random wait when busy.
- **P-Persistent**: Probabilistic approach. Compromise between the two.

### MCQ Focus Section
- CSMA stands for **Carrier Sense Multiple Access**.
- **1-Persistent** has the **highest collision rate** under heavy load.
- **Non-Persistent** has the **lowest collision rate** but higher delay.
- **P-Persistent** transmits with **probability p** when channel is idle.
- All CSMA protocols **sense the channel** before transmitting — unlike ALOHA.
- CSMA still has collisions due to **propagation delay** (station may sense idle but a frame is already on the way).

---

## 6.4 CSMA/CD (Carrier Sense Multiple Access with Collision Detection)

### Definition
**CSMA/CD** extends CSMA by adding **collision detection** — a station continues to listen while transmitting, and if it detects a collision, it **stops transmission immediately**, sends a **jam signal**, and waits a random time before retrying.

### Detailed Explanation

#### How CSMA/CD Works
1. Station senses the channel. If idle → start transmitting.
2. **While transmitting**, the station continues to listen (monitors the channel).
3. If a **collision is detected** during transmission:
   a. Stop transmitting immediately.
   b. Send a **jam signal** (48 bits) to notify all stations of the collision.
   c. Wait a random time determined by the **Binary Exponential Backoff** algorithm.
   d. Retry from step 1.

#### Binary Exponential Backoff
- After the n-th collision, the station randomly picks a wait time from {0, 1, 2, ..., 2ⁿ − 1} × slot time.
- After 10 collisions, the range freezes at 2¹⁰ − 1 = 1023 slots.
- After 16 collisions, the station gives up and reports an error.
- This algorithm adapts the wait time to the level of congestion.

#### Minimum Frame Size
- For collision detection to work, the frame must be long enough for the sender to still be transmitting when the collision signal arrives back.
- Minimum frame size = 2 × propagation delay × data rate.
- In Ethernet: minimum frame size = **64 bytes** (512 bits).

### Key Points / Highlights
- CSMA/CD = **sense, transmit, detect, abort, backoff, retry**.
- Used in **wired Ethernet** (IEEE 802.3).
- **Not used in wireless** (Wi-Fi uses CSMA/CA instead — collision avoidance).
- Minimum Ethernet frame = **64 bytes**.

### MCQ Focus Section
- CSMA/CD is used in **Ethernet (IEEE 802.3)**.
- **Jam signal** = 48 bits sent to notify all stations of a collision.
- In Binary Exponential Backoff, after n-th collision, wait range = **{0 to 2ⁿ - 1}** slot times.
- After **16 collisions**, the station gives up.
- **Minimum Ethernet frame size** = **64 bytes**. Frames shorter than this are called **runt frames**.
- CSMA/CD **cannot** be used in wireless because a station cannot send and listen simultaneously on the same frequency.
- Wi-Fi uses **CSMA/CA** (Collision Avoidance) instead of CSMA/CD.
- **Collision domain** = the area where collisions can occur. A hub creates one; a switch separates them.

---

## 6.5 Random Access

### Definition
In **Random Access** protocols, no station has priority or predetermined control over others. Any station can attempt to transmit at any time, and collisions are resolved through specific mechanisms.

### Detailed Explanation
- In random access, **no central controller** decides which station can transmit.
- Each station independently decides when to transmit.
- Collisions are possible and expected — they are handled through **backoff algorithms** and **retransmission**.
- Examples: **ALOHA, Slotted ALOHA, CSMA, CSMA/CD, CSMA/CA**.
- Random access works well under **low to moderate traffic**. Under heavy traffic, too many collisions degrade performance.

### MCQ Focus Section
- Random access = **no centralized control**.
- Collisions are resolved through **backoff and retransmission**.
- ALOHA, CSMA, and CSMA/CD are all **random access** protocols.
- Best suited for **bursty, low-to-moderate traffic**.

---

## 6.6 Controlled Access

### Definition
In **Controlled Access** protocols, stations must receive **permission** before transmitting. A control mechanism ensures only one station transmits at a time, eliminating collisions.

### Detailed Explanation

#### 1. Reservation
- Time is divided into intervals. In each interval, there is a **reservation period** followed by a **data transmission period**.
- Stations that want to transmit **reserve a slot** during the reservation period.
- After all reservations are made, stations transmit in the **reserved order**.
- No collisions during data transmission.

#### 2. Polling
- A **primary (controller) station** controls access by **polling** each secondary station in turn.
- The controller asks each station: "Do you have data to send?"
- If yes, the station transmits. If no, the controller moves to the next station.
- Two types:
  - **Roll-Call Polling**: Controller polls each station in sequence.
  - **Hub Polling**: Stations pass the poll to the next station in a decentralized manner.
- **Disadvantage**: Polling overhead. If the controller fails, the entire network stops.

#### 3. Token Passing
- A special control frame called a **token** circulates among stations in a logical ring.
- A station can transmit **only when it possesses the token**.
- After transmission (or if it has no data), the station passes the token to the next station.
- **No collisions** because only the token holder can transmit.
- Used in **Token Ring (IEEE 802.5)** and **FDDI**.
- **Problem**: If the token is lost or a station fails, recovery mechanisms are needed.

### Key Points / Highlights
- Controlled access = **no collisions** (unlike random access).
- Three methods: **Reservation, Polling, Token Passing**.
- Token passing is used in **Token Ring** and **FDDI**.

### MCQ Focus Section
- **Token Passing**: Only the station holding the token can transmit.
- **Polling** requires a **central controller (primary station)**.
- If the **token is lost** in Token Passing, a recovery mechanism generates a new token.
- **Token Ring** uses **IEEE 802.5**.
- **FDDI** (Fiber Distributed Data Interface) uses token passing on a dual-ring fiber optic network.
- Controlled access protocols have **zero collisions** but have **overhead** (token management, polling).
- **Polling** has single point of failure at the controller.

---

## 6.7 Ethernet Protocol

### Definition
**Ethernet** is the most widely used **LAN technology**, standardized as **IEEE 802.3**. It uses **CSMA/CD** for media access control and operates at the Data Link and Physical layers.

### Detailed Explanation

#### Ethernet Frame Format (IEEE 802.3)
| Field | Size | Description |
|-------|------|-------------|
| Preamble | 7 bytes | Alternating 1s and 0s for synchronization |
| SFD (Start Frame Delimiter) | 1 byte | 10101011 — marks the start of the frame |
| Destination MAC | 6 bytes | MAC address of the receiver |
| Source MAC | 6 bytes | MAC address of the sender |
| Type/Length | 2 bytes | Type of protocol (Ethernet II) or length of data |
| Data + Padding | 46-1500 bytes | Actual data; padded if less than 46 bytes |
| FCS (Frame Check Sequence) | 4 bytes | CRC-32 for error detection |

#### Key Ethernet Specifications
- **Minimum frame size**: 64 bytes (excluding preamble and SFD).
- **Maximum frame size**: 1518 bytes (excluding preamble and SFD).
- **Minimum data size**: 46 bytes (padded if less).
- **Maximum data size**: 1500 bytes (= MTU, Maximum Transmission Unit).

#### Ethernet Standards
| Standard | Speed | Cable | Distance |
|----------|-------|-------|----------|
| 10BASE-T | 10 Mbps | UTP Cat3 | 100 m |
| 100BASE-TX | 100 Mbps | UTP Cat5 | 100 m |
| 1000BASE-T | 1 Gbps | UTP Cat5e/6 | 100 m |
| 10GBASE-T | 10 Gbps | UTP Cat6a | 100 m |
| 1000BASE-SX | 1 Gbps | Multi-mode fiber | 550 m |
| 1000BASE-LX | 1 Gbps | Single-mode fiber | 5 km |

#### MAC Address
- **48 bits (6 bytes)** long, written as 6 pairs of hexadecimal digits (e.g., AA:BB:CC:DD:EE:FF).
- First 3 bytes = **OUI** (Organizationally Unique Identifier) — identifies the manufacturer.
- Last 3 bytes = **Device Identifier** — unique to the device.
- **Burned into** the NIC (Network Interface Card) by the manufacturer — also called **physical address** or **hardware address**.
- **Broadcast MAC**: FF:FF:FF:FF:FF:FF — sends to all devices on the LAN.

### Key Points / Highlights
- Ethernet = IEEE **802.3**. Uses **CSMA/CD**.
- MAC address = **48 bits (6 bytes)**. Unique per NIC.
- Min frame = **64 bytes**; Max frame = **1518 bytes**; MTU = **1500 bytes**.
- Ethernet uses **CRC-32** for error detection.

### MCQ Focus Section
- Ethernet is defined by **IEEE 802.3**.
- **Preamble** = 7 bytes; **SFD** = 1 byte (10101011).
- **Minimum Ethernet frame** = 64 bytes; **minimum data** = 46 bytes.
- **Maximum data (MTU)** = 1500 bytes.
- MAC address = **48 bits** = **6 bytes**. First 3 bytes = **OUI**.
- **Broadcast MAC** = FF:FF:FF:FF:FF:FF.
- **10BASE-T** means 10 Mbps, Baseband, Twisted pair.
- Ethernet uses **Manchester encoding** (traditional 10 Mbps) for the Physical Layer.
- Modern Gigabit Ethernet uses **full-duplex** and does not use CSMA/CD (no collision domain in full-duplex).
- **FCS** field uses **CRC-32** for error detection.

---
---

# UNIT 7: NETWORK LAYER — IP Addressing

---

## 7.1 Network Layer Design Issues

### Definition
The **Network Layer** (Layer 3 of OSI) is responsible for **source-to-destination delivery** of packets across multiple networks. It provides **logical addressing (IP addressing)**, **routing**, **forwarding**, and **packet fragmentation/reassembly**.

### Detailed Explanation

#### Key Functions
1. **Logical Addressing**: Assigns unique IP addresses to each device for identification across networks.
2. **Routing**: Determines the best path for data to travel from source to destination.
3. **Forwarding**: Moving a packet from an input interface to the appropriate output interface of a router.
4. **Fragmentation and Reassembly**: Splitting large packets into smaller fragments when necessary (based on MTU of the link) and reassembling them at the destination.
5. **Packetizing**: Encapsulating data from the Transport Layer into packets with IP headers.

#### Store-and-Forward vs Datagram vs Virtual Circuit

**1. Datagram Approach (Connectionless)**
- Each packet is treated **independently** — may take different routes.
- No setup phase. Each packet has full destination address.
- Used in the **Internet (IP protocol)**.
- **Advantages**: Flexible, fault-tolerant, no connection setup overhead.
- **Disadvantages**: Packets may arrive out of order; each packet must carry full address.

**2. Virtual Circuit Approach (Connection-Oriented)**
- A **path is established first** before data transfer begins. All packets follow the **same path**.
- Uses a short **virtual circuit identifier** (VCI) instead of full destination address in each packet.
- Three phases: **setup, data transfer, teardown**.
- Examples: ATM, MPLS, Frame Relay.
- **Advantages**: Packets arrive in order, less per-packet overhead.
- **Disadvantages**: Setup overhead, less fault-tolerant (path fails → connection lost).

### Key Points / Highlights
- Network Layer provides **logical addressing** and **routing**.
- IP uses the **datagram** (connectionless) approach.
- Virtual circuits use a **connection-oriented** approach.

### MCQ Focus Section
- **IP** is a **connectionless**, **datagram-based** protocol.
- In datagram networks, each packet may take a **different route**.
- In virtual circuit networks, all packets follow the **same pre-established path**.
- **ATM** and **MPLS** use virtual circuits; **IP** uses datagrams.
- **Forwarding** = local action at a router; **Routing** = global decision on path.

---

## 7.2 IP Addressing — Classful

### Definition
**IP Addressing** is a scheme for assigning unique logical addresses to every device (host/router interface) on a network. **Classful addressing** divides the IP address space into five fixed classes (A, B, C, D, E) based on the first few bits.

### Detailed Explanation

An **IPv4 address** is a **32-bit** number, typically written in **dotted decimal** notation (e.g., 192.168.1.1). It consists of two parts: **Network ID** and **Host ID**.

#### IP Address Classes

| Class | First Bits | Range (First Octet) | Network Bits | Host Bits | Default Subnet Mask | Number of Networks | Hosts per Network |
|-------|------------|--------------------|--------------|-----------|--------------------|--------------------|----|
| A | 0 | 1–126 | 8 | 24 | 255.0.0.0 (/8) | 126 | ~16.7 million |
| B | 10 | 128–191 | 16 | 16 | 255.255.0.0 (/16) | ~16,384 | ~65,534 |
| C | 110 | 192–223 | 24 | 8 | 255.255.255.0 (/24) | ~2 million | 254 |
| D | 1110 | 224–239 | — | — | — | Multicast | — |
| E | 1111 | 240–255 | — | — | — | Reserved/Experimental | — |

#### Special IP Addresses
- **0.0.0.0**: This network, this host (used during boot/DHCP).
- **127.x.x.x** (especially 127.0.0.1): **Loopback** address — refers to the local machine itself. Used for testing.
- **255.255.255.255**: **Limited broadcast** — broadcast to all devices on the local network.
- **Network address**: Host bits all set to 0. Identifies the network itself.
- **Broadcast address**: Host bits all set to 1. Broadcasts to all hosts on that network.

#### Private IP Addresses (RFC 1918)
- Not routable on the Internet. Used for internal networks.
- **Class A**: 10.0.0.0 – 10.255.255.255
- **Class B**: 172.16.0.0 – 172.31.255.255
- **Class C**: 192.168.0.0 – 192.168.255.255

### Key Points / Highlights
- IPv4 = **32-bit address**, written in **dotted decimal** notation.
- Class A = large networks (few networks, many hosts); Class C = small networks (many networks, few hosts).
- **127.0.0.1** = loopback address.
- **Class D** = multicast; **Class E** = reserved.

### MCQ Focus Section
- IP address **192.168.1.1** belongs to **Class C** (first octet 192 is in 192-223 range).
- IP address **10.0.0.1** belongs to **Class A** and is a **private** address.
- **127.0.0.1** is the **loopback** address.
- Class A uses **/8**, Class B uses **/16**, Class C uses **/24** as default subnet mask.
- The first octet **0** and **127** are not assigned to any class for regular use.
- IP **172.16.5.1** is a **Class B private** address.
- **Class D** (224-239) is used for **multicasting**.
- The main problem with classful addressing is **wasteful address allocation** — e.g., a Class A network allocates ~16.7 million host addresses even if only a few hundred are needed.

---

## 7.3 IP Addressing — Classless (CIDR)

### Definition
**Classless Inter-Domain Routing (CIDR)** is a method of IP addressing that eliminates the fixed class boundaries of classful addressing. It uses a **variable-length subnet mask (VLSM)** to allocate IP addresses more efficiently, indicated by a **prefix length** (e.g., /20).

### Detailed Explanation

- In CIDR, any number of bits can be designated as the network part.
- The prefix length **n** (in /n notation) specifies how many bits are used for the network portion.
- Number of host addresses = **2^(32-n)** (for IPv4).
- Usable hosts = 2^(32-n) − 2 (subtract network and broadcast addresses).
- CIDR enables **route aggregation** (supernetting) — multiple networks can be represented by a single routing entry.
- Example: 192.168.0.0/22 means first 22 bits are the network part → covers 2^(32-22) = 1024 addresses.

#### Advantages of CIDR over Classful
- More flexible and efficient use of IP address space.
- Reduces the size of routing tables through **route aggregation**.
- Slows down the exhaustion of IPv4 addresses.

### Key Points / Highlights
- CIDR uses **prefix notation** (/n) instead of fixed classes.
- Allows **variable-length subnet masks (VLSM)**.
- Enables **supernetting** (combining networks) and efficient allocation.

### MCQ Focus Section
- CIDR eliminates the concept of **fixed classes** (A, B, C).
- In CIDR notation **/24**, the first **24 bits** are the network portion.
- Number of addresses in /n = **2^(32-n)**.
- CIDR helps reduce **routing table size** through aggregation.
- **VLSM** allows different subnets to have different subnet mask lengths.
- CIDR was introduced to address the inefficiency of **classful addressing**.

---

## 7.4 Subnetting

### Definition
**Subnetting** is the process of dividing a single large network into **smaller sub-networks (subnets)** by borrowing bits from the **host portion** of the IP address to create a new **subnet field**.

### Detailed Explanation

- Purpose: Reduce broadcast domains, improve security, efficient use of IP addresses.
- When bits are borrowed from the host portion, the subnet mask changes.
- **Number of subnets** = 2^s (where s = number of borrowed bits).
- **Number of hosts per subnet** = 2^h − 2 (where h = remaining host bits; subtract 2 for network and broadcast).

#### Example
Network: 192.168.1.0/24 — need 4 subnets.
- Borrow 2 bits from host portion: /24 → /26.
- Subnet mask: 255.255.255.192.
- Number of subnets: 2² = 4.
- Hosts per subnet: 2⁶ − 2 = 62.
- Subnets:
  - 192.168.1.0/26 (hosts: .1 to .62, broadcast: .63)
  - 192.168.1.64/26 (hosts: .65 to .126, broadcast: .127)
  - 192.168.1.128/26 (hosts: .129 to .190, broadcast: .191)
  - 192.168.1.192/26 (hosts: .193 to .254, broadcast: .255)

### Key Points / Highlights
- Subnetting borrows bits from the **host portion**.
- More subnets = fewer hosts per subnet.
- Always subtract 2 from total hosts (network address and broadcast address).

### MCQ Focus Section
- Subnetting creates **smaller networks** from a larger one.
- **/26** means 26 bits for network, 6 bits for hosts → **62 usable hosts** per subnet.
- Borrowing **3 bits** from host creates **8 subnets** (2³).
- A subnet mask of **255.255.255.224** = **/27** (27 network bits).
- **All-0s** host address = network address; **All-1s** host address = broadcast address.

---

## 7.5 Supernetting

### Definition
**Supernetting** (also called **route aggregation** or **route summarization**) is the process of combining multiple smaller contiguous networks into a **single larger network** by moving the network/host boundary to the left (using fewer network bits).

### Detailed Explanation

- Opposite of subnetting: subnetting borrows host bits → supernetting gives back network bits.
- Used to **reduce routing table entries** by representing multiple networks with one entry.
- Requirements for supernetting:
  1. Networks must be **contiguous** (consecutive).
  2. The number of networks being combined should be a **power of 2**.
  3. The first network address must be **evenly divisible** by the total number of networks.

#### Example
Combining 4 Class C networks: 192.168.0.0/24 through 192.168.3.0/24.
- Supernet: 192.168.0.0/**22** (borrowed 2 bits back from network portion).
- This single entry represents all 4 networks.

### Key Points / Highlights
- Supernetting = combining networks. Subnetting = dividing networks.
- Reduces **routing table size**.
- Networks must be **contiguous** and a **power of 2** in count.

### MCQ Focus Section
- Supernetting moves the subnet mask to the **left** (fewer network bits).
- Subnetting moves the subnet mask to the **right** (more network bits).
- Supernetting is key to **CIDR** and route aggregation.
- Combining 8 Class C networks requires a **/21** supernet mask.

---

## 7.6 Network Layer Services

### Definition
The Network Layer provides services to the Transport Layer, primarily responsible for **packetization**, **routing**, and **forwarding** of data across networks.

### Detailed Explanation

- **Packetization**: Encapsulating transport-layer segments into packets by adding the IP header.
- **Routing**: Finding the best path using routing algorithms and building routing tables.
- **Forwarding**: Actual movement of packets at each router based on the routing/forwarding table.
- **Error Handling**: ICMP (Internet Control Message Protocol) reports errors.
- **Fragmentation**: Splitting packets that exceed a link's MTU.

### MCQ Focus Section
- Network layer provides **host-to-host** delivery.
- **ICMP** is used for error reporting (e.g., Destination Unreachable, Time Exceeded).
- **Ping** uses ICMP Echo Request and Echo Reply.
- **Traceroute** uses ICMP Time Exceeded messages.

---

## 7.7 Network Layer Performance

### Definition
Network layer performance is measured by metrics like **delay**, **throughput**, **packet loss**, and **congestion** levels.

### Detailed Explanation

- **Delay**: Total time for a packet to traverse the network (includes processing, queuing, transmission, propagation).
- **Throughput**: Actual rate of successful data delivery.
- **Packet Loss**: Percentage of packets that fail to reach the destination (often due to congestion/buffer overflow).
- **Congestion**: When too many packets are in the network, causing delays and packet loss.

### MCQ Focus Section
- Packet loss is primarily caused by **buffer overflow** at routers.
- High congestion leads to increased **delay** and **packet loss**.
- **Throughput** is limited by the **bottleneck link** in the path.

---

## 7.8 Forwarding of IP Packets

### Definition
**Forwarding** is the process by which a router moves an incoming packet from its input interface to the appropriate output interface based on the destination IP address and the **forwarding table** (routing table).

### Detailed Explanation

#### Forwarding Process
1. Router receives a packet on an incoming interface.
2. Extracts the **destination IP address** from the IP header.
3. Performs a **longest prefix match** in the forwarding table.
4. Forwards the packet to the appropriate **next-hop router** or directly delivers to the destination if on a directly connected network.
5. The **TTL (Time to Live)** field is decremented by 1 at each hop. If TTL reaches 0, the packet is **discarded** and an ICMP Time Exceeded message is sent back.

#### Longest Prefix Match
- When multiple entries in the routing table match a destination, the entry with the **longest matching prefix** (most specific match) is chosen.
- This ensures the most specific route is used.

### Key Points / Highlights
- Forwarding uses the **forwarding table** and **longest prefix match**.
- **TTL** prevents packets from looping forever.
- Forwarding is a **local** action at each router.

### MCQ Focus Section
- **Longest prefix match** selects the most specific route.
- If **TTL = 0**, the packet is **discarded** and ICMP Time Exceeded is sent.
- **Default route** (0.0.0.0/0) matches when no other route matches.
- Forwarding is done at **Layer 3** using **IP addresses**.

---

## 7.9 IP Header (IPv4)

### Definition
The **IPv4 header** contains control information required for routing and delivering packets. It has a minimum size of **20 bytes** and a maximum of **60 bytes**.

### Detailed Explanation

| Field | Size | Description |
|-------|------|-------------|
| Version | 4 bits | IP version (4 for IPv4) |
| IHL (Header Length) | 4 bits | Length of header in 32-bit words (min 5 = 20 bytes) |
| Type of Service (ToS/DSCP) | 8 bits | Priority/quality of service |
| Total Length | 16 bits | Total packet size (header + data) in bytes. Max = 65,535 bytes |
| Identification | 16 bits | Unique ID for fragment reassembly |
| Flags | 3 bits | Controls fragmentation (DF = Don't Fragment, MF = More Fragments) |
| Fragment Offset | 13 bits | Position of fragment relative to original packet |
| TTL (Time to Live) | 8 bits | Max number of hops; decremented at each router |
| Protocol | 8 bits | Upper layer protocol (6 = TCP, 17 = UDP, 1 = ICMP) |
| Header Checksum | 16 bits | Error check for header only (not data) |
| Source IP Address | 32 bits | Sender's IP address |
| Destination IP Address | 32 bits | Receiver's IP address |
| Options + Padding | 0–40 bytes | Optional fields (Record Route, Timestamp, etc.) |

### Key Points / Highlights
- IPv4 header minimum = **20 bytes**; maximum = **60 bytes**.
- **TTL** prevents infinite loops. Decremented at each hop.
- **Protocol field**: 6 = TCP, 17 = UDP, 1 = ICMP.
- **Header Checksum** covers only the header, not the data.

### MCQ Focus Section
- IPv4 header minimum size = **20 bytes** (5 × 32-bit words).
- **Total Length** field = max value is **65,535 bytes**.
- **TTL** stands for **Time to Live** — max value = 255.
- Protocol number **6** = TCP; **17** = UDP; **1** = ICMP.
- The **DF (Don't Fragment)** flag prevents fragmentation.
- The **MF (More Fragments)** flag = 1 means more fragments follow; 0 for the last fragment.
- **Header checksum** is recalculated at every router (because TTL changes).
- **IHL** = 5 means header is 20 bytes (5 × 4). IHL = 15 means 60 bytes (maximum).

---

## 7.10 IPv6 Addressing

### Definition
**IPv6 (Internet Protocol version 6)** is the successor to IPv4, designed to solve the **address exhaustion** problem. It uses **128-bit addresses**, providing a vastly larger address space compared to IPv4's 32 bits.

### Detailed Explanation

#### IPv6 Address Format
- **128 bits** long, written as **8 groups of 4 hexadecimal digits** separated by colons.
- Example: 2001:0DB8:0000:0000:0000:0000:0000:0001
- **Abbreviation rules**:
  - Leading zeros in a group can be omitted: 2001:DB8:0:0:0:0:0:1
  - One group of consecutive all-zero groups can be replaced by **: (double colon)**: 2001:DB8::1
  - :: can be used only **once** in an address.

#### Key Features of IPv6
- **128-bit address** → 2¹²⁸ possible addresses (~3.4 × 10³⁸).
- **Simplified header**: Fixed 40-byte header (IPv4 header is variable: 20-60 bytes).
- **No broadcast**: Uses **multicast** and **anycast** instead.
- **No header checksum**: Eliminates checksum overhead at each hop (relies on upper layers).
- **No fragmentation by routers**: Only the source can fragment; routers use **Path MTU Discovery**.
- **IPSec is mandatory** (built-in security).
- **Auto-configuration**: Supports **SLAAC** (Stateless Address Auto-Configuration).
- **Extension headers**: Optional headers are placed after the main header in a chain.

#### IPv6 Header Fields (Fixed 40 Bytes)
| Field | Size | Description |
|-------|------|-------------|
| Version | 4 bits | Always 6 |
| Traffic Class | 8 bits | Priority/QoS (similar to ToS in IPv4) |
| Flow Label | 20 bits | Identifies a flow of packets for special handling |
| Payload Length | 16 bits | Length of data after the header |
| Next Header | 8 bits | Type of next header (extension header or upper layer protocol) |
| Hop Limit | 8 bits | Same as TTL in IPv4 |
| Source Address | 128 bits | Sender's IPv6 address |
| Destination Address | 128 bits | Receiver's IPv6 address |

#### IPv6 Address Types
- **Unicast**: Identifies a single interface. Packet delivered to that specific interface.
- **Multicast**: Identifies a group of interfaces. Packet delivered to all members of the group.
- **Anycast**: Identifies a group of interfaces. Packet delivered to the **nearest** member of the group.
- **Note**: IPv6 has **no broadcast** — broadcast is replaced by multicast (ff02::1 = all nodes).

### Key Points / Highlights
- IPv6 = **128 bits**; IPv4 = **32 bits**.
- IPv6 header is **fixed at 40 bytes** (simpler than IPv4).
- IPv6 has **no broadcast** — uses multicast and anycast.
- **No router fragmentation** in IPv6; only source fragments.
- **No header checksum** in IPv6.

### MCQ Focus Section
- IPv6 address = **128 bits** = **8 groups of 4 hex digits**.
- **::1** is the **loopback** address in IPv6 (equivalent to 127.0.0.1 in IPv4).
- **::** is the **unspecified** address (equivalent to 0.0.0.0 in IPv4).
- IPv6 header is **40 bytes** (fixed); IPv4 is **20-60 bytes** (variable).
- IPv6 replaced **TTL** with **Hop Limit**.
- IPv6 uses **Next Header** field instead of Protocol field.
- **Flow Label** is a new field in IPv6 (not present in IPv4).
- IPv6 does **not** have a header checksum field.
- **Anycast** delivers to the **nearest** member of a group.
- IPv4 to IPv6 transition techniques: **Dual Stack, Tunneling, Header Translation**.

---

---

# UNIT 8: NETWORK LAYER — Routing

---

## 8.1 Routing Algorithms

### Definition
**Routing algorithms** determine the **best path** (optimal route) for packets to travel from source to destination through a network. They build and maintain **routing tables** used by routers for forwarding decisions.

### Detailed Explanation

#### Classification of Routing Algorithms
- **Static Routing**: Routes manually configured by the administrator. Don't change unless manually updated. Suitable for small, simple networks.
- **Dynamic Routing**: Routes automatically discovered and updated by routing protocols. Adapts to network topology changes. Suitable for large, complex networks.
- **Adaptive**: Changes routes based on network conditions (traffic, topology).
- **Non-Adaptive**: Routes fixed, not changing with conditions (static routing).

---

## 8.2 Shortest Path Algorithm (Dijkstra's Algorithm)

### Definition
**Dijkstra's algorithm** finds the **shortest path** from a single source node to all other nodes in a weighted graph. It is a **link-state** algorithm used in routing protocols like **OSPF**.

### Detailed Explanation

- Each router has **complete knowledge** of the network topology (link-state database).
- The algorithm builds a **shortest path tree** from the source router to all destinations.
- It uses a **greedy approach**: at each step, it selects the unvisited node with the smallest known distance and updates distances to its neighbors.
- **Steps**:
  1. Set distance to source = 0, all others = infinity.
  2. Mark all nodes as unvisited.
  3. Select the unvisited node with the smallest distance.
  4. Update distances to all its unvisited neighbors.
  5. Mark the current node as visited.
  6. Repeat until all nodes are visited.

### Key Points / Highlights
- Used in **OSPF (Open Shortest Path First)**.
- Requires **complete topology knowledge**.
- Greedy algorithm — always picks the nearest unvisited node.
- Produces a **shortest path tree**.

### MCQ Focus Section
- Dijkstra's algorithm is used in **link-state** routing (OSPF).
- It finds the shortest path from **one source to all destinations**.
- Time complexity: **O(n²)** (basic implementation) or **O(n log n)** with priority queue.
- It does **not** work with **negative edge weights**.
- OSPF uses **Dijkstra's algorithm** to build the shortest path tree.

---

## 8.3 Distance Vector Routing

### Definition
**Distance Vector Routing** is a routing algorithm where each router maintains a **routing table** (vector) containing the **distance** (cost/hop count) and **direction** (next hop) to every other destination. Routers periodically share their routing tables with **directly connected neighbors**.

### Detailed Explanation

- Based on the **Bellman-Ford algorithm**.
- Each router knows only its **neighbors** and the **cost to reach them**.
- Routers exchange routing tables with neighbors **periodically** (even if no changes occurred).
- When a router receives a neighbor's routing table, it updates its own table if a shorter path is found.

#### Key Properties
- **Decentralized**: Each router has only local knowledge.
- **Iterative**: Updates continue until tables converge.
- **Asynchronous**: Updates don't need to happen simultaneously.

#### Count-to-Infinity Problem
- A major drawback of Distance Vector Routing.
- When a link goes down, it takes many iterations for routers to realize the destination is unreachable.
- Routers keep incrementing the distance count with each update cycle, never reaching the correct value of infinity.
- **Solutions**:
  - **Split Horizon**: A router does not advertise a route back to the neighbor from which it learned the route.
  - **Poison Reverse**: Instead of not advertising, the router advertises the route with a metric of **infinity** (∞) back to the neighbor.
  - **Triggered Updates**: Send updates immediately when a change is detected, rather than waiting for periodic updates.
  - **Setting a Maximum**: Define a maximum hop count (e.g., 16 in RIP means unreachable).

### Key Points / Highlights
- Based on **Bellman-Ford** algorithm.
- Routers share routing tables with **neighbors only**.
- Suffers from **count-to-infinity** problem.
- Solutions: **Split Horizon, Poison Reverse, Triggered Updates**.
- Used in **RIP (Routing Information Protocol)**.

### MCQ Focus Section
- Distance Vector uses **Bellman-Ford**; Link State uses **Dijkstra's**.
- Routers exchange **entire routing tables** with **neighbors** periodically.
- **Count-to-infinity** is caused by **slow convergence** after a link failure.
- **Split Horizon** prevents advertising a route back to the neighbor from which it was learned.
- **RIP** uses **hop count** as the metric; maximum = **15 hops** (16 = unreachable).
- RIP sends updates every **30 seconds**.
- Distance Vector is also called the **Bellman-Ford algorithm** or **Ford-Fulkerson algorithm**.

---

## 8.4 Link State Routing

### Definition
**Link State Routing** is a routing algorithm where each router has **complete knowledge of the entire network topology**. Each router independently builds a **map** of the network and runs **Dijkstra's algorithm** to find the shortest path to all destinations.

### Detailed Explanation

#### How Link State Routing Works
1. **Discover neighbors**: Each router discovers its directly connected neighbors and measures the cost to each.
2. **Build Link-State Packets (LSPs)**: Each router creates a packet containing its ID, its neighbors, and the cost to each.
3. **Flood LSPs**: Each router sends its LSP to **all** other routers in the network (not just neighbors) — this is called **flooding**.
4. **Build topology map**: Each router uses the collected LSPs to build a **complete graph** of the network.
5. **Run Dijkstra's algorithm**: Each router independently computes the shortest path tree.

#### Advantages over Distance Vector
- **Faster convergence**: Reacts quickly to topology changes.
- **No count-to-infinity problem**.
- **Complete topology knowledge**: Better decision-making.
- **Scalable**: Works better in large networks.

#### Disadvantages
- Requires **more memory** (stores entire topology).
- Requires **more processing power** (runs Dijkstra's).
- **Flooding** generates more traffic initially.

### Key Points / Highlights
- Each router knows the **complete network topology**.
- Uses **Dijkstra's algorithm** for shortest path computation.
- LSPs are **flooded** to all routers.
- Used in **OSPF** and **IS-IS** protocols.

### MCQ Focus Section
- Link State routing uses **flooding** to distribute topology information.
- Each router runs **Dijkstra's algorithm** independently.
- **OSPF** is based on Link State routing.
- Link State converges **faster** than Distance Vector.
- **LSP** = Link-State Packet (contains neighbor info and link costs).
- Link State routing does **not** suffer from the count-to-infinity problem.
- Each router maintains a **Link-State Database (LSDB)** with the full topology.

---

## 8.5 Unicast Routing Protocols

### Definition
**Unicast Routing Protocols** are protocols used to build and maintain routing tables for forwarding packets from a single source to a single destination. They are classified into **Interior Gateway Protocols (IGP)** and **Exterior Gateway Protocols (EGP)**.

### Detailed Explanation

#### Interior Gateway Protocols (IGP)
Used **within** an Autonomous System (AS).

**1. RIP (Routing Information Protocol)**
- Type: Distance Vector.
- Metric: **Hop count** (max 15; 16 = unreachable).
- Updates: Every **30 seconds** (periodic).
- Uses **UDP port 520**.
- Versions: RIPv1 (classful, broadcast), RIPv2 (classless, multicast, supports VLSM).
- **Simple** but limited to small networks (max 15 hops).

**2. OSPF (Open Shortest Path First)**
- Type: Link State.
- Metric: **Cost** (based on bandwidth — higher bandwidth = lower cost).
- Uses **Dijkstra's algorithm**.
- Supports **VLSM** and **CIDR**.
- Uses **areas** for hierarchical design (Area 0 = backbone area).
- Updates: Send only when topology changes (triggered updates).
- Encapsulated directly in **IP** (protocol number 89, not UDP/TCP).
- Faster convergence, no hop count limit.
- Best for **large enterprise networks**.

#### Exterior Gateway Protocol (EGP)
Used **between** Autonomous Systems.

**3. BGP (Border Gateway Protocol)**
- Type: Path Vector (advanced form of Distance Vector).
- The **routing protocol of the Internet**.
- Uses **TCP port 179**.
- Metric: Based on **path attributes** (AS path length, next hop, local preference, etc.).
- Manages routing between ISPs and large organizations.
- Two types: **iBGP** (internal) and **eBGP** (external).
- Focuses on **policies** and **path selection**, not just shortest path.

### Key Points / Highlights
| Protocol | Type | Metric | Algorithm | Scope |
|----------|------|--------|-----------|-------|
| RIP | Distance Vector | Hop count (max 15) | Bellman-Ford | IGP (small networks) |
| OSPF | Link State | Cost (bandwidth) | Dijkstra | IGP (large networks) |
| BGP | Path Vector | Path attributes | Path selection | EGP (Internet) |

### MCQ Focus Section
- **RIP** max hop count = **15**; uses **UDP port 520**.
- **OSPF** uses **Dijkstra's algorithm** and has **no hop limit**.
- **BGP** uses **TCP port 179** and is the **protocol of the Internet**.
- **IGP** = within an AS; **EGP** = between ASes.
- **OSPF** sends updates only on **topology changes**; **RIP** sends every **30 seconds**.
- **BGP** is a **Path Vector** protocol, not pure Distance Vector.
- **OSPF Area 0** is the **backbone area** — all other areas must connect to it.
- **RIPv1** is classful; **RIPv2** supports classless (VLSM/CIDR).
- An **Autonomous System (AS)** is a collection of networks under a single administrative control.

---

---

# UNIT 9: NETWORK LAYER — Congestion Control

---

## 9.1 Congestion Control Algorithms

### Definition
**Congestion** occurs when the demand for network resources (bandwidth, buffer space, processing power) exceeds the available capacity. **Congestion control** refers to mechanisms and algorithms used to prevent, detect, and resolve congestion in a network.

### Detailed Explanation

#### Congestion vs Flow Control
| Feature | Flow Control | Congestion Control |
|---------|-------------|-------------------|
| Concern | Sender overwhelming the receiver | Network being overwhelmed |
| Scope | Between sender and receiver (end-to-end) | Across the entire network |
| Location | Transport Layer | Network + Transport Layer |

#### Approaches to Congestion Control

**1. Open-Loop Congestion Control (Prevention)**
- Policies designed to **prevent** congestion before it occurs.
- Applied at the **design stage**.
- Techniques:
  - **Retransmission Policy**: Careful timing of retransmissions to avoid unnecessary traffic.
  - **Window Policy**: Use Selective Repeat (less wasteful) over Go-Back-N.
  - **Acknowledgment Policy**: Delayed ACKs, piggybacking to reduce ACK traffic.
  - **Discarding Policy**: Routers discard less important packets when buffers are nearly full.
  - **Admission Control**: In virtual circuit networks, refuse new connections if the network is congested.
  - **Traffic Shaping**: Control the rate and pattern of data entering the network.

**2. Closed-Loop Congestion Control (Detection and Resolution)**
- Detects congestion after it occurs and takes corrective action.
- Steps: **Monitor → Detect → Respond**.
- Techniques:
  - **Backpressure**: Congested nodes inform upstream nodes to slow down. Used in hop-by-hop flow control.
  - **Choke Packets**: A congested router sends a special **choke packet** directly to the source, telling it to reduce its sending rate.
  - **Implicit Signaling**: Source infers congestion from symptoms like packet loss or increased delay (no explicit notification).
  - **Explicit Signaling**: Network devices explicitly notify the source of congestion by setting bits in packets (e.g., **ECN — Explicit Congestion Notification**).

#### Traffic Shaping Techniques

**1. Leaky Bucket Algorithm**
- A bucket (buffer) with a **fixed outflow rate** (leak rate).
- Incoming packets are placed in the bucket.
- Packets leave the bucket at a **constant rate**, regardless of the input rate.
- If the bucket overflows (buffer full), excess packets are **discarded**.
- **Effect**: Converts bursty traffic into a **smooth, constant-rate** output.
- **Disadvantage**: Does not allow bursts — output rate is always constant.

**2. Token Bucket Algorithm**
- A bucket holds **tokens** generated at a fixed rate.
- To send a packet, a station must **consume a token** from the bucket.
- If the bucket is full of tokens and a burst arrives, the station can send **burst traffic** (up to the bucket capacity).
- If the bucket is empty (no tokens), the station must **wait** for new tokens.
- **Effect**: Allows **controlled bursts** while maintaining an average rate.
- **Advantage over Leaky Bucket**: Allows bursty traffic (more flexible).
- Maximum burst size = bucket capacity (number of tokens).
- Maximum output rate = bucket size / time + token generation rate.

### Key Points / Highlights
- **Open-loop** = prevention; **Closed-loop** = detection and reaction.
- **Leaky Bucket** converts bursty traffic to constant rate.
- **Token Bucket** allows controlled bursts — more flexible than leaky bucket.
- **Choke packets** tell the source to slow down.
- **ECN** is an explicit signaling mechanism.

### MCQ Focus Section
- **Leaky Bucket** produces a **constant output rate** — no bursts.
- **Token Bucket** allows **bursts** up to the bucket capacity.
- **Open-loop** congestion control works **before** congestion; **Closed-loop** works **after**.
- **Choke packet** is sent from a **congested router to the source**.
- **ECN** = Explicit Congestion Notification — uses bits in the IP header.
- **Backpressure** works in **hop-by-hop** manner (from congested node to upstream).
- **Implicit signaling**: Source detects congestion from **packet loss** or **timeout**.
- **Traffic shaping** is an **open-loop** technique.
- Token Bucket is **more flexible** than Leaky Bucket because it permits bursts.
- In the **Token Bucket**, if the bucket is empty, the sender must **wait** for tokens.

---
---

# UNIT 10: TRANSPORT LAYER

---

## 10.1 Transport Layer Services

### Definition
The **Transport Layer** (Layer 4 of OSI) provides **end-to-end (process-to-process)** communication between applications running on different hosts. It ensures that data from a sending application is delivered to the correct receiving application reliably and efficiently.

### Detailed Explanation

#### Key Functions

**1. Process-to-Process Delivery**
- While the Network Layer provides host-to-host delivery (using IP addresses), the Transport Layer provides **process-to-process** delivery using **port numbers**.
- A port number identifies a specific application/process on a host.
- **Socket** = IP Address + Port Number. A socket uniquely identifies a process on the Internet.

**2. Port Numbers**
- **16-bit** number, ranging from **0 to 65535**.
- Categories:
  - **Well-Known Ports (0-1023)**: Reserved for standard services. Examples: HTTP (80), HTTPS (443), FTP (20/21), SSH (22), Telnet (23), SMTP (25), DNS (53), DHCP (67/68), POP3 (110), IMAP (143).
  - **Registered Ports (1024-49151)**: Assigned to specific applications. Examples: MySQL (3306), RDP (3389).
  - **Dynamic/Private Ports (49152-65535)**: Temporary/ephemeral ports assigned to client applications automatically.

**3. Multiplexing and Demultiplexing**
- **Multiplexing**: At the sender, gathering data from multiple application processes, encapsulating with port numbers, and passing to the Network Layer.
- **Demultiplexing**: At the receiver, delivering data to the correct application process based on the port number in the segment header.

**4. Connection Management**
- TCP provides connection-oriented service (connection setup, data transfer, connection teardown).
- UDP provides connectionless service (no connection setup).

**5. Flow Control**
- Prevents the sender from overwhelming the receiver.
- TCP uses **Sliding Window** mechanism with a **receive window** (rwnd) advertised by the receiver.

**6. Error Control**
- Ensures reliable delivery.
- TCP uses **checksums**, **acknowledgments**, **sequence numbers**, and **retransmissions**.

**7. Congestion Control**
- TCP adjusts its sending rate to avoid network congestion.
- Mechanisms: **Slow Start, Congestion Avoidance, Fast Retransmit, Fast Recovery**.

### Key Points / Highlights
- Transport Layer provides **process-to-process** delivery using **port numbers**.
- **Socket** = IP Address + Port Number.
- Two main protocols: **TCP (reliable)** and **UDP (unreliable)**.
- Port numbers range from **0 to 65535**.

### MCQ Focus Section
- Network Layer = **host-to-host**; Transport Layer = **process-to-process**.
- Data Link Layer = **hop-to-hop (node-to-node)**.
- **Port 80** = HTTP; **Port 443** = HTTPS; **Port 53** = DNS; **Port 25** = SMTP; **Port 21** = FTP Control.
- **Well-known ports** = 0-1023; **Registered** = 1024-49151; **Dynamic** = 49152-65535.
- A **socket** uniquely identifies a network connection endpoint.
- **Multiplexing** is at the sender; **Demultiplexing** is at the receiver.
- TCP provides **reliable, ordered** delivery; UDP provides **best-effort** delivery.

---

## 10.2 TCP — Transmission Control Protocol

### Definition
**TCP (Transmission Control Protocol)** is a **connection-oriented, reliable, byte-stream** protocol at the Transport Layer. It guarantees that data is delivered **completely, in order, and without errors** from source to destination.

### Detailed Explanation

#### Key Characteristics of TCP
- **Connection-oriented**: Requires a connection to be established before data transfer (3-way handshake).
- **Reliable**: Uses acknowledgments, sequence numbers, checksums, and retransmissions.
- **Full-duplex**: Both sides can send and receive simultaneously.
- **Byte-stream**: Treats data as a stream of bytes, not as separate messages.
- **Flow Control**: Uses sliding window (receiver's advertised window — **rwnd**).
- **Congestion Control**: Uses Slow Start, Congestion Avoidance, Fast Retransmit, Fast Recovery.
- **Ordered delivery**: Uses sequence numbers to reassemble data in the correct order.

### 10.2.1 TCP Header Format

| Field | Size | Description |
|-------|------|-------------|
| Source Port | 16 bits | Port of the sending application |
| Destination Port | 16 bits | Port of the receiving application |
| Sequence Number | 32 bits | Byte number of the first byte of data in this segment |
| Acknowledgment Number | 32 bits | Next byte number expected from the other side |
| Header Length (Data Offset) | 4 bits | Length of TCP header in 32-bit words (min 5 = 20 bytes) |
| Reserved | 6 bits | Reserved for future use (set to 0) |
| Flags (Control Bits) | 6 bits | URG, ACK, PSH, RST, SYN, FIN |
| Window Size | 16 bits | Size of the receive window (for flow control) |
| Checksum | 16 bits | Error detection for header + data + pseudo-header |
| Urgent Pointer | 16 bits | Points to urgent data (valid only if URG flag is set) |
| Options + Padding | 0-40 bytes | Optional fields (e.g., MSS, Window Scaling, Timestamps) |

#### TCP Flags
- **SYN**: Synchronize — used during connection establishment.
- **ACK**: Acknowledgment — indicates the ACK number is valid.
- **FIN**: Finish — used to close a connection.
- **RST**: Reset — used to abort a connection or reject an invalid segment.
- **PSH**: Push — tells the receiver to deliver data to the application immediately.
- **URG**: Urgent — indicates urgent data is present (Urgent Pointer is valid).

#### Minimum TCP Header = **20 bytes**; Maximum = **60 bytes**.

### 10.2.2 TCP Handshaking Operations

#### Three-Way Handshake (Connection Establishment)
1. **SYN**: Client sends a segment with **SYN = 1** and an initial sequence number (ISN) to the server.
2. **SYN-ACK**: Server responds with **SYN = 1, ACK = 1**, its own ISN, and acknowledges the client's ISN + 1.
3. **ACK**: Client sends **ACK = 1**, acknowledging the server's ISN + 1.
- After this, the connection is **established** and data transfer can begin.

#### Four-Way Handshake (Connection Termination)
1. **FIN**: Side A (e.g., client) sends **FIN = 1** to close its side.
2. **ACK**: Side B (server) acknowledges with **ACK = 1**.
3. **FIN**: Side B sends its own **FIN = 1** to close its side.
4. **ACK**: Side A acknowledges with **ACK = 1**.
- After this, the connection is **fully closed**.
- Between steps 2 and 3, the connection is **half-closed** — one direction is closed but the other can still send data.

#### TCP Congestion Control Mechanisms

**1. Slow Start**
- Starts with a small congestion window (**cwnd = 1 MSS**).
- **Doubles** cwnd for every ACK received (exponential growth).
- Continues until cwnd reaches the **slow start threshold (ssthresh)**.

**2. Congestion Avoidance**
- After cwnd ≥ ssthresh, growth switches to **linear** (additive increase).
- cwnd increases by **1 MSS per RTT** (not per ACK).
- Continues until congestion is detected.

**3. Fast Retransmit**
- If the sender receives **3 duplicate ACKs** (4 identical ACKs total), it assumes a packet was lost and **retransmits immediately** without waiting for the timeout.

**4. Fast Recovery**
- After Fast Retransmit, instead of going back to Slow Start, set **ssthresh = cwnd/2** and **cwnd = ssthresh + 3 MSS**.
- Continues with Congestion Avoidance (does not restart from 1).

### Key Points / Highlights
- TCP header minimum = **20 bytes**.
- Connection: **3-way handshake (SYN, SYN-ACK, ACK)**.
- Termination: **4-way handshake (FIN, ACK, FIN, ACK)**.
- TCP flags: **SYN, ACK, FIN, RST, PSH, URG**.
- Congestion control: **Slow Start → Congestion Avoidance**. Reset on timeout; Fast Recovery on 3 dup ACKs.

### MCQ Focus Section
- TCP uses **3-way handshake** for connection setup: **SYN → SYN-ACK → ACK**.
- TCP uses **4-way handshake** for connection termination.
- TCP header minimum = **20 bytes**; maximum = **60 bytes**.
- **Sequence number** identifies the byte position of the first byte in the segment.
- **ACK number** = next byte expected from the other side.
- **Window Size** is used for **flow control** (advertised receive window).
- **3 duplicate ACKs** trigger **Fast Retransmit**.
- **Slow Start** = exponential growth; **Congestion Avoidance** = linear growth.
- When timeout occurs, **cwnd = 1 MSS** and **ssthresh = cwnd/2** (restart Slow Start).
- When 3 duplicate ACKs occur, **ssthresh = cwnd/2** and **cwnd = ssthresh** (Fast Recovery, skip Slow Start).
- TCP provides **reliable, ordered, error-checked** delivery.
- TCP checksum covers **header + data + pseudo-header** (includes source/destination IP).
- **MSS** = Maximum Segment Size — the maximum data payload in one TCP segment.
- **Half-close**: One side has sent FIN, the other side can still send data.

---

## 10.3 UDP — User Datagram Protocol

### Definition
**UDP (User Datagram Protocol)** is a **connectionless, unreliable, lightweight** protocol at the Transport Layer. It provides minimal services — no connection setup, no reliability guarantees, no flow control, no congestion control.

### Detailed Explanation

#### Key Characteristics of UDP
- **Connectionless**: No handshaking before sending data. Each datagram is independent.
- **Unreliable**: No acknowledgments, no retransmissions. Best-effort delivery.
- **No flow control**: Sender can overwhelm the receiver.
- **No congestion control**: Does not adapt to network conditions.
- **No ordering**: Datagrams may arrive out of order.
- **Lightweight**: Very low overhead — header is only **8 bytes**.
- **Message-oriented**: Preserves message boundaries (unlike TCP's byte-stream).

### 10.3.1 UDP Header Format

| Field | Size | Description |
|-------|------|-------------|
| Source Port | 16 bits | Port of the sending application |
| Destination Port | 16 bits | Port of the receiving application |
| Length | 16 bits | Total length of UDP datagram (header + data) in bytes. Minimum = 8 |
| Checksum | 16 bits | Error detection (optional in IPv4, mandatory in IPv6) |

**Total UDP Header Size = 8 bytes** (compared to TCP's minimum 20 bytes).

#### When to Use UDP
- Real-time applications where speed is more important than reliability: **VoIP, video streaming, online gaming**.
- Simple request-response protocols: **DNS (port 53)**, **DHCP (ports 67/68)**.
- **Broadcasting and multicasting**: UDP supports these; TCP does not.
- Applications that implement their own reliability: **TFTP, SNMP, RTP**.
- When low overhead and latency are critical.

### TCP vs UDP Comparison

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable (ACK, retransmission) | Unreliable (best-effort) |
| Ordering | Ordered delivery | No ordering |
| Flow Control | Yes (sliding window) | No |
| Congestion Control | Yes | No |
| Header Size | 20-60 bytes | 8 bytes |
| Speed | Slower (overhead) | Faster (minimal overhead) |
| Data Type | Byte-stream | Message-oriented |
| Broadcasting | No | Yes |
| Use Cases | HTTP, FTP, SMTP, SSH | DNS, DHCP, VoIP, Streaming |

### Key Points / Highlights
- UDP header = **8 bytes** only (Source Port, Dest Port, Length, Checksum).
- **No connection setup**, **no reliability**, **no flow/congestion control**.
- Faster than TCP due to minimal overhead.
- Used for real-time, speed-sensitive applications.

### MCQ Focus Section
- UDP header size = **8 bytes**; TCP header minimum = **20 bytes**.
- UDP is **connectionless** and **unreliable**.
- UDP **does not** guarantee delivery, ordering, or duplicate protection.
- **DNS** primarily uses **UDP** (port 53) for queries; uses TCP for zone transfers.
- **DHCP** uses **UDP** (ports 67/68).
- UDP supports **broadcasting**; TCP does **not**.
- UDP checksum is **optional** in IPv4 but **mandatory** in IPv6.
- UDP preserves **message boundaries** (message-oriented); TCP does not (byte-stream).
- **RTP (Real-time Transport Protocol)** runs over UDP for VoIP and video streaming.
- UDP minimum datagram size = **8 bytes** (header only, no data).
- TCP is used where **reliability** is important; UDP where **speed** is important.

---

---

# UNIT 11: APPLICATION LAYER

---

## 11.1 Domain Name System (DNS)

### Definition
The **Domain Name System (DNS)** is an **application layer protocol** that translates human-readable **domain names** (e.g., www.google.com) into machine-readable **IP addresses** (e.g., 142.250.190.4). It acts as the "phone book" of the Internet.

### Detailed Explanation

#### Why DNS?
- Humans find it easier to remember domain names than numerical IP addresses.
- Computers need IP addresses to communicate.
- DNS bridges this gap by providing name-to-IP resolution.

#### DNS Architecture

**1. Hierarchical Namespace**
- DNS uses a **hierarchical, tree-structured** naming system.
- Root domain → Top-Level Domains (TLDs) → Second-Level Domains → Subdomains.
- Example: mail.google.com → "com" (TLD) → "google" (second-level) → "mail" (subdomain).

**2. Types of Top-Level Domains (TLDs)**
- **Generic TLDs (gTLDs)**: .com, .org, .net, .edu, .gov, .mil, .int, .info, .biz.
- **Country-Code TLDs (ccTLDs)**: .in (India), .us (USA), .uk (UK), .jp (Japan), .au (Australia).

**3. DNS Server Hierarchy**
- **Root DNS Servers**: The starting point of DNS resolution. There are **13 root server clusters** worldwide (labeled A through M).
- **TLD DNS Servers**: Responsible for top-level domains (.com, .org, .in, etc.).
- **Authoritative DNS Servers**: Hold the actual DNS records for a specific domain.
- **Local (Recursive/Resolver) DNS Server**: The DNS server configured on your device (e.g., your ISP's DNS or Google's 8.8.8.8). It handles queries on your behalf.

#### DNS Resolution Process

**1. Recursive Query**
- The client sends a query to the local DNS server.
- The local server takes **full responsibility** — it queries other servers as needed and returns the final answer to the client.
- Client ↔ Local DNS = recursive.

**2. Iterative Query**
- The queried server responds with the **best answer it knows** (a referral to another server if it doesn't know).
- The local DNS server then queries the referred server.
- Local DNS ↔ Root/TLD/Authoritative = iterative.

#### DNS Record Types
| Record Type | Description |
|-------------|-------------|
| **A** | Maps domain name to **IPv4 address** |
| **AAAA** | Maps domain name to **IPv6 address** |
| **CNAME** | Canonical Name — alias for another domain name |
| **MX** | Mail Exchange — specifies mail server for the domain |
| **NS** | Name Server — specifies authoritative DNS server for the domain |
| **PTR** | Pointer — for **reverse DNS** (IP to domain name) |
| **SOA** | Start of Authority — administrative info about the DNS zone |
| **TXT** | Text — arbitrary text (used for SPF, DKIM, verification) |

#### DNS Caching
- DNS servers and clients **cache** query results for a period defined by the **TTL (Time to Live)** value in the DNS record.
- Reduces DNS traffic and speeds up resolution for repeated queries.

#### DNS Protocol Details
- Uses **UDP port 53** for regular queries (fast, small).
- Uses **TCP port 53** for zone transfers and large responses (>512 bytes).

### Key Points / Highlights
- DNS translates **domain names to IP addresses**.
- Hierarchical system: Root → TLD → Authoritative servers.
- Uses **UDP port 53** (queries) and **TCP port 53** (zone transfers).
- **A record** = IPv4; **AAAA record** = IPv6; **MX record** = mail server.
- DNS caching improves performance using TTL-based expiry.

### MCQ Focus Section
- DNS uses **UDP port 53** for queries and **TCP port 53** for zone transfers.
- There are **13 root server clusters** (A through M).
- **A record** maps a domain name to an **IPv4** address; **AAAA** maps to **IPv6**.
- **CNAME** is an alias for another domain name.
- **MX record** specifies the **mail server** for a domain.
- **PTR record** is used for **reverse DNS lookup** (IP → domain).
- **Recursive query**: Client expects a **complete answer** from its DNS server.
- **Iterative query**: DNS server gives the **best answer it has** or a referral.
- DNS is an **Application Layer** protocol.
- **FQDN** = Fully Qualified Domain Name (e.g., www.google.com.).
- DNS uses a **hierarchical namespace**, not a flat namespace.
- **NS record** identifies the authoritative name server for a zone.
- **Google Public DNS** = 8.8.8.8 and 8.8.4.4.

---

## 11.2 Electronic Mail (E-Mail)

### Definition
**Electronic Mail (E-Mail)** is an application layer service that allows users to compose, send, receive, and manage text-based messages (along with attachments) over a network. The email system involves multiple protocols working together.

### Detailed Explanation

#### Components of an Email System

**1. User Agent (UA)**
- The email client software used to compose, read, and manage emails.
- Examples: Microsoft Outlook, Gmail (web interface), Thunderbird, Apple Mail.

**2. Message Transfer Agent (MTA)**
- The software that transfers email messages between mail servers.
- Runs on the mail server.
- Uses **SMTP** for sending/relaying mail.

**3. Mail Server**
- Stores incoming emails in **mailboxes** for users.
- Has both an **MTA** (for sending/receiving from other servers) and a **Mail Delivery Agent (MDA)** (for placing mail in the user's mailbox).

#### Email Protocols

**1. SMTP (Simple Mail Transfer Protocol)**
- Used for **sending/pushing** emails from client to server and between servers.
- Port: **25** (standard), **587** (submission with authentication), **465** (deprecated, SMTPS).
- **Push protocol** — the sender pushes the email to the server.
- Uses **TCP** for reliable delivery.
- Only handles **ASCII text** — for attachments and multimedia, **MIME** (Multipurpose Internet Mail Extensions) is used.
- SMTP commands: HELO/EHLO, MAIL FROM, RCPT TO, DATA, QUIT.

**2. POP3 (Post Office Protocol version 3)**
- Used for **retrieving/pulling** emails from the mail server to the client.
- Port: **110** (standard), **995** (POP3S with SSL/TLS).
- **Pull protocol** — the client pulls emails from the server.
- Two modes:
  - **Download and Delete**: Emails are removed from the server after download. Cannot access emails from another device.
  - **Download and Keep**: Emails remain on the server after download.
- Simpler than IMAP. Not ideal for accessing emails from multiple devices.

**3. IMAP (Internet Message Access Protocol)**
- Used for **retrieving/managing** emails on the mail server.
- Port: **143** (standard), **993** (IMAPS with SSL/TLS).
- Emails remain on the **server** — client can view, organize, search, and manage them without downloading.
- Supports **multiple folders**, **searching**, and **partial downloading** of messages.
- Ideal for accessing emails from **multiple devices** — state is synchronized.
- More feature-rich and complex than POP3.

#### Email Flow
1. Sender composes email using **User Agent**.
2. Email is sent via **SMTP** to the sender's mail server.
3. Sender's mail server forwards the email via **SMTP** to the recipient's mail server.
4. Recipient retrieves the email using **POP3** or **IMAP**.

#### MIME (Multipurpose Internet Mail Extensions)
- Extends the format of email to support **non-ASCII text**, **attachments**, and **multimedia** (images, audio, video).
- MIME headers define the type and encoding of the content.
- Content types: text/plain, text/html, image/jpeg, application/pdf, multipart/mixed, etc.

### Key Points / Highlights
- Email uses three main protocols: **SMTP** (sending), **POP3** (retrieving — simple), **IMAP** (retrieving — advanced).
- SMTP = push protocol; POP3/IMAP = pull protocols.
- **MIME** enables sending attachments and multimedia via email.
- IMAP keeps emails on the server; POP3 typically downloads them.

### MCQ Focus Section
- **SMTP** uses port **25**; **POP3** uses port **110**; **IMAP** uses port **143**.
- SMTP is a **push** protocol; POP3 and IMAP are **pull** protocols.
- **IMAP** keeps emails on the **server**; **POP3** typically downloads to the client.
- **IMAP** is better for **multi-device access**; POP3 is simpler but limited.
- **MIME** allows emails to carry **attachments and non-ASCII content**.
- SMTP uses **TCP** for reliable email delivery.
- SMTP is used between **sender and mail server** and between **mail servers**.
- POP3/IMAP is used between **mail server and recipient's client**.
- **SMTP** can only handle **7-bit ASCII text** natively; MIME extends this.
- Email flow: Sender UA → (SMTP) → Sender MTA → (SMTP) → Receiver MTA → (POP3/IMAP) → Receiver UA.

---

## 11.3 FTP (File Transfer Protocol)

### Definition
**FTP (File Transfer Protocol)** is an application layer protocol used for transferring files between a **client** and a **server** over a TCP network. It provides mechanisms for uploading, downloading, renaming, deleting, and managing files on a remote server.

### Detailed Explanation

#### Key Characteristics
- Uses **TCP** for reliable file transfer.
- Uses **two separate connections** (unique among application protocols):
  1. **Control Connection (Port 21)**: Used for sending commands and receiving responses. Persistent — stays open throughout the FTP session.
  2. **Data Connection (Port 20)**: Used for actual file transfer. Created and closed for each file transfer/directory listing.

#### FTP Connection Modes

**1. Active Mode**
- The server **initiates** the data connection back to the client.
- Client sends PORT command with its IP and port.
- Server connects from port 20 to the client's specified port.
- **Problem**: May be blocked by client-side firewalls (incoming connection to client).

**2. Passive Mode**
- The client **initiates** the data connection to the server.
- Client sends PASV command; server responds with an IP and port.
- Client connects to the server's specified port.
- **Better for firewalled environments** — all connections are initiated by the client.

#### FTP Commands
| Command | Description |
|---------|-------------|
| USER | Send username |
| PASS | Send password |
| LIST | List files in current directory |
| RETR | Retrieve (download) a file |
| STOR | Store (upload) a file |
| DELE | Delete a file |
| MKD | Make a directory |
| RMD | Remove a directory |
| CWD | Change working directory |
| PWD | Print working directory |
| QUIT | Close the connection |

#### FTP Response Codes
- **1xx**: Positive preliminary (action started).
- **2xx**: Positive completion (action successful). Example: 200 OK, 226 Transfer complete.
- **3xx**: Positive intermediate (need more info). Example: 331 Username OK, need password.
- **4xx**: Transient negative (try again). Example: 421 Service not available.
- **5xx**: Permanent negative (error). Example: 530 Not logged in.

#### Limitations of FTP
- **Not secure by default**: Username, password, and data are sent in **plain text** (no encryption).
- **Secure alternatives**:
  - **SFTP (SSH File Transfer Protocol)**: File transfer over SSH. Uses port **22**. Encrypted.
  - **FTPS (FTP Secure/FTP-SSL)**: FTP with SSL/TLS encryption. Uses ports **989/990**.
  - Both provide encrypted, secure file transfer.

#### Anonymous FTP
- Allows users to connect to an FTP server **without a personal account**.
- Username: **anonymous** or **ftp**; Password: usually an email address or blank.
- Provides **read-only** access to public files.

### Key Points / Highlights
- FTP uses **two connections**: Control (port 21) and Data (port 20).
- **Active mode**: Server initiates data connection. **Passive mode**: Client initiates data connection.
- FTP is **not secure** by default — use **SFTP (port 22)** or **FTPS** for secure transfers.
- Uses **TCP** for reliable transfer.

### MCQ Focus Section
- FTP control connection = **port 21**; data connection = **port 20**.
- FTP uses **two connections** — this is called **out-of-band control** (control and data on separate connections).
- **Active mode**: Server connects **to** client (port 20 → client port).
- **Passive mode**: Client connects **to** server (used to bypass firewalls).
- FTP sends data in **plain text** — passwords are **not encrypted**.
- **SFTP** uses **port 22** (runs over SSH); **FTPS** uses SSL/TLS encryption.
- FTP operates over **TCP** (not UDP) for reliable delivery.
- **Anonymous FTP** allows login with username "anonymous".
- FTP is **stateful** — the server maintains session state (current directory, mode, etc.).
- The control connection is **persistent** (stays open); the data connection is **non-persistent** (opens and closes per transfer).
- **HTTP** uses **in-band control** (commands and data on same connection); **FTP** uses **out-of-band control**.

---

---

> **— End of Book —**
>
> *This comprehensive guide covers all topics as per the Computer Networks syllabus.*
> *Use it for concept building, exam revision, placement preparation, and technical interviews.*
> *Good luck!* 🎓
