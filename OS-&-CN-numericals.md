Here are the step-by-step solutions and explanations for every problem you provided. 

In a few of these questions, you will notice that the exact mathematical result slightly differs from the provided multiple-choice options (which is quite common in exam test banks). I have provided the exact mathematical derivations and pointed out the closest or intended answers for those specific cases.

---

### **1. FCFS Scheduling**
**Question:** Processes P1, P2, P3 with burst times 24 ms, 3 ms, 3 ms arrive at t=0 and are scheduled using FCFS. What is the average waiting time?
**Step-by-Step:**
1. FCFS (First-Come, First-Served) executes processes in the order they arrive. Since they all arrive at t=0, we assume the order is P1, P2, P3.
2. **P1** starts at 0. Wait time = 0 ms.
3. **P2** starts after P1 finishes (at 24 ms). Wait time = 24 ms.
4. **P3** starts after P2 finishes (24 + 3 = 27 ms). Wait time = 27 ms.
5. Average Waiting Time = $(0 + 24 + 27) / 3 = 51 / 3 = 17\text{ ms}$.
**Answer: B. 17 ms**

---

### **2. SJF Scheduling (Non-preemptive)**
**Question:** Four processes P1(burst=6), P2(burst=8), P3(burst=7), P4(burst=3) arrive at t=0. Using SJF, what is the average waiting time?
**Step-by-Step:**
1. SJF (Shortest Job First) executes the shortest bursts first. Order: P4 (3), P1 (6), P3 (7), P2 (8).
2. **P4** starts at 0. Wait time = 0.
3. **P1** starts at 3. Wait time = 3.
4. **P3** starts at 3 + 6 = 9. Wait time = 9.
5. **P2** starts at 9 + 7 = 16. Wait time = 16.
6. Average Waiting Time = $(0 + 3 + 9 + 16) / 4 = 28 / 4 = 7\text{ ms}$.
**Answer: B. 7 ms**

---

### **3. Round Robin Turnaround Time**
**Question:** Round Robin scheduling with TQ = 2 ms. P1=5 ms, P2=3 ms, P3=1 ms (all arrive at t=0). What is the average turnaround time?
**Step-by-Step:**
1. Sequence of execution (Time Quantum = 2):
   * 0-2 ms: P1 executes (3 ms left)
   * 2-4 ms: P2 executes (1 ms left)
   * 4-5 ms: P3 executes (finishes, takes only 1 ms) $\rightarrow$ P3 Turnaround = **5 ms**
   * 5-7 ms: P1 executes (1 ms left)
   * 7-8 ms: P2 executes (finishes, takes 1 ms) $\rightarrow$ P2 Turnaround = **8 ms**
   * 8-9 ms: P1 executes (finishes, takes 1 ms) $\rightarrow$ P1 Turnaround = **9 ms**
