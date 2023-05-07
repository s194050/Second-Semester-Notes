### Week 1 - Intro
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

### Week 2 - Protocols
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

### Week 3 - RMI
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


### Week 4 - P2P
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

### Week 5 - Logical Time
1) What is the causality relation?  
	1) Causality is linked to temporal ordering
	* if e<sub>i</sub> causes e<sub>j</sub>, then e<sub>i</sub> must happen before e<sub>j</sub>
2) Why might two (remote) processes capturing the same event sequence break the causality relation?  
	1) Because you would be unable to know which happened before, and as such there can be no ordering
3) What is logical time? 
	1)  Every process has a logical clock that is advanced with a set of rules. Every event is assigned a timestamp, which obey the fundamental monotonicity property. This ensures that there is casuality between events.
4) Define and explain Lamport's happened-before relation. 
	1) Lamport's notation of causal ordering
		* HB1: if If ∃ process pi : e ➝ i e’, then e ➝ e'
		* HB2: For any message m, send(m) ➝ receive(m)
		* HB3: If e, e’, e’’ are events such that e ➝ e’ and e’ ➝ e’’ then e ➝ e’’
	* Lamport's notation helps ensure causality as it is a way of ordering events.

5) In what sense concurrency is different than parallelism?
	1) Concurrent events, are events sharing data and as such execution order changes output/input, where as parallelism is events that have no shared data and as such the order does not matter.
	2) In what sense concurrency is different than parallelism?
		1) Concurrency is the ability of a system to execute multiple tasks simultaneously, while parallelism is the ability of a system to execute multiple tasks at the same time. Concurrency and parallelism are both used to improve performance, but they are different. Concurrency is about dealing with and managing multiple tasks in a single processor, while parallelism is about running multiple processors simultaneously in order to increase performance.
6) What does it mean when two events are concurrent? 
	1) They are executed at about the same time, but the order is unknown until after execution.
7) What is a logical clock? 
	1) A monotonically increasing software counter, which associates a value in an ordered domain with each event in a system.
8) State the clock consistency property of logical clocks.  
	1) The clock consistency property states that if two events (e.g., message transmissions) are causally related (i.e., one event occurs before the other), then the logical clock values associated with the two events must be in the correct order (i.e., the logical clock value associated with the earlier event must be smaller than that of the later event).
	2) 
10) What are the rules that define a Lamport logical clock? 
	1) Logical Clock rules:
	* e -> e' => L(e) < L(e')
	* CR1: If ∃ process p<sub>i</sub> such that e ➝<sub>i</sub> e’, then L<sub>i</sub> (e) < L<sub>i</sub> (e’)
	* CR2: If a is the sending of a message by p<sub>i</sub> and b is the receipt of the same message by p<sub>j</sub> , then L<sub>i</sub>(a) < L<sub>j</sub>(b)
	* CR3: If e, e’, e’’ are 3 events : L(e) < L(e’) and L(e’) < L(e’’) then L(e) < L(e’’)
11) Name one significant problem of Lamport clocks.  
	1) Lamport clocks describes global time by a single number, which is not enough and "hides" essential information
	2) This results in possible missed causality, or wrong.
12) What is a vector clock?  
	1) Overcome the shortcomings of the Lamport clock
	* Lamport: e -> f *then* L(e) < L(f) - Clock consistency
	* Vector: e -> f *iff* V(e) < V(f) - Strong consistency
		* A vector clock for a system of N processes, is an array of N integers.
		* Each process p<sub>i</sub> keeps it own vector clock V<sub>i</sub> which it uses to timestamp local events
13) What are the implementation rules of a vector clock?  
	1) Implementation rules:
	* VC1: Initially, V<sub>i</sub>[ j ] := 0, for i, j = 1, 2, ...., N
	* VC2: Just before p<sub>i</sub> timestamps an event, it sets V<sub>i</sub>[ i ] := V<sub>i</sub>[ i ] + 1
	* VC3: p<sub>i</sub> includes the value t = V<sub>i</sub> in every message that pi sends
	* VC4: When p<sub>i</sub> receives a timestamp t in a message  
		- p<sub>i</sub> sets V<sub>i</sub>[ j ] := max(V<sub>i</sub>[ j ], t[ j ]) for j = 1, 2, ...., N  
		- applies VC2  
		- timestamp the event receive(m)
14) State the consistency property of vector clocks.  
	1) $e \rightarrow f \iff V(e)< V(f)$ 
15) Why vector clocks are necessary? 
	1) They are needed to capture the correct causality of the events occuring.
16) What are the key differences between Lamport clocks and vector clocks? 
	1)  Instead of using a single clock, vector clocks uses a vector for each process and such the causality of each is captured correctly.
17) Explain how ordering on a vector clock works.  
	1) $V \leq V' \iff V[j] \leq V'[j]\; for \; j=1,2,...,N$ 
18) Name the drawbacks of vector clocks  
	1) They have a very large message overhead as it grows linearly with the number of processes in the system.
19) What is Singhal-Kshemkalyani’s Differential Technique? 
	1) An algorithm that implements efficient vector clocks.
20) What kind of optimizations does the S-K technique introduce?  
	1) When a process p<sub>i</sub> sends a msg to a process p<sub>j</sub> it piggybacks only those entries of its vector clock that differ since the last message sent to p<sub>j</sub>
21) How to cut down the storage overhead in S-K technique?
	1) Add to additional vectors that keep track of Last updated and Last sent, such that only the necessary clock values are updated during a transmission


