## Introduction
* What is FLOPS in Computer architecture?
	FLOPS stands for Floating Point Operations Per Second. It is a measure of the performance of a computer's floating-point unit (FPU) and indicates how many floating-point calculations a computer can perform in one second. This metric is often used to compare the processing power of different computers, especially those used for scientific or engineering applications that rely heavily on complex mathematical calculations.

* The "Power wall" - CPU performance is limited by power and temperature as a result.
	* Cannot dissipate more than 150 W on silicon die
	* Cannot deliver enough current to power all parts of the chip - A.k.a Dark silicon


## Power Dissipation in Multicores
![[Pasted image 20230307132353.png]]
* P<sub>dyn</sub> is dynamic power dissipation caused by toggling in the load C<sub>L</sub>
* $P_{dyn}=\frac{C_{L}\cdot V^2_{DD}}{t_p}$ 
* ![[Pasted image 20230307132608.png]]
* ![[Pasted image 20230307132639.png]]
* V<sub>DD</sub> is the power supply voltage
* f is the clock frequency

* Frequency scaling and voltage scaling
	* Normally done in CPU to save powerful
	* $P_{CPU} = k \cdot V^2_{DD} \cdot f_{CLK}$ 
	* Slow-down clock -> longer slacks
	* Reduce V<sub>DD</sub> -> small slacks

Check slides for further notes.

## Floating-Point Formats in Machine Learning
* ![[Pasted image 20230307144706.png]] 

