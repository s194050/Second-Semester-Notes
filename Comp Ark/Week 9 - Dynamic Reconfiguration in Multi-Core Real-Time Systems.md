## Background
* Computing systems are typically implemented using two solutions:
	* Software running on a processor
	* ASIC chip implementing the required functionality
	* What is an ASIC chip?
		* An ASIC (Application-Specific Integrated Circuit) chip is a type of integrated circuit designed for a specific purpose or application, rather than for general use. It is customized to perform a particular function, such as processing data for a specific computer application or performing calculations for a specific electronic device. ASICs are used in a wide range of applications, including consumer electronics, telecommunications, automotive systems, and medical devices. They can provide high performance and low power consumption compared to general-purpose microprocessors.
* Reconfigurable computing
	* Combines flexibility of software with high performance of hardware
	* Implemented using FPGA's
	* Hardware can be configured when no longer needed

* An FPGA is usually seperated into two parts:
	* Static part - Memory, I/O, Hard processors
	* Reconfigurable fabric - Accelerating units

* Dynamic Partial Reconfiguration (DPR)
	* Allows reconfiguration of select areas of an FPGA after intial config
	* The remaining part of the system continues to operation without interruption

* An FPGA can be seen as a two layer device - It is only an abstraction, as it is not two silicon layers in the real world.

* Something is usually used is self-healing hardware
	* It is implemented as a state machine, that consistently writes the bit-stream.



## Approach
* Real time applications often have multiple modes of operation
	* A mode is defined as a set of executing tasks
	* Run-time change between modes
* Modes may have different guaranteed service requirements

![[Pasted image 20230328133520.png|400]]
* 



## Reconfiguration of Computation Resources
* The ICAP is an FSM
	* It consists of a control FSM
		* with two operating modes SPM-Stream & CPU-Stream
* SPM-Stream
	* ![[Pasted image 20230328140101.png|200]]
* CPU-stream
	* The Processor streams directly the data (from off-chip memory)  
	* Avoids potentially large SPMs


* Beside controller size, another big importance is it can reduce the amount of hardware that needs to be used

* Benchmark experiments:
	* Four different data sets are used for testing computation.
	* ![[Pasted image 20230328140411.png|400]]

* First test condition is how much hardware is used
	* DDR helps in saving on hardware like LUTs, FF, but in the end requires more BRAM, so it saves on hardware, but costs more in memory
* Second test condition is WCET (Worst-case execution time)
	* ![[Pasted image 20230328140938.png|400]]
	* 
## ## Reconfiguration of Communication Resources
* The TDM schedule is determined at compile time, this ensures that every processor has the necessary bandwidth
* DDR wants to change this by changing this schedule at run-time

* To ensure that all NI's change to the correct config for a mode. 
	* A packet is sent out to every NI by the master node, that they are supposed to swap at certain point in time
* ![[Pasted image 20230328142625.png|400]]
* There is always a trade-off, either its:
	* hardware
	* memory
	* speed
