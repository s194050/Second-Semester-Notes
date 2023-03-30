## Elections
* The election algorithm
	* An algorithm for choosing a unique process to play a particular role
	* ![[Pasted image 20230330134057.png|400]]
* What is the election algorithm in distributed systems, and how does it work?
	* The election algorithm is a process used in distributed systems to select a new leader or coordinator when the current one fails or becomes unavailable. It ensures that only one node becomes the leader at any given time, preventing conflicts and ensuring that the system remains functional.

	   There are several election algorithms used in distributed systems, but the most common one is the Bully algorithm. Here's how it works:
		
		1. Each node in the system has a unique ID assigned to it, with the highest ID being the most powerful.
		
		2. When a node detects that the leader has failed, it sends an "election" message to all other nodes in the system with a higher ID than itself.
		
		3. The nodes with higher IDs respond with an "OK" message, indicating that they are still alive and willing to be the leader.
		
		4. If no response is received within a set time limit, the initiating node assumes that it is now the leader and broadcasts this information to all other nodes.
		
		5. If multiple nodes respond with OK messages, they enter into a second round of elections until only one node remains as the new leader.
		
		The election algorithm ensures that only one node becomes the leader at any given time, preventing conflicts and ensuring that the system remains functional even when nodes fail or become unavailable.

* Election Algorithm requirements
	* ![[Pasted image 20230330134303.png|400]]
* The performance is measured by:
	* the total network utilisation
	* the turnaround time. Which is defined as the number of serialized message transmission times between the initiation and termination of a single round
* An example is the Ring-based election algorithm
	* ![[Pasted image 20230330134639.png|400]]
* It functions as follows:
	* ![[Pasted image 20230330134856.png|400]]
* When the coordinator receives the elected message, it once again marks it self as a non-participants. Then it sends an elected message, to the neighbour and lets it know that it was the original sender.
* There is an **assumption** that the processes has an ID or some identifier
* The turnaround time for this algorithm is $3N-1$ 
* It is useful understanding the properties of election algorithms in general
	* But it tolerates no failures, which limits its practical value
	* The bully algorithm fixes this issue


### Failure Detectors
* A service that processes queries about whether a particular process has failed
* A failure detector is not necessarily accurate ( asynchronous systems)
* There exists two classes of failure detectors <u>unreliable</u> & <u>reliable</u>
	* The majority falls into the category of unreliable failure detectors


* Unreliable Failure detectors
	* May produce one of two values when given the identity of a process
		* Unsuspected or suspected
	* Both of these are hints, which may not accurately reflect whether the process has actually failed
	* ![[Pasted image 20230330140741.png|400]]

* Reliable Failure detector
	* Always accurate in detecting a process's failure
	* It always processes' queries with either a Unsuspected(Hint) or Failed
		* Failed means that the detector has determined that the process has crashed
	* It requires that the system is synchronous to work

* The Bully Algorithm
	* It allows processes to crash during an election
	* It assumes that message delivery is reliable
	* It also assumes that the system is synchronous
	* Furthermore:
		* It assumes that each process knows which processes have higher identifiers and that it can communicate with all such processes
	* Consult slides on how it works
	* The best case:
		* Sends N-2 coordinator messages
		* The turnaround time is 1
	* Worst case
		* N-1 messages
		* Turnaround is approx. 5 messages
			* election, answer, election, answer, coordinator

## Consensus
* The consensus problem
	* Informally: the processes propose value and have to agree on one among these values
	* Formally:
		* ![[Pasted image 20230330143737.png|400]]
* The consensus algorithm:
	* ![[Pasted image 20230330144021.png|400]]
* How does the consensus algorithm work in distributed systems?
	* Consensus algorithms are used in distributed systems to ensure that all nodes agree on a particular value or decision. The primary goal of a consensus algorithm is to maintain consistency and reliability across the distributed system, even when some nodes fail or behave maliciously. 

		Consensus algorithms work by allowing multiple nodes to propose values and then using a set of rules to determine which value is selected as the final decision. The most commonly used consensus algorithm is the Paxos algorithm, which includes three roles: proposer, acceptor, and learner. 

		The process works as follows:
		
		1. The proposer proposes a value.
		
		2. The acceptors receive the proposal and vote on whether or not to accept it.
		
		3. If a majority of acceptors accept the proposal, it is considered valid.
		
		4. The learner receives the accepted proposal and learns about the decision.
		
		5. If an acceptor fails or behaves maliciously, the system can still achieve consensus by using redundancy and backup mechanisms.
		
		Overall, consensus algorithms ensure that all nodes agree on a specific decision without relying on a central authority or server. This makes distributed systems more reliable, scalable, and fault-tolerant. 
* The consensus problem is easy to solve when there are no failures

* In presence of crash failures the following assumptions are needed:
	* A synchronous system, where up to f of the N processes exhibit crash failures
* The idea of the solution is as follows:
	* ![[Pasted image 20230330144458.png|400]]

* A variant of consensus is the Byzantine Generals
	* ![[Pasted image 20230330145929.png|400]]
	* Requires:
		* Termination: eventually each correct process sets is decision variables
		* Agreement: the decision value of all correct processes is the same
		* Integrity: if the commander is correct, then all correct processes decide on the value that the commander proposed

* Another variant is Interactive Consistency
	* ![[Pasted image 20230330150201.png|400]]


### Imposibility Results
![[Pasted image 20230330151444.png|400]] 
* These solutions are not possible in asynchronous systems
	* ![[Pasted image 20230330151800.png|400]]
