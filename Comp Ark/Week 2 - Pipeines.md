# Pipelining
* Use parallelism
	* Pipe lines
	* ILP - Instruction Level Parallelism
	* TLP - Thread Level Parallelism
* Principle of locality
	* Memory and caches
* Optimise the most frequent case
	* Benchmarks and get characterisation, to find the most frequent case
* Amdahl's law 
		Amdahl's law, named after computer scientist Gene Amdahl, is a principle that describes the theoretical speedup in latency of the execution of a task at fixed workload that can be expected of a system whose resources are improved. It states that the speedup in execution time for a program using multiple processors in parallel computing will never be faster than the ratio of improved performance to the total amount of performance available. For example, if only 30% of a program can be parallelized and made to run three times as fast using three processors, then the overall speedup achieved by using all three processors would be 1.3 (1/0.3 = 3).
* CPI 
		CPI (Cycles Per Instruction) in pipelining is a measure of the number of cycles taken by a processor to execute an instruction, taking into account the time required to fetch the instruction, decode it, execute it and write back any results. It is typically used to compare different processors or different implementations of the same processor architecture.
* Be careful of dependencies. Too big a pipleline can create a big delay, which might slow the whole system.
* Stalling the pipeline can help avoid structural hazards
	* Done using bubbles
* Memory structural hazard
	* Are fixed at hardware level
* Register File Structural Hazard
	* Fixed using split clock - This cannot be done on an FPGA
* Most important hazard is the dependency issue
	* ![[Pasted image 20230207134324.png]]
* Three generic dependency hazards
	* Read after write (RAW)
		* ![[Pasted image 20230207134459.png]]
	* Write after read (WAR)
		* ![[Pasted image 20230207134516.png]]
	* Write after write (WAW)
		* ![[Pasted image 20230207134539.png]]
* Forwarding can help resolve the three above hazards

# Caches
* Temporal Locality
		Temporal locality in caches refers to the phenomenon where data or instructions needed by the processor are generally found near recently accessed data or instructions. In other words, when a processor accesses a particular piece of data, it is likely that the same data will be accessed again in the near future. This phenomenon is used by caches to store data for faster access. Whenever a processor requests for a piece of data, the cache checks if it already contains that data. If it does, then it can quickly retrieve it and provide it to the processor instead of having to fetch it from memory or from an external source. This reduces the processing time and makes programs run faster.
* Spatial Locality
		Spatial locality (also called the locality of reference or the principle of locality) is a concept in computer science which states that a processor will access items that are stored close to each other in memory more often than items that are further away. In other words, information or instructions which are needed by the processor tend to be clustered together in memory, and this clustering of information can be used to optimize performance. This concept is especially important when considering caching, as it allows the processor to quickly access items stored nearby. By utilizing spatial locality, caches can store frequently used data and instructions closer to the processor, reducing memory access times and increasing overall system performance.

* Direct Mapped Cache  
		A Direct Mapped Cache is a type of cache memory that stores each memory address in a single location in the cache. The cache memory is divided into blocks and each block can contain one or more memory addresses. When a processor references a memory address, it first looks in the direct mapped cache to see if the address is present. If it is, the processor retrieves the data from the direct mapped cache. If the address is not present, then the processor must go to main memory or another level of cache to retrieve the data. This type of caching has low latency and high hit rates, but can suffer from conflict misses due to collisions when multiple locations map to the same block.
* 4-way set associative cache 
		A 4-way set associative cache is a type of CPU cache that uses a 4-way mapping scheme to store data. Data is stored in sets, which contain four lines of data. A memory address is mapped to one of these sets, with each set containing four lines of data. When retrieving a word from memory, the CPU first looks for it in the set associated with the memory address; if the word is not found, then it looks at the other three sets. This mapping scheme allows for faster access times than a direct-mapped cache and provides more flexibility than a fully associative cache.

* Cache miss rate
	* Fraction of access that result in a miss. What is a cache miss?
		* A cache miss is when the processor looks for a piece of data in the cache memory but it isn't found and must be retrieved from main memory instead. The fraction of access that result in a miss is referred to as the cache miss rate.
	* It is possible to execute other instructions when a miss happens
* Types of cache misses
	* Compulsory
	* Conflict
	* Capacity
* What is a cache block?
		A cache block is a small, fixed-size portion of memory that stores recently accessed data. It is used to speed up access to frequently requested data by storing it in a fast, local memory location. Each block of data is indexed and associated with a particular address in the cache, so that when the same address is requested, the cached data can be quickly retrieved.
* Six basic optimisations
	* Larger block size
		* Reduces compulsory
		* Increases conflict & capacity
	* Larger total capacity
		* Increases hit time and power consumption
	* Higher associativity
		* Reduces conflict
		* Increases hit time and power consumption
			* Happens due to larger amount of hardware
	* Higher number of cache levels
		* Reduces overall memory access time
	* Giving priority to read misses over writes
		* Reduces miss penalty
		* Due to the read operation stalling the process more than the write
	* Avoiding address translation in cache indexing
		* Reduces hit time

* Advanced Optimisations
	* Reduce hit time
		* Small and simple first-level caches
		* Way prediction in caches
			* Try to predict the way to pre-set mux - Extends to block prediction as well (Way selection)
	* Increase bandwidth
		* Pipelined caches
	* Reduce miss penalty
		* Critical word first, merging write buffers
	* Reduce miss rate
		* Compiler optimisations
	* Reduce miss penalty or miss rate via parallelisation
		* Hardware or compiler prefetching

* L1 Caches - The bigger the size the longer the access time
	* Due to size of decoder
* 