# Design Documentation 

The interface is the same as Part 1 except for small cahnges. 

CPU.java

## CPU.java

We added a 16 bit machine status register (MSR) which tracks the health of the machine. 

We also added a machine fault register (MFR) which will contain the machine fault if it occurs. 

We also made note of the following locations in memory:

| Memory Address  	|  Usage 	
|---				|---	
| 	0	  			| Reserved for Trap	
| 	1  				| Reserved for machine fault
| 	2 				| Store PC for Trap
| 	3 				| Not Used
| 	4 				| Store PC for machine fault
| 	5 				| Not Used