### Week 6 - Global States
1) What is a global state?  
	1)  They are described by two things:
		* The states of participating processes together with - the states of the channels between these processes
		* Can be described by a tuple:
		* $S = <p_1,p_2,c_{12},c_{21}>$ 
2) How can we describe the global state of a distributed system?  
	1) By using the distributed snapshot algorithm
3) What are the components of an event?  
	1) Each event is described by $e = <p,s,s',M,C>$  
	2) process p goes from state s to s', M is the message sent on channel C
4) When is an event possible?  
	1) ![[Pasted image 20230506124426.png|400]]
5) What is a possible computation?  
	1) A possible computation of the system is a sequence of possible events, starting from the initial global state of the system
6) Which assumptions do we rely on for distributed snapshot algorithms?
	1) ‣ Channels are ERROR-FREE and SEQUENCE PRESERVING (FIFO)
	2) ‣ Channels deliver transmitted msgs after UNKNOWN BUT FINITE DELAY
	3)  The only events in the system which can give rise to changes in the state are communicating events
7) What is a consistent cut?  
	1) A consistent global state is defined by:
		* A state after a certain amount of events happened (H)
		* GS(H) = The state of each process p<sub>i</sub> after p<sub>i</sub> ’s last event in H for each channel, the sequence of msgs sent in H but not received  in H
		* Also known as a **"CUT"** 
8) What is the difference between a consistent global picture and consistent global state?  
	1) The global picture, represents a view of the system from an external view
	2) The global state is an acurate representation of the systems global state
9) What is a marker?  
	1) A specific control message used to construct a CUT
10) Describe Chandy and Lamport's algorithm  
	1) It records its own state, and then sends a marker on each channel connected to the process. If a process receives a marker and its own state is not recorded, do the SEND MARKERS procedure. Else records the state of the channel and does nothing.
11) When does Chandy and Lamport's algorithm terminate?  
	1) The algorithm terminates after each process has received a marker on all of its incoming channels
12) What is the complexity of this algorithm (in messages)?  
	1) O(e) messages, where e is the number of edges
13) What is the time complexity of this algorithm?  
	1) O(d) time, where d is the diameter of the network. (the longest of all the shortest paths in a network)
14) Give two policies for turning local snapshots into a global snapshot  
	1) In a practical implementation, the recorded local snapshots must be put together to create a global snapshot of the distributed system
		1)  each process sends its local snapshot to the initiator of the algorithm
		2) each process sends the information it records along all outgoing channels and each process receiving such information for the first time propagates it along its outgoing channels
15) Does Chandy and Lamport's algorithm guarantee a global snapshot of a state that occured  during the system's execution? Why (not)?  
	1) No as we cannot determine what the true sequence of events are
		1)  When we record a process’ state, we are unable to know whether the events which we have already seen in this process lay before or after incomparable events in other processes
16) Describe the difference between pre- and post-recording events.
	1) pre recording: events in a computation which take place BEFORE the process in which they occur records its own state	
	2) post recording:  all other events
	3) The algorithm finds a global state which corresponds to a PERMUTATION of the actual order of the events, such that all pre-recording events come before all post-recording events
17) What is a stable property?  
	1) a property that persists, such as termination or deadlock
18) What is a stable predicate?  
	1) A way of evaluating a system, on whether it will ever reach deadlock or termination etc., as they are always true, if true at any point
	2) a stable predicate is a condition that holds true over an extended period, despite the possibility of failures and message delays that may occur in the system.
19) What is a consistent run?  
	1) * A **run** of a computation is a total ordering **R** that includes all the events in the global history and that is consistent with each local history  
		*  In other words, the events of p<sub>i</sub> appear in **R** in the same order in which they appear in 
		  h<sub>i</sub>  
		*  A run corresponds to the notion that events in a distributed computation actually occur in a total order  
		*  A distributed computation may correspond to many runs  
		*  A run **R** is said to be <u>consistent</u> if for all events e and e’, e ➝ e’ implies that e appears before e’ in   **R**  
		* A consistent run allows for the leads to relation:
20) What is the relationship between a consistent run and consistent global states?  
	1) A consistent run results in a sequence of consistent global states
21) What is a non-stable predicate?  
	1) The condition encoded by the predicate may not persist long enough for it to be true when the predicate is evaluated
	2) If a predicate Φ is found to be true, we do not know whether Φ ever held during the actual run
22) How can we evaluate non-stable predicates?  
	1) • Evaluating a non-stable predicate over a single computation makes no sense
	2) Means that it can be true in some global states, but false in others
		* Evaluating a non-stable predicate over a single computation makes no sense  
		* The evaluation must be extended to the entire lattice of the computation 
		* It is possible to evaluate a predicate over an entire computation using an observation obtained by a passive monitor 
23) What is an observation?  
	1) ![[Pasted image 20230506130826.png|500]]
24) Name some differences between observations and runs  
	1) In summary, a run refers to a specific execution of the system, while an observation refers to the act of measuring or recording some aspect of the system's behavior during that run. 
25) How can we know if a non-stable predicate possibly occurred?  
	1) There exists a consistent observation O of the computation such that Φ holds in a global state of O. This can otherwise be implemented by the algorithm
26) How can we know if a non-stable predicate definitely occurred?  
	1) For every consistent observation O of the computation, there exists a global state of O in which Φ holds. This can otherwise be implemented by the algorithm
