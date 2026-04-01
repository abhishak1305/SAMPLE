### **1) PCB (Process Control Block)**

**PCB** is a data structure used by OS to store all information about a process for execution and context switching.

**"P S P C M S I" →**

* **P →** PID
* **S →** State
* **P →** Program Counter
* **C →** CPU Registers
* **M →** Memory
* **S →** Scheduling
* **I →** I/O

---

### **2) Process Synchronization**

**Process Synchronization** is the mechanism used by the OS to coordinate multiple processes so they access shared resources safely without conflicts or data inconsistency.

---

### **3) Critical Section**

A **critical section** = code that accesses shared resources and must be executed by only one process at a time.

**Critical Section** is the part of a process where shared resources are accessed and must be executed by only one process at a time.

---

### **4) Semaphore**

**Semaphore** is a synchronization variable used to control access to shared resources by multiple processes using wait (P) and signal (V) operations.

A semaphore is a synchronization tool used in operating systems to control how multiple processes or threads access shared resources safely.

#### *Basic Operations*

* **wait (P operation)** → tries to enter, decreases the count
* **signal (V operation)** → leaves, increases the count

#### *Types of Semaphores*

**1. Binary Semaphore (0 or 1)**

* **1 →** resource is available

* **0 →** resource is not available (someone is using it)

* Works like a lock (mutex)

* Only one process can enter at a time

**2. Counting Semaphore (0 to N)**

* Allows multiple processes (up to a limit)
* Used when multiple instances of a resource exist

#### *Meaning of Values (0 to n)*

* **n →** all resources are free
* **1 to n →** some resources are in use
* **0 →** no resources available (process must wait)

A 0–n semaphore counts how many resource instances are available, and blocks processes when the count reaches 0.

---

### **5) Concurrent Processes**

**Concurrent Processes** are processes that execute simultaneously or overlap in execution time, potentially interacting with shared resources.

---

### **6) Co-operating Processes**

**Co-operating Processes** is one that can affect or be affected by other processes while executing. These processes typically share data, communicate, or work together toward a common task.

---

### **7) Mutex vs Semaphore**

A **mutex** (short for mutual exclusion) is a synchronization tool used to ensure that only one process or thread can access a critical section at a time.

#### *Mutex*

* Only one process at a time
* Simpler, strict locking mechanism

#### *Semaphore*

* Can allow multiple processes (0 to n)
* Uses a counter

---

### **8) Race Condition**

A **race condition** occurs when multiple processes access shared data simultaneously, leading to unpredictable and incorrect results.

---

### **9) Precedence Graph**

A **precedence graph** is a directed graph used to check whether a transaction schedule is conflict-serializable by detecting cycles.

#### *How to Check Correctness*

* If the graph has **no cycles → schedule is serializable (safe)**
* If the graph has a **cycle → schedule is not serializable (unsafe)**

---

### **10) Key Characteristics**

* **Process creation:** A parent creates child processes
* **Resource sharing:** Children may share resources with parent
* **Execution:** Parent and child can run concurrently
* **Termination:**

  * Child may finish before parent
  * Or parent may terminate and affect children

---

### **11) Monitor**

A **monitor** is a high-level synchronization mechanism that allows only one process at a time to access shared data, using built-in mutual exclusion and condition variables.

#### *Condition Variables*

Monitors also use condition variables for waiting and signaling:

* **wait() →** process goes to sleep
* **signal() →** wakes up a waiting process

This helps coordinate processes more efficiently.

---

### **12) IMP**

**Semaphore** is a counter that allows multiple threads to access resources up to a limit.
**Mutex** is a lock that allows only one thread at a time.
**Monitor** is a high-level construct that automatically manages mutual exclusion and synchronization using built-in mechanisms.

---

### **13) Dining Philosopher Problem**

#### *a) The Problem*

*Each philosopher tries to:*

* Pick up left fork
* Pick up right fork
* Eat
* Put down forks

**What can go wrong?**

#### *b) Deadlock Situation*

*If all philosophers pick up their left fork at the same time:*

* Everyone is holding one fork
* No one can get the second fork
* Everyone waits forever

**This is called deadlock**

#### *c) Other Issues*

* **Starvation:** One philosopher may never get both forks
* **Concurrency control:** Multiple processes competing for limited resources

#### *d) Why This Problem is Important*

*It helps us understand:*

* Resource sharing
* Deadlock conditions
* Process synchronization

