## Global states
* What is a global state?
	* They are described by two things:
		* The states of participating processes together with - the states of the channels between these processes
		* Can be described by a tuple:
		* $S = <p_1,p_2,c_{12},c_{21}>$ 
* Events:
	* Each event is described by $e = <p,s,s',M,C>$  
	* What is an event in relation to global states in a distributed system?
		In a distributed system, an event refers to any change in the state of a node that affects the global state of the system. This can include changes in data, messages being sent or received, or other actions taken by the node. Events are important in distributed systems because they allow nodes to coordinate and synchronize their actions, ensuring that the global state of the system remains consistent across all nodes. By detecting and responding to events, nodes can adjust their behavior and ensure that all nodes are working together towards a common goal.

## Distributed Snapshots
* Assumption: The algorithm relies on:
	* Channels are error free and sequency preserving (FIFO)
	* Channels deliver transmitted msgs after unknown but finite delay
	* Furthermore, we consider only communicating events
* A consistent global state is defined by:
	* A state after a certain amount of events happened (H)
	* GS(H) = The state of each process p<sub>i</sub> after p<sub>i</sub> ’s last event in H for each channel, the sequence of msgs sent in H but not received  in H
	* Also known as a **"CUT"** 
* How to construct H?
	* Process pi follows two rules    
		1.SEND MARKERS  
			Record p<sub>i</sub> ’s state  
			Before sending any more messages from p<sub>i</sub> , send a marker on each  
			channel c<sub>ij </sub>directed away from p<sub>i </sub> 
		2.RECEIVE MARKER  
			On arrival of a marker via channel c<sub>ji</sub> :  
			<u>IF</u> p<sub>i </sub>has not recorded its state  
			<u>THEN</u> SEND MARKERS rule; record c<sub>ji </sub>’s state as empty  
			<u>ELSE</u> record c<sub>ji</sub> ’s state as the sequence of messages received on c<sub>ji</sub> since pi last noted its state
* What is the snapshot algorithm in distributed systems?
	The snapshot algorithm is a technique used in distributed systems to capture a consistent global state of the system at a particular point in time. It involves taking a snapshot of the current state of each process and communication channel in the system, while ensuring that the snapshots are taken concurrently and consistently across all processes. This algorithm is useful for debugging, monitoring, and analyzing distributed systems, as it provides insight into the internal workings of the system at a specific moment in time.

* Algorithm complexity:
	* O(e) messages, where e is the number of edges
	* O(d) time, where d is the diameter of the network.

* The recorded global states never occur in the actual execution.
	* The algorithm finds a global state based on a partial ordering -> of events.
	* Thus, we cannot determine what the **true sequence** of these events is
* What does the algorithm find then?
	* Pre-recording events: events in a computation which take place **before** the process in which they occur records its own state
	* Post-recording events: all other events
	* The algorithm finds a global state which corresponds to a PERMUTATION of  the actual order of the events, such that all pre-recording events come before all post-recording events
	* The recorded global state, S*, is the one which would be found after all the pre-recording events and before all the post-recording events  
* S* is a state which could possibly have occurred, in the sense that:  
		‣ It is possible to reach S* via a sequence of possible events starting from the initial state of the system, S<sub>i</sub> (in the previous example: <e<sub>1,</sub> e<sub>2</sub> , e<sub>5</sub> >)  
		‣ It is possible to reach the final state of the system, S<sub>f</sub>, via a sequence of possible events starting from S* (in the previous example: <e<sub>3</sub>, e<sub>4</sub> , e<sub>6</sub> >)  
	* ![[Pasted image 20230309142207.png]]

* A recorded global state is useful in **detecting stable properties**
	* Examples:
		* Failure recovery: a global state (checkpoint) is periodically saved and recovery from a process failure is done by restoring the system to the last saved global state
		* Debugging: the system is restored to a consistent global state and the execution resumes from there in a controlled manner

## Evaluating predicates
* Let $\Sigma$ be a global state - it represents a state of the past, that may have no bearing to the present
	* Does it make sense to evaluate $\Phi$ on it?
* A special case: stable predicates

* A **run** of a computation is a total ordering **R** that includes all the events in the global history and that is consistent with each local history  
	*  In other words, the events of p<sub>i</sub> appear in **R** in the same order in which they appear in h<sub>i</sub>  
	*  A run corresponds to the notion that events in a distributed computation actually occur in a total order  
	*  A distributed computation may correspond to many runs  
• A run **R** is said to be <u>consistent</u> if for all events e and e’, e ➝ e’ implies that e appears before e’ in   **R**  

* A consistent run allows for the leads to relation:
	* ![[Pasted image 20230309143948.png]] 

* From this a Lattice can be constructed
	* The set of all consistent global states of computation along with the leads-to relation defines a lattice.
	* A path in the lattice is a sequence of global states of increasing levels that corresponds to a consistent run

### Non-stable predicates
* Means that it can be true in some global states, but false in others
	* Evaluating a non-stable predicate over a single computation makes no sense  
	* The evaluation must be extended to the entire lattice of the computation 
	* It is possible to evaluate a predicate over an entire computation using an observation obtained by a passive monitor 

* A consistent run of a distributed computation is a total ordering **R** of its events that corresponds to one of the possible actual executions  
*  An observation is a total ordering Ω of events constructed from within the system  
*  A single run may have many observations  
*  An observation can correspond to:  
		‣ A consistent run  
		‣ A run which is not consistent  
		‣ No run at all  
• Consistent Observation: An observation is consistent if it corresponds to a consistent run  