27) What are issues faced in recording a global state?  
	1)  First and foremost are the assumptions that we require to record a global state.
		1) We require it to be FIFO
		2) Message delays are finite
		3) Channels are error free
	2) In the real world it is nigh impossible to guarentee the above
	3) Scalability is also a real problem, as the information recorded increases exponentially
28) Describe the main assumptions needed with regards to consistent global states?  
	1) ![[Pasted image 20230506131736.png]]
29) Does the Chandy-Lamport global snapshot algorithm works correctly for non-FIFO  channels?  
	1) It will not work correctly for non-FIFO channels.
	2) This is due to non-FIFO allows for messages to be delivered out of order, which means there is no causality in the eyes of the algorithm, and as such it cannot determine a consistent global state
30) Can a distributed system have a unique global state at all times? Why (not)?  
	1) It is not always possible for a distributed system to have a unique global state at all times. This is because distributed systems are subject to various types of faults and failures, such as node failures, network partitions, message loss, and message delays, which can lead to inconsistencies in the system's state.
	2) However, with the correct assumption it would be possible
31) What is the difference between a consistent cut and a consistent global state?
	1) A consistent cut delimits the global state, as it represents a consistent picture of the global state of the system


### Week 7 - mutex
1) What are the two failure assumptions we typically make when discussing mutual exclusion?
	1) Each pair of processes is connected by reliable channels
	2) No process failure implies a threat to the other processes' ability to communicate
2) Why is mutual exclusion necessary in a distributed system that needs coordinated behavior?
	1) If a collection of processes share a resource (or collection of resources), then mutual exclusion is required to prevent interference and ensure consistency when accessing the resources
3) What makes mutual exclusion a more difficult problem in distributed systems than in the operating systems domain?
	1)  Critical section is more complex in distributed systems
	* Because of no shared variables, etc. semaphores nor facilities supplied by a single kernel.
4) Describe the distributed systems mutual exclusion model
	1) * enter() - enter a CS
	* resourceAccess() - access shared resource in CS
	* exit() - leave the CS
5) What are the three properties of a mutual exclusion algorithm? Describe each of these.
	1)  [ME1] Safety: at most one process can execute in the CS at a time  
	* [ME2] Liveness: requests to enter and exit the CS eventually succeed  
		* Implies freedom from both deadlock and starvation
		* The absense of starvation  is a fairness condition
	*  [ME3] Ordering: if one request to enter the CS happened-before another, then entry to the CS is granted in that order
		* Happend before ordering of CS requests may imply liveness
6) Which one of these properties is absolutely required?
	1) Safety is absolutely necessary - known as the correctness property
7) What is a deadlock?
	1) two or more processes becoming stuck indefinitely while attempting to enter or exit the critical section, by virtue of their mutual interdependence
8) What is starvation?
	1) a poor algorithm might lead to starvation: the indefinite postponement of entry for a process that has requested it
9) What are some performance criteria for mutual exclusion algorithms?
	1)  The bandwidth consumed, which is proportional to the number of messages sent in each entry and exit operation
	 2) The client delay incurred by a process at each entry and exit operation
	 3)  Throughput of the system: the rate at which the collection of processes as a whole can access the CS, given that some communication is necessary between successive processes
10) Name the three basic approaches for mutual exclusion in distributed systems.
	1) Token based approaches
	2) Non-token based approaches
	3) Quorum based approaches
11) Describe the token-based approach
	1) * A unique token is shared among the processes
	* A process is allowed to enter its CS if it posseses the tokens. When done it passes it on
	* MUTEX is ensured because the <u>token is unique</u>
12) Describe the Central Server algorithm. Which properties does it satisfy?
	1) One such approach is the Central server algorithm
	* Performance: 
		* Entering, it takes 2 messages a request followed by a grant
		* it delays the requesting process by the time for this round-trip
		* Exiting: takes 1 message, known as release. Assuming asynchronous message passing it will not delay exiting the process
	* Weakness is that it is centralised (The server is the bottleneck)
	* ME1 and ME2
13) What happens in the Central Server algorithm when a message gets lost or a process crashes?
	1)  None of the algorithms would tolerate the loss of messages, if the channels were unreliable
	2)  It can tolerate the crash failure of a client process that neither holds nor has requested the token
14) What is one weakness of the Central Server Algorithm?
	1) Weakness is that it is centralised (The server is the bottleneck)
15) Describe the Ring-based algorithm. Which properties does it satisfy?
	1) Basic idea: exclusion is conferred by obtaining a token in the form of a message from process to process in a single direction around the ring.
	* Each process p<sub>i</sub> has a communication channel to the next process in the ring p<sub>(i+1)mod N</sub> 
	* ME1 and ME2
16) What happens in the Ring-based algorithm when a message gets lost or a process crashes?
         3) It cannot tolerate a crash failure of any single process
         4) None of the algorithms would tolerate the loss of messages, if the channels were unreliable
17) What is one weakness of the Ring-based algorithm?
	1) Weakness is special topology/structure
18) Describe Lamport's algorithm. Which properties does it satisfy?
	1) An apporach is Lamport's algorithm
	* Requires communication channels to deliver in FIFO order
	* Based on Lamport's logical clocks
	* The idea: the algorithm executes CS requests in the increasing order of timestamps
		* Timestamp = (clock value, id of the process)
	* A total ordering => requires the further rule:
		* CR4: a (in p<sub>i</sub>) => b (in p<sub>i</sub>) if and only if either L<sub>i</sub>(a) < L<sub>j</sub> (b) or L<sub>i</sub>(a) = L<sub>j</sub>(b) ∧ p<sub>i</sub> ≺ p<sub>j</sub> 
	* It satisfies ME1, ME2, and ME3
