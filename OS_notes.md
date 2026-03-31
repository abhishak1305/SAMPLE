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