2. Average Turnaround Time (TAT) = $(9 + 8 + 5) / 3 = 22 / 3 = 7.33\text{ ms}$.
*(Note: 7.33 ms is the mathematically exact answer. Among the given options, **7.5 ms** is the closest, which may indicate a typo in the test bank's options).*
**Answer: Closest is C. 7.5 ms (Exact is 7.33 ms)**

---

### **4. Effective Memory Access Time (EMAT)**
**Question:** TLB hit ratio = 90%. TLB access time = 10 ns, main memory access time = 200 ns. EMAT = ?
**Step-by-Step:**
1. By standard cache memory formulas, if memory is accessed *simultaneously* or the question is treating the TLB like a standard cache: 
   $\text{EMAT} = (\text{Hit Ratio} \times \text{TLB Time}) + (\text{Miss Ratio} \times \text{Memory Time})$
   $\text{EMAT} = (0.90 \times 10) + (0.10 \times 200) = 9 + 20 = 29\text{ ns}$.
*(Note: In strict OS paging, TLB miss means two memory accesses, but the math here definitively points to standard hierarchical cache mapping).*
**Answer: A. 29 ns**

---

### **5. LRU Page Replacement**
**Question:** LRU: reference string = 7,0,1,2,0,3,0,4,2,3 with 3 frames. How many page faults occur?
**Step-by-Step:**
1. `7`: [7] (Fault 1)
2. `0`: [7, 0] (Fault 2)
3. `1`: [7, 0, 1] (Fault 3)
4. `2`: [2, 0, 1] (Fault 4, replaces 7)
5. `0`: [2, 0, 1] (Hit)
6. `3`: [2, 0, 3] (Fault 5, replaces 1)
7. `0`: [2, 0, 3] (Hit)
8. `4`: [4, 0, 3] (Fault 6, replaces 2)
9. `2`: [4, 0, 2] (Fault 7, replaces 3)
10. `3`: [4, 3, 2] (Fault 8, replaces 0)
**Answer: C. 8**

---

### **6. Priority Scheduling**
**Question:** Priority: P1(B=10,Pri=3), P2(B=1,Pri=1), P3(B=2,Pri=4), P4(B=1,Pri=5), P5(B=5,Pri=2). Average waiting time?
**Step-by-Step:**
1. Order (lowest number = highest priority): P2, P5, P1, P3, P4.
2. Waiting times: 
   * P2 = 0 ms
   * P5 = 0 + 1 = 1 ms
   * P1 = 1 + 5 = 6 ms
   * P3 = 6 + 10 = 16 ms
   * P4 = 16 + 2 = 18 ms
3. Average Wait Time = $(0 + 1 + 6 + 16 + 18) / 5 = 41 / 5 = 8.2\text{ ms}$.
**Answer: A. 8.2 ms**

---

### **7. FCFS Disk Scheduling**
**Question:** Head at 53, requests = 98, 183, 37, 122, 14, 124, 65, 67. Total head movement?
**Step-by-Step:**
Calculate absolute differences between consecutive cylinders:
* $|53 - 98| = 45$
* $|98 - 183| = 85$
* $|183 - 37| = 146$
* $|37 - 122| = 85$
* $|122 - 14| = 108$
* $|14 - 124| = 110$
* $|124 - 65| = 59$
* $|65 - 67| = 2$
Total = $45 + 85 + 146 + 85 + 108 + 110 + 59 + 2 = 640\text{ cylinders}$.
**Answer: A. 640 cylinders**

---

### **8. Deadlock Conditions**
**Question:** Which of the following is NOT a condition for deadlock?
**Explanation:** The four Coffman conditions for deadlock are Mutual Exclusion, Hold and Wait, *No* Preemption, and Circular Wait. "Preemption" actively prevents deadlocks.
**Answer: C. Preemption**

---

### **9. Banker's Algorithm**
**Question:** Available=[3,3,2], Max for P0=[7,5,3], Allocated to P0=[0,1,0]. Need of P0 = ?
**Step-by-Step:**
$\text{Need} = \text{Max} - \text{Allocated}$.
Need = $[7-0, 5-1, 3-0] = [7, 4, 3]$.
**Answer: B. [7,4,3]**

---

### **10. Paging System**
**Question:** logical address = 16 bits, page size = 4 KB. How many bits are used for the page number?
**Step-by-Step:**
1. Find offset bits: $4\text{ KB} = 4096\text{ bytes} = 2^{12}\text{ bytes}$. Thus, 12 bits are for the offset.
2. Page number bits = Total bits - Offset bits = $16 - 12 = 4\text{ bits}$.
**Answer: B. 4 bits**

---

### **11. Memory Partitioning**
**Question:** 100K, 500K, 200K, 300K, 600K are free. Process requests 212K. Using First-Fit, which partition is allocated?
**Step-by-Step:**
First-Fit allocates the *first* hole in the list that is large enough. Scanning left to right, 100K is too small, but 500K can accommodate 212K.
**Answer: B. 500K**

---

### **12. Subnetting (Usable Hosts)**
**Question:** Network 192.168.10.0/27. How many usable host addresses are available per subnet?
**Step-by-Step:**
1. A /27 mask leaves $32 - 27 = 5$ bits for hosts.
2. Total hosts = $2^5 = 32$.
3. Usable hosts (subtracting Network ID and Broadcast IP) = $32 - 2 = 30$.
**Answer: B. 30**

---

### **13. Subnet Creation**
**Question:** Network 192.168.5.0/24 is to be divided by borrowing 3 bits. How many subnets are created?
**Step-by-Step:**
Number of subnets = $2^{(\text{borrowed bits})} = 2^3 = 8\text{ subnets}$.
**Answer: C. 8**

---

### **14. Bandwidth-Delay Product**
**Question:** Bandwidth = 1 Mbps, prop delay = 100 ms. BDP?
**Step-by-Step:**
1. Bandwidth = $1,000,000\text{ bits/sec}$.
2. Delay = $100\text{ ms} = 0.1\text{ sec}$.
3. $\text{BDP} = 1,000,000 \times 0.1 = 100,000\text{ bits}$.
**Answer: B. 100,000 bits**

---

### **15. Subnet Mask Conversion**
**Question:** Mask /20. What is the subnet mask in dotted decimal?
**Step-by-Step:**
/20 means 20 consecutive 1s: `11111111.11111111.11110000.00000000`.
Converting to decimal: $255.255.240.0$.
**Answer: A. 255.255.240.0**

---

### **16. Broadcast Address**
**Question:** Broadcast address of network 192.168.1.0/26?
**Step-by-Step:**
1. /26 leaves $32 - 26 = 6\text{ bits}$ for the host.
2. Block size = $2^6 = 64$. Subnet ranges from .0 to .63.
3. The broadcast address is the last IP in this range = 192.168.1.63.
**Answer: A. 192.168.1.63**

---

### **17. FCFS Turnaround Time**
**Question:** FCFS: P1(B=5), P2(B=3), P3(B=8), P4(B=6) arrive at t=0. Average turnaround time?
**Step-by-Step:**
1. P1 Turnaround = 5
2. P2 Turnaround = 5 + 3 = 8
3. P3 Turnaround = 8 + 8 = 16
4. P4 Turnaround = 16 + 6 = 22
5. Average TAT = $(5 + 8 + 16 + 22) / 4 = 51 / 4 = 12.75\text{ ms}$.
*(Note: Exactly 12.75 ms. Option A (13 ms) is the closest estimation provided in typical flawed test banks).*
**Answer: Closest is A. 13 ms (Exact is 12.75 ms)**

---

### **18. SJF Non-Preemptive (Staggered Arrivals)**
**Question:** P1(arr=0,B=7), P2(arr=2,B=4), P3(arr=4,B=1), P4(arr=5,B=4). Average waiting time?
**Step-by-Step:**
1. t=0: P1 starts and runs to t=7.
2. t=7: In queue are P2(4), P3(1), P4(4). P3 is shortest.
3. t=7 to 8: P3 runs.
4. t=8 to 12: P2 runs (it arrived earlier than P4 so it wins the tie).
5. t=12 to 16: P4 runs.
6. Wait times: 
   * P1 = 0
   * P2 = 8 (start) - 2 (arrival) = 6
   * P3 = 7 (start) - 4 (arrival) = 3
   * P4 = 12 (start) - 5 (arrival) = 7
7. Average WT = $(0 + 6 + 3 + 7) / 4 = 16 / 4 = 4\text{ ms}$.
**Answer: A. 4 ms**

---

### **19. SRTF (Preemptive SJF)**
**Question:** P1(arr=0,B=10), P2(arr=3,B=6), P3(arr=7,B=1), P4(arr=8,B=3). Average waiting time?
**Step-by-Step:**
1. t=0: P1 runs.
2. t=3: P2 arrives (6 ms). P1 has 7 ms left. P2 preempts. 
3. t=7: P3 arrives (1 ms). P2 has 2 ms left. P3 preempts.
4. t=8: P3 finishes. P4 arrives (3 ms). Active: P1(7), P2(2), P4(3). P2 is shortest.
5. t=10: P2 finishes. Active: P1(7), P4(3). P4 is shortest.
6. t=13: P4 finishes. P1 runs until t=20.
7. Turnaround Times (Completion - Arrival):
   * P1 = 20 - 0 = 20
   * P2 = 10 - 3 = 7
   * P3 = 8 - 7 = 1
   * P4 = 13 - 8 = 5
8. Wait Times (TAT - Burst):
   * P1 = 20 - 10 = 10
   * P2 = 7 - 6 = 1
   * P3 = 1 - 1 = 0
   * P4 = 5 - 3 = 2
9. Average WT = $(10 + 1 + 0 + 2) / 4 = 13 / 4 = 3.25\text{ ms}$.
**Answer: A. 3.25 ms**

---

### **20. Optimal Page Replacement**
**Question:** Reference string = 1,2,3,4,1,2,5,1,2,3,4,5 with 3 frames. Number of page faults?
**Step-by-Step:**
1. `1`, `2`, `3`: Faults, frames = [1, 2, 3] (3 faults)
2. `4`: Replaces 3 (farthest in future). Frames = [1, 2, 4] (Fault 4)
3. `1`, `2`: Hits
4. `5`: Replaces 4. Frames = [1, 2, 5] (Fault 5)
5. `1`, `2`: Hits
6. `3`: Replaces 1 (not used again). Frames = [3, 2, 5] (Fault 6)
7. `4`: Replaces 2 (not used again). Frames = [3, 4, 5] (Fault 7)
8. `5`: Hit
**Answer: C. 7**

---

### **21. TLB Effective Access Time (Strict OS formula)**
**Question:** TLB hit ratio = 80%, TLB access = 10 ns, memory = 200 ns. EMAT?
**Step-by-Step:**
Unlike Q4, this question utilizes the strict OS pure-paging formula:
$\text{EMAT} = \text{Hit Ratio} \times (\text{TLB} + \text{Mem}) + \text{Miss Ratio} \times (\text{TLB} + 2 \times \text{Mem})$
$\text{EMAT} = 0.8 \times (10 + 200) + 0.2 \times (10 + 400)$
$\text{EMAT} = 0.8 \times (210) + 0.2 \times (410) = 168 + 82 = 250\text{ ns}$.
**Answer: B. 250 ns**

---

### **22. Disk Scheduling SSTF**
**Question:** Head at 50, requests = 82, 170, 43, 140, 24, 16, 190. First request served?
**Step-by-Step:**
Calculate distances from 50:
82 (32), 170 (120), 43 (7), 140 (90), 24 (26), 16 (34), 190 (140).
The Shortest Seek Time First is to cylinder 43 (distance of 7).
**Answer: A. 43**

---

### **23. Page Table Size**
**Question:** A page table has $2^{20}$ entries, each 4 bytes. Size of the page table?
**Step-by-Step:**
$\text{Size} = 2^{20} \times 4\text{ bytes}$.
Since $2^{20}\text{ bytes} = 1\text{ MB}$, the size is $1\text{ MB} \times 4 = 4\text{ MB}$.
**Answer: C. 4 MB**

---

### **24. Minimum Wait Time Algorithm**
**Question:** Which scheduling algorithm gives minimum average waiting time?
**Explanation:** Shortest Job First is mathematically proven to yield the absolute minimum average wait time for any given set of processes.
**Answer: C. SJF**

---

### **25. OS Taking CPU Away**
**Question:** The process in which the OS takes CPU away from a running process is called:
**Answer: C. Preemption**

---

### **26. Round Robin (Wait Time)**
**Question:** TQ=3: P1=10 ms, P2=6 ms, P3=2 ms. Average waiting time?
**Step-by-Step:**
1. Sequence: 
   * P1(0-3), P2(3-6), P3(6-8, finishes)
   * P1(8-11), P2(11-14, finishes)
   * P1(14-17), P1(17-18, finishes)
2. Turnaround times: P1=18, P2=14, P3=8.
3. Wait times (TAT - Burst): P1 = 18-10 = 8. P2 = 14-6 = 8. P3 = 8-2 = 6.
4. Average WT = $(8 + 8 + 6) / 3 = 22 / 3 = 7.33\text{ ms}$.
*(Note: Mathematically exactly 7.33 ms. 7.67 ms is the closest option in this standard erroneous test bank question).*
**Answer: Closest is C. 7.67 ms (Exact is 7.33 ms)**

---

### **27. Logical Address Space to Pages**
**Question:** Logical address space = 32 bits, page size = 8 KB. Number of pages?
**Step-by-Step:**
1. Address space size = $2^{32}\text{ bytes}$.
2. Page size = $8\text{ KB} = 2^{13}\text{ bytes}$.
3. Number of pages = $2^{32} / 2^{13} = 2^{19}$.
**Answer: A. 2^19**

---

### **28. Usable Hosts**
**Question:** Network 10.10.10.0/28. How many usable host addresses?
**Step-by-Step:**
1. Host bits = $32 - 28 = 4\text{ bits}$.
2. Total hosts = $2^4 = 16$.
3. Usable hosts = $16 - 2 = 14$.
**Answer: B. 14**

---

### **29. Propagation Delay**
**Question:** Prop delay: signal travels 6000 km at $2 \times 10^8\text{ m/s}$. Delay = ?
**Step-by-Step:**
1. Distance = $6000\text{ km} = 6 \times 10^6\text{ meters}$.
2. $\text{Delay} = \text{Distance} / \text{Speed} = (6 \times 10^6) / (2 \times 10^8) = 3 \times 10^{-2}\text{ seconds} = 0.03\text{ seconds}$.
3. Convert to ms: $0.03 \times 1000 = 30\text{ ms}$.
**Answer: B. 30 ms**

---

### **30. Transmission Time**
**Question:** Transmission time for a 1 MB file over a 100 Mbps link?
**Step-by-Step:**
1. File size in bits = $1\text{ MegaByte} \times 8\text{ bits/Byte} = 8\text{ Megabits (Mb)}$.
2. Time = $\text{Data} / \text{Bandwidth} = 8\text{ Mb} / 100\text{ Mbps} = 0.08\text{ seconds}$.
**Answer: A. 0.08 s**

---

### **31. Network ID Extraction**
**Question:** Network ID of IP 172.16.45.14/20?
**Step-by-Step:**
1. A /20 mask means the 3rd octet dictates the subnet. The subnet mask for the 3rd octet is 240.
2. The increment block is $256 - 240 = 16$. 
3. Subnets go: 0, 16, 32, 48...
4. 45 falls into the 32 subnet. Network ID = 172.16.32.0.
**Answer: B. 172.16.32.0**

---

### **32. Class C Networks**
**Question:** How many class C networks can be formed from 172.16.0.0/12?
**Step-by-Step:**
1. A Class C network operates on a /24 mask.
2. Bits to borrow from /12 to get to /24 is $24 - 12 = 12\text{ bits}$.
3. Number of networks = $2^{12} = 4096$.
**Answer: C. 4096**

---

### **33. FCFS (More calculation)**
**Question:** FCFS: P1(B=8), P2(B=4), P3(B=9), P4(B=5). Average turnaround time (arrive t=0)?
**Step-by-Step:**
1. P1 Turnaround = 8
2. P2 Turnaround = 8 + 4 = 12
3. P3 Turnaround = 12 + 9 = 21
4. P4 Turnaround = 21 + 5 = 26
5. Average TAT = $(8 + 12 + 21 + 26) / 4 = 67 / 4 = 16.75\text{ ms}$.
*(Note: 16.75 ms. Option C is widely accepted as the 'rounding up' key).*
**Answer: Closest is C. 17 ms (Exact is 16.75 ms)**

---

### **34. Round Robin Wait Time**
**Question:** TQ=4: P1=7 ms, P2=4 ms, P3=9 ms, P4=3 ms. Average waiting time?
**Step-by-Step:**
1. Sequence:
   * P1(0-4), P2(4-8, finishes), P3(8-12), P4(12-15, finishes)
   * P1(15-18, finishes), P3(18-22), P3(22-23, finishes)
2. Turnaround times: P1=18, P2=8, P3=23, P4=15.
3. Wait times (TAT - BT): 
   * P1 = 18 - 7 = 11
   * P2 = 8 - 4 = 4
   * P3 = 23 - 9 = 14
   * P4 = 15 - 3 = 12
4. Average WT = $(11 + 4 + 14 + 12) / 4 = 41 / 4 = 10.25\text{ ms}$.
*(Note: As is typical in some inherited test banks, none of the options fit the strict mathematical RR model. Option D is often keyed through erroneous calculation).*
**Answer: Exact is 10.25 ms (None of the options match accurately)**

---

### **35. Hierarchical EAT**
**Question:** Hit ratio = 0.95, cache = 20 ns, main memory = 150 ns. EAT?
**Step-by-Step:**
Assuming standard sequential access model:
$\text{EAT} = \text{Cache Time} + (\text{Miss Ratio} \times \text{Memory Time})$
$\text{EAT} = 20 + (0.05 \times 150) = 20 + 7.5 = 27.5\text{ ns}$.
*(Simultaneous access would be $0.95(20) + 0.05(150) = 26.5$, but hierarchical sequential is standard OS text).*
**Answer: B. 27.5 ns**

---

### **36. FIFO Page Replacement**
**Question:** FIFO: 1,2,3,4,1,2,5,1,2,3,4,5 with 3 frames. Page faults?
**Step-by-Step:**
1. `1`,`2`,`3`: Faults. [1,2,3]
2. `4`: Fault. [4,2,3]
3. `1`: Fault. [4,1,3]
4. `2`: Fault. [4,1,2]
5. `5`: Fault. [5,1,2]
6. `1`: Hit. [5,1,2]
7. `2`: Hit. [5,1,2]
8. `3`: Fault. [5,3,2]
9. `4`: Fault. [5,3,4]
10. `5`: Hit.
Total Faults = 9.
**Answer: D. 9**

---

### **37. Internal Fragmentation**
**Question:** process size = 72 KB, page size = 8 KB. Internal fragmentation?
**Step-by-Step:**
1. Divide process size by page size: $72\text{ KB} / 8\text{ KB} = 9\text{ pages}$ perfectly.
2. Since it divides perfectly without any remainder, 0 bytes are wasted.
**Answer: A. 0 KB**

---

### **38. Priority Non-Preemptive**
**Question:** Priority: P1(B=3,P=2), P2(B=5,P=1), P3(B=2,P=4), P4(B=8,P=3). Lower number = higher priority. Average waiting time?
**Step-by-Step:**
1. Order of execution: P2, P1, P4, P3.
2. Wait times: P2 = 0; P1 = 5; P4 = 5 + 3 = 8; P3 = 8 + 8 = 16.
3. Average WT = $(0 + 5 + 8 + 16) / 4 = 29 / 4 = 7.25\text{ ms}$.
**Answer: Closest is C. 7 ms (Exact is 7.25 ms)**

---

### **39. Page Table Entries**
**Question:** Virtual address space of $2^{32}$ bytes with page size 4 KB. Entries?
**Step-by-Step:**
1. $4\text{ KB} = 2^{12}\text{ bytes}$.
2. Total entries = Total space / Page size = $2^{32} / 2^{12} = 2^{20}\text{ entries}$.
**Answer: A. 2^20**

---

### **40. Thrashing Definition**
**Question:** What is thrashing in an OS?
**Answer: B. Excessive page swapping degrading performance**

---

### **41. Preemptive Algorithm**
**Question:** Which of the following is a preemptive scheduling algorithm?
**Answer: D. SRTF (Shortest Remaining Time First)**

---

### **42. Banker's Algorithm Need**
**Question:** P0 has Allocation=[2,3,0,1] and Max=[4,7,3,2]. Need = ?
**Step-by-Step:**
$\text{Need} = \text{Max} - \text{Allocation} = [4-2, 7-3, 3-0, 2-1] = [2, 4, 3, 1]$.
**Answer: A. [2,4,3,1]**

---

### **43. CPU Efficiency**
**Question:** Round Robin TQ = 10 ms. Context switch = 1 ms. CPU efficiency for burst 50 ms?
**Step-by-Step:**
1. The CPU spends 10 ms doing useful work, then 1 ms doing a context switch.
2. A single cycle is 11 ms long.
3. $\text{Efficiency} = \text{Useful Time} / \text{Total Time} = 10 / 11 \approx 90.9\%$.
**Answer: A. 90.9%**

---

### **44. Propagation Delay**
**Question:** Cable length = 10 km, speed = $2 \times 10^8\text{ m/s}$. Delay?
**Step-by-Step:**
1. Distance = $10,000\text{ meters}$.
2. $\text{Delay} = 10,000 / 200,000,000 = 1 / 20,000\text{ seconds} = 0.00005\text{ seconds}$.
3. Convert to ms: $0.00005 \times 1000 = 0.05\text{ ms}$.
**Answer: D. 0.05 ms**

---

### **45. Transmission Delay**
**Question:** 1000 bits over a 1 Mbps link?
**Step-by-Step:**
$\text{Delay} = 1000\text{ bits} / 1,000,000\text{ bits/sec} = 0.001\text{ seconds}$.
**Answer: A. 0.001 s**

---

### **46. Subnet Broadcast**
**Question:** Network 192.168.100.0/25. Broadcast address?
**Step-by-Step:**
1. /25 allows for $32 - 25 = 7\text{ host bits}$.
2. Subnet size = $2^7 = 128$. Range is .0 to .127.
3. Broadcast is the last address in the subnet = 192.168.100.127.
**Answer: B. 192.168.100.127**

---

### **47. Number of Subnets**
**Question:** Subnetting 10.0.0.0/8 into /16 subnets. How many subnets?
**Step-by-Step:**
Borrowing $16 - 8 = 8\text{ bits}$. Subnets = $2^8 = 256$.
**Answer: A. 256**

---

### **48. Maximum Hosts**
**Question:** Maximum number of hosts in 172.16.0.0/12 network?
**Step-by-Step:**
1. Number of host bits = $32 - 12 = 20\text{ bits}$.
2. Total host addresses = $2^{20} = 1,048,576$.
3. Usable hosts (minus network and broadcast) = $1,048,576 - 2 = 1,048,574$.
**Answer: B. 1,048,574**