19) What is one weakness of Lamport's algorithm?
	1) Weakness is the FIFO channels
20) Describe Ricart and Agrawala's algorithm. Which properties does it satisfy?
	1) Ricart and Agrawala's idea
	* Does not require communication channels to be FIFO
	* The basic idea is:
		* processes that require entry to a CS multicast a request message  
		* processes can enter the CS only when all the other processes have replied to this message  
		* node p<sub>j</sub> does not need to send a REPLY to node p<sub>i</sub> if p<sub>j</sub> has a request with  timestamp lower than the request of pi (since pi cannot enter before p<sub>j</sub> anyway in this case)
21) What is one weakness of Ricart and Agrawala's algorithm?
	1) Weakness is the requirement of participation from all processes
22) Can we make Ricart and Agrawala's algorithm crash fault-tolerant?
	1)  By implementing consensus
	2) can be adapted to tolerate the crash failure of such a process, by taking it to grant all requests implicitly
23) What is a quorum-based approach?
	1) Each process requests permission to execute the CS from a subset of processes (Quorum)
	* The quorums are formed in such a way that when two processes concurrently request access to the CS
	* at least one process receives both the requests
	* this process is responsible to make sure that only one request executes the CS at any time
24) What is a Quorum?
	1) A subset of processes
25) Explain the concepts behind quorum-based mutual exclusion algorithms.
	1)  To enter a critical sections, a processes requires validation from all the processes in its assigned quroum. This ensures that only one process accesses a CS at any time
26) What is the intersection property and why is it necessary?
	1) There needs to be an intersection between Quorums, otherwise they would not be able to agree on anything, as it would be as if the were seperate
27) Which conditions do quorums in Maekawa's algorithm satisfy?
	1) ![[Pasted image 20230506135056.png|400]]
28) Is Maekawa's algorithm crash fault-tolerant?
	1) can tolerate some process crash failures: if a crashed process is not in a voting set that is required, then its failure will not a ect the other processes

### Week 8 - multicast
1) What is the difference between sending one message, multicast, and broadcast?
	1) A message is to a single process
	2) Whereas a multicast is communication to all processes in the system
	3) The broadcast is communication to a sub-group of them
2) What is the difference between an open and a closed group, w.r.t. multi-casting?
	1) In an open group, processes outside the group may send to it
	2) In the closed group only members of the group can multicast to it. If any process outside tries to multicast to the closed group it is reflected to itself
3) Which properties should a reliable 1-to-1 channel satisfy?
	1)  Validity: if a correct process multicasts message *m*, then every correct process eventually delivers *m*
	* No duplication: a correct process *p* delivers a message *m* at most once
	* No creation: if a correct process *p* delivers a message *m* with sender *s*,  then *m* was previously multicast by process *s*
	*  Validity is a liveness property
	 * No duplication and No creation are safety properties
	*  No duplication + No creation = integrity property
4) Describe the system model we use for multicast communication
	1) Process may fail only by crashing
	2) Processes are members of groups, which are the destination of multicast messages
	3) Communication primitives:
			‣ multicast(g, m): sends a message m to all members of the group g
			‣ deliver(m): delivers a message sent by multicast to the calling process
5) What extra elements do we add to messages?
	1) ‣ the unique identifier of the process sender(m) that sent it
		 ‣ the unique destination group identifier group(m)
6) What are the differences (in properties) between a basic reliable multi-cast channel and a reliable 1-to-1 channel?
	1)  Multicast
		1) No Creation [B-multicast]: if a correct process p delivers a message m with sender s, then m was previously multicast by process s
		2) No Duplication [B-multicast]: a correct process p delivers a message m at most once
		3) Validity [B-multicast]: if a correct process multicasts message m, then every correct process eventually delivers m
	2) 1-to-1 reliable 
		1)  No Creation [reliable channel]: if some process q delivers a message m with sender p, then m was previously sent to q by process p
		2) No Duplication [reliable channel]: no message is delivered by a process more than once
		3) the validity property of the communication channels: if a correct process p sends a message m to a correct process q, then q eventually delivers m
7) What does it mean when we say a basic multicast algorithm is correct?
	1) Correctness is defined by satisfying: Validity, no duplication and no creation predicates
	2) As basic multicast satisfies these it is a 'correct' algorithm
8) What is the ack-implosion problem?
	1) The acknowledgements sent as part of the reliable send operation are liable to arrive from many processes at about the same time
	2)  The multicasting process’s buffer will rapidly fill and it is liable to drop acknowledgments
	3) It will therefore retransmit the msg, leading to yet more acks and further waste of network bandwidth
10) Describe the specification differences between basic multicast and reliable multicast.
	1)  By adding a further property known as:
	2)  Agreement: if a correct process delivers message m, then all the other correct processes in group(m) will eventually deliver m
	3) It results in, where for B-multicast that insures Validity -> Liveness for the sender, that Reliable Multicast Validity + Agreement -> Liveness for the system
11) How does R-multicast work?
	1)  First, the process B-multicasts the message to processes in its own group, including it self.
	2)  When this message is B-delivered, the recipient in turn B-multicasts the message to the group (if not the original sender).
	3) Then it R-delivers the message
	4)  Since a message may arrive more than once, duplicates are not delivered