#### *e) Common Solutions (High-Level)*

* Allow only 4 philosophers at a time
* Use mutex/semaphores to control fork access
* Make philosophers pick forks in a specific order

> “The Dining Philosopher Problem is a synchronization problem where multiple processes compete for limited resources, demonstrating deadlock and starvation issues.”

---

### **14) Reader–Writer Problem**

“The **Reader–Writer problem** ensures that multiple readers can access shared data simultaneously, but writers get exclusive access to prevent data inconsistency.”

“There are three conflict types:

* **write–write**
* **write–read**
* **read–write**

All of which can cause inconsistency. Only **read–read** is safe because it doesn’t modify data.”

---

### **15) Producer–Consumer Problem**

#### *The Basic Idea*

There are two types of processes:

* **Producer →** generates data (items)
* **Consumer →** uses or removes that data

Both share a buffer (queue) of fixed size.

---

#### *The Problem*

Because the buffer is limited:

* If the buffer is **full → producer must wait**
* If the buffer is **empty → consumer must wait**

Without proper control:

* Data may be overwritten
* Consumer may read invalid data
* Race conditions occur

---

#### *Key Conditions*

* Producer cannot add data if buffer is full
* Consumer cannot remove data if buffer is empty
* Only one process should access buffer at a time (**critical section**)

---

#### *How It Is Solved (Using Semaphores)*

We use **three semaphores**:

* **mutex →** ensures mutual exclusion (only one accesses buffer)
* **empty →** counts empty slots
* **full →** counts filled slots

---

#### *Initialization*

* **empty = n** (buffer size)
* **full = 0**
* **mutex = 1**

---

#### *Working Logic*

**Producer:**

* wait(empty)
* wait(mutex)
* add item
* signal(mutex)
* signal(full)

**Consumer:**

* wait(full)
* wait(mutex)
* remove item
* signal(mutex)
* signal(empty)

---

### **16) Classical Synchronization Algorithms**

“For two processes, **Peterson’s algorithm** ensures mutual exclusion using flags and turn variables. For n processes, **Lamport’s Bakery algorithm** is used, where processes take numbers and the smallest number gets access to the critical section.”

---

### **17) Classical Two-Process Solution**

This is for exactly two processes (**P1 and P2**).

#### *Peterson’s Solution (Most Important)*

This is the standard classical solution.

**Key Idea:**
Use two variables:

* **flag[i] →** indicates if a process wants to enter
* **turn →** whose turn it is

---

#### *Logic (for process i)*

```
flag[i] = true;
turn = j;
while (flag[j] && turn == j);
// critical section
flag[i] = false;
```

---

#### *What It Ensures*

* **Mutual exclusion ✔**
* **No deadlock ✔**
* **No starvation ✔**

---

### **18) Classical N-Process Solutions**

When we have more than 2 processes, Peterson alone doesn’t work directly.

---

#### *(A) Bakery Algorithm (Lamport’s Bakery)*

This is the most famous n-process solution.

**Idea:**

* Like taking a token number in a bakery
* Process with the smallest number enters first

---

#### *Steps*

* Process takes a number
* Wait until its number is the smallest
* Enter critical section
* Reset number after leaving

---

#### *What It Ensures*

* **Mutual exclusion ✔**
* **Fairness ✔ (no starvation)**

---

### **19) Hardware Primitives for Synchronization**

“**Hardware primitives** are atomic CPU instructions like Test-and-Set and Compare-and-Swap that ensure safe synchronization by preventing race conditions.”

“**Atomic** means: once started, no interruption is possible”

---

#### *Important Hardware Primitives*

**1. Test-and-Set (TAS)**
This is the most common one.

**Idea:**
Check value and set it in one atomic step

**Working:**

* If lock was **false → process enters**
* If lock was **true → process waits**

---

**2. Compare-and-Swap (CAS)**

**Idea:**
Compare a value and update it only if it matches expected value

Used in modern systems for efficient locking.

---

#### *Key Characteristics*

* Executed at hardware level (CPU instruction)
* **Atomic → no interruption**
* Used to build:

  * Mutex
  * Semaphore
  * Spinlocks

---

### **20) Thread**

A **thread** is the **smallest unit of execution within a process**.

* A process can have **multiple threads**

* All threads share the same:

  * Memory
  * Resources

* But each thread has its own:

  * Program counter
  * Stack
  * Registers

