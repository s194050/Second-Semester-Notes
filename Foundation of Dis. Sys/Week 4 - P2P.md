### Introduction
* A P2P System is a distributed collection of peer nodes, in which they act as clients and servers
* Servers are well connected to the core of the internet - Clients only talk to servers
* Nodes are only located at the periphery of the internet - Clients talk to other clients
* P2P is symmetric - no distinction between nodes
* P2P is decentralised where the opposite is valid for Client-server

* P2P
	* Highly available
	* Fault-tolerant
	* Self-organizing
	* Scalable
	* Difficult to shut down
* P2P networks are usually overlay networks
	* What is an overlay network  	
		An overlay network is a computer network that is built on top of another network. It can be used to provide additional functionality, such as increased security, fault tolerance and scalability. An overlay network can also be used to create virtual private networks (VPNs) for remote access.
	* Overlay requires maintenance
		* Done by periodically ping to make sure others are alive
		* If a neighbour is down, establish a new edge
	* Gives large design flexibility, but comes at the cost of maintenance
* P2P Systems needs to allow it to churn

### Topologies

* Evaluating Topologies
	* Manageability
	* Information Coherence
	* Extensibility
	* Fault tolerance
	* Censorship

* Centralised
	* Systems all in one Placement
	* Information is centralised
	* Not extensible
	* Single point of failure
	* Easy to shut down
* Hierarchical
	* Chain of authority
	* Cache consistency
	* Add more leaves, rebalance
	* Root is vulnerable
	* Just shut down the root
* Decentralised
	* Difficult, many owners
	* Difficult, unreliable peers
	* Anyone can join
	* Redundancy
	* Difficult to shut down
* Hybrid - Centralised + Decentralised
	* Same as decentralised
	* Better than decentralised
	* Anyone can join
	* Redundancy
	* Difficult to shut down

* Searching VS Addressing
	* Two basic ways to find objects
		* Search for them
		* Address them using there *unique name*
	* Difference between them are Fundamental
		* Determines how the network is constructed
		* determines how the objects are placed
		* determines efficiency of object location
* Addressing network
	* Find by addressing them with their unique name etc. URLs
* Searching networks
	* Find objects by searching with keywords that match the objects description etc. Google

* Unstructured vs Structured P2P
	* Unstructured
		* Based on searching
	* Structured
		* Based on addressing

* Common Topologies
	* Flat unstructured
		A flat unstructured topology is a network topology in which all nodes are connected to each other without any hierarchy or structure. All nodes have an equal connection to each other, and there is no central node. This type of network structure is typically used for small networks that require minimal complexity and low cost.
	* Two-level unstructured 
		Two-level unstructured topology is a type of computer network topology in which each node is connected to two other nodes, creating a mesh of interconnected nodes arranged in two levels. The nodes at each level are connected to each other in an unstructured manner, with no particular pattern or organization. This type of network is typically used for small networks, such as home networks or small business networks, as it offers the advantage of flexibility and scalability.
	* Flat structured
		A flat structured topology is a network topology where all nodes are connected directly to a single central switch or hub. In this type of topology, each node is connected to the same level and each node is able to communicate with any other node on the network without having to pass through any other nodes. This type of topology is cost-effective and easy to setup, however it can be prone to performance issues if too many nodes are connected.

### Data Location
Data lookup solutions - Data retrieving and sending
* Central server
	* Advantages:
		* Search complexity of O(1)
		* Fuzzy and complex queries Possible
	* Disadvantages
		* The central server is a critical element in regards to scalability and availability
		* Single point of failure
		* Memory consumption is O(N)
* Flooding search in P2P  		
	In a peer-to-peer (P2P) network, flooding search is used to find a file or data stored on another computer in the network. It involves sending out copies of a query packet to every node in the network until the desired information is found. The query packet typically includes information about the type of file being sought, as well as optional criteria such as size, name, and other attributes. Every node that receives the query packet then performs a search of its own local storage for matching files. If any are found, it will send back a response packet with details about those files. This process continues until all nodes in the network have received and responded to the query or until no more matches can be found.
	* Search results are **NOT** guaranteed, flooding stopped by TTL
	* Pros: Simplicty, no topology constraints, storage cost is O(1)
	* Cons: Does not scale well, high network overhead, complexity of looking up and retrieving data is O(N<sup>2</sup>)

* Definition of TTL in P2P 
	(Time To Live) is a setting in P2P networks that limits the number of "hops" (or intermediate nodes) a message can pass through before it is discarded. It is used to prevent messages from endlessly circulating around the network and consuming resources.


* Distributed indexing - Distributed hash tables
	* Increases scalability O(log n)
	* Fast for lookups O(1)
	* Distributed Hash Table
		Distributed Hash Table (DHT) is a type of peer-to-peer (P2P) computing that uses a distributed hash table to store and retrieve data from a set of participating nodes. The network is structured such that each node stores a subset of the data, and can forward requests to other nodes to find the rest. This makes it possible for the network to maintain high availability, even if individual nodes are unreliable or go offline. DHTs are used for distributed storage, distributed caching, and content distribution.
	* Nodes form an overlay network
	* Functionality of the DHT's are described in the slides

* Pros:
	* Completely decentralised
	* Routing algorithm achives low hop count O(log n)
	* Storage cost per nod: O(log n)
	* If a data item is stored in the system, the DHT guarantees that it is found
* Cons: 
	* Objects are tracked by unreliable nodes
	* Keywword-based searches
	* The overlay must be structured according to a given topology
	* Routing tables must be updated every time a node joins or leaves

### Superpeers

* Two-level overlay
	* Highly Scalable
	* Disadvantages: superpeers must be reliable, powerful and well connected to the internet
		* Superpeers must maintain large State
		* The system relies on a small number of superpeers

### Loosely Structure Overlays

* Loosely structured networks 
	* Loosely structured networks are computer networks that are not based on any formal network structure. Instead, they rely on a decentralized approach to networking, allowing multiple nodes to connect with each other in an ad-hoc fashion. This type of network is often used in peer-to-peer applications and wireless networks. Loosely structured networks do not require a central server or controller and do not necessarily have any predefined roles for nodes or links. Instead, the nodes are free to establish connections in whatever way they choose. This makes them highly resilient and able to quickly adapt to changes in the environment, but also somewhat unpredictable and difficult to manage.