12) What sort of failure scenarios does R-multicast help against?
	1)  A faulty sender, as if the sender crashes after sending the message, the target will still be reached.
13) What is the atomicity property?
	1)  If a process that multicasts a message R-multicast crashes before is has delivered it, than it it is possible that the message will not be delivered to any process in the group R-deliver
	2)  But if it is delivered to some correct process, then all the other correct processes will deliver it
14) Is the R-multicast algorithm efficient?
	1) No, as it has a large overhead in bigger systems, due to the amount of messages sent
15) Name three common ordering requirements for messages
	1) FIFO, Causal and Total ordering
16) What kind of components are useful for implementing FIFO ordering?
	1)  Sequence numbers, which denotes the order
17) Which assumptions do we make to make our ordering algorithms work?
	1)  Non-overlapping groups 
18) What kind of components are useful for implementing causal ordering?
	1)  Vector timestamps: the entries count the number of multicast messages from each process that happened-before the next message to be multicast
19) Which question are we trying to solve when implementing total ordering? Name two possible approaches to this problem.
	1)  What determines the ordering. 
	2) It can be solved by either using the Sequencer, or the Distributed Agreement
20) What is the difference between the liveness criteria for sender and system?
	1) Liveness for the sender only depends on Validity, while Liveness for the system requires Validity and Agreement
21) Explain each property of a correct basic multicast.
		1) No Creation [B-multicast]: if a correct process p delivers a message m with sender s, then m was previously multicast by process s
		2) No Duplication [B-multicast]: a correct process p delivers a message m at most once
		3) Validity [B-multicast]: if a correct process multicasts message m, then every correct process eventually delivers m
22) Which properties are ’safety’ properties of a correct basic multicast?
	1) No Duplication and No Creation
23) Which properties are ’liveness’ properties of a correct basic multicast?
	1) Validity
### Week 9 - Elections and consensus
1) What is an election algorithm?
	1) An algorithm for choosing a unique process to play a particular role
	2)  ![[Pasted image 20230330134057.png|400]]
2) What are process roles and election calls in distributed elections?
	1)  At any point in time, a process is either a participant(It is engaged in some run of the algo) or a non-participant
	2)  A process calls the election if it takes an action that initiates a particular run of the election algorithm
3) What is an important requirement for the choice of elected process?
	1) The choice of elected process must be unique, even if several processes call elections concurrently
5) What are the requirements during any particular run of the election algorithm?
	1) E1 (safety): A participant process pi has elected_i = ⊥ or elected_i = P where P is chosen as the non-crashed process at the end of the run with the largest identifier
	2) E2 (liveness): All processes pi participate and eventually set elected_i ≠ ⊥ -or crash
6) What is the performance of an election algorithm (network bandwidth and turnaround time)?
	1) its total network bandwidth utilization (proportional to the total number of messages sent)
	2) the turnaround time: the number of serialized message transmission times between the initiation and termination of a single round
7) What are the goals and properties of a ring-based election algorithm?
	1) elect a single process, called the coordinator, which is the process with the largest identifier
8) Describe election in a ring-based election algorithm.
	1)  Every process is marked as a non-participant
		1) Any process can begin an election by:
			‣ marking itself as a participant,
			‣ placing its identifier in an election message
			‣ sending it to its clockwise neighbour
9) Describe notification in a ring-based election algorithm.
	1)  When the coordinator receives the elected message, it once again marks it self as a non-participants. Then it sends an elected message, to the neighbour and lets it know that it was the original sender.
	2)  Each process receives an elected message, which makes it mark itself as a non-participant, which is done until the elected message reaches the newly elected process.
10) What is the performance of a ring-based election algorithm?
	1) Total number of messages is $N-1$
	2) The turnaround time for this algorithm is $3N-1$ 
11) What are the limitations of the ring-based algorithm?
	1) it tolerates no failures makes it of limited practical value
	2) However, with a reliable failure detector it is in principle possible to reconstitute the ring when a process crashes
12) What is a failure detector?
	1) service that processes queries about whether a particular process has failed
13) What are the categories of failure detectors?
	1) Unreliable and reliable
14) What is an unreliable failure detector?
	1) May produce one of two values when given the identity of a process
		* Unsuspected or suspected
	* Both of these are hints, which may not accurately reflect whether the process has actually failed
	* ![[Pasted image 20230330140741.png|400]]
15) What is a reliable failure detector?
	1)  Always accurate in detecting a process's failure
	* It always processes' queries with either a Unsuspected(Hint) or Failed
		* Failed means that the detector has determined that the process has crashed
	* It requires that the system is synchronous to work
16) What are the goals and properties of the bully algorithm?
	1) It allows processes to crash during an election
	* It assumes that message delivery is reliable
	* It also assumes that the system is synchronous
17) What are the types of messages in the bully algorithm?
	1) Election: sent to announce an election
	2) answer: sent in response to an election message
	3) coordinator: sent to announce the identity of the elected process(new coordinator)
18) Describe the bully algorithm.
	1) The process that knows it has the highest identifier can elect itself as the coordinator simply by sending a coordinator message to all processes
	2) A process with a lower identifier begins an election by sending en election message to those processes that have a higher identifier
	3) ![[Pasted image 20230506154831.png|400]]
	4) If a process receives a coordinator message from a process with a lower identifier, it immediately initiates a new election. This is how the algorithm gets its name: a process with a higher identifier will bully a lower identifier process out of the coordinator position as soon as it comes online.
