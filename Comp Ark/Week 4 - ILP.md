## Instruction-level Parallelism
* Two approaches
	* Exploit parallelism dynamically
	* Exploit parallelism statically

* Basic Block (BB)
	* Code sequence with no branches, except at entry and out
* If an instruction is parallel it has no dependencies

* Name dependency - two instructions share the same register
	* Anti-dependence - Write after read hazard, data is written before register is read
	* Output dependence - Write after write hazard, data is written before the correct value is written
* Control dependencies
	* In general these dependencies should be preserved to preserver program order
	* But they can be ignored, if it does not change the correctness of the program 
	* Two properties are critical to program correctness
		* Exception behaviour
			* Any changes in instruction executions order, must not change how exceptions are raised.
			* No new exceptions are introduced
		* Data flow
			* Actual flow of data values among instructions that produce results, as well as those that consume then
			* Branches makes this flow dynamic

* Loop unrolling is useful, but it introduces some issues
	* Usually the upper bound of the loop is unknown
	* A way to avoid this problem is to generate a pair of consecutive loops
* 1st loop executes $n \mod k$ times, and has a body that is the original loop
* 2nd loop is the unrolled body surrounded by outer loop that iterates  $n/k$ 

## Branch Prediction to increase ILP
* Another way instead of loop unrolling is **branch prediction** 
	* Static branch prediction 
		* Static branch prediction is a type of branch prediction in which the direction of the branch (taken or not taken) is determined by the processor based on information in the instruction itself. This type of prediction does not require any data from prior executions of the same instruction and is usually very accurate.
	* Dynamic branch prediction
		* Dynamic branch prediction, on the other hand, requires data from prior executions of the same instruction to determine which direction the branch should take. This type of prediction is more complicated and less reliable than static branch prediction but can be more accurate in certain cases.

* Two-level branch predictor
	* A two-level predictor in hardware is a type of branch prediction that utilises two different levels of prediction logic in order to improve branch prediction accuracy. The first level is a simple branch predictor, such as a static branch predictor or a two-level adaptive predictor, which predicts whether a branch will be taken or not. The second level is an additional hardware component that can make more complex predictions based on the results of the first level predictor. This additional hardware component can make use of multiple inputs such as instruction history, register values, and more to construct more accurate predictions. Additionally, this second level hardware component can also update the first-level predictor with better information so that it can become more accurate over time.

* Tournament Branch Predictors in hardware 
	*  A tournament predictor is a type of branch predictor that uses a combination of multiple predictors to improve branch prediction accuracy. This type of predictor typically consists of two or more predictors, such as a two-level adaptive predictor and a static branch predictor. The tournament predictor then chooses which of the predictors to use for each branch, based on previous performance. The idea behind the tournament predictor is that by combining multiple predictors, the overall accuracy of the prediction can be improved.

* Dynamic branch prediction summary
	* Branch history table (BHT)
		* 2 bits for loop accuracy
	*  Correlation 
		* Recently executed branches correlated with next branch
		* Branch history part of selection
	* Tournament Predictors
		* Global and local predictor
		* Combined with a selector

## Dynamic Scheduling to exploit ILP

* Hardware rearranges the instruction execution order
* Works even when dependence is not known at compile time

* In-order execution 
	* In-order execution is a type of instruction execution strategy in which instructions are processed in the order they appear in the program code. This means that instructions are executed one at a time, in sequence, from top to bottom. The result of executing each instruction is stored in memory for use when the next instruction is executed.
* Out-of-order execution 
	* Out-of-order execution (also known as dynamic execution) is a technique used in computer architecture to improve the performance of processors. It allows the processor to execute instructions in a different order than they were written in the program code. This allows the processor to execute instructions more efficiently by taking advantage of otherwise wasted cycles when one instruction can’t be executed until data from another instruction is available. Out-of-order execution can also help take advantage of parallelism between instructions, allowing multiple instructions to be executed at once.


# Time-predictable architecture
## Real-time systems
* Definition
	* Correct logical results
	* Meeting all deadlines
* Judged by Worst-case Execution Time (WCET)

## Time-predictable 
* What is Network on Chip (NoC)  

* Time-division multiplexing 