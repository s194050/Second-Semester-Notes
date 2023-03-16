## Distributed mutual exclusion
* Assumptions:
	* Each pair of processes is connected by reliable channels
	* No process failure implies a threat to the other processes' ability to communicate

* Critical section is more complex in distributed systems
	* Because of no shared variables, e.t.c semaphores nor 
	* facilities supplied by a single kernel.
* As such the only solution is distributed mutex based solely on message passing in context of:
	* unpredictable message delays
	* no complete knowledge of the state of the system
* Terminology:
	* enter() - enter a CS
	* resourceAccess() - access shared resource in CS
	* exit() - leave the CS
* The mutual exclusion algorithm:
	* [ME1] Safety: at most one process can execute in the CS at a time  
	* [ME2] Liveness: requests to enter and exit the CS eventually succeed  
		* Implies freedom from both deadlock and starvation
		* The absense of starvation  is a fairness condition
	*  [ME3] Ordering: if one request to enter the CS happened-before another, then entry to the CS is granted in that order
		* Happend before ordering of CS requests may imply liveness
* Safety is absolutely necessary - known as the correctness property

 * Design of distributed mutex can be described by three basic algorithms:
	 * Token based
	 * Non-token based
	 * Quorum based

### Token based algorithms
* A unique token is shared among the processes
* A process is allowed to enter its CS if it posseses the tokens. When done it passes it on
* MUTEX is ensured because the <u>token is unique</u>

* One such approach is the Central server algorithm
	* Performance: 
		* Entering, it takes 2 messages a request followed by a grant
		* it delays the requesting process by the time for this round-trip
		* Exiting: takes 1 message, known as release. Assuming asynchronous message passing it will not delay exiting the process
	* Weakness is that it is centralised (The server is the bottleneck)

* Another approach is the ring-based algorithm
	* Basic idea: exclusion is conferred by obtaining a token in the form of a message from process to process in a single direction around the ring.
	* Each process p<sub>i</sub> has a communication channel to the next process in the ring p<sub>(i+1)mod N</sub> 
	* ![[Pasted image 20230316140259.png]]
	* Algorithm:
		* If a process does not require to enter the CS when it receives the token, then it immediately forwards  the token to its neighbour  
		* A process that requires the token waits until it receives it, but retains it  
		*  To exit the CS, the process sends the token on to its neighbour
	* It is inefficient as it continuously consumes network bandwidth.
	* Weakness is special topology/structure

### Non-token based algorithms
* Two or more successive rounds of messages are exchanged among the processes to determine which process will enter the CS next
* A process enters the CS when an <u>assertion</u>, defined on its local variables becomes true.
* Mutex is enforced because the assertion becomes <u>true only at one site at any given time</u>

* An apporach is Lamport's algorithm
	* Requires communication channels to deliver in FIFO order
	* Based on Lamport's logical clocks
	* The idea: the algorithm executes CS requests in the increasing order of timestamps
		* Timestamp = (clock value, id of the process)
* A total ordering => requires the further rule:
	* CR4: a (in p<sub>i</sub>) => b (in p<sub>i</sub>) if and only if either L<sub>i</sub>(a) < L<sub>j</sub> (b) or L<sub>i</sub>(a) = L<sub>j</sub>(b) ∧ p<sub>i</sub> ≺ p<sub>j</sub> 

* Ricart and Agrawala's idea
	* Does not require communication channels to be FIFO
	* The basic idea is:
		* processes that require entry to a CS multicast a request message  
		* processes can enter the CS only when all the other processes have replied to this message  
		* node p<sub>j</sub> does not need to send a REPLY to node p<sub>i</sub> if p<sub>j</sub> has a request with  timestamp lower than the request of pi (since pi cannot enter before p<sub>j</sub> anyway in this case)
	* 