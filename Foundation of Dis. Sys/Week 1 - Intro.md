## Introduction
* Distributed system can be centralised.
* Pervasive Computing (Ubiquitous)
	   Pervasive computing (also known as ubiquitous computing) is a form of technology that is always present and connected, allowing users to access data and services from any device in any location. It relies on a wide-reaching network of sensors, computers, and other devices to provide a seamless experience for users. Examples of pervasive computing include the internet of things (IoT), smart homes, wearables, and automated systems.

# Models

* Architectural model is the structure of the system
	* Etc. Placement of components
* Fundamental models is the properties
	* Fx. Failure of an algorithm

#### Architectural Model
1. Communicating entities
   * System perspective
	   * Processes
	   * Distributed systems are coupled processes
	   * There is no single entities, depends on the abstraction
   * Programming perspective
	   * Web services, multi agent systems, etc.
2. Communication Paradigms.
	* How to communicate in distributed system
	* Inter-process communication
	* Remote invocation
	* Both of the above are direct communication
	* Indirect communication - Through third parties
3. Roles and Responsibilities
	* Client-server - Request -> reply
		* A process can both be a client and a server
		* Web servers and most Internet services are a clients of the DNS service 
	* Peer-to-peer (P2P)
		* The aim of the P2P architecture is to exploit the resources (both data and hardware) in a large number of participating computers for the fulfilment of a given task or activity
4. Placement
	* Physical mapping
		* No clear solutions exists
		* Depends on design choices
	* It is most optimal to have the application locally opposed to stored on a server

### Interaction Model
* Based on assumptions
* When process/entities interact we cannot determine the rate which it will proceed
* Timing cannot in general be predicted
* No single notion of time (No Global Clock!)
	* Each computer in a distributed system has its own internal clock
* Two extreme posistions
	* Synchronous distributed systems
		* Strong assumption of time
	* Asynchronous distributed systems
		* No assumption of time

### Design Challenges
* Heterogenity - Variety / differences
	* Ex. IoT
* Openness - Possibility of extending
	* Ex. API
* Scalability
	* Can a system handle increased scale?
* Security
	* MIRAI DDoS attack  	
		MiraI DDoS (Distributed Denial of Service) attack is a type of cyber attack that uses a network of infected computers, known as bots, to overwhelm the target with traffic or requests for information. The goal of this type of attack is to make a website or online service unavailable by flooding it with requests for data or disrupting its web server. It can be used to target websites, networks, applications, and other online services.
 * Failure Handling
	 * Failure of entities
	 * Failure of channels
	 * Different classes of failure
		 * Crash, Omission, Send-omission, Receive-omission
 * Transparency
	 * Means to hide the complexity of the system, such that it is perceived as a whole
Impossible to focus and satisfy all of the above points.
### Case study - Design of a client-server system
* Thin client 
	* All processing is done server side, only presentation is done client-side
	* Ex. Online Internet Banking
* Thick client
	* Application processing on the client-side
	* Ex. ATM Banking System
* Hybrid client - a blend between the above two points
	* 