19) What is the performance of the bully algorithm?
	1) The best case:
		* Sends N-2 coordinator messages
		* The turnaround time is 1
	* Worst case
		* N-1 messages
		* Turnaround is approx. 5 messages
			* election, answer, election, answer, coordinator
20) Describe the system model of consensus.
	1) Collection of processes pi (i = 1, 2, ..., N)
	2) Processes communicate by message passing
	3) Communication is reliable
	4)  Processes can fail: byzantine (arbitrary) process failures, crash failures
21) Explain the definition of the consensus problem.
	1) Informally: the processes propose values and have to agree on one among these values
	* Formally:
		* ![[Pasted image 20230330143737.png|400]]
22) What are the requirements of a consensus algorithm?
	1) Termination: eventually each correct process sets its decision variables
	2)  Agreement: the decision value of all correct processes is the same
			 IF
			 pi and pj are correct and have entered the decided state
			 THEN di = dj (i, j = 1, 2, ..., N)
	 3) Integrity: if the correct processes all proposed the same value, then any correct process in the decided state has chosen that value 
23) Describe an algorithm to solve consensus in a synchronous system.
	1) ![[Pasted image 20230506155236.png]]
24) What is the Byzantine generals problem?
	1) Three or more generals must agree to attack or retreat
		‣ One general, the commander, issues the order
		‣ Other generals, the lieutenants, must decide to attack or retreat
	2) One or more generals may be treacherous:
		‣ If the commander is treacherous, he proposes attacking to one general and retreating to another
		‣ If the lieutenant is treacherous, he tells one of his peers that the commander told him to attack and another that they are to retreat
25) What is the difference of the Byzantine generals problem from consensus?
	1) Difference from consensus: a single process supplies a value that the others are to agree upon (instead of each of them proposing a value)
26) What are the requirements for the Byzantine generals problem?
	1) Termination: eventually each correct process sets its decision variables
	2) Agreement: the decision value of all correct processes is the same
	3) Integrity: if the commander is correct, then all correct processes decide on the value that the commander proposed
27) What is the interactive consistency problem?
	1) Every process proposes a single value
	2) Goal: correct processes agree on a vector of values (decision vector), one for each process
		‣ Example: each of a set of processes want to obtain the same information about their respective states
28) What are the requirements for interactive consistency?
	1) Termination: eventually each correct process sets its decision vector
	2) Agreement: the decision vector of all correct processes is the same
	3) Integrity: if pi is correct, then all correct processes decide on vi as the ith component of their vector
29) How to construct a solution to the Interactive Consistency problem from the Byzantine Generals problem?
	1) ![[Pasted image 20230506155700.png]]
30) How to construct a solution to the Consensus problem from the Interactive Consistency problem?
	1) ![[Pasted image 20230506155709.png]]
31) Briefly describe how to prove safety and liveness in a ring-based election algorithm.
	1) ![[Pasted image 20230506155743.png]]
	2) ![[Pasted image 20230506155800.png]]
32) What are adaptive timeouts and what benefit do they have?
	1)  Reflecting the observed network delay conditions
	2) if a local failure detector receives a “p is here” in 20 secs instead of the expected maximum of 10 secs, then it could reset its timeout value or p accordingly
	3) The failure detector remains unreliable (only hints!), but the probability of its accuracy increases
33) What requirement does a system need to use reliable failure detectors?
	1) The system has to be synchronous
34) Briefly describe how the consensus problem can be solved in the absence of failures.
	1) ![[Pasted image 20230506155947.png]]
35) Briefly describe how the consensus problem can be solved in the presence of crash failures.
	1) ![[Pasted image 20230506160006.png]]
36) Give a lower bound on the number of rounds required to reach a consensus in the presence of failures.
	1) Any algorithm to reach consensus despite up to f crash failures requires at least f + 1 rounds of message exchanges, no matter how it is constructed.
37) Relate the number of processes and failures to describe impossibility of the Byzantine Generals problem in a synchronous system.
	1)  no solution of the BG problem is possible if the total number of processes (N) is less than three times the number of failures (f), i.e., N ≤ 3f
38) Describe consensus impossibility in asynchronous systems.
	1) no algorithm can guarantee to reach consensus in an asynchronous system, even with one process crash failure
	2) Thus we immediately know from this result that there is no guaranteed solution in an asynchronous system to the BG and IC problems
	3) This impossibility is circumvented by masking faults or using failure detectors

### Week 10 - Cyber security
1) How do you define the security of a system?  
	1)  Preserving the C.I.A
	* Confidentiality
	* Integrity
	* Availability
2) What is Confidentiality?  
	1) The avoidance of the unauthorized disclosure of information
3) What is Integrity?  
	1) The property that information has not be altered in an unauthorized way
4) What is Availability?  
	1) The property that information and systems are accessible and usable in a timely fashion by those authorized to do so
5) Can you name some tools for Confidentiality?  
	1) Encryption, access control, Authentication, physical security
6) What is Access Control?  
	1) Rules and policies that limit access to con dential information to those people and/or systems with a “need to know”
7) What is Authentication?  
	1) The determination of the identity that someone has
		1) Can be done by something the person has, knows or is
8) What is Physical Security?  
	1) The establishment of physical barriers to limit access to protected computational resources
9) Can you name some tools for Integrity?  
	1) Backups, checksums, data correcting codes
