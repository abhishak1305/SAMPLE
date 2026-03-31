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
