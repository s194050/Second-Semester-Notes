### Week 1
1. What is an architectural model of a distributed system?  
		A way of modelling a distributed system. This model focuses on placement of the components and the relation between the different components.
		An example is a P2P system.
		
2.  What is a fundamental model of a distributed system?  
	 Also a way of modelling distributed systems. This model focuses on a more abstract description of the properties that are common in all distributed systems.
	  Systems based on assumptions.
	  
3.  What is the difference between an architectural model and a fundamental model of a distributed system?  
	1. An architectural model is a high-level model of a distributed system that describes the overall structure and components of the system, such as the network topology, communication protocols, and services. A fundamental model of a distributed system is a low-level model that describes the technical details of how the components interact and communication between them. This includes aspects such as message passing, synchronization protocols, deadlock prevention algorithms, and fault tolerance mechanisms.
	 
4. What is a process in a distributed system?  
	A distributed system consists of coupled processes. So a process is a single device/system.
	
5.  What is a communication paradigm?  
	 A defined way for distributed systems to communicate with each other.
	 
6.  Can you name some examples of different communication paradigms?  
	  Two direct communication paradigms are inter-process communication and remote invocation. A indirect communication paradigm is communication through a third party.
	  
7.  What is a client server system?  
	 A client server system is a distributed system requests a reply from a server, before doing anything. So all requests are done through [request -> reply].
	 
8.  What is a P2P system?  
	  The aim of the P2P architecture is to exploit the resources (both data and hardware) in a large number of participating computers for the fulfilment of a given task or activity.
	  This distributed system in practical terms function as each client is a peer and they all run on the same interface, and offer the same set of interfaces to each other. 
	  There is no distinction between client and server processes.
	
9.  What is the main difference between client server systems and P2P systems, in terms of architectural style?  
	 The client server system, utilises a centralised structure, whereas the P2P system is a decentralised system. Each system determines the role of an individual process.
	 
10. What is the difference between synchronous and asynchronous distributed systems?
	  These assumptions are concerned with time. A synchronous system has a strong assumption of time, whereas the asynchronous makes no assumptions of time. Thus their names.
	  
11. Can you describe some design challenges for distributed systems?
	  The following are design challenges: Heterogenity - Variety / differences,  Openness - Possibility of extending, Scalability ETC. All are mentioned in week 1 notes.
	  
12. What is failure model in distributed systems?  
	  The failure model defines the ways in which failures may occur in order to provide an understanding of the effects of failures. All systems should be expected to have failures occur and as such correct planning and handling of failures can help reduce the penalty.
	  
13. Can you name some examples of taxonomy of failures?  
	  System crashes, Omission failures - a process or communication channel fails to perform actions that it is supposed to do. Arbitrary failures, Timing failures - these can only occur in synchronous systems.
	  
14. What is transparency? (similar question for all the other design challenges)
	  Means to hide the complexity of the system, such that it is perceived as a whole.
	  Aim: to make certain aspects of distribution invisible to the application  programmer so that they need only be concerned with the design of their  particular application

### Week 2
1. Describe a simple ACK/NACK Protocol and the corresponding error control mechanism.  
	The sender sends a message to the reciever. If the message is recieved it responds with an ACK - otherwise if the message is corrupted in sends a NACK. This is the error control as it ensures that a corrupted message is resent.

2.  What is Polling protocol?  
	* Alternative strategy to the ACK/NACK protocol is using **Polling**
	* Polling is implemented by making the receiver take the initiative
	* POLL: Request to send data
	* REPT: request to repeat transmission due error in data received

1.  What are PAR protocols?  
	 Protocols with only an ACK and a timeout, are called Positive acknowledge and Retransmission protocols (PAR)
	
4. What is a PAR Protocol with Timeout and Sequence Numbers?  
    A PAR Protocol with Timeout and Sequence Numbers is a reliable data transmission protocol designed to guarantee the delivery of data packets over an unreliable network. It uses a system of sequence numbers and timeouts to ensure that all data packets are delivered in order and without errors. The protocol specifies that when a packet is sent, the sender must include its sequence number, the receiver must acknowledge receipt of the packet, and if the sender does not receive an acknowledgement within a specified timeout period, it must resend the packet. If a duplicate packet is received, it is discarded as invalid.
	