10) Can you name some tools for Availability?  
	1) Physical protection, countermeasures against system overload, countermeasures against system crashing
11) What is Assurance?  
	1) Refers to how trust is provided and managed
12) Can you name some tools for Assurance?  
	1) Tools: Policies, Permissions, Protections
13) What is Authenticity?  
	1)  The ability to determine that statements, policies and permissions issued by persons or systems are genuine/authentic
		* Can be seen as authentication + integrity
14) What is Anonymity?  
	1) The property that certain records or transactions not to be attributable to any individual
15) Can you describe some examples of attacks?  
	1) Eavesdropping, Man in the middle, Denial of service, repudiation
16) What are Encryption and Decryption?  
	1)  Encryption is by encrypting a message, that makes it unreadable by anyone without the correct key.
	2) Decryption is using the correct key to read an encrypted message
17) What are Cryptographic Hash Functions?  
	1) Encryption of data, that by used for validating if a message is correct
18) Describe what is a digital signature and which properties satisfy.  
	1)  Digital signature, is a way of authenticate who the message is from, based on some public key.
	2)  Authentication and Integrity
19) What is a Public Key Infrastructure (PKI)?  
	1) A public key infrastructure (PKI) provides all the components necessary for different types of users and entities to be able to communicate securely and in a predictable manner
20) What is the difference between a Registration Authority (RA) and Certificate Authority (CA)?  
	1) RA:
		1) A registration authority (RA) is the PKI component that accepts a request for a digital certificate and performs the necessary steps of registering and authenticating the person requesting the certificate
	2) CA:
		1) A certificate authority (CA) is trusted authority that certificates individuals’ identities and creates electronic documents (digital certificate) indicating that individuals are who they say they are
21) What is a digital certificate?  
	1) A digital certificate establishes an association between the subject’s identity and a public key
	2) A digital certificate binds an entity’s identity to a public key
22) What are the steps for Obtaining a Digital Certificate?  
	1) ![[Pasted image 20230507135812.png]]
23) What is a simple classification of Authentication Protocols?  
	1)  Classified based on the cryptographic technique used:
		1) Symmetric cryptography uses a single private key to both encrypt and decrypt data
		2)  Asymmetric cryptography (a.k.a public-key cryptography) uses a secret key (private key) and a public key
24) Describe a basic authentication protocol.
	1) ![[Pasted image 20230507135923.png]]
### Week 11 - Remote Attestation
1) Can you name 3 reasons why IoT devices are prone to many cyberattacks?
	1)  Easy to exploit
	2) Attractive target
	3) Amplify the attack impact
2) What is Remote Attestation?
	1) Two-party: Security protocol
	2) Verifier: an external trusted entity, not always present, not possible to physically reach a device
	3)  Prover: a (potentially) compromised device
	4) RA allows the Verifier to guarantee the authentication and integrity of the software running on Prover
	5) Verify that Prover is NOW running the initial application
	6) In short it can be seen as a Malware detection technique:
3) What are the main categories of Remote Attestation approaches?
	1) Hardware design
	2) Memory
	3)  Number of devices
	4) Network topology
	5) Communication data
4) What are the advantanges and disadvantages of software-based Remote Attestation protocols?
	1) Advantage: No hardware requirements
	2) Limitations:
			● Verifier must know exact hardware configuration
			● Difficult to prove time optimality
			● Assumes “adversarial silence” during attestation
			● Limited to “one-hop” networks
5) What is the difference between software-based and hybrid Remote Attestation protocols?
	1)  Hybrid requires hardware
6) Describe execution of a hybrid Remote Attestation protocol.
	1) 1. Challenge N
	2)  Measure the software state and hash it
	3) Send an authenticated response, including N and the hash h
	4) The verifier now checks if the message is what it is supposed to be
7) What is the goal of swarm attestation?
	1) Verify the internal state of a large group of devices
	2) Should be more efficient than attesting each node individually
8) Describe SEDA protocol (swarm attestation).
	1) Algorithm logic:
		1. Verifier selects random Prover (P0) initializes attestation
		2. Spanning tree is created rooted at P0
		3. Each Prover (device) gets attested by its parent (leaves first)
		4. Sub-tree roots accumulate results and reports to their parent
		5. P0 reports overall result to Verifier
9) What is the goal of dynamic attestation protocols?
	1) Program Memory Attestation schemes do not address runtime attacks
10) Describe C-FLAT protocol (dynamic attestation).
	1) Proposes a complete attestation of the run-time state of the Prover
	2) A single hash value that represents the entire control flow of the Prover’s state
	3) Treat loops as sub-graphs and report their hash values and # of iterations separately
	4) Advantages
			• Better dection level: Detects runtime attacks
	5) Disadvantages
			• The protocols rely on customized hardware support
			• The computations are not efficient
11) What is the main advantage of Distributed Services attestation?
	1) Verifies both trustworthiness of the devices and legitimate operations
12) Describe SARA protocol (Attestation of asynchronous distributed IoT services).
	1) ![[Pasted image 20230506164145.png]]
13) What are the potential implications of not implementing remote attestation in critical infrastructure IoT devices?
	1)  They are vulnerable to attacks, and as such cannot be relied upon
14) Can remote attestation be used to ensure the integrity of data transmitted by IoT devices?
	1)  Yes, as the whole idea to verify, that they are trustworthy
15) How can remote attestation be used to verify the identity of IoT devices and prevent spoofing attacks?
	1) By using a TPM module
