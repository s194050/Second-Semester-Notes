### Introduction
* Causality is linked to temporal ordering
	* if e<sub>i</sub> causes e<sub>j</sub>, then e<sub>i</sub> must happen before e<sub>j</sub>
* Each computer has its own internal (physical) clock
* Even if two processes read their clocks at the same time, their local clocks may supply different time values.
	* Happens because of clock drift from perfect time
	* Drift rates differ from one another
* If clocks are not perfectly synchronised the causality between events might not be entirely captured.

* The concept of causality is fundamental to the design and analysis of parallel and distributed computing.
* Usually it is tracked using physical time - However this is not possible in distributed systems as it is impossible to have a global physical time

### Clock and Events

* To conserve event ordering, a solution might be logical time.
	* What is logical time in distributed systems? 
		* Logical time in distributed systems is a way of establishing order among events that occur across multiple nodes or computers in a distributed system. Logical clocks provide a total ordering of events, making them useful for maintaining consistency in distributed systems. Logical clocks allow processes to assign timestamps to incoming messages, and use those timestamps to determine the order of events.
	* Every process has a logical clock
	* Every even is assigned a timestamp
	* Timestamps obey the fundamental monotonicity property.
		* What is fundamental monotonicity property? 	
			The fundamental monotonicity property states that if a function is monotonic, then any of its superlevel sets (sets containing all points with values greater than or equal to a given value) are convex. This means that if a function is increasing, then all of its superlevel sets are convex. Likewise, if the function is decreasing, then all of its sublevel sets (sets containing all points with values less than or equal to a given value) are convex.

* **Happened-Before Relation** (->)
	* Lamport's notation of causal ordering
		* HB1: if If ∃ process pi : e ➝ i e’, then e ➝ e'
		* HB2: For any message m, send(m) ➝ receive(m)
		* HB3: If e, e’, e’’ are events such that e ➝ e’ and e’ ➝ e’’ then e ➝ e’’
	* -> is **IRREFLEXIVE PARTIAL ORDERING** on the set of all events in the distributed system
		* Irreflexive: $\lnot(a\rightarrow a)$  
			* What does irreflexive mean? 
				* Irreflexive means that an element cannot relate to itself. This can be seen in a relation or graph, where there are no self-loops.
		* Partial ordering: Not all events can be related by ->
		* ![[Pasted image 20230302133612.png]]
			* a and e is not orderered by ->. They are however concurrent (a || e)

### Logical (Lamport Clocks)
* Logical clock: A monotonically increasing software counter, which associates a value in an ordered domain with each event in a system.
* Definition:
	* ![[Pasted image 20230302133945.png]]
* Logical Clock rules:
	* e -> e' => L(e) < L(e')
	* CR1: If ∃ process p<sub>i</sub> such that e ➝<sub>i</sub> e’, then L<sub>i</sub> (e) < L<sub>i</sub> (e’)
	* CR2: If a is the sending of a message by p<sub>i</sub> and b is the receipt of the same message by p<sub>j</sub> , then L<sub>i</sub>(a) < L<sub>j</sub>(b)
	* CR3: If e, e’, e’’ are 3 events : L(e) < L(e’) and L(e’) < L(e’’) then L(e) < L(e’’)
* To capture the -> relation numerically: processes update their logical clocks and transmit the values of their logical clocks in messages as follows:
	* LC1: L<sub>i</sub> is incremented before each event is issued at process p<sub>i</sub> : L<sub>i</sub> := L<sub>i</sub>+ 1
	* LC2: (a) When p<sub>i</sub> sends a msg m, it piggybacks on m the value t = L<sub>i</sub>  
		(b) On receiving (m, t), a process p<sub>j</sub> 
				- computes L<sub>j</sub> := max(L<sub>j</sub>, t)  
				- applies LC1  
				- timestamp the event receive(m)
* Clocks that follow the above rules are known as **Lamport Logical Clocks**

* Shortcoming of the Lamport Clocks:
	* ![[Pasted image 20230302141121.png]] 
	* Causal ordering of messages is not captured.
* Problem:
	* Lamport clocks describes global time by a single number, which is not enough and "hides" essential information
* Solution: Vector clocks

### Vector Clocks
* Overcome the shortcomings of the Lamport clock
	* Lamport: e -> f *then* L(e) < L(f) - Clock consistency
	* Vector: e -> f *iff* V(e) < V(f) - Strong consistency
* A vector clock for a system of N processes, is an array of N integers.
* Each process p<sub>i</sub> keeps it own vector clock V<sub>i</sub> which it uses to timestamp local events
	* ![[Pasted image 20230302141646.png]] 
* V<sub>i</sub>[j] describes p<sub>i</sub> 's knowledge of p<sub>j</sub>'s logical clock

* Implementation rules:
	* VC1: Initially, V<sub>i</sub>[ j ] := 0, for i, j = 1, 2, ...., N
	* VC2: Just before p<sub>i</sub> timestamps an event, it sets V<sub>i</sub>[ i ] := V<sub>i</sub>[ i ] + 1
	* VC3: p<sub>i</sub> includes the value t = V<sub>i</sub> in every message that pi sends
	* VC4: When p<sub>i</sub> receives a timestamp t in a message  
		- p<sub>i</sub> sets V<sub>i</sub>[ j ] := max(V<sub>i</sub>[ j ], t[ j ]) for j = 1, 2, ...., N  
		- applies VC2  
		- timestamp the event receive(m)

* Ordering of vectors:
	* e -> e' <-> V(e) < V(e')
	* Ordering relation:
		* ![[Pasted image 20230302142640.png]]

* Drawback of vector clocks are that an overhead is introduced, and it grows linearly with the number of processes in the system.

### Efficient Implementation
* Singhal-Kshemkalyani’s Differential Technique:
	* Solution: When a process p<sub>i</sub> sends a msg to a process p<sub>j</sub> it piggybacks only those entries of its vector clock that differ since the last message sent to p<sub>j</sub>
	* Assumption: Communication channels follow FIFO discipline for message delivery
* What is Singhal-Kshemkalyani’s Differential Technique in distributed systems?
	* Singhal and Kshemkalyani’s Differential Technique is an algorithm used in distributed systems to detect discrepancies between replicas of a distributed system. It uses a combination of message passing, vector clocks, and logical timestamps to detect discrepancies between replicas of the same data. The algorithm works by assigning each replica with a unique vector clock that is updated as the replica receives messages from other replicas. This vector clock allows the replica to determine if it has any out-of-date information compared to other replicas. If any discrepancies are found, the differential technique will then send messages to the other replicas so that they can update their versions with the latest data from the out-of-date replica. This helps to ensure that all replicas have the same up-to-date information about the distributed system.

* Worst case (m = n): every element of the vector clock has been updated since the last message. As such the next message will need to carry the entire vector **n** 
* Direct implementation:
	* Implementation will result in a $O(n²)$ storage overhead at each process
	* This can be done better

* New implementation uses two additional vectors.
* ![[Pasted image 20230302150223.png]]
	* LU: Last updated, when was the clock updated.
	* LS: Last sent, figure out what needs to be sent.
	* V: Current values.