5.  What is Anonymous Acknowledgement Problem in distributed systems?  
	1. All ACK messages are annonymous and as such the sender has no means of knowing exactly which data is referred to when it was received. - Generallised the prbolem is that the cooperating parties do not know what their collective state is

6.  What is a PAR Protocol with Numbered ACK? 
	1. An implementation that solves the Anonymous Acknowledgement problem by using numbers for each data, such that senders and reciever both know the global state

7. What is necessary for Exchange of State Information protocols?  
	1. It is done to establish a reliable exchange. 
	2. 

8. What is a two-way exchange protocol?  
	1.  It is a handshake protocol where, before exchanging data, sender and receiver does a *"handshake"* in which they agree to:
		* Agree to establish connection
		* Agree on connection parameters

9. Describe the working of the three-way handshake protocol.  
	1.  The general scheme is the initiating protocol sends a request message, with a value x
	2. the responder then sends a response message with (x,y)
	3. The initiating entity then responds with (x,y) to show that is has received.

10.  Which error control mechanisms can be used to solve the problem of corrupotion of data  message?  
		Checksum + ACK/NACK + retransmission
	
11. Which error control mechanisms can be used to solve the problem of the deadlock of the  sender (because no ack message)?  
	Timeout solves this issue
	
12.  What is a duplication of output error?  
	1.  The same initial message is sent multiple times, due to one of them being delayed, which in turn results in a floating corps and at some point both messages will be received which is not the intent.

13.  Which error control mechanisms can be used to solve the problem of duplication of output? 
	1. Sequencing numbers.

14.  What is a floating corps error?  
	1. A floating corpse is a message that has been lost for some time.
	* The message is then retransmitted
	* At some point the lost message will arrive and cause confusion

15. Which error control mechanisms can be used to solve the problem of floating corps?  
	1. Sequence numbers in ACK messages

16. What is a sequence number?  
	1. A number that shows which message is sent when in a transmission, fx. the first message is often sequence 0.

17. What is a corruption of data message error?  
	1. Something has happenend to a message during transmission that made it corrupted

18.  What is a deadlock of the sender (because no ack message) error?
	1. A sender is waiting for the response by the recipient, which will never arrive. Thus a deadlock.

### Week 3
1.  What are communication paradigms in distributed systems?  
	1. How do entities communicate, and specifically which communication paradigms do they use.
2.  What is the difference between direct and indirect communication?  
	1. Indirect communication is through a third party / third entity - while direct is either interprocess or remote invocation
3. What is interprocess communication in distributed systems?  
	1.  It is defined in terms of destinations and messages. It is message passing between a pair of processes supported by two communication operations - send and receive.

4. What is message passing and what are the blocking operations in message passing?  
	1.  Message passing is the way messages are transmitted between two process. A blocking operation means that either the sender or receiver is waiting for the other process to respond, before doing anything else, as such it is in fact blocking the whole program.

5. What is a socket?  
	1. A socket is an abstraction that basically means the destination of the message.
	2. What is a socket in distributed systems? A socket is a communications endpoint in a distributed system, which is used for communication between two processes. It provides the mechanism for processes to exchange data and is the basis for most network programming.

6. What is UDP protocol?  
	1. UDP is a connectionless protocol that does not guarantee reliable transmission. In UDP you do not know whether your message arrives or not.
7. What is TCP protocols?  
	1. The opposite of UDP as the TCP protocol is reliable and connection-oriented. You are guaranteed to receive a status message if the message has been received.

8. What is the difference between UDP datagram communication and TCP stream  communication?   
	UDP datagram communication is connectionless, meaning that each message is sent independently of any other messages, without using any handshaking protocols. This makes it less reliable than TCP stream communication, since there is no guarantee that each message will be received. UDP also has shorter packet sizes and lower overhead than TCP, which makes it faster. 

	TCP stream communication is connection oriented, meaning that a connection needs to be established between two hosts before any data can be transmitted. It uses handshaking protocols to ensure reliable transmission of data and also provides flow control and error-checking mechanisms. This makes it more reliable than UDP but slower since the overhead is higher.
	
9. What is multicast?  
	1.  Is a protocol that sends a single message from one process to each of the members of a group of processes.

10. What can multicast be useful for?  
	1. Multicast messages provide a useful infrastructure for construction distributed systems:
		1. Fault tolerance based on replicated services.
		2. Better performance through replicated data.
		3. Propagation of event notifications

 11.  What is a Remote Procedure Call?  
	 1. Allows client programs to call procedures in server programs, that are running in separate processes.