16) What are the key components of a hardware-based remote attestation system for IoT devices?
	1) A TPM module?
17) How can fog computing facilitate the implementation of remote attestation in large networks?
	1) Overall, fog computing can provide a powerful platform for implementing remote attestation in large networks. By leveraging the distributed and decentralized nature of fog computing, organizations can build secure and scalable systems for authenticating IoT devices and ensuring the integrity and authenticity of the data they transmit.
### Week 12 - Blockchain
1) What is the first blockchain based cryptocurrency?
	1) Bitcoin
2) Which 3 building block make up blockchain technology?
	1) 
		* Cryptography (Hashfunctions, digital signatures)
		* Data structure (Hash pointers, Blockchain)
		* Decentralisation(P2P Network, consensus algorithm)
3) Describe the idea behind hash functions and cryptographic hash functions.
	1) Takes data and hashes it into fixed-length hash.
	2) A hash function is a cryptographic hash function if it is:
		1) Collision resistant
		2) Preimage resistant
		3) Second preimage resistant
4) Name at least 2 security properties of a cryptographic hash function
	1) 1) Collision resistant
		2) Preimage resistant
		3) Second preimage resistant
5) What do we mean with collision resistance?
	1) That it should be night impossible to generate the same hash, from different data
6) What do we mean with preimage resistance?
	1) Given the hash value, it should be impossible to find the original data
7) What do we mean with second preimage resistance?
	1)   Given the data, it should be impossible to find other data that gives the same hash
8) What are hashes used for?
	1) A safe way to store information, be it passwords or data for comparing in security
9) What is a hash pointer?
	1) ‣ a pointer to where some information is stored AND
		‣ a cryptographic hash of the information
10) What is a blockchain?
	1)  A linked list that is build with hash pointers instead of pointers
11) What is the key property of tamper-evident log structures?
	1) IF SOMEBODY ALTERS DATA THAT IS EARLIER IN THE LOG, WE DETECT IT
12) What is a digital signature?
	1)  Digital signature: digital analog to a handwritten signature on paper
	    Meant for authenticity (authentication + integrity): the ability to determine that statements, policies, and permissions issued by persons or systems are genuine/authentic
13) What are the two key properties of digital signatures?
	1)  only you can sign with a private key, but anyone who sees the signature can verify that it’s valid through your public key
	2)  signature is tied to a particular document
		1) They cannot be cut and pasted to another document
14) Explain what a bitcoin address is, in terms of standard cryptographic techniques.
	1) An address is a public key.
15) Explain the basic idea behind spending coins in a typical cryptocurrency
	1)  By making a new statement, that has a hash pointer to the coin, and who the person it is being sent to is, which is an public key. By signing with your own public key, you have now spend the coin
16) What is double-spending?
	1)  Multiple signed statements of the same coin
17) How do blockchain technologies try to prevent double spending?
	1)  By consuming coins, such that they are destroyed
18) Name some aspects of decentralization
	1) Peer to peer network
	2) Mining
19) What is a distributed consensus protocol?
	1) ![[Pasted image 20230506170544.png]]
20) What do nodes in a cryptocurrency have to reach consensus on?
	1)  They must agree on which transactions were broadcast, and in which order these transactions happend
21) Describe the basic idea behind the bitcoin consensus algorithm (simplified).
	1) ![[Pasted image 20230506170758.png]]
22) Describe the steps that happen (in rough lines) when a Bitcoin transaction is made.
	1)  A request for an transaction is sent to the P2P network
	2)  It then has to validate the transaction.
	3)  When it is verified it is combined with other transactions to create a new block of data
	4)  This block is then added to the existing blockchain
23) Is double spending technically possible in Bitcoin? Why (not)?
	1) In theory it is possible
	2) Honest nodes follow the policy of extending the longest valid branch, so which branch will they extend? There is no right answer! At this point, the two branches are the same length — they only differ in the last block and both of these blocks are valid.
	    The node that chooses the next block then may decide to build upon either one of them, and this choice will largely determine whether or not the double‐spend succeeds
24) How does Bitcoin prevent branching out into multiple chains?
	1)  It selects by consensus the longest chain
25) Name some distributed consensus models.
	1) Proof of Work 
	2) Proof of Stake
	3) Delegated PoS
26) Name some differences between permissionless and permissioned blockchains
	1)  permissionless
		1)  Participation open to the public
		2)  Peer-to-peer transactions
		3)  Typically tied to cryptocurrency
		4) Fully decentralized (in principle...)
			1) Challenges:
			2) Privacy, security, scaling, control, complexity, 
	2) permissioned
		1)  Participation can be private and/or controlled
		2) Trusted participants
		3) More efficient than many public blockchains
		4) Can support privacy and confidentiality in transaction
		5) Challenges:
			1) Some level of centralized trust through governing authority
27) What is a 51% attack?
	1) Modification of a blockchain
	2)  A single entity controls more than 50% of the networks computing power
		1) With this control it can allow the attack to modify the blockchain
28) Is a 51% attack technically possible in Bitcoin? Why (not)?
	1) Yes it is technically possible, but it requires a huge amount of computing power, which currently is not possible
29) Name some advantages and disadvantages of blockchain technology.
	1) Advantages:
		1) Decentralisation
		2) Transparency
		3) security
		4) Efficiency
	2) Disadvantages
		1) Scalability
		2) Regulation
		3) Energy consumption
		4) Complexity