👉 Threads are often called **“lightweight processes”**

---

### **21) Why Threads Are Used**

Threads make programs:

* **Faster →** parallel execution
* **Responsive →** UI doesn’t freeze
* **Efficient →** less overhead than processes

---

### **22) Types of Threads**

#### *1. User-Level Threads*

* Managed by user programs
* Fast but less powerful

#### *2. Kernel-Level Threads*

* Managed by OS
* Slower but more control

---

### **23) Multithreading Example**

Think of a web browser:

* One thread → loading page
* One thread → playing video
* One thread → handling clicks

All happen simultaneously.

---

### **24) Advantages and Disadvantages of Threads**

#### *Advantages*

* Better CPU utilization
* Faster execution
* Easy communication (shared memory)

#### *Disadvantages*

* Synchronization issues (race condition)
* Debugging is harder
* Can lead to deadlocks

---

“A **thread** is the smallest unit of execution within a process that shares resources with other threads, enabling efficient and concurrent execution.”

---

### **25) Multithreading Models**

These describe the relationship between **user-level threads** and **kernel-level threads**.

---

#### *1. Many-to-One Model*

* Many user threads → one kernel thread
* Managed in user space

**Pros:** fast, low overhead
**Cons:** if one blocks → all block

**Example systems:** early Java threading, some old libraries

---

#### *2. One-to-One Model*

* Each user thread → one kernel thread

**Pros:** true parallelism
**Cons:** higher overhead

**Used in:** Windows operating system, Linux operating system

---

#### *3. Many-to-Many Model*

* Many user threads mapped to many kernel threads

**Pros:** flexible, efficient
**Cons:** complex to implement

---

### **26) Scheduler Activations**

#### *What It Is*

A mechanism where:

* The OS (kernel) and user-level thread library **cooperate**
* Kernel informs the user-level scheduler about events using **upcalls**

---

#### *Key Idea*

* Kernel gives a set of **virtual processors** to user threads
* User-level library decides which thread runs
* Kernel notifies when:

  * Thread blocks
  * Thread resumes

👉 Combines:

* Efficiency of user threads
* Power of kernel threads

---

“**Scheduler activations** provide coordination between user-level and kernel-level threads by allowing the kernel to notify the thread library about scheduling events.”

---

### **27) Examples of Threaded Programs**

#### *1. Web Browser*

* One thread → UI
* One → network requests
* One → rendering

---

#### *2. Web Server*

* Each client request handled by a separate thread

---

#### *3. Word Processor*

* Typing
* Spell checking
* Auto-save

All in parallel

---

#### *4. Database System*

* Multiple queries handled simultaneously using threads

---

“**Multithreading models** define how user and kernel threads are mapped, such as many-to-one, one-to-one, and many-to-many. **Scheduler activations** allow coordination between user and kernel threads using upcalls. Threaded programs like browsers and servers use multiple threads to perform tasks concurrently and efficiently.”

---
### **28) Deadlock**

A deadlock is a state where a set of processes are permanently blocked because each process is waiting for a resource held by another process.

To make it concrete, imagine two processes:

* Process A holds Resource 1 and is waiting for Resource 2
* Process B holds Resource 2 and is waiting for Resource 1

Neither can move forward because each is waiting for the other to release a resource. This circular waiting creates a deadlock.

---

### **29) The Four Necessary Conditions (Coffman Conditions)**

For a deadlock to occur, all four of these conditions must hold true:

#### *1. Mutual Exclusion*

At least one resource cannot be shared and is held exclusively by one process.

#### *2. Hold and Wait*

A process is holding at least one resource and waiting to acquire additional resources.

#### *3. No Preemption*

Resources cannot be forcibly taken away; they must be released voluntarily.

#### *4. Circular Wait*

A circular chain of processes exists where each process is waiting for a resource held by the next.

If even one of these conditions is prevented, deadlock cannot occur.

---

### **32) How to Handle Deadlocks**

#### *1. Prevention*

Design the system so at least one of the four conditions cannot happen
Example: enforce a strict order of resource acquisition

#### *2. Avoidance*

Dynamically check if allocating a resource will lead to deadlock
Example: Banker’s Algorithm

#### *3. Detection and Recovery*

Allow deadlocks to occur, detect them, and recover by:

* Killing a process
* Releasing resources

---

### **33) Starvation**

