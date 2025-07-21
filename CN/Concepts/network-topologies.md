# Network Topology

A Network Topology is the arrangement with which computer systems or network devices are connected to each other. Topologies may define both physical and logical aspect of the network. Both logical and physical topologies could be same or different in a same network.

The types of computer network topologies are as follows:

- Point-to-Point Topology
- Bus Topology
- Star Topology
- Ring Topology
- Mesh Topology
- Tree Topology
- Daisy Chain Topology
- Hybrid Topology

## Point-to-Point Topology

Point-to-point networks contains exactly two hosts such as computer, switches or routers, servers connected back to back using a single piece of cable. Often, the receiving end of one host is connected to sending end of the other and vice-versa.

<img src="../Assets/PPP.png" alt="Point-to-Point Topology" />

If the hosts are connected point-to-point logically, then may have multiple intermediate devices. But the end hosts are unaware of underlying network and see each other as if they are connected directly.

**Point-to-point Protocol (PPP)** is a communication protocol of the data link layer that is used to transmit multiprotocol data between two directly connected (point-to-point) computers. It is a byte - oriented protocol that is widely used in broadband communications having heavy loads and high speeds.

### Services provided by PPP

- Defining the frame format of the data to be transmitted.
- Defining the procedure of establishing link between two points and exchange of data.
- Stating the method of encapsulation of network layer data in the frame.
- Stating authentication rules of the communicating devices.
- Providing address for network communication.
- Providing connections over multiple links.
- Supporting a variety of network layer protocols by providing a range os services.

## Bus Topology

In case of Bus topology, all devices share single communication line or cable.Bus topology may have problem while multiple hosts sending data at the same time. Therefore, Bus topology either uses CSMA/CD technology or recognizes one host as Bus Master to solve the issue. It is one of the simple forms of networking where a failure of a device does not affect the other devices. But failure of the shared communication line can make all other devices stop functioning.

<!-- IMAGE -->

Both ends of the shared channel have line terminator. The data is sent in only one direction and as soon as it reaches the extreme end, the terminator removes the data from the line.

### Advantages of Bus Topology

- Simple control of traffic flow.
- Failure of a node does not influence the network.

### Disadvantages of Bus Topology

- If the transmission channel fails, the entire network fails.
- It is complicated to isolate faults to any one particular component tied into the bus.
- Because of the back of the concentration points, the problem resolution is challenging.

## Star Topology

All hosts in Star topology are connected to a central device, known as hub device, using a point-to-point connection. That is, there exists a point to point connection between hosts and hub. The hub device can be any of the following:

- Layer-1 device such as hub or repeater 
- Layer-2 device such as switch or bridge 
- Layer-3 device such as router or gateway

<!-- IMAGE -->

As in Bus topology, hub acts as single point of failure. If hub fails, connectivity of all hosts to all other hosts fails. Every communication between hosts, takes place through only the hub.Star topology is not expensive as to connect one more host, only one cable is required and configuration is simple.

### Advantages of Star Topology

- Star topology needs minimal line cost because connecting n nodes requires (n 1) lines.
- If any of the work stations fails, it makes no effect on communication of the work stations, and thus the remaining portion of the network is unaffected.
- If new nodes are inserted into the network, it needs just a link to the server. Thus transmission delay between two nodes does not increase.
- The software, fault isolation and traffic flow is simple.

### Disadvantages of Star Topology

- The entire network depends on a central computer, so if the server fails, the whole networks working fails.
- The distributed processing capability is limited.

## Ring Topology

In ring topology, each host machine connects to exactly two other machines, creating a circular network structure. When one host tries to communicate or send message to a host which is not adjacent to it, the data travels through all intermediate hosts. To connect one more host in the existing structure, the administrator may need only one more extra cable.

<!-- IMAGE -->

Failure of any host results in failure of the whole ring.Thus, every connection in the ring is a point of failure. There are methods which employ one more backup ring.

### Advantages of Ring Topology

- It is a truly distributed data processing system.
- It is more decent than the star network.
- If one station fails in the network or a channel between two fails, an alternate routing is possible.

