1)   **PCB** is a data structure used by OS to store all information about a process for execution and context switching.
      P S P C M S I" →
      P → PID
      S → State
      P → Program Counter
      C → CPU Registers
      M → Memory
      S → Scheduling
      I → I/O

2) **Process Synchronization** is the mechanism used by the OS to coordinate multiple processes so they access shared resources safely without conflicts or data inconsistency.

3) A **critical section** = code that accesses shared resources and must be executed by only one process at a time.
       **Critical Section** is the part of a process where shared resources are accessed and must be executed by only one process at a time.
4) **Semaphore** is a synchronization variable used to control access to shared resources by multiple processes using wait (P) and signal (V) operations.
      A semaphore is a synchronization tool used in operating systems to control how multiple processes or threads access shared resources safely.
         It uses two basic operations:
      
      wait (P operation) → tries to enter, decreases the count
      signal (V operation) → leaves, increases the count
         Types of semaphores
      
      1. Binary Semaphore (0 or 1)
            1 → resource is available
            0 → resource is not available (someone is using it)
      
            Works like a lock (mutex)
            Only one process can enter at a time
      
      2. Counting Semaphore (0 to N)
      
      Allows multiple processes (up to a limit)
      Used when multiple instances of a resource exist
   
      What values from 0 to n mean
      The number represents how many instances of a resource are available
      
      So:
      
      n → all resources are free
      any value between 1 and n → some resources are in use
      0 → no resources available (process must wait)
   
      A 0–n semaphore counts how many resource instances are available, and blocks processes when the count reaches 0.
   
5)  