Starvation is a condition where a process waits indefinitely for resources because other processes continuously get preference.

#### *How to Prevent Starvation*

* Aging: Gradually increase the priority of waiting processes over time
* Fair scheduling algorithms (e.g., Round Robin)
* Balanced resource allocation strategies

#### *Deadlock vs Starvation (Quick Difference)*

* Deadlock → All involved processes are blocked forever
* Starvation → Some processes keep running, but one waits indefinitely

---

### **34) Security Vulnerabilities**

These are weaknesses attackers exploit:

#### *Buffer Overflow*

Occurs when a program writes more data than a buffer can hold, overwriting memory and potentially executing malicious code.

#### *Trapdoors (Backdoors)*

Hidden entry points in programs that bypass normal authentication.

#### *Backdoors*

Similar to trapdoors but often intentionally left for debugging or later exploited.

#### *Cache Poisoning*

Corrupting cache data (e.g., DNS cache) so users are redirected to malicious sites.

---

### **35) Application Security**

#### *Virus*

A malicious program that attaches to files and spreads when executed.

---

### **36) Program Threats**

* Trojan Horse: Malicious code disguised as legitimate software
* Logic Bomb: Triggers on a specific condition
* Worm: Self-replicates across networks

---

### **37) System and Network Threats**

* Denial of Service (DoS): Overloads system resources
* Man-in-the-Middle (MITM): Intercepts communication
* Phishing: Tricks users into revealing credentials
* Replay Attacks: Reuses captured data

---
### **38) Logical Address Space**

A **logical address** (also called *virtual address*) is the address generated by the CPU when a program executes.

* It is what the **program sees and uses**
* Each process has its **own logical address space**
* Starts typically from **0 up to a limit** (e.g., 0 to 4GB)

👉 Example:
When a program accesses memory location `100`, that is a **logical address**, not the real location in RAM.

---

### **38-A) Physical Address Space**

A **physical address** is the actual location in **main memory (RAM)**.

* It is the **real address in hardware**
* Managed by the **memory unit**
* Not directly visible to the user program

👉 Example:
Logical address `100` may map to physical address `5000` in RAM.

---

### **39) Address Translation (Key Concept)**

The mapping from logical → physical address is done by a hardware component called the **MMU (Memory Management Unit)**.

* CPU generates logical address
* MMU converts it into physical address
* Program never sees the physical address

---

### **40) Simple Diagram (Verbal Explanation)**

```
CPU → Logical Address → MMU → Physical Address → Memory
```

---

### **41) Why This Separation is Important**

* **Memory Protection**: Processes cannot access each other's memory
* **Efficient Memory Use**: Supports paging and segmentation
* **Virtual Memory**: Allows programs larger than RAM

Logical address is the virtual address generated by the CPU, while physical address is the actual address in RAM obtained after translation by the MMU.

---

### **42) Swapping**

Swapping is a memory management technique where a process is temporarily moved from main memory (RAM) to secondary storage (disk) and brought back when needed.

#### *Why Swapping is Used*

* To free up RAM for other processes
* To support multiprogramming (running multiple processes)

#### *How It Works*

* Process is in RAM
* OS moves it to disk (swap out)
* Later, OS brings it back to RAM (swap in)

#### *Key Points*

* Requires swap space on disk
* Involves I/O operations (slow compared to RAM)
* Excessive swapping leads to thrashing (performance degradation)

---

### **43) Contiguous Memory Allocation**

In this technique, each process is allocated a single continuous block of memory.

#### *Types of Contiguous Allocation*

##### *a) Fixed Partitioning*

* Memory is divided into fixed-size partitions
* One process per partition

Problem: Internal fragmentation (unused space inside partition)

##### *b) Variable Partitioning*

* Memory is allocated based on process size
* Partitions are created dynamically

Problem: External fragmentation (free memory scattered)

---

### **44) Thrashing**

Thrashing in operating systems refers to a situation where the system spends more time swapping pages in and out of memory than actually executing processes. It is essentially a performance collapse caused by excessive paging.

---

### **45) Paging**

Paging is a memory management technique that divides:

* Logical memory → Pages (fixed size)
* Physical memory → Frames (same size as pages)

#### *How It Works*

* Each page is mapped to a frame using a page table
* Logical address = (page number + offset)
* The OS uses the page table to find the corresponding frame

---

### **46) Segmentation**

Segmentation divides memory based on logical units of a program:

