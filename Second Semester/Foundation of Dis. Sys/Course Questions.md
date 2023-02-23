### Week 1
1. What is an architectural model of a distributed system?  
		A way of modelling a distributed system. This model focuses on placement of the components and the relation between the different components.
		An example is a P2P system.
		
2.  What is a fundamental model of a distributed system?  
	 Also a way of modelling distributed systems. This model focuses on a more abstract description of the properties that are common in all distributed systems.
	  Systems based on assumptions.
	  
3.  What is the difference between an architectural model and a fundamental model of a distributed system?  
	 
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
(1) Describe a simple ACK/NACK Protocol and the corresponding error control mechanism.  
(2) What is Polling protocol?  
(3) What are PAR protocols?  
(4) What is a PAR Protocol with Timeout and Sequence Numbers?  
(5) What is Anonymous Acknowledgement Problem in distributed systems?  
(6) What is a PAR Protocol with Numbered ACK?  
(7) Why are necessary the protocols for Exchange of State Information?  
(8) What is a two-way exchange protocol?  
(9) Describe the working of the three-way handshake protocol.  
(10) Which error control mechanisms can be used to solve the problem of corrupotion of data  
message?  
(11) Which error control mechanisms can be used to solve the problem of the deadlock of the  
sender (because no ack message)?  
(12) What is a duplication of output error?  
(13) Which error control mechanisms can be used to solve the problem of duplication of output?  
(14) What is a floating corps error?  
(15) Which error control mechanisms can be used to solve the problem of floating corps?  
(16) What is a sequence number?  
(17) What is a corruption of data message error?  
(18) What is a deadlock of the sender (because no ack message) error?

### Week 3
(1) What are communication paradigms in distributed systems?  
(2) What is the difference between direct and indirect communication?  
(3) What is interprocess communication in distributed systems?  
(4) What is message passing and what are the blocking operations in message passing?  
(5) What is a socket?  
(6) What is UDP protocol?  
(7) What is TCP protocols?  
(8) What is the difference between UDP datagram communication and TCP stream  
communication?  
(9) What is multicast?  
(10) What can multicast be useful for?  
(11) What is a Remote Procedure Call?  
(12) What are Remote Method Invocations in distributed systems?  
(13) What are Remote objects?  
(14) What is remote object reference?  
(15) What is remote interface?  
(16) What are the main design choices for implementing Remote Method Invocation?  
(17) What is maybe RMI Semantics and which error control mechanisms are needed to  
implement such semantics?  
(18) What is at-least-once RMI Semantic and which error control mechanisms are needed to  
implement such semantics?  
(19) What is at-most-once RMI Semantic and which error control mechanisms are needed to  
implement such semantics?  
(20) What is time-coupling and space-coupling in distributed Systems?  
(21) What are advantages and disadvantages of indirect communication in distributed systems?  
(22) Can you name some examples of indirect communication?  
(23) What is a Tuple Space system?  
(24) What is a Public-Subscribe system?


### Week 4
(1) What is a Peer-to-Peer (P2P) system?  
(2) What are the main differences between Client-Server and P2P systems?  
(3) What are the characteristics of P2P systems?  
(4) What is an overlay network?  
(5) What are advantages of overlay networks?  
(6) Can you name some problems of P2P systems?  
(7) What are the characteristics of centralized overlays?  
(8) What are the characteristics of hierarchical overlays?  
(9) What are the characteristics of decentralized overlays?  
(10) What is the difference between centralized and decentralized overlays?  
(11) What is the difference between searching and addressing networks?  
(12) What is the difference between structured and unstructured P2P overlay networks?  
(13) What is the lookup problem in P2P systems?  
(14) What are the strategies for data retrieval in distributed systems?  
(15) What are the advantages and disadvantages of data retrieval approaches in P2P systems  
with a central server?  
(16) What is flooding search in P2P systems?  
(17) What are the advantages and disadvantages of flooding search approach for data retrieval  
in P2P systems?  
(18) What are Distributed Hash Tables (DHT)?  
(19) How to design a DHT?  
(20) What are the advantages and disadvantages of DHT?  
(21) What is the role of superpeers in P2P systems?  
(22) What are loosely structured overlays?  
(23) What are the advantages and disadvantages of loosely structured overlays?  
(24) What are the properties of Gnutella protocol?  
(25) What are the four most common overlay topologies?  
(26) What advantages and disadvantages does a flat unstructured network topology  
have?  
(27) What advantages and disadvantages does a two-level unstructured network  
topology have?  
(28) What advantages and disadvantages does a flat structured network topology have?  
(29) What information do we store in each DHT node?  
(30) How do we perform routing in an overlay network of DHT nodes?  
(31) What methods can we use to account for failures in an overlay network of DHT  
nodes?  
(32) Which lookup methods support fuzzy queries?  
(33) How large is the node state and the communication overhead when using a central  
server?  
(34) How large is the node state and the communication overhead for a flooding search?
(35) How large is the node state and the communication overhead when using a DHT?