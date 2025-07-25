# Network Models

Network models define the architecture and protocols used for communication in computer networks. The two primary reference models are:

- TCP/IP Model
- OSI Model

## TCP/IP Model

Transmission Control Protocol/Internet Protocol (TCP/IP) model is a concise version of the OSI Model. The TCP/IP protocol suite was developed before the OSI model. But the layers in the TCP/IP protocol suite do not exactly match those in the OSI model.

### TCP/IP Protocol

- The original TCP/IP protocol uses four layers host-to-network, Internet, Transport, and Application layer.
- The host-to-network layer is equivalent to the combination of physical and data link layers in the OSI model.
- The Internet layer in TCP/IP is equivalent to the Network layer of the OSI model. And the Application layer does the job of the Session, Presentation, and Application layers with the Transport layer in TCP/IP.
- In the TCP/IP model, the first four layers provide physical standards, network interface, internetworking, and transport functions.
- The first topmost layers (application, presentation, and session layers) in the OSI model are represented in TCP/IP by a single layer called the application layer.
- In the Transport layer, the TCP/IP model defines three protocols Transmission Control Protocol (TCP), User Datagram Protocol (UDP), and the Stream Control Transmission Protocol (SCTP).

### Layers of TCP/IP Model

#### 1. Application Layer

In TCP/IP, the Application layer protocols provide services to the application software running on a computer. The application layer uses HTTP, POP3, and SMTP protocols. The application layer provides an interface between the software running on a computer and the network itself.

#### 2. Transport Layer

In TCP/IP, the Transport layer includes transmission control protocol (TCP) and user datagram protocol (UDP). TCP provides services to the application layer that reside above the transport layer or higher within the TCP/IP model.

#### 3. Internet Layer (Network Layer)

The Internet layer in the TCP/IP model is the Network Layer 3 of the OSI model. It stores the IP addresses and the routing data. When data is transmitted from a node on one LAN to a node on a different LAN, the Internet Layer is used. IPv4, IPv6, ICMP, and routing protocols (among others) are the Internet Layer TCP/IP protocols.

#### 4. Host-to-Network Layer (Link Layer)

In TCP/IP, the Host-to-Network layer is also called the network interface or link layer. It provides services to the upper layer within the model. When a hosts or routers IP process chooses to send an IP packet to a different router or host, that host or router then uses the link-layer details to send that packet to the next host/router.

This layer is the lowermost layer of the TCP/IP model; it is concerned with the physical transmission of data. It is like a combination of the data link layer and physical layer of the OSI model.

## OSI Model

OSI or Open System Interconnection model was developed by International Standards Organization (ISO), which allows different communication systems to communicate via standard protocols. It gives a layered networking framework that conceptualizes how communications should be done between heterogeneous systems. In layman's terms, the OSI establishes a standard for computer systems to communicate with one another.

The model divides the flow of data in a communication system into seven abstraction levels or seven interconnected layers. The seven layers of the OSI Model are a physical layer, data link layer, network layer, transport layer, session layer, presentation layer, and application layer, as shown in the following diagram -

<!-- Diagram of OSI Layers -->

> Each intermediary layer provides a class of functionality to the layer above it while also receiving service from the layer below. Standard communication protocols are used to implement classes of functionality in software.

- The physical layer, data link layer, and network layer are the network support layers. The layers manage the physical transfer of data from one device to another.
- The session layer, presentation layer, and application layer are the user support layers. These layers allow communication among unrelated software in dissimilar environments.
- The transport layer links the two groups.

### Layers of OSI Model

- **Physical Layer** − Its function is to transmit individual bits from one node to another over a physical medium.
- **Data Link Layer** − It is responsible for the reliable transfer of data frames from one node to another connected by the physical layer.
- **Network Layer** − It manages the delivery of individual data packets from source to destination through appropriate addressing and routing.
- **Transport Layer** − It is responsible for delivery of the entire message from the source host to destination host.
- **Session Layer** − It establishes sessions between users and offers services like dialog control and synchronization.
- **Presentation Layer − It monitors syntax and semantics of transmitted information through translation, compression, and encryption.
- **Application Layer** − It provides high-level APIs (application program interface) to the users.

