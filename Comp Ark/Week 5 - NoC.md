* Everything is multi-core and using NoC-based interconnect
	* CMP - Chip multi-processors
	* MPSoC - Multi-processor Systems-on-chip
* "Cores" communicating through a packet switches NoC

* Two types of NoCs
	* Most networks are best-effort (BE) NoCs
		* Packets travelling in BE is similar to car travel on roads
		* Generally low latency but can be high during congestion
		* Work conserving
		* HW implementation: Typically relatively large
	* Alternative is guaranteed-service (GS) NoCs, typically using virtual circuit switching
		* Packets travelling in GS, are similar to train travel
		* Schedule determines bandwidth A->B, and can avoid run-time arbitration
		* Not work conserving
		* HW implementation: Typically small
* Best way to communicate theoretically in modern Networking on SoCs is Globally Asynchronous and locally synchronous.

* Motivations for NoCs
	* Technology:
		* Long wires -> repeaters
		* Register as repeater -> pipelined wire
		* Adding X-Y switching -> Pipelined mesh; i.e a NoC
			* ![[Pasted image 20230228133959.png]]
	* Design methodology:
		* Systematic and structure approach to communication in a SoC
		* Reuse and modularity
		* Plug-and-play design based on: IP blocks, Std. interfaces like OCP.
* What does mesochronous mean?
	* Mesochronous describes a timing mechanism in which the speed of an event is determined by its position in the sequence. It is commonly used to describe the timing of different electronic devices and components that must synchronize with one another in order to function properly.

* NoC terminology
	* Network components:
		* Network interfaces (NI)
		*  Routers
		* Links
	*  Packet (header+payload, packet = no. of flits, flit = no. of phits)
	* Network topology
		* Mesh, Torus, Bi-torus, Tree, Fat-tree, Ring, hierarchical structures, ...
	* Routing
		* Which path/route to follow (deterministic/adaptive, minimal/non-minimal, ...)
		*  Store-and-forward / cut-through (wormhole) / virtual cut-through
		* Dimension order routing (arithmetic) / Source routing / Table driven routing / 
	*  Switching strategy
		*  Circuit switching (end-to-end connection, possibly “virtual”) 
		*  Packet switching 
	* Flow control
		*  Packet level (NI –NI)
		*  Flit level (R – R) 

* How is a packet routed through a NoC
	* Source routing
		* Packet header contains route
		* Routers just execute switching
	* Distributed routing
		* Packet header contains destination node id.
		* Routers make decisions
			* I.e static
			* Dynamic/adaptive
			* Dimension order routing
			* Deflection / "hot potato"
* Deadlocks are an big issue and needs to be avoided.
	* Done by avoid cycles.
		* and assume packets are consumed at destination
	* Virtual channels are also a solution for avoiding deadlocks
		* What is a virtual channel in a NoC? 
			* In a Network-on-Chip (NoC), a virtual channel (VC) is a logical data path that enables the transfer of data between two nodes on the network. Each node is assigned its own VC, which can be used to send and receive data simultaneously. Virtual channels provide a higher level of abstraction than physical channels, allowing for more efficient communication between nodes. They also allow for better control over data flow, providing Quality of Service (QoS) guarantees for specific types of traffic.
		* Prevents a stalled packet from blocking the link and thereby other packets
		* Implemented using:
			* Arbitration in merge.
			* Cred based flow control.
* What is a Flit in a NoC?
	* A flit is the basic unit of data transmission in a Network-on-Chip (NoC). It is analogous to a packet in a traditional computer network. A flit contains the necessary header information, such as the destination address, required to route the data along its path. The flit can also contain payload data and an optional checksum for error detection.
* What is credits in a NoC?
	* Credits in a NoC are virtual tokens that are used to track the flow of data packets. Each packet contains a credit, and when the receiving node receives it, the credit is removed and the packet is processed. This way, the NoC can monitor and control the flow of data packets and ensure that packets are not dropped due to overcrowding.
* What is a phit in a NoC?
	* A phit (packet header information type) is a data structure used to store the routing information of a packet in a Network-on-Chip (NoC). The phit is typically stored in the packet header and contains information such as the source and destination node, virtual channel ID, priority, flow control flags, etc. It is used for routing the packet through the NoC and ensuring that it reaches its intended destination.
* What is a crossbar in a NoC?
	* A crossbar in a Network-on-Chip (NoC) is a network switch that connects multiple endpoints within the NoC. It functions like an electrical switchboard and provides communication between several components within the chip. The crossbar can be used to route data or control signals from one component to another, as well as providing arbitration between multiple requests for access to the same resource.