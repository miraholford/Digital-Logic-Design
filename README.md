# Digital-Logic-Design

###### A high-level overview of the bridge between hardware and software
-------

##Introduction 

We use computers everyday. Yet, not many of us can claim they understand, even on a very high level, how exactly computers operate. Yes we all understand there is a RAM, a CPU and everything is represented as 1's and 0's, but do we really understand what happens from the second you press the "On button" and the moment that your operating system's icon comes on the screen? Well let's dive in!

##Overview of Computer Architecture

Computers are really not that complicated. Here is the big idea: a **CPU** (Central Processing Unit) reads bits of data from **memory**, performs calcuations or logical operations, and writes the resulting data back into memory. That's literally it. There are sometimes other devices called **peripheral devices** that provide input and output and secondary mass storage. To give you an idea of how fast processors are, Intel's "ancient" Pentium microprocessor can run at over 300 **MIPS** (million instructions per second). In the late 1990's computers had about a maximum of 64 "Megs of **RAM**" (Megabytes, millions of bytes, of Random-Access-Memory) packed in a few SIMMs (Single In-Line Memory Modules). By now, as technology has progressed, the price of RAM has dropped and now computers are equipped with Gigabytes of RAM.

Remember that by definition, a computer is a universally _programmable_ device, meaning it can model any task that involves logical and arithmetic operations. However, a computer is never "aware" of what it is doing. It must be following a certain program that tells it which operation it must carry out next. **Von Neumann Architecture** refers to a paradigm invented by John von Neumann in 1946 that basically said "why not just store the program that the computer is to run in its own memory?" Seems intuitive right? Well it was a huge discovery at the time! So under this architecture, instructions were written in a specific portion of RAM, where the CPU accessed and read them one by one, and carried out their orders and storing the result back in the RAM. Let's look at each one of these components individually.

###The CPU
Here is a basic picture of a CPU without all the unnecessary detail:
![CPU Components](http://upload.wikimedia.org/wikipedia/commons/d/d8/ABasicComputer.gif)

CPUs are really characterized by their **instruction set** and internal **registers**. An instruction set is really a list of key value pairs mapping numbers (instruction codes called **opcodes**) to abstract operations that the **ALU** (Arithmetic Logic Unit) will compute. These operations could be "load", "add", "subtract", etc. Registers are simple 32-bit (or 64, depenending on the platform structure) storage units that the **control unit** (the guy that does all the thinking) can use to hold values as it is talking to the ALU to carry out a computation. For example, the instruction `var_1 = 3 + var_1` would be carried out as follows: the the control unit retrieves the value in var_1 and saves it in some register; it then asks the ALU to add that value to the number 3 and proceeds to store it in some other register; it then goes back and updates the value of var_1 in memory. Simple enough?

Some CPUs can interpret hundreds or even thousands of different instructions. But another design used in RISC (Reduced Instructions Set Chip) microprocessors, has a few instructions in its set, but is able to perform each instruction much more quickly. Just for some context, keep in mind that all CPUs have an internal clock, that generates electrical pulses at a fixed frequency. Each one of these **clock cycles** (somewhere in the Gigahertz for modern processors) is synchornized with a single CPU operation. So the faster the clock of the CPU, the more operations it can carry out, and the faster the computer.

So how does the CPU communicate with everyone? Through parallel lines called **buses**. A CPU really needs to be able to carry memory addresses and data values. Not surprisingly, there are two different types of buses: **data bus** and **address bus**. Another thing that determines the overall speed of the computer is the width (how many bits wide it is) and speed of the buses.

###Memory
Computer memory is really a 1-dimensional array of **bits**, arranged in groups of 8, called **bytes**. Each byte is given a unique address that the CPU can use to access it. The cool thing about memory is that CPU does not have to read or write memory bytes sequentially; bytes can be accessed in any arbitary sequence, hence the name **_Random Access Memory_**. One thing to keep in mind is that RAM is volatile; this means that every time we turn off the computer, the RAM is wiped clean. This is why there is another kind of memory that is permanent and non-erasable (or at least it is in principle). This is called **read-only memory** or **ROM**. Here is where we can store the initialization code that boots up the operating system everytime we turn on the computer. So basically, when you turn on your computer, the CPU starts writing the initialization code or **boot record** from the ROM onto the RAM. The ROM **BIOS** (Basic Input Output System), whose job is to take control of the keyboard, display, etc. is also run at this stage. Then once BIOS has finished running and everything necassary for starting the operating system has properly been loaded onto RAM, the control unit allows the operating system to start executing its instructions. Kind of cool eh?