### Characteristics of OSI Model

The top layer of the OSI model deals mainly with system-related difficulties, which are only used in the software. The program layer is the closest to the user. Software applications communicate with both end-user and application frameworks. A layer that is directly above the other is called the top layer.

The OSI model's lowest layer deals with data transmission difficulties. Hardware and software are used to implement the data link and physical layers. The physical layer is the OSI model's lowest layer, and it's the one nearest to the physical media. The physical layer is primarily in charge of putting data on the physical medium.

### Advantages of OSI Model

- In the field of computer networking, it is regarded as a standard model.
- Both connectionless and connection-oriented services are supported by the model. When users need faster data transmissions via the internet, they can use connectionless services, and when they need reliability, they can use the connection-oriented model.
- It's adaptable to a wide range of protocols.
- Having all services packed in one layer makes the model less adaptive and secure.

### Disadvantages of OSI Model

- The session layer, which manages sessions, and the presentation layer, which handles user interaction, aren't as useful as the OSI model's other layers.
- Some services, such as transport and data-link layers, are repeated at different tiers.
- Layers cannot work simultaneously; each layer must wait for data from the preceding layer to be received.

## OSI Model Layers

The 7 Layers of OSI model:

| Layers No. | Layers Name         | Function                                                              |
|------------|---------------------|-----------------------------------------------------------------------|
| Layer 1    | Physical Layer      | Transmission method used to propagate bits through a network         |
| Layer 2    | Data Link Layer     | Frame formatting for transmitting data across a physical line        |
| Layer 3    | Network Layer       | Network addressing and packet transmission on the network            |
| Layer 4    | Transport Layer     | Data tracking as it moves through a network                          |
| Layer 5    | Session Layer       | Job management tracking                                               |
| Layer 6    | Presentation Layer  | Encoding the language used in transmission                           |
| Layer 7    | Application Layer   | User networking applications and interfacing to the network          |

### Physical Layer

The Physical Layer is the lowermost layer in the OSI model and its major responsibility includes the actual propagation of the unstructured data bits (0s and 1s) across the network, from the physical layer of the sending device to the physical layer of the receiving device.

The Physical layer contains information in the form of bits. It transmits individual bits from one node to the next node. The transmission media defined by the physical layer include metallic cable, optical fiber, and the wireless radio-wave.

- **Bit Synchronization** Physical layer provides the bit synchronization of bits by providing a clock. This clock controls the sender and receiver providing synchronization at bit level.
- **Bit Rate Control** Physical layer defines the transmission rate. The number of bits sent per second.
- **Physical Topologies** The physical layer specifies how the different devices are arranged in a network (bus, ring, star, and mesh topology).
- **Transmission mode** The physical layer checks if the transmission is simplex, half-duplex, or full-duplex. It defines how the data flows between the two connected devices.

### Data Link Layer

It is the second layer of the OSI model. The data link layer is responsible for providing error-free communication across the physical link connecting the primary and secondary nodes within a network. It provides hop-to-hop delivery. It packages the data from the physical layer into a group called blocks.

The data link layer provides the final framing of the information signal, and it provides synchronization facilities for the orderly flow of data between the nodes.

- **Framing** Breaks messages into frames and reassembles frames into messages.
- **Error handling** It is used to soles the damaged, lost, and duplicate frames.
- **Flow Control** It keeps a fast transmitter from flooding a slow receiver.
- **Access Control** In access control, if many hosts have usage of the medium, When a single communication channel is shared by multiple devices, the MAC sub-layer of data link layer helps to determine which device has control over the channel at a given time.

### Network Layer

The network layer provides details that enable data to be routed between devices in an environment using multiple networks, sub-networks, or both.