12.  What are Remote Method Invocations in distributed systems?  
	1. It is an extension of local method invocation - It allows an object living in one process to invoke methods of an object living in another process, as an example Java RMI.

13. What are Remote objects?  
	1. Objects that can receive remote invocations.

14. What is remote object reference?  
	1. Other objects can invoke the methods of a remote object if they access to its remote object reference

15. What is remote interface?  
	1. Every remote object has a remote interface that specifies which of its methods can be invoked remotely. Such that only the wanted methods can be accessed.

16. What are the main design choices for implementing Remote Method Invocation?   The main design choices for implementing Remote Method Invocation are:
	1. Retry request messages - whether to retransmit the request message until either a reply is received or the server is assumed to have failed
	2. Duplicate filtering: when retransmissions are used, whether to filter out duplicate requests at the server
	3.  Retransmission of results: whether to keep a history of result messages to enable lost results to be retransmitted without re-executing the operations at the server
	4.  Combination of these choices lead to a variety of possible semantics for the reliability of remote invocations: Maybe, At-least-once, At-most-once

17. What is maybe RMI Semantics and which error control mechanisms are needed to implement such semantics?  
	1.  Maybe semantics ensure that a remote method may be executed once or not at all.  No error control mechanism is used in maybe semantics.

18. What is at-least-once RMI Semantic and which error control mechanisms are needed to  implement such semantics?  
	1. The invoker receiver either a result or an exception. If an exception is received a retransmission is done. The error control mechanism is the possibility for retransmission

19. What is at-most-once RMI Semantic and which error control mechanisms are needed to  implement such semantics?  
	1. The invoker receives either a result or an exception. The error control mechanism is retransmission and duplicate filtering, as it ensures that a message is received at-most-once.  A method is never executed more than once.

20. What is time-coupling and space-coupling in distributed Systems?  
	1. Time-coupling and space-coupled:  Communication directed towards a given receiver or receivers, must exist at that moment in time.
	2. Time-uncoupled / space-uncoupled: Sender does not need to know the identity of the receiver(s); sender(s) and they can have independent lifetimes.

21. What are advantages and disadvantages of indirect communication in distributed systems? 
	1. Scenarios where users connect and disconnect very often. Event dissemination where receivers may be unknown and change often. Scenarios with a large amount of participants.
	2. Performance overhead. Difficult to manage. Difficult to achieve end-to-end properties, such as security and real time behaviour.

22. Can you name some examples of indirect communication?  
	1. Message queue systems. Tuple space. distributed event-based systems. Groups.

23. What is a Tuple Space system?   
	1. A tuple space system is a type of distributed computing platform that uses a shared memory system to coordinate communication between different components of a distributed application. It is based on the concept of tuples, which are containers for information. The shared memory system in the tuple space contains tuples that can be read, written and matched by any process connected to the system. The main purpose of a tuple space system is to facilitate communication and data exchange between distributed processes.
	
24. What is a Public-Subscribe system?
	1. A public-subscribe system, also known as a pub/sub system, is a messaging system that allows users to subscribe to specific topics in order to receive messages from publishers. Publishers send these messages to a message broker, which then delivers the messages to all subscribers who have subscribed to the topic that the publisher is sending. This type of messaging system is often used by applications that require real-time data and notifications.


### Week 4
1. What is a Peer-to-Peer (P2P) system?  
	1. A P2P system is a distributed collection of peer nodes that act both as servers and clients.

2. What are the main differences between Client-Server and P2P systems?  
	1. Clients only talk to servers, and the servers are well connected to the "core" of the internet
	2. Clients talk to other clients. Only nodes located at the "periphery of the internet"

3. What are the characteristics of P2P systems?  
	1. Symmetric
	2. Local Knowledge
	3. Decentralisation
	4. Robustness
	5. High Scalability
	6. Low-cost

4. What is an overlay network?  
	1. An overlay network is a computer network that is built on top of another network. It can be used to provide additional functionality, such as increased security, fault tolerance and scalability. An overlay network can also be used to create virtual private networks (VPNs) for remote access.

5. What are advantages of overlay networks?  
	1. Gives large design flexibility, but comes at the cost of maintenance