* Code
* Data
* Stack

Each segment can have a different size.

---

### **47) Offset**

An offset is the part of an address that specifies the exact location inside a page or segment.

* Page number → which page
* Offset → line number on that page

---
### **48) Page Replacement**

Page replacement is used in virtual memory systems when:

* A page fault occurs
* There are no free frames available

👉 The OS must decide which page to remove from memory to load the new page.

---

### **49) Page Replacement Algorithms**

#### *1. FIFO (First-In, First-Out)*

Replaces the oldest page in memory

#### *2. Optimal (OPT) - (only theory)*

Replaces the page that will not be used for the longest time in future

#### *3. LRU (Least Recently Used)*

Replaces the page that was not used for the longest time in past

#### *4. LFU (Least Frequently Used)*

Removes the page with the lowest usage count

Optimal (theoretically best), LRU (practically used)

---

### **50) One-Line Answer**

First Fit, Best Fit, and Worst Fit are memory allocation strategies used in contiguous memory allocation to decide how processes are placed in available memory blocks, each with trade-offs in speed and fragmentation.

---

### **51) First Fit**

Allocates the first block of memory that is large enough.

#### *Advantages*

* Fast and simple
* Less search time

#### *Disadvantages*

* Causes external fragmentation
* Leaves small unusable gaps

---

### **52) Best Fit**

Allocates the smallest block that is sufficient.

#### *Advantages*

* Minimizes wasted space initially
* Better memory utilization (in theory)

#### *Disadvantages*

* Slower (must search entire memory)
* Creates many tiny fragments

---

### **53) Worst Fit**

Allocates the largest available block.

#### *Advantages*

* Leaves large leftover blocks
* Reduces small fragment creation

#### *Disadvantages*

* Poor memory utilization
* Can waste large memory blocks

---
### **54) Interrupt**

Interrupt = A signal that temporarily stops the CPU to handle an important event

---

### **55) Types of Interrupts**

#### *1. Hardware Interrupts*

Generated by physical devices
Example: keyboard, mouse, disk

#### *2. Software Interrupts*

Generated by programs
Example: system calls (asking OS for services)

#### *3. Timer Interrupts*

Used by OS to manage multitasking
Example: switching between processes

---

### **56) Fragmentation**

#### *Internal Fragmentation*

Unused space inside allocated memory block
Happens in paging / fixed partitions

👉 Example: Page size 4KB, process uses 3KB → 1KB wasted

#### *External Fragmentation*

Free memory exists but is scattered
Happens in segmentation / contiguous allocation

👉 Solution: Compaction

---

### **57) Overlays**

Technique to run programs larger than memory

* Only required parts of program are loaded at a time

---

### **58) Virtual Memory**

Virtual memory allows:

* Execution of programs larger than physical memory

#### *Key Idea*

* Only part of program is in RAM
* Rest stays on disk

---

### **59) Demand Paging**

A type of virtual memory where:

* Pages are loaded only when needed

#### *Working*

* Page not in memory → page fault
* OS loads it on demand

#### *Advantages*

* Efficient memory use
* Faster program start

#### *Disadvantages*

* Page fault overhead
* Can cause thrashing

---
### **60) File and File System Mounting**

A file is a collection of related data stored on secondary storage.

File system mounting is the process of making a storage device (like a hard disk, USB drive, or partition) accessible to the operating system by attaching it to a directory.

#### *What does “mount” mean?*

To mount means to connect a file system to a specific folder (called a mount point) so you can access its files.

* Without mounting, the OS cannot use the data on that device.

---

### **61) Allocation Methods in File Systems**

There are three main methods:

---

### **62) Contiguous Allocation**

In **contiguous allocation**, all blocks of a file are stored **next to each other** on the disk.

**Example:**
If a file needs 4 blocks, it might be stored in blocks 10, 11, 12, 13.

#### *Advantages*

* Very fast access (sequential and direct)
* Simple to implement

#### *Disadvantages*

* **External fragmentation** (free space gets scattered)
* Difficult to expand file size later

---

### **63) Linked Allocation**

In **linked allocation**, file blocks are **scattered anywhere on disk**, and each block contains a pointer to the next block.

**Example:**
Block 5 → Block 20 → Block 13 → Block 8

#### *Advantages*

* No external fragmentation
* Files can grow easily

#### *Disadvantages*

* Slower access (must follow pointers)
* Pointer storage overhead
* Not good for direct/random access

