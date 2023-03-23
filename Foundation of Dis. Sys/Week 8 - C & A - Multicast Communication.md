* Delivery Guarantees
	* Group communication requires coordination and agreement
* Send message to all members of the group:
	* Goal is satisfying some group delivery guarantees:
	* Agreement on the set of messages that every process in the group should receive
	* Agreement on the delivery ordering across the group members
	
* Essential feature of multicast is:
	* a process issues only one multicast operation to send a message to each of a group of processes.
	* it is done instead of issuing multiple send operations to individual processes.
* Once again reliable communication is assumed
	* There is no duplication and no creation = integrity property
* Further assumptions:
	* Processes may fail only by crashing
	* Processes are members of groups - which are the destination for the messages sent using multicast

* Communication primitives
	* multicast(g,m)
	* deliver(m) - delivers a message sent by multicast to the calling processes
		* It is not the same as receive, as a multicast message is not always passed on to the application layer 

## Set of messages
### Basic multicast
* A basic multicast satisfies the following properties:
	* Validity: if a correct process multicasts message *m*, then every correct process eventually delivers *m*
	* No duplication: a correct process *p* delivers a message *m* at most once
	* No creation: if a correct process *p* delivers a message *m* with sender *s*,  then *m* was previously multicast by process *s*
* Validity is a liveness property
* No duplication and No creation are safety properties
*  No duplication + No creation = integrity property
![[Pasted image 20230323133456.png|600]]
* Correctness means that a basic multicast algorithm must satisfy the above three properties
	* It is derived assuming reliable channels

* Basic multicast suffers from the ACK-impolosion problem
* However a functional problems also exists called the Faulty sender problem.
	* If the sender fails, some processes might receive the message while other might not - This means some might deliver the message and some might not
	* There is no agreement on the set of messages that the set of processes deliver
	* Solution: We want to ensure AGREEMENT even when the sender fails

### Reliable Multicast
* It solves the faulty sender problem

* Validity is changed:
	* Validity: if a correct process multicasts message m then it will eventually deliver m
* Agreement:
	* If a correct process delivers message *m*, then all the other correct processes in group(m) will eventually deliver *m*
* Validity -> liveness for the sender
* Validity + Agreement -> liveness for the system


## Ordering of messages to be delivered
* Ordered Multicast



### FIFO
* Has to respect the ordering of the sender
* If a correct process issues multicast(g, m) and then multicast(g, m’) (multicast(g, m) ➝ i multicast(g, m’)), then every correct process that delivers m’ will deliver m before m’
* Partial relation
![[Pasted image 20230323141854.png|400]]
* Basic FIFO Multicast
	* FO-Multicast
	* FO-deliver
* 



### Causal
* multicast(g, m) ➝ multicast(g, m’), then any correct process that delivers m’ will deliver m before m’
* Partial relation
* Causal ordering implies FIFO ordering
![[Pasted image 20230323141911.png|400]]
* Implementation requires vector timestamps
* 


### Total 
* If a correct process delivers message m before it delivers m’, then any other correct process that delivers m’ will deliver m before m’
* Total relation
	* Every process delivers messages in the same sequence
![[Pasted image 20230323141930.png|400]]