6. Can you name some problems of P2P systems?  
	1. Overlay construction and maintenance
	2. Data location
	3. Data dissemination
	4. Per-node state
	5. Tolerance to churn
		1. What is churn in distributed systems?
			1. Churn in distributed systems is the rate at which nodes are joining and leaving the network. It is an important metric that helps to measure the health of a distributed system. Churn can be caused by a variety of factors, including hardware or software failures, environmental conditions, or user actions. Monitoring churn can help detect problems in a distributed system and help identify potential solutions to improve its stability and performance.

7. What are the characteristics of centralized overlays?  
	1.  Systems all in one Placement
	* Information is centralised
	* Not extensible
	* Single point of failure
	* Easy to shut down

8. What are the characteristics of hierarchical overlays?  
	1.  Chain of authority
	* Cache consistency
	* Add more leaves, rebalance
	* Root is vulnerable
	* Just shut down the root

9.  What are the characteristics of decentralized overlays?  
	1.  Difficult, many owners
	* Difficult, unreliable peers
	* Anyone can join
	* Redundancy
	* Difficult to shut down

10. What is the difference between centralized and decentralized overlays? 
	1. Centralized overlays are centralized systems that provide a single point of contact for all users and use one or more central servers to manage user interactions. This type of overlay is useful for applications that require a single point of control, but can be vulnerable to single points of failure. 
	2. Decentralized overlays are distributed systems that provide multiple points of contact for users, allowing them to interact with each other without relying on a single server. This type of overlay is useful for applications that require multiple independent nodes and can offer increased scalability and robustness.

11.  What is the difference between searching and addressing networks?  
	1. Addressing network
	* Find by addressing them with their unique name etc. URLs
	2. Searching networks
	* Find objects by searching with keywords that match the objects description etc. Google

12. What is the difference between structured and unstructured P2P overlay networks?  
	* Unstructured
		* Based on searching
	* Structured
		* Based on addressing

13. What is the lookup problem in P2P systems?  
	1. Node A wants to store a data item D.
	2. Node B wants to retrieve D without prior knowledge of D's current location
	3. How should the distributed system, especially data placement and retrieval, be organized (in particular, with regard to scalability and efficiency)?

14. What are the strategies for data retrieval in distributed systems?  
	1. Central servers
	2. Flooding
	3. Distributed indexing (Distributed Hash Tables)
	4. Superpeers
	5. Loosely structure overlays.

15. What are the advantages and disadvantages of data retrieval approaches in P2P systems with a central server?  
	1. Advantages:
		* Search complexity of O(1)
		* Fuzzy and complex queries Possible
	* Disadvantages
		* The central server is a critical element in regards to scalability and availability
		* Single point of failure
		* Memory consumption is O(N)

16. What is flooding search in P2P systems?  
	1. In a peer-to-peer (P2P) network, flooding search is used to find a file or data stored on another computer in the network. It involves sending out copies of a query packet to every node in the network until the desired information is found. The query packet typically includes information about the type of file being sought, as well as optional criteria such as size, name, and other attributes. Every node that receives the query packet then performs a search of its own local storage for matching files. If any are found, it will send back a response packet with details about those files. This process continues until all nodes in the network have received and responded to the query or until no more matches can be found.
		* Search results are **NOT** guaranteed, flooding stopped by TTL

17. What are the advantages and disadvantages of flooding search approach for data retrieval in P2P systems?  
	1. Pros: Simplicty, no topology constraints, storage cost is O(1)
	2. Cons: Does not scale well, high network overhead, complexity of looking up and retrieving data is O(N<sup>2</sup>)

18. What are Distributed Hash Tables (DHT)?  
	1. Distributed Hash Table (DHT) is a type of peer-to-peer (P2P) computing that uses a distributed hash table to store and retrieve data from a set of participating nodes. The network is structured such that each node stores a subset of the data, and can forward requests to other nodes to find the rest. This makes it possible for the network to maintain high availability, even if individual nodes are unreliable or go offline. DHTs are used for distributed storage, distributed caching, and content distribution.

19. How to design a DHT? 
	1. Distribute hash buckets to nodes - Key -> hash bucket -> node
		1. Step 1: From keys and nodes to IDs (from same ID space)
		2. Step 2: Partition the ID space (so that each node stores some *k, v* pairs)
		3. Step 3: Build overlay network
		4. Step 4: Routing algorithm (route puts/gets through the overlay)

20. What are the advantages and disadvantages of DHT?  
	* Pros:
		* Completely decentralised
		* Routing algorithm achieves low hop count O(log n)
		* Storage cost per nod: O(log n)
		* If a data item is stored in the system, the DHT guarantees that it is found
	* Cons: 
		* Objects are tracked by unreliable nodes
		* Keywword-based searches
		* The overlay must be structured according to a given topology
		* Routing tables must be updated every time a node joins or leaves

21. What is the role of superpeers in P2P systems?  
	1. Two-level overlay:  Superpeers are used to track the locations of an object.
		1. Each node connects to a superpeer and advertises the list of objects it stores
		2. Search requests are sent to the supernode - which forwards them to to other supernodes.

22. What are loosely structured overlays? 
	1. Loosely structured networks are computer networks that are not based on any formal network structure. Instead, they rely on a decentralized approach to networking, allowing multiple nodes to connect with each other in an ad-hoc fashion. This type of network is often used in peer-to-peer applications and wireless networks. Loosely structured networks do not require a central server or controller and do not necessarily have any predefined roles for nodes or links. Instead, the nodes are free to establish connections in whatever way they choose. This makes them highly resilient and able to quickly adapt to changes in the environment, but also somewhat unpredictable and difficult to manage.

23. What are the advantages and disadvantages of loosely structured overlays?  
	1. Advantages
		1. No topology constraints - flat architecture
		2. Searches are more efficient than with plain flooding
	2. Disadvantages
		1. Does not support keyword-based searches
		2. Search requests have a TTL
		3. Does not guarantee a low number of hops, nor that the object in fact will be found

24. What are the properties of Gnutella protocol? 
	1. Gnutella is a protocol for peer-to-peer search, consisting of:
			‣ A set of message formats
			 ✓ 5 basic message types
			‣ A set of rules governing the exchange of messages
				✓ Broadcast
				✓ Back-propagate
				✓ Handshaking
			‣ An hostcache for node bootstrap

25. What are the four most common overlay topologies?  
	1. Centralised, Hierarchical, Decentralised, Hybrid

26. What advantages and disadvantages does a flat unstructured network topology  have?  
	1. Advantages: 
			• Flat unstructured network topology is easy to expand and modify. 
			• It is cost effective as no additional hardware is required. 
			• All computers on the network are equal, so everyone can access information quickly. 
	2. Disadvantages: 
			• Data transfer speeds are slow because of the lack of structure. 
			• There is no central control, which can lead to security issues. 
			• Troubleshooting is difficult as there is no hierarchy or organization to the network.

27. What advantages and disadvantages does a two-level unstructured network  topology have?  
	1. Advantages: 
			• A two-level unstructured network topology is easy to set up and requires minimal maintenance. 
			• It is also flexible and can easily accommodate new nodes. 
			• Its decentralized nature makes it resistant to failure. 
	2. Disadvantages: 
			• Due to its decentralized nature, the two-level unstructured network topology is less efficient than more structured networks, as it requires more messages to be sent in order to complete tasks. 
			• It also has a limited scalability, as the number of nodes increases, the network can become overloaded. Additionally, it is more vulnerable to security threats due to its distributed nature.

28. What advantages and disadvantages does a flat structured network topology have?  
	1. Allows for efficient data location
	2. These constraints result in a long join and leave procedures


29. What information do we store in each DHT node?  
	1.  a pair (k, v) is stored at the node n such that (examples):
			 *  its identifier ID(n) is the closest to ID(k);
			 *  its identifier ID(n) is the largest node id smaller than ID(k)

30.  How do we perform routing in an overlay network of DHT nodes?  
	1. Recursive routing: initiator starts the process, contacted nodes forward the message
	2. Iterative routing: initiator personally contact the nodes at each routing step

31.  What methods can we use to account for failures in an overlay network of DHT nodes?  
	1. Acknowledge each hop (recursive routing)
	2. Resend through a different neighbour

32. Which lookup methods support fuzzy queries?  
	1. Central server
	2. Flooding search

33. How large is the node state and the communication overhead when using a central  server?  
	1. Node state: O(N)
	2. Communication overhead: O(1)

34. How large is the node state and the communication overhead for a flooding search?
	1. Node state: O(1)
	2. Communication overhead: $\geq O(N^2)$  

35. How large is the node state and the communication overhead when using a DHT?
	1. Node state: $O(\log(N))$ 
	2. Communication overhead: $O(\log(N))$ 