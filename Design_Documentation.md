# Design Documentation 

The interface is the same as Part 1 except for small changes. 

## CPU.java

We added a 16 bit machine status register (MSR) which tracks the health of the machine. 

We also added the machine fault register (MFR) which is array of 4 boolean values for the different faults that can happen. 

We also made note of the following locations in memory:

| Memory Address  	|  Usage 	
|---				|---	
| 	0	  			| Reserved for Trap	
| 	1  				| Reserved for machine fault
| 	2 				| Store PC for Trap
| 	3 				| Not Used
| 	4 				| Store PC for machine fault
| 	5 				| Not Used

Here are the possible machine faults which can be on/off:

| ID  				|  Fault	
|---				|---	
| 	0	  			| Illegal memory address to reserved locations
| 	1  				| Illegal TRAP code
| 	2 				| Illegal operation (Opcode)
| 	3 				| Illegal memory address beyond 2048


Two new instrictions were added:

1. HLT -  Opcode: 0  --> Stops the machine
2. TRAP - Opcode: 36 --> Sets the trap code which is MFR[1] to true. Stores PC + 1 into memory location 2. It fetches the instruction at memory location 0 into PC. That is the next instruction that is executed to handle the trap or machine fault. 

