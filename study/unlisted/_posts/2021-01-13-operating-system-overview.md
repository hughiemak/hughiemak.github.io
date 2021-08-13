---
layout: post
title:  "Operating System Overview"
date:   2021-01-13 00:01
---

What happens when a program runs?
- The disk stores the program.
- The program is <b>loaded</b> into the memory.
- The CPU <b>fetches</b> instructions from the memory, <b>decode</b> the instructions, and <b>execute</b> them.
- This is the <b>Von Neumann architecture</b>.
<!-- The disk, memory and CPU are connected through the bus.
Memory is non-volatile. That's why we need a disk.
To process the data, we need CPU. -->

How CPU works?
- Fetch an instruction from memory.
	* According to <b>program counter</b>
	* Fetch data from memory to <b>instruction register</b>
- Decode: Figure out which intruction this is.
- Execute: arithmatic/logic operations, memory, condition, branch, etc.

OS's major functions
* Manage resources (virtualization)
* Provide services (system call)
	* Run programs
	* Memory sharing
	* Enable interaction with IO devices

Virtualization
* OS takes a physical resource and transforms it into a virtual form of itself.
* OS as a virtual machine.

System call
* OS provides services via system call to run process, access memory/devices, etc.

Virtualizing the CPU
* The system has a very large number of virtual CPUs.
* Turns a single CPU into a seemingly infinite number of CPUs.
* Allow many processes to seemingly run at the same time.

Memory:
* The physical memory is an array of bytes.
* A program keeps all of its data structures in memory.
	* Read/load: specify an address to be able to access the data
	* Write/store: Specify the data to be written to the given address
* The memory ranges from two processes can be overlapped.
* But each process has its own private memory.
	* Each running program has allocated memory at its own address space.
	* Each seems to be updating the value independently.
* Each process accesses its own private virtual adress space.
	* OS maps address space onto the physical memory
	* A memory reference within one running program does no affect the address spae of other processes
	* Pysical memory is a shared resources, managed by OS