The networking components that operate at the network layer include routers and their software. It determines which network configuration is most appropriate for the function provided by the network and addresses and routes data within a network by establishing, maintaining, and terminating connectors between them.

It provides the upper layers of the hierarchy with independence from the data transmission and switching technologies used to interconnect systems.

It also provides the source and destination network addresses, subnet information, and source and destination node addresses. In this, the network is subdivided into subnet-work that is separated by routers.

### Transport Layer

We can say that the transport layer controls and ensures the end-to-end integrity of the data message propagated through the network between two devices, providing the reliable, transparent transfer of data between the endpoints.

- **Segmentation and Reassembly** In this, a message is divided into small pieces. Reassemble the message correctly upon arriving at the destination.
- **Reliability** It ensures that packets arrive at their destination. Reassembles out-of-order messages.
- **Service Decisions** It is used to check what types of service to provide error-free point-to-point, datagram, etc.
- **Mapping** It determines which messages belong to which connections.
- **Naming** It must be translated into an internal address and route, send to node XYZ.
- **Flow Control** It keeps a fast transmitter from flooding a slow receiver.
- **Error Control** To retransmit the damaged segments.

### Session Layer

The session layer creates communication channels between devices. It is responsible for opening sessions, ensuring they remain open and functional while the data is being transferred, and close the session when the communication ends.

The session layer can also set checkpoints during a data transfer. If a session is interrupted, then the devices can resume data transfer from the last checkpoint.

The session layer is responsible for network availability for data storage and processes capacity. It provides the logical connection entities at the application layer.

- Network log-on and log-off procedures
- User authentication
- Determines the type dialog available simplex, half-duplex, and full-duplex.
- Synchronization of data flow for recovery purposes.
- Creation of dialog units and activity units.

### Presentation Layer

The presentation layer prepares the data for its upper layer or the application layer. It defines how two devices should encode, encrypt, and compress the data.

- The presentation layer receives any data transmitted by the application layer and prepares it for transmission over the session layer.
- It specifies how the end-user applications should format the data.
- This layer provides for the translation between the local representation of data and the representation of data that will be used for transfer between the end-users. The result of encryption, data compression, and virtual terminals are examples of translation services.

### Application Layer

The application layer is the topmost layer in the OSI model and acts as the general manager of the network by proving access to the OSI environment. This layer provides distributed information services and controls the sequence of activities within an application and also the sequence of events between the computer application and the user of the application. It communicates directly with the users application program.

The application layer uses HTTP, FTP, POP, SMTP, and DNS protocols that allow the software to send and receive information and present meaningful data to users.

## OSI vs TCP/IP

| OSI Model                                                                 | TCP/IP Model                                                                                          |
|---------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
| OSI represents Open System Interconnection.                               | TCP/IP model represents the Transmission Control Protocol / Internet Protocol.                        |
| OSI is a generic, protocol-independent standard.                          | TCP/IP model depends on standard protocols around which the network is built.                         |
| OSI was developed first, and then protocols were created to fit it.       | Protocols were created first, and then the TCP/IP model was developed.                                |
| Provides quality services.                                                | Does not provide quality services.                                                                    |
| Clearly defines services, interfaces, and protocols.                      | Does not clearly mention services, interfaces, or protocols.                                          |
| Protocols are hidden and can be replaced easily.                          | Protocols are not hidden; replacing protocols is not easy.                                            |
| More complex compared to TCP/IP.                                          | Simpler than OSI.                                                                                     |
| Supports both connection-oriented and connectionless services at different layers. | Supports both connection-oriented and connectionless services in the transport layer.               |
| Uses a vertical approach.                                                 | Uses a horizontal approach.                                                                           |
| Smallest header size is 5 bytes.                                          | Smallest header size is 20 bytes.                                                                     |
| Protocols are unknown and can be modified with technology changes.        | Changing protocols is not easy in TCP/IP.                                                             |
