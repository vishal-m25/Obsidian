 ## topics to note
- compiler and linker
- registers in coding
- deadlock occurrence and prevention techniques
- CO concepts
- DBMS (1NF,2NF,....)
- network components and driver uses



## Recal
- system call



# Note
## OS
- OS -- it is service as an interface 
- #### Linker
	- Linker is a program in a system which helps to link object modules of a program into a single object file. It performs the process of linking. Linkers are also called as link editors. Linking is a process of collecting and maintaining piece of code and data into a single file. Linker also links a particular module into system library. It takes object modules from assembler as input and forms an executable file as output for the loader.
		types:
		- static linking (linked during compile time)
		- dynamic linking (linked during run time)
- binding of instructions and data to memory addresses can be done in 
	- load time
	- compile time
	- execution time
- Semaphore (counting , binary) {wait() and signal()}
- Thread is not shared among PC and stack
- Unsafe states are ___not deadlock__
- operating modes of __AT__ 
	- real 
	- protected
- Size of virtual memory is based on __address buss__
- <b>Relocation register</b> is know as basic register
- <b>Atomic</b> is known as uninterruptible
- __Banker's__ algorithm is used in deadlock avoidance 

- #### Belady’s Anomaly in Page Replacement Algorithms
	- ***Bélády’s anomaly*** is the name given to the phenomenon where increasing the number of page frames results in an increase in the number of page faults for a given memory access pattern.
	- FIFO follows this anomaly


## DBMS
- ### Tuple Relational Calculus (TRC)
	TRC is a **non-procedural query language** in database management systems characterized by:
	- Focuses on selecting entire tuples (rows) from a relation
	- Uses tuple variables to represent database rows
	- Declarative approach that specifies **what data** is needed, not how to retrieve it
	- Notation: { T | Condition(T) }
	**Example**:  
	To select employees in Department 10, the TRC query would be:  
	{ T | EMPLOYEE(T) AND T.DEPT_ID = 10 }[1](https://www.geeksforgeeks.org/tuple-relational-calculus-trc-in-dbms/)[2](https://www.geeksforgeeks.org/difference-between-tuple-relational-calculus-trc-and-domain-relational-calculus-drc/)
	
- ### Domain Relational Calculus (DRC)
	DRC differs from TRC by:
	- Selecting specific attribute values instead of whole tuples
	- Using domain variables (column-level selection)
	- More expressive and complex query capabilities
	- Notation: { a1, a2, ... | Condition(a1, a2, ...) }[2](https://www.geeksforgeeks.org/difference-between-tuple-relational-calculus-trc-and-domain-relational-calculus-drc/)


- Subschema refers to an application programmer's view of the data item types and record types, which he or she uses




## COMPUTER NETWORKS
- OSI layers
	- application
		- application (frontend)
		- presentation (design and images ,documents in data)
		- session (internet .. medium of transport)
	- transport (path , connection control / controls the path of data transfer)
	- network (logical addressing)
	- network interface
		- data link (providing physical address)
		- physical (.. router .. server .. hub ....)

- __Devices__
	- repeater (regenerate at each junction due to loss)
	- hub (multiport repeater)
	- bridge (data transfer through MAC)
	- switch (store data to buffer )
	- router (data transfer through IP)
	- gateway (pass to enter different networks)

	- [hop to hop, end to end ,host to host]


| TCP                                     | UDP                                           |
| --------------------------------------- | --------------------------------------------- |
| connection created before data transfer | no connection is created before data transfer |
| best for end to end                     | best for broadcast                            |
| guarantees data delivery                | no guarantee for data delivery                |
| comparably slow                         | fast                                          |
| lost packages can be tracked            | lost packages cannot be tracked               |
| 20-60 bytes variable length             | 8-bytes fixed length header                   |


| ARP                         | RARP                                |
| --------------------------- | ----------------------------------- |
| Address Resolution Protocol | Reverse Address Resolution Protocol |
| maps IP to MAC              | maps 48 bit MAC to IP               |
| maintained by localhost     | maintained by RARP server           |

| TELNET                             | FTP                            |
| ---------------------------------- | ------------------------------ |
| Telecommunication Network Protocol | File transfer protocol         |
| for text transfers                 | for file transfer(dowmloading) |
| general security                   | high security                  |



projects/hardy-mercury-449710-f9/locations/global/collections/default_collection/dataStores/farm-store_1738555123738