### Disadvantages of Ring Topology

- Communication delay is directly proportional to the multiple nodes in the network.
- It has more complicated control software.

## Mesh Topology

In this type of topology, a host is connected to one or multiple hosts.This topology has hosts in point-to-point connection with every other host or may also have hosts which are in point-to-point connection to few hosts only.

<!-- IMAGE -->

Hosts in Mesh topology also work as relay for other hosts which do not have direct point-to-point links. Mesh technology comes into two types:

- **Full Mesh**: All hosts have a point-to-point connection to every other host in the network. Thus for every new host n(n-1)/2 connections are required. It provides the most reliable network structure among all network topologies. 
- **Partially Mesh**: Not all hosts have point-to-point connection to every other host. Hosts connect to each other in some arbitrarily fashion. This topology exists where we need to provide reliability to some hosts out of all.

### Techniques Used in Mesh Network Topology

- **Mesh Topology Routing Technique** In routing, the nodes have routing logic, as per the network requirements. The routing logic directs the data to reach the destination using the shortest distance, or it informs the broken links so that the network will avoid those nodes. The routing helps to reconfigure the failed nodes.
- **Mesh Topology Flooding Technique** In flooding, the same data is transmitted to all network nodes. Hence, no routing logic is required here. Moreover, in flooding, the network is robust, and it is not interested to lose data, but it leads to unwanted load over the network.

### Advantages of Mesh Topology

- Each and every connection can carry its own data load.
- It is robust.
- Fault is identified easily.
- It provides security and privacy.

### Disadvantages of Mesh Topology

- Installation and configuration is difficult.
- Cabling cost is more.
- Bulk wiring is required.

## Tree Topology

Also known as Hierarchical Topology, this is the most common form of network topology in use presently.This topology imitates as extended Star topology and inherits properties of bus topology.

This topology divides the network in to multiple levels/layers of network. Mainly in LANs, a network is bifurcated into three types of network devices. The lowermost is access-layer where computers are attached. The middle layer is known as distribution layer, which works as mediator between upper layer and lower layer. The highest layer is known as core layer, and is central point of the network, i.e. root of the tree from which all nodes fork.

<!-- IMAGE -->

All neighboring hosts have point-to-point connection between them.Similar to the Bus topology, if the root goes down, then the entire network suffers even.though it is not the single point of failure. Every connection serves as point of failure, failing of which divides the network into unreachable segment.

### Advantages of Tree Topology

- Controlling and control software is very simple.
- A new node at the lowest levels can be inserted very efficiently.

### Disadvantages of Tree Topology

- If the topmost computer fails, it can lead to the failure of the entire network.
- If an intermediate level computer fails, it can cause the loss of its lower level machines from the network.
- If an original node is to be added at higher levels, it is complicated.
- If the levels boost, it can lead to an intricate network.

## Daisy Chain Topology

This topology connects all the hosts in a linear fashion. Similar to Ring topology, all hosts are connected to two hosts only, except the end hosts.Means, if the end hosts in daisy chain are connected then it represents Ring topology.

<!-- IMAGE -->

Each link in daisy chain topology represents single point of failure. Every link failure splits the network into two segments.Every intermediate host works as relay for its immediate hosts.

## Hybrid Topology

A network structure whose design contains more than one topology is said to be hybrid topology. Hybrid topology inherits merits and demerits of all the incorporating topologies.

<!-- IMAGE -->

> The above picture represents an arbitrarily hybrid topology. The combining topologies may contain attributes of Star, Ring, Bus, and Daisy-chain topologies. Most WANs are connected by means of Dual-Ring topology and networks connected to them are mostly Star topology networks. Internet is the best example of largest Hybrid topology.

### Advantages of Hybrid Topology

- It is effective and flexible.
- Troubleshooting is easy.
- Error detecting is reliable.
- It is scalable because the size can be increased easily.

### Disadvantages of Hybrid Topology

- Designing is difficult or complex.
- It is costly.