---

### **64) Indexed Allocation**

In **indexed allocation**, a special block called an **index block** stores all the addresses of the file’s blocks.

**Example:**
Index block → [10, 25, 3, 18]

#### *Advantages*

* Supports direct access
* No external fragmentation
* Flexible file growth

#### *Disadvantages*

* Extra space needed for index block
* Slight overhead for small files

---
### **65) Types of Devices**

#### *Dedicated Devices*

* Assigned to only one process at a time
* Example: printer

**Advantages**

* No conflict
* Simple management

**Disadvantages**

* Poor utilization (others must wait)

---

#### *Shared Devices*

* Multiple processes can use the device simultaneously
* Example: disk

**Advantages**

* Better utilization
* Efficient

**Disadvantages**

* Requires synchronization

---

#### *Virtual Devices*

* OS creates virtual instances of devices
* Example: spooling for printers

👉 A single physical device behaves like multiple devices

---

### **66) Direct Access Storage Devices (DASD)**

Devices like hard disks that allow direct data access.

---

#### *Channels*

* Specialized processors that manage I/O operations
* Offload work from CPU

👉 CPU gives instruction → channel handles data transfer

---

#### *Control Units*

* Interface between device and system
* Manage device operations

👉 Control signals and communication

---

### **67) Disk Scheduling Methods (in simple language)**

Disk scheduling is the technique used by the operating system to decide **which disk request to handle first**.

---

### **68) FCFS (First Come First Serve)**

Requests are handled **in the order they arrive**.

**Example:**
Queue: 98, 183, 37 → processed in same order

#### *Advantages*

* Simple and fair

#### *Disadvantages*

* Poor performance (long seek time)

---

### **69) SSTF (Shortest Seek Time First)**

The request closest to the current head position is served first.

#### *Advantages*

* Faster than FCFS
* Reduces seek time

#### *Disadvantages*

* Can cause **starvation** (far requests may wait too long)

---

### **70) SCAN (Elevator Algorithm)**

The disk head moves in one direction, serving requests, then reverses direction.

#### *Advantages*

* Better performance than SSTF
* Less starvation

#### *Disadvantages*

* Slight delay for newly arrived requests

---

### **71) C-SCAN (Circular SCAN)**

The head moves in one direction only. After reaching the end, it jumps back to the beginning.

#### *Advantages*

* Provides **uniform waiting time**

#### *Disadvantages*

* Extra movement when jumping back

---

### **72) LOOK and C-LOOK**

These are improved versions of SCAN and C-SCAN.

* **LOOK:** Goes only as far as the last request (not the disk end)
* **C-LOOK:** Same as C-SCAN but only up to last request

#### *Advantages*

* Avoid unnecessary movement
* More efficient

---
### **73) Introduction to IPC**

**Inter-Process Communication (IPC)** is a mechanism that allows processes to **communicate and share data** with each other.

---

### **74) Why IPC is Needed**

* Processes are isolated for safety
* They still need to **exchange information**
* Required for coordination and synchronization

👉 Example: One process produces data, another consumes it

---

### **75) IPC Methods**

IPC is broadly divided into:

* **Shared Memory**
* **Message Passing**

---

### **76) Pipes**

Pipes allow communication between processes using a **unidirectional data stream**.

#### *Types*

* **Unnamed Pipes**

  * Used between related processes (parent-child)

* **Named Pipes (FIFOs)**

  * Used between unrelated processes

---

### **77) popen() and pclose()**

* **popen()**

  * Opens a pipe to execute a command
  * Returns a file pointer

* **pclose()**

  * Closes the pipe
  * Waits for process termination

👉 Used for process communication via command execution

---

### **78) Shared Memory**

Shared memory allows multiple processes to **access the same memory region**.

#### *Features*

* Fastest IPC method
* No need for kernel intervention after setup

#### *Issue*

* Requires **synchronization** (semaphores, mutex)

---

### **79) FIFOs (Named Pipes)**

* Special type of pipe with a **name in the file system**
* Allows communication between **unrelated processes**

#### *Characteristics*

* Works like a file
* Persistent until deleted

---

### **80) Message Queues**

Processes communicate by sending **messages to a queue**.

#### *Features*

* Messages stored in kernel
* Supports **asynchronous communication**
* Can prioritize messages

#### *Advantages*

* No shared memory issues
* Easier synchronization

---
