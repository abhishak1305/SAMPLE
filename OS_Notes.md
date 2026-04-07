# OPERATING SYSTEMS — Complete Theory Book

> **A Comprehensive Revision Guide for Exams, Placements & Interviews**

---

---

# UNIT 1: INTRODUCTION TO OPERATING SYSTEM

---

## 1.1 Operating System — Meaning

### Definition
An **Operating System (OS)** is a **system software** that acts as an **intermediary** between the computer hardware and the user. It manages computer hardware resources and provides services for the execution of application programs.

### Detailed Explanation

An OS is the most fundamental software that runs on a computer. Without an OS, a computer is just a collection of electronic components with no usable functionality.

#### Key Roles of an Operating System

**1. Resource Manager**
- The OS manages all hardware resources — CPU, memory, I/O devices, files, and network.
- It allocates resources to processes efficiently and fairly.

**2. Interface Provider**
- Provides a **user interface** (CLI — Command Line Interface, or GUI — Graphical User Interface) for users to interact with the computer.
- Provides an **API/System Call interface** for programs to request OS services.

**3. Extended Machine (Virtual Machine)**
- The OS hides the complexity of hardware from the user and presents a simpler, abstract machine.
- Users don't need to know about hardware registers, disk sectors, or interrupt handling — the OS handles all of that.

**4. Control Program**
- Controls the execution of user programs to prevent errors and improper use of the computer.
- Manages I/O device operations and ensures security.

#### Where the OS Sits

```
User Applications
      ↓
  Operating System (Kernel + System Programs)
      ↓
  Hardware (CPU, Memory, Disk, I/O Devices)
```

### Key Points / Highlights
- The OS is the **first software loaded** when a computer starts (after BIOS/firmware).
- The OS acts as a **resource manager**, **interface provider**, and **control program**.
- The **kernel** is the core part of the OS that runs in privileged mode.
- Without an OS, users would have to write programs in machine language for direct hardware control.

### MCQ Focus Section
- The OS acts as an **intermediary** between user and hardware.
- The core component of an OS is the **kernel**.
- The OS is classified as **system software**, not application software.
- The OS provides **abstraction** — hides hardware complexity from users.
- **Bootstrap loader** is the program that loads the OS into memory during startup.
- An OS is both a **resource allocator** and a **control program**.

---

## 1.2 Supervisor Mode and User Mode

### Definition
Modern processors operate in (at least) two distinct modes:
- **Supervisor Mode (Kernel Mode / Privileged Mode)**: The OS kernel runs in this mode with **unrestricted access** to all hardware and system instructions.
- **User Mode**: Application programs run in this mode with **restricted access** — they cannot directly access hardware or execute privileged instructions.

### Detailed Explanation

#### Why Two Modes?
- To **protect** the OS and critical system resources from being accidentally or maliciously damaged by user programs.
- A **mode bit** in the hardware indicates the current mode: **0 = Kernel Mode**, **1 = User Mode**.

#### Kernel Mode (Supervisor Mode)
- The OS kernel executes in this mode.
- Has **full access** to all hardware, memory, and CPU instructions.
- Can execute **privileged instructions** (e.g., I/O operations, interrupt management, modifying page tables, halting the CPU).
- A crash in kernel mode can bring down the **entire system**.

#### User Mode
- User applications execute in this mode.
- Has **limited access** — cannot directly access hardware or execute privileged instructions.
- If a user program attempts a privileged instruction, the hardware generates a **trap** (exception), and the OS takes control.
- A crash in user mode typically affects **only that program**, not the entire system.

#### Mode Switching
- When a user program needs OS services (e.g., file access, memory allocation), it makes a **system call**.
- The system call triggers a **trap/software interrupt**, switching the mode from **User → Kernel**.
- The OS executes the requested service in kernel mode.
- After completion, the mode switches back from **Kernel → User**, and control returns to the user program.

### Example
When a user program wants to read a file:
1. Program calls `read()` — a system call.
2. Mode switches from **User Mode → Kernel Mode** (via trap).
3. The OS kernel performs the file read operation.
4. Mode switches back from **Kernel Mode → User Mode**.
5. Data is returned to the program.

### Key Points / Highlights
- Two modes ensure **protection** and **security** of the OS.
- **Mode bit**: 0 = Kernel, 1 = User.
- **Privileged instructions** can only run in kernel mode.
- **System calls** trigger the switch from user mode to kernel mode.
- Mode switching involves a **trap** (software interrupt).

### MCQ Focus Section
- **Mode bit = 0** means the system is in **Kernel Mode**.
- **Mode bit = 1** means the system is in **User Mode**.
- **Privileged instructions** (e.g., I/O, halt, interrupt disable) can only be executed in **kernel mode**.
- If a user program tries to execute a privileged instruction, a **trap** occurs.
- The transition from user mode to kernel mode happens via a **system call** (trap/software interrupt).
- The transition from kernel mode to user mode happens when the OS returns control to the user process.
- **Dual-mode operation** protects the OS from errant user programs.
- Examples of privileged instructions: **HLT (halt CPU)**, **set timer**, **disable interrupts**, **modify page tables**, **I/O instructions**.

---

## 1.3 Multiprogramming and Multiprocessing System

### Definition
- **Multiprogramming**: The technique of keeping **multiple programs in main memory simultaneously** so that the CPU can switch between them, ensuring the CPU is never idle when there is work to do.
- **Multiprocessing**: A system with **two or more CPUs (processors)** within a single computer, allowing multiple processes to execute **truly simultaneously (in parallel)**.

### Detailed Explanation

#### Multiprogramming
- In a **uniprogramming** system, only one program is in memory at a time. When it waits for I/O, the CPU sits idle — very wasteful.
- In **multiprogramming**, multiple programs are loaded into memory. When the currently running program waits for I/O, the OS **switches the CPU to another ready program**.
- **Goal**: Maximize **CPU utilization** by reducing idle time.
- The OS uses **scheduling algorithms** to decide which program to run next.
- Multiprogramming does **not** mean programs run simultaneously — only one runs at a time on a single CPU. It is **concurrent** (interleaved), not parallel.
- **Multitasking** (Time-sharing) is a logical extension of multiprogramming where the CPU switches between programs so rapidly that users feel each program is running simultaneously. It provides **interactive** computing with **fast response times**.

#### Multiprocessing
- A system with **multiple physical CPUs/cores**.
- Multiple processes can run **truly in parallel** (at the same time) — one on each CPU.
- Types:
  - **Symmetric Multiprocessing (SMP)**: All processors are equal (peers). Each processor runs the OS and user processes. Most common today.
  - **Asymmetric Multiprocessing (AMP)**: One processor is the master (runs the OS); others are slaves (run user processes). The master assigns tasks.
- **Advantages**: Increased throughput, reliability (if one CPU fails, others continue), true parallelism.

#### Related Terms

| Term | Meaning |
|------|---------|
| **Multiprogramming** | Multiple programs in memory; CPU switches between them |
| **Multitasking** | Multiprogramming + frequent switching for interactivity |
| **Multiprocessing** | Multiple CPUs; true parallel execution |
| **Multithreading** | Multiple threads within a single process; can run concurrently/parallel |
| **Batch System** | Jobs submitted in batches; no user interaction during execution |

### Key Points / Highlights
- Multiprogramming improves **CPU utilization** by overlapping CPU and I/O operations.
- Multitasking adds **user interaction** and **fast response time** to multiprogramming.
- Multiprocessing provides **true parallelism** with multiple CPUs.
- SMP = all CPUs are equal; AMP = master-slave relationship.

### MCQ Focus Section
- **Multiprogramming** keeps multiple programs in **memory** to keep the CPU busy.
- **Multitasking** = multiprogramming with **time-sharing** and user interaction.
- **Multiprocessing** = multiple **CPUs/processors** for parallel execution.
- In multiprogramming on a single CPU, execution is **concurrent** (not truly parallel).
- **SMP** = all processors can run both OS and user code. **AMP** = master assigns work.
- The primary goal of multiprogramming is to maximize **CPU utilization**.
- The primary goal of time-sharing (multitasking) is to minimize **response time**.
- **Batch systems** do not provide user interaction — jobs are processed in batches.
- Multiprogramming requires **memory management** and **CPU scheduling**.
- **Degree of multiprogramming** = number of processes currently in memory.

---

## 1.4 OS Structure

### Definition
**OS Structure** refers to the internal organization and design of an operating system. Different structural approaches offer different trade-offs in terms of performance, security, maintainability, and flexibility.

### Detailed Explanation

#### 1. Monolithic Structure (Simple / No Clear Structure)
- The entire OS runs as a **single large program** in kernel mode.
- All OS services (file system, memory management, process management, I/O, etc.) run in the same address space.
- **Advantages**: Fast performance (no mode switching between services, direct function calls).
- **Disadvantages**: Difficult to maintain and extend. A bug in any part can crash the entire system. No clear separation of concerns.
- **Examples**: Early UNIX, MS-DOS (partially).

#### 2. Layered Approach
- The OS is organized into **hierarchical layers**, where each layer uses services only from the **layer below** it and provides services to the **layer above**.
- **Layer 0** = Hardware. **Topmost Layer** = User interface.
- **Advantages**: Modularity, easy debugging (one layer at a time), clear separation of concerns.
- **Disadvantages**: Difficult to define layers properly. Performance overhead due to inter-layer communication. Not widely used in practice.
- **Example**: THE operating system (by Dijkstra).

#### 3. Microkernel
- Only the **essential** services run in kernel mode — **process management, memory management, and IPC (Inter-Process Communication)**.
- All other services (file system, device drivers, network stack) run in **user mode** as separate processes (servers).
- Communication between services happens through **message passing** (IPC).
- **Advantages**: More stable and secure (if a service crashes, it doesn't bring down the kernel). Easier to extend and port. Smaller kernel.
- **Disadvantages**: **Performance overhead** due to frequent message passing between user-mode services.
- **Examples**: Mach, MINIX, QNX, L4.

#### 4. Modular Approach (Loadable Kernel Modules)
- The kernel has a core set of components, and additional services are loaded as **modules** dynamically at runtime.
- Modules can be loaded and unloaded without rebooting.
- Combines benefits of monolithic (performance) and microkernel (modularity).
- **Examples**: Modern Linux, Solaris.

#### 5. Hybrid Kernel
- Combines elements of **monolithic and microkernel** architectures.
- Critical services run in kernel mode (for performance), while some services run in user mode (for stability).
- **Examples**: Windows NT, macOS (XNU kernel).

#### 6. Virtual Machine (VM) Architecture
- Creates an illusion that each user has their own **dedicated machine** (hardware).
- A **hypervisor** (Virtual Machine Monitor — VMM) runs on the actual hardware and creates virtual machines.
- Each VM can run its own OS.
- **Types**:
  - **Type 1 (Bare-metal)**: Hypervisor runs directly on hardware. Examples: VMware ESXi, Hyper-V, Xen.
  - **Type 2 (Hosted)**: Hypervisor runs on top of a host OS. Examples: VMware Workstation, VirtualBox.

### Key Points / Highlights
| Structure | Key Feature | Example |
|-----------|------------|---------|
| Monolithic | Everything in kernel space | Early UNIX, Linux (partially) |
| Layered | Hierarchical layers | THE OS |
| Microkernel | Minimal kernel, services in user space | Mach, MINIX, QNX |
| Modular | Loadable kernel modules | Modern Linux, Solaris |
| Hybrid | Mix of monolithic + microkernel | Windows NT, macOS |
| Virtual Machine | Hypervisor creates VMs | VMware, VirtualBox |

### MCQ Focus Section
- **Monolithic** kernel = all services in kernel mode. Fastest but least modular.
- **Microkernel** = minimal kernel. Most modular and secure, but **slower** (IPC overhead).
- **Layered OS** was proposed by **Dijkstra** (THE operating system).
- In a **microkernel**, file systems and device drivers run in **user mode**.
- In a **monolithic kernel**, a bug in a driver can crash the **entire system**.
- **Linux** is primarily **monolithic** but supports **loadable kernel modules** (modular).
- **Windows NT** uses a **hybrid kernel** architecture.
- A **Type 1 hypervisor** runs directly on hardware (bare-metal).
- A **Type 2 hypervisor** runs on top of an existing OS (hosted).
- **Microkernel** uses **message passing** for communication between services.

---

## 1.5 System Calls

### Definition
A **System Call** is a programmatic interface through which a user program requests a service from the **operating system kernel**. It provides the means for a user-level process to interact with the hardware and access kernel services in a controlled manner.

### Detailed Explanation

#### Why System Calls?
- User programs run in **user mode** and cannot directly access hardware.
- System calls provide a **controlled gateway** to kernel-mode services.
- They ensure **security and protection** — the OS validates each request before executing it.

#### How System Calls Work
1. User program invokes a system call (e.g., `open()`, `read()`, `write()`).
2. A **trap instruction** (software interrupt) is executed.
3. The CPU switches from **User Mode → Kernel Mode**.
4. The OS identifies the system call number and executes the corresponding kernel function.
5. The result is returned to the user program.
6. The CPU switches back from **Kernel Mode → User Mode**.

#### Categories of System Calls

**1. Process Control**
- Create, terminate, load, execute, wait, signal processes.
- Examples: `fork()`, `exec()`, `exit()`, `wait()`, `kill()`.

**2. File Management**
- Create, delete, open, close, read, write, reposition files.
- Examples: `open()`, `close()`, `read()`, `write()`, `lseek()`, `unlink()`.

**3. Device Management**
- Request, release, read, write devices.
- Examples: `ioctl()`, `read()`, `write()`.

**4. Information Maintenance**
- Get/set time, date, system data, process attributes.
- Examples: `getpid()`, `alarm()`, `sleep()`, `time()`.

**5. Communication**
- Create/delete communication connection, send/receive messages.
- Examples: `pipe()`, `shmget()`, `msgget()`, `socket()`, `send()`, `recv()`.

**6. Protection**
- Set/get file permissions, allow/deny access.
- Examples: `chmod()`, `chown()`, `umask()`.

#### System Call vs Library Function
- A **system call** directly invokes kernel code (e.g., `write()`).
- A **library function** (e.g., `printf()`) is a user-space wrapper that may internally call system calls.
- Library functions provide **convenience and abstraction** over raw system calls.

### Key Points / Highlights
- System calls are the **primary interface** between user programs and the OS kernel.
- They trigger a **mode switch** from user mode to kernel mode.
- Six categories: **Process, File, Device, Information, Communication, Protection**.
- In UNIX/Linux, system calls are accessed via **C library (glibc)** wrapper functions.

### MCQ Focus Section
- A system call triggers a **trap** (software interrupt) to switch to kernel mode.
- `fork()` creates a **new process** in UNIX/Linux.
- `exec()` **replaces** the current process image with a new program.
- `open()`, `read()`, `write()`, `close()` are **file management** system calls.
- `wait()` makes a parent process wait for a child process to terminate.
- `exit()` terminates a process.
- System calls are executed in **kernel mode**.
- The system call interface is maintained by a **system call table** with numbered entries.
- **API** (Application Programming Interface) wraps system calls for ease of use (e.g., Win32 API, POSIX API).
- `fork()` returns **0 to the child** and the **child's PID to the parent**.

---

## 1.6 Functions of Operating System

### Definition
The functions of an OS are the core **services and operations** it provides to manage computer resources and facilitate user interaction.

### Detailed Explanation

**1. Process Management**
- Creating, scheduling, executing, suspending, resuming, and terminating processes.
- Process synchronization and inter-process communication.
- Deadlock handling.

**2. Memory Management**
- Tracking which parts of memory are in use and by whom.
- Allocating and deallocating memory to processes.
- Implementing virtual memory, paging, and segmentation.

**3. File System Management**
- Creating, deleting, reading, writing files and directories.
- Managing file permissions, ownership, and access control.
- Organizing files using directory structures.

**4. I/O Device Management**
- Managing all I/O devices (keyboard, mouse, disk, printer, monitor).
- Providing device drivers as interfaces between the OS and hardware.
- Buffering, caching, and spooling of I/O operations.

**5. Storage Management (Disk Management)**
- Managing disk space — allocation, deallocation, and free-space tracking.
- Disk scheduling algorithms for efficient disk access.

**6. Security and Protection**
- **Security**: Defending against external threats (viruses, unauthorized access).
- **Protection**: Controlling access to system resources among users and processes.
- Authentication (password, biometric) and access control (file permissions).

**7. Networking**
- Managing network connections and communication protocols.
- Enabling resource sharing over a network.

**8. User Interface**
- Providing **CLI** (command-line interface) and/or **GUI** (graphical user interface).
- Some systems provide both (e.g., Linux provides terminal + desktop environment).

### Key Points / Highlights
- The OS manages **five key resources**: CPU, Memory, Files, I/O Devices, and Network.
- Every function involves **allocation, monitoring, and deallocation** of resources.

### MCQ Focus Section
- **Process management** includes CPU scheduling, synchronization, and deadlock handling.
- **Memory management** implements virtual memory, paging, segmentation.
- **Spooling** (Simultaneous Peripheral Operations Online) queues I/O jobs (e.g., print queue).
- **Buffering** temporarily stores data during transfer between two devices of different speeds.
- **Caching** stores copies of frequently accessed data in faster storage.
- The OS provides both **security** (external threats) and **protection** (internal access control).

---

## 1.7 Evolution of Operating Systems

### Definition
Operating systems have evolved over decades from simple batch processing systems to the sophisticated, multi-user, multi-tasking systems we use today.

### Detailed Explanation

#### 1. No OS (1940s-1950s)
- Programs were written in **machine language** and entered via **punch cards**.
- The programmer had direct access to hardware.
- Only **one program** could run at a time.
- Very low CPU utilization — the CPU was idle during I/O operations.

#### 2. Batch Processing Systems (1950s-1960s)
- Jobs were collected and grouped into **batches**.
- An **operator** loaded batches into the computer; jobs ran one after another without user interaction.
- A **resident monitor** (early OS) managed job execution.
- **Improvement**: Reduced setup time between jobs.
- **Problem**: CPU still idle during I/O; no user interaction.

#### 3. Multiprogramming Systems (1960s)
- Multiple programs loaded into memory simultaneously.
- CPU **switches** to another job when the current one waits for I/O.
- **Greatly improved CPU utilization**.
- Required **memory management** and **CPU scheduling**.

#### 4. Time-Sharing (Multitasking) Systems (1960s-1970s)
- Extension of multiprogramming with **rapid CPU switching** among jobs.
- Each user gets a **time slice** (quantum) of CPU time.
- Provides **interactive** computing — users can interact with running programs.
- **Response time** is the key metric (fast response).
- Example: **MULTICS**, early **UNIX**.

#### 5. Personal Computer (PC) Operating Systems (1980s)
- OS designed for **single-user, single-machine** use.
- Emphasis on **user-friendliness** and GUI.
- Examples: **MS-DOS**, **Windows**, **Mac OS**.

#### 6. Distributed Operating Systems (1980s-1990s)
- Multiple computers connected by a network work together as a **unified system**.
- Resources are **shared** across machines transparently.
- Users don't need to know where resources are located.
- Example: **Amoeba**, **LOCUS**.

#### 7. Real-Time Operating Systems (RTOS)
- Designed for systems where **timing is critical** — response must be within a **strict deadline**.
- **Hard Real-Time**: Missing a deadline is a system failure (e.g., aircraft control, medical devices, ABS brakes).
- **Soft Real-Time**: Missing a deadline degrades quality but is tolerable (e.g., multimedia streaming, video conferencing).

#### 8. Mobile Operating Systems (2000s-Present)
- Designed for smartphones, tablets, and wearable devices.
- Optimized for **touch interfaces**, **battery efficiency**, and **wireless connectivity**.
- Examples: **Android**, **iOS**.

### Key Points / Highlights
| Era | OS Type | Key Feature |
|-----|---------|-------------|
| 1940s-50s | No OS | Direct hardware programming |
| 1950s-60s | Batch | Jobs in batches, no interaction |
| 1960s | Multiprogramming | Multiple jobs in memory |
| 1960s-70s | Time-Sharing | Interactive, time slices |
| 1980s | PC OS | Single user, GUI |
| 1980s-90s | Distributed | Network of computers |
| Ongoing | RTOS | Strict timing deadlines |
| 2000s+ | Mobile OS | Touch, battery, wireless |

### MCQ Focus Section
- **Batch systems** have no user interaction; jobs are processed in groups.
- **Multiprogramming** keeps CPU busy by switching during I/O waits.
- **Time-sharing** provides **interactive** computing with rapid CPU switching.
- **MULTICS** was a pioneering time-sharing OS; **UNIX** was derived from it.
- **Hard real-time** systems cannot miss deadlines; **Soft real-time** allows some tolerance.
- **MS-DOS** was a **single-user, single-tasking** OS.
- **UNIX** was one of the first time-sharing, multi-user operating systems.
- **Distributed OS** makes multiple computers appear as one system.
- **Spooling** was introduced in batch systems to overlap I/O with computation.
- The evolution order: No OS → Batch → Multiprogramming → Time-sharing → PC/Distributed/Real-time → Mobile.

---

---

# UNIT 2: PROCESS MANAGEMENT

---

## 2.1 Process Concept

### Definition
A **process** is a **program in execution**. It is an active entity, unlike a program which is a passive entity (a file stored on disk). A process includes the program code (text), current activity (program counter, registers), stack, data section, and heap.

### Detailed Explanation

#### Program vs Process
| Feature | Program | Process |
|---------|---------|---------|
| Nature | **Passive** (static) | **Active** (dynamic) |
| Stored In | Disk (file) | Main memory |
| Lifetime | Permanent (until deleted) | Temporary (created & terminated) |
| Resources | None | CPU, memory, files, I/O |
| Execution | Not executing | Currently executing |

- A single program can have **multiple processes** (e.g., multiple instances of a web browser).
- Each process has its own **independent address space**, program counter, and resources.

#### Components of a Process (Process Memory Layout)

```
+-------------------+
|      Stack        |  ← Function call frames, local variables, return addresses
+-------------------+
|        ↓          |
|    (free space)   |
|        ↑          |
+-------------------+
|       Heap        |  ← Dynamically allocated memory (malloc, new)
+-------------------+
|       Data        |  ← Global and static variables
+-------------------+
|       Text        |  ← Program code (instructions)
+-------------------+
```

- **Text Section**: The compiled program code (instructions). Read-only.
- **Data Section**: Global and static variables. Divided into:
  - **Initialized data**: Variables with predefined values.
  - **Uninitialized data (BSS)**: Variables initialized to zero by default.
- **Heap**: Memory dynamically allocated during runtime (e.g., `malloc()`, `new`). Grows upward.
- **Stack**: Stores function call frames — local variables, return addresses, parameters. Grows downward. Follows **LIFO** order.

### Key Points / Highlights
- A **process** = program + execution state + resources.
- A process has four memory segments: **Text, Data, Heap, Stack**.
- Multiple processes can be created from the **same program**.
- Each process has a **unique Process ID (PID)**.

### MCQ Focus Section
- A process is a **program in execution** — it is an **active** entity.
- The **text section** contains the executable code.
- The **stack** stores function call information; the **heap** stores dynamically allocated memory.
- Stack grows **downward**; Heap grows **upward**.
- Two processes of the same program have **separate address spaces** but share the same **text (code)** section conceptually.
- A **zombie process** is a process that has finished execution but still has an entry in the process table.
- An **orphan process** is a process whose parent has terminated.

---

## 2.2 Process Life Cycle (Process States)

### Definition
During its lifetime, a process transitions through several **states** depending on its current activity and resource availability. These states define the **process life cycle**.

### Detailed Explanation

#### Process States

**1. New (Created)**
- The process is being **created**.
- OS is allocating resources and initializing the PCB.

**2. Ready**
- The process is loaded into memory and is **waiting to be assigned the CPU**.
- It has all resources except the CPU.
- Multiple processes can be in the ready state — they form the **ready queue**.

**3. Running**
- The process is currently **being executed by the CPU**.
- On a single-processor system, only **one process** can be in the running state at a time.

**4. Waiting (Blocked)**
- The process is waiting for some **event** to occur (e.g., I/O completion, signal, resource availability).
- It cannot proceed until the event happens.
- When the event occurs, it moves back to the **Ready** state.

**5. Terminated (Exit)**
- The process has **finished execution** or has been killed.
- The OS deallocates resources and removes the process from the process table.

#### State Transitions

```
       ┌──────────────────────────────┐
       ↓                              │
[New] → [Ready] → [Running] → [Terminated]
            ↑          │
            │          ↓
            └── [Waiting/Blocked]
```

- **New → Ready**: Process is admitted to the ready queue.
- **Ready → Running**: CPU **scheduler** selects the process (**dispatch**).
- **Running → Waiting**: Process requests I/O or waits for an event.
- **Waiting → Ready**: I/O or event completes.
- **Running → Ready**: Process is **preempted** (time quantum expires, higher-priority process arrives).
- **Running → Terminated**: Process finishes execution or is killed.

### Key Points / Highlights
- Five states: **New, Ready, Running, Waiting, Terminated**.
- A process moves from Ready → Running when it is **dispatched** by the scheduler.
- A process moves from Running → Waiting when it needs **I/O or an event**.
- **Preemption** moves a process from Running → Ready (without it finishing).

### MCQ Focus Section
- A process in **Ready** state has everything **except the CPU**.
- A process in **Waiting (Blocked)** state is waiting for an **I/O or event**.
- Only **one process** can be in the **Running** state per CPU at a time.
- **Preemption** = forcibly removing a running process and putting it back in the Ready queue.
- A process goes from **Running → Ready** on preemption (e.g., time slice expired).
- A process goes from **Running → Waiting** when it initiates an I/O operation.
- A process goes from **Waiting → Ready** when its I/O completes (NOT directly to Running).
- A **new process** starts in the **New** state, not Ready.
- The **scheduler** decides which Ready process gets the CPU next.

---

## 2.3 Process Control Block (PCB)

### Definition
A **Process Control Block (PCB)** is a **data structure** maintained by the operating system for each process. It contains all the information needed to manage the process. Also known as **Task Control Block (TCB)**.

### Detailed Explanation

#### Contents of a PCB

| Field | Description |
|-------|-------------|
| **Process ID (PID)** | Unique identifier for the process |
| **Process State** | Current state (New, Ready, Running, Waiting, Terminated) |
| **Program Counter (PC)** | Address of the next instruction to execute |
| **CPU Registers** | Contents of all CPU registers (accumulator, index, stack pointer, general-purpose registers) |
| **CPU Scheduling Info** | Priority, scheduling queue pointers, scheduling parameters |
| **Memory Management Info** | Page tables, segment tables, base/limit registers |
| **Accounting Info** | CPU time used, time limits, process creation time, PID |
| **I/O Status Info** | List of I/O devices allocated, open file list |
| **Parent PID** | PID of the parent process |
| **Child PIDs** | List of child process IDs |

#### Role of PCB in Context Switching
- When the OS switches the CPU from one process to another (**context switch**):
  1. Save the state of the current process into its **PCB**.
  2. Load the state of the next process from its **PCB**.
- The PCB is the **blueprint** that allows a process to be paused and resumed seamlessly.

#### Context Switch
- **Context Switch** = saving the context (state) of one process and loading the context of another.
- This is **pure overhead** — no useful work is done during a context switch.
- Context switch time depends on **hardware support** (number of registers, memory speed).
- Frequent context switches reduce overall system performance.

### Key Points / Highlights
- The PCB is the **most important data structure** in process management.
- Every process has **exactly one PCB**, stored in **kernel memory**.
- The PCB enables **context switching** — pausing and resuming processes.
- Context switching is **overhead** — the OS should minimize it.

### MCQ Focus Section
- PCB contains: **PID, process state, program counter, registers, scheduling info, memory info**.
- A **context switch** saves state to one PCB and loads state from another.
- Context switching is **pure overhead** — no user work is done.
- The **program counter** in the PCB stores the address of the **next instruction**.
- PCBs are stored in the **kernel's process table**.
- PCB is also called **Task Control Block (TCB)**.
- During a context switch, the **entire register set** of the process is saved/restored.
- More registers → longer context switch time.

---

## 2.4 Operations on Processes

### Definition
The OS provides operations to **create, terminate, suspend, resume, and manage** processes during their lifetime.

### Detailed Explanation

#### 1. Process Creation
- A process can create new processes. The creating process = **parent**; the created process = **child**.
- This creates a **process tree** (hierarchy).
- In UNIX/Linux: `fork()` creates a child process.
- Child can be:
  - **Duplicate of parent** (fork): Child gets a copy of the parent's address space.
  - **New program** (exec): After fork, the child calls `exec()` to load a new program.
- Resource sharing options: Parent and child share all, some, or no resources.
- Execution options: Parent and child execute **concurrently**, or parent **waits** for child (`wait()`).

#### 2. Process Termination
- A process terminates when it finishes its last statement or calls `exit()`.
- The OS deallocates all resources (memory, files, I/O).
- A parent can terminate a child using `kill()` or `abort()`.
- **Cascading termination**: If a parent terminates, all its children may also be terminated (OS-dependent).
- **Zombie process**: A child process that has terminated but whose parent hasn't called `wait()` yet. Its PCB still exists in the process table.
- **Orphan process**: A child process whose parent has terminated. In UNIX, orphans are adopted by the **init** process (PID 1).

#### 3. Process Suspension and Resumption
- A process can be **suspended** (swapped out to disk) to free memory.
- It can be **resumed** (swapped back in) when needed.

### Key Points / Highlights
- `fork()` creates a **copy** of the parent process.
- `exec()` replaces the process image with a new program.
- `wait()` makes the parent wait for the child to terminate.
- `exit()` terminates a process.
- **Zombie** = terminated child, parent hasn't called wait().
- **Orphan** = child whose parent terminated, adopted by init (PID 1).

### MCQ Focus Section
- `fork()` returns **0** to the child and **child's PID** to the parent.
- `fork()` returns **-1** on failure.
- After `fork()`, parent and child execute **concurrently**.
- `exec()` does **not create a new process** — it replaces the current process image.
- A process calls `exit()` to terminate itself.
- `wait()` blocks the parent until a child terminates.
- **Zombie process**: Terminated child + parent hasn't called `wait()`.
- **Orphan process**: Active child + parent has terminated. Adopted by **init (PID 1)**.
- **Cascading termination**: All descendants are killed when an ancestor terminates.
- In UNIX, every process (except init) has a parent — forming a **process tree**.

---

## 2.5 Cooperating and Independent Processes

### Definition
- **Independent Process**: A process that cannot affect or be affected by other processes. It does not share data with any other process.
- **Cooperating Process**: A process that can affect or be affected by other processes. It shares data or communicates with other processes.

### Detailed Explanation

#### Independent Processes
- Operates in complete isolation.
- No shared data, no inter-process communication.
- Result is **deterministic** — depends only on its own input.
- Example: A standalone calculator program.

#### Cooperating Processes
- Interact with other processes through **shared memory** or **message passing**.
- Result may be **non-deterministic** (depends on execution order/timing).
- **Reasons for cooperation**:
  - **Information sharing**: Multiple users need access to the same data.
  - **Computation speedup**: Break a task into subtasks that run in parallel.
  - **Modularity**: Divide functions into separate processes for better design.
  - **Convenience**: Users may want to work on multiple tasks simultaneously.

#### Communication Models
1. **Shared Memory**: Processes share a region of memory. Faster (no kernel involvement after setup). Requires **synchronization** (e.g., semaphores). Example: Producer-Consumer problem.
2. **Message Passing**: Processes communicate by sending and receiving messages through the OS. Slower (kernel involved in every message). Easier to implement in distributed systems. Example: Pipes, message queues.

### Key Points / Highlights
- Independent processes are isolated; cooperating processes share data/communicate.
- Two IPC models: **Shared Memory** (faster) and **Message Passing** (easier for distributed).
- Cooperating processes need **synchronization** to avoid race conditions.

### MCQ Focus Section
- An **independent process** cannot affect or be affected by other processes.
- A **cooperating process** shares data with or communicates with other processes.
- **Shared memory** is faster because it avoids kernel involvement after initial setup.
- **Message passing** is better for **distributed systems** (processes on different machines).
- **Race condition** occurs when the output depends on the **order of execution** of cooperating processes.
- The **Producer-Consumer problem** is a classic example of cooperating processes.

---

## 2.6 Process Management in UNIX

### Definition
In **UNIX/Linux**, processes are managed using a combination of system calls and kernel data structures. Every process is identified by a unique **PID** and is part of a **process tree** rooted at the **init** process (PID 1).

### Detailed Explanation

#### Key System Calls for Process Management in UNIX

| System Call | Function |
|-------------|----------|
| `fork()` | Creates a new child process (duplicate of parent) |
| `exec()` family | Replaces process image with a new program (`execl`, `execv`, `execvp`, etc.) |
| `wait()` / `waitpid()` | Parent waits for child to terminate |
| `exit()` | Terminates the calling process |
| `getpid()` | Returns PID of the calling process |
| `getppid()` | Returns PID of the parent process |
| `kill()` | Sends a signal to a process (can be used to terminate) |
| `nice()` | Changes the priority of a process |

#### UNIX Process Creation Flow
1. System boots → **init process** (PID 1) is created by the kernel.
2. `init` spawns other system processes (e.g., `login`, `getty`).
3. User logs in → a **shell process** is created.
4. User types a command → shell calls `fork()` to create a child, then `exec()` to run the command.
5. Shell calls `wait()` to wait for the command to finish (for foreground processes).

#### UNIX Process Hierarchy
- Every process has a **single parent** (except `init`).
- Process tree rooted at **init** (PID 1) or **systemd** (modern Linux).
- Processes can be managed using signals (SIGKILL, SIGTERM, SIGSTOP, SIGCONT, etc.).

### Key Points / Highlights
- UNIX process creation: `fork()` → `exec()` → `wait()` → `exit()`.
- **init** (PID 1) is the ancestor of all processes.
- **Signals** are used for inter-process communication and process control.
- `kill -9 <PID>` sends **SIGKILL** (forceful termination, cannot be caught).

### MCQ Focus Section
- PID **0** is the **idle/swapper** process; PID **1** is **init/systemd**.
- `fork()` creates a **child** that is a copy of the parent.
- `exec()` does NOT return on success — the process image is replaced.
- **SIGKILL (signal 9)** cannot be caught or ignored — always kills the process.
- **SIGTERM (signal 15)** is the default signal sent by `kill` — can be caught and handled gracefully.
- **SIGSTOP** pauses a process; **SIGCONT** resumes it.
- In UNIX, `init` process **never dies** — it adopts all orphan processes.

---

---

# UNIT 3: CPU SCHEDULING

---

## 3.1 Types of Scheduling

### Definition
**CPU Scheduling** is the mechanism by which the OS decides which process in the ready queue gets the CPU next. Scheduling occurs at different levels depending on when the decision is made.

### Detailed Explanation

#### 1. Long-Term Scheduler (Job Scheduler)
- Selects which processes from the **job pool (disk)** should be brought into **main memory** (ready queue).
- Controls the **degree of multiprogramming** (number of processes in memory).
- Runs **infrequently** — when a process terminates, a new one may be admitted.
- Should select a good mix of **CPU-bound** and **I/O-bound** processes.
  - **CPU-bound**: Spends most time doing computations (few I/O requests).
  - **I/O-bound**: Spends most time doing I/O (frequent, short CPU bursts).

#### 2. Short-Term Scheduler (CPU Scheduler)
- Selects which process from the **ready queue** should get the CPU next.
- Runs **very frequently** — invoked every time a scheduling decision is needed.
- Must be **fast** because it executes so often.
- This is the scheduler people usually mean when they say "CPU scheduling."

#### 3. Medium-Term Scheduler (Swapper)
- **Swaps processes** out of memory to disk (and back) to manage the degree of multiprogramming.
- Used when too many processes are in memory — some are swapped out to reduce contention.
- Reduces the degree of multiprogramming temporarily.

| Scheduler | Selects From → To | Frequency | Controls |
|-----------|-------------------|-----------|----------|
| Long-Term | Disk → Ready Queue | Infrequent | Degree of multiprogramming |
| Short-Term | Ready Queue → CPU | Very Frequent | Which process runs next |
| Medium-Term | Memory ↔ Disk (Swap) | Moderate | Memory utilization |

### Key Points / Highlights
- **Long-term** controls how many processes are in memory.
- **Short-term** decides which process runs next — must be very fast.
- **Medium-term** manages swapping for memory management.
- Time-sharing systems may not have a long-term scheduler.

### MCQ Focus Section
- The **short-term scheduler** is the most frequently invoked.
- The **long-term scheduler** controls the **degree of multiprogramming**.
- **CPU-bound** processes need more CPU time; **I/O-bound** need more I/O time.
- A good long-term scheduler selects a **mix** of CPU-bound and I/O-bound processes.
- The **medium-term scheduler** performs **swapping** (moving processes to/from disk).
- **Time-sharing systems** typically have **no long-term scheduler** — all submitted processes go directly to memory.
- The short-term scheduler is also called the **CPU scheduler** or **dispatcher**.

---

## 3.2 Scheduling Criteria

### Definition
**Scheduling criteria** are metrics used to evaluate and compare the performance of different CPU scheduling algorithms.

### Detailed Explanation

| Criteria | Definition | Goal |
|----------|-----------|------|
| **CPU Utilization** | Percentage of time the CPU is busy | **Maximize** |
| **Throughput** | Number of processes completed per unit time | **Maximize** |
| **Turnaround Time** | Total time from process submission to completion. TAT = Completion Time − Arrival Time | **Minimize** |
| **Waiting Time** | Total time a process spends waiting in the ready queue. WT = TAT − Burst Time | **Minimize** |
| **Response Time** | Time from submission to the **first response** (not completion). Important in interactive systems | **Minimize** |

### Key Points / Highlights
- **Maximize**: CPU Utilization, Throughput.
- **Minimize**: Turnaround Time, Waiting Time, Response Time.
- **Turnaround Time** = Completion Time − Arrival Time.
- **Waiting Time** = Turnaround Time − Burst Time (CPU time).
- **Response Time** is critical for **interactive (time-sharing)** systems.

### MCQ Focus Section
- **Throughput** measures how many processes **complete** per unit time.
- **Turnaround Time** includes **waiting time + execution time + I/O time**.
- **Waiting Time** = total time spent in the **ready queue**.
- **Response Time** = time from **submission to first response** (not completion).
- We want to **maximize** CPU utilization and throughput.
- We want to **minimize** turnaround time, waiting time, and response time.
- For **batch systems**, throughput and turnaround time are most important.
- For **interactive systems**, response time is most important.

---

## 3.3 CPU Scheduler — Preemptive and Non-Preemptive

### Definition
- **Non-Preemptive Scheduling**: Once a process is allocated the CPU, it keeps the CPU until it **voluntarily releases** it (by terminating or entering a waiting state). The scheduler cannot forcibly take the CPU away.
- **Preemptive Scheduling**: The OS can **forcibly take the CPU** from a running process and assign it to another process (e.g., when a higher-priority process arrives or the time quantum expires).

### Detailed Explanation

#### Non-Preemptive (Cooperative)
- Process keeps the CPU until it finishes or blocks for I/O.
- Simple to implement — no need for timers or priority handling during execution.
- **Problem**: A long process can monopolize the CPU (**starvation** of short processes).
- Used in simpler systems (e.g., early Windows 3.x).

#### Preemptive
- The OS can interrupt a running process at any time.
- Requires a **timer interrupt** (hardware clock) to enforce CPU time limits.
- Better for **interactive and real-time** systems.
- Requires more careful handling of **shared data** (race conditions possible if kernel data is being updated when preemption occurs).
- Used in modern OS (Windows, Linux, macOS).

#### Scheduling Decisions Occur When:
1. Process switches from **Running → Waiting** (e.g., I/O request) — Non-preemptive
2. Process switches from **Running → Ready** (e.g., interrupt, time slice expired) — **Preemptive only**
3. Process switches from **Waiting → Ready** (e.g., I/O complete) — **Preemptive only**
4. Process **Terminates** — Non-preemptive

**Non-preemptive** scheduling makes decisions only at points 1 and 4.
**Preemptive** scheduling can make decisions at **all four points**.

### Key Points / Highlights
- **Non-preemptive**: Process keeps CPU until done or blocked. Simple but can cause starvation.
- **Preemptive**: OS can take CPU away. Used in modern OS. Better for interactivity.
- Preemptive scheduling requires **timer interrupts** and careful **synchronization**.

### MCQ Focus Section
- **FCFS** and **Non-preemptive SJF** are **non-preemptive**.
- **Round Robin**, **Preemptive SJF (SRTF)**, and **Preemptive Priority** are **preemptive**.
- Preemptive scheduling is necessary for **time-sharing** and **real-time** systems.
- Non-preemptive scheduling is simpler but suffers from the **convoy effect** (in FCFS).
- Preemptive scheduling may cause **race conditions** if not handled properly.
- **Dispatcher** is the module that gives control of the CPU to the selected process.

---

## 3.4 Dispatcher

### Definition
The **Dispatcher** is the OS module that gives control of the CPU to the process selected by the short-term scheduler. It performs the actual context switch.

### Detailed Explanation

#### Functions of the Dispatcher
1. **Context Switching**: Saving the state of the old process and loading the state of the new process.
2. **Switching to User Mode**: Changing the mode bit from kernel to user mode.
3. **Jumping to the proper location**: Setting the program counter to the correct address in the new process to resume execution.

#### Dispatch Latency
- **Dispatch Latency** = the time taken by the dispatcher to stop one process and start another.
- It is **pure overhead** — should be minimized.
- Includes time for: saving/restoring context + mode switching + jumping to the new process.

### Key Points / Highlights
- The dispatcher performs the **actual context switch** — the scheduler only **selects** the process.
- **Dispatch latency** should be as small as possible.
- Dispatcher is invoked during every **process switch**.

### MCQ Focus Section
- **Scheduler** selects the process; **Dispatcher** gives it the CPU.
- **Dispatch latency** = time to switch from one process to another.
- Dispatch latency is always **greater than zero** (it includes context switching overhead).
- The dispatcher switches the CPU to **user mode** before handing control to the process.

---

## 3.5 Scheduling Algorithms

### 3.5.1 First Come First Serve (FCFS)

#### Definition
**FCFS** schedules processes in the order they arrive in the ready queue. The process that arrives first gets the CPU first. It is **non-preemptive**.

#### Detailed Explanation
- The simplest scheduling algorithm.
- Implemented using a **FIFO queue**.
- Once a process starts executing, it runs to completion (non-preemptive).
- **Convoy Effect**: Short processes stuck behind a long process, leading to high average waiting time.

#### Key Points / Highlights
- **Non-preemptive**. First in, first served.
- Simple but suffers from the **convoy effect**.
- Average waiting time is generally **not optimal**.
- Not suitable for **interactive/time-sharing** systems.

#### MCQ Focus Section
- FCFS is **non-preemptive**.
- FCFS suffers from the **convoy effect** (short processes wait for long ones).
- FCFS does **not** cause starvation — every process gets the CPU eventually.
- FCFS is the simplest algorithm but has **high average waiting time** for varied burst times.
- FCFS is fair in the sense of **arrival order** but not in terms of efficiency.

---

### 3.5.2 Shortest Job First (SJF)

#### Definition
**SJF** selects the process with the **smallest CPU burst time** next. It can be **non-preemptive** or **preemptive (SRTF — Shortest Remaining Time First)**.

#### Detailed Explanation

**Non-Preemptive SJF**
- Once a process starts, it runs to completion.
- Optimal for **minimizing average waiting time** among non-preemptive algorithms.

**Preemptive SJF (SRTF — Shortest Remaining Time First)**
- If a new process arrives with a burst time shorter than the **remaining time** of the currently running process, the current process is preempted.
- Optimal among all algorithms for **minimizing average waiting time**.

**Problem: Predicting Burst Time**
- SJF requires knowledge of the **next CPU burst length**, which is usually **not known** in advance.
- The OS uses **estimation** — typically **exponential averaging** of past burst times.

**Starvation**
- Long processes may **starve** — they may never get the CPU if short processes keep arriving.
- **Solution**: **Aging** — gradually increase the priority of waiting processes over time.

#### Key Points / Highlights
- SJF gives the **minimum average waiting time**.
- **SRTF** (preemptive SJF) is the optimal algorithm for minimizing average waiting time.
- SJF can cause **starvation** of long processes.
- **Aging** is the solution to starvation in SJF.
- The main difficulty is **predicting the next CPU burst** length.

#### MCQ Focus Section
- SJF is **optimal** for minimizing **average waiting time**.
- **Non-preemptive SJF**: Process keeps CPU once started.
- **Preemptive SJF (SRTF)**: Current process can be preempted if a shorter job arrives.
- SJF can cause **starvation** — solved by **aging**.
- SJF requires **prediction** of next CPU burst (not practically available — uses estimation).
- **Exponential averaging** is used to predict next burst: τ(n+1) = α × t(n) + (1-α) × τ(n).

---

### 3.5.3 Round Robin (RR)

#### Definition
**Round Robin** assigns a fixed **time quantum (time slice)** to each process. Processes are executed in **circular order** — each gets the CPU for one quantum, then moves to the back of the ready queue. It is **preemptive**.

#### Detailed Explanation
- Designed for **time-sharing (interactive)** systems.
- Ready queue is treated as a **circular FIFO** queue.
- If a process **finishes** before the quantum expires, it releases the CPU voluntarily.
- If the quantum **expires** and the process hasn't finished, it is **preempted** and placed at the **end** of the ready queue.

#### Choosing the Time Quantum
- **Too small** quantum: Too many context switches → high overhead, low throughput.
- **Too large** quantum: Behaves like **FCFS** — poor response time.
- **Rule of thumb**: 80% of CPU bursts should be shorter than the time quantum.
- Typical quantum: **10 to 100 milliseconds**.

#### Key Points / Highlights
- **Preemptive** algorithm. Designed for fairness and interactivity.
- Performance depends heavily on the **time quantum size**.
- No starvation — every process gets a fair share of CPU time.
- Higher number of context switches than FCFS and SJF.
- Average waiting time is often **higher** than SJF but **more fair**.

#### MCQ Focus Section
- Round Robin is **preemptive** and designed for **time-sharing** systems.
- If time quantum → ∞, RR degenerates to **FCFS**.
- If time quantum → 0 (very small), too many **context switches** occur (processor sharing).
- RR does **not** cause **starvation** — every process gets CPU time.
- RR provides better **response time** than FCFS and SJF.
- The time quantum should be chosen carefully — **too small or too large is bad**.
- Average turnaround time in RR is generally **higher** than SJF.

---

### 3.5.4 Priority Scheduling

#### Definition
Each process is assigned a **priority**, and the CPU is allocated to the process with the **highest priority**. Can be **preemptive** or **non-preemptive**.

#### Detailed Explanation
- **Higher number = higher priority** or **Lower number = higher priority** (depends on the OS convention).
- **Preemptive Priority**: If a new process arrives with a higher priority than the running process, the running process is preempted.
- **Non-Preemptive Priority**: A higher-priority process waits until the current process finishes or blocks.
- **Starvation Problem**: Low-priority processes may **never** execute if high-priority processes keep arriving.
- **Solution: Aging** — gradually increase the priority of processes that have been waiting for a long time.
- Priority can be:
  - **Internally defined**: Based on measurable quantities (time limits, memory requirements, number of open files).
  - **Externally defined**: Set by the user or administrator (importance of the task, department, etc.).

#### Key Points / Highlights
- Priority scheduling can cause **starvation** of low-priority processes.
- **Aging** solves starvation — increases priority over time.
- SJF is a special case of priority scheduling where priority = inverse of CPU burst time.

#### MCQ Focus Section
- **Starvation** = a process waits indefinitely because higher-priority processes keep arriving.
- **Aging** = gradually increasing priority of waiting processes to prevent starvation.
- **SJF** is a special case of priority scheduling (priority = shortest burst).
- Priority scheduling can be **preemptive or non-preemptive**.
- In most UNIX systems, **lower number = higher priority**.
- Priority inversion can occur in real-time systems — solved by **priority inheritance protocol**.

---

### 3.5.5 Multilevel Feedback Queue Scheduling

#### Definition
**Multilevel Feedback Queue (MLFQ)** scheduling uses **multiple queues** with different priority levels and **allows processes to move between queues** based on their behavior (CPU usage). It adapts to the nature of the process dynamically.

#### Detailed Explanation

- Multiple ready queues, each with a **different priority level** and potentially a different scheduling algorithm.
- A new process enters the **highest-priority queue**.
- If a process uses **too much CPU time** (CPU-bound), it is demoted to a **lower-priority queue**.
- If a process **waits too long** in a lower queue, it can be promoted to a **higher-priority queue** (aging).
- Higher-priority queues typically use **shorter time quanta** (for interactive processes).
- Lower-priority queues use **longer time quanta** or even FCFS (for CPU-bound processes).

#### Parameters to Define MLFQ
1. Number of queues.
2. Scheduling algorithm for each queue.
3. Method to determine when to promote a process.
4. Method to determine when to demote a process.
5. Method to determine which queue a process enters initially.

#### Example
- **Queue 0** (highest priority): RR with quantum = 8ms.
- **Queue 1** (medium priority): RR with quantum = 16ms.
- **Queue 2** (lowest priority): FCFS.
- A process that exceeds 8ms is moved to Queue 1. If it exceeds 16ms there, it's moved to Queue 2.

### Key Points / Highlights
- MLFQ is the **most general** and **most complex** CPU scheduling algorithm.
- Automatically **separates** CPU-bound and I/O-bound processes.
- Uses **aging** to prevent starvation.
- Most modern OS use some form of MLFQ.

#### MCQ Focus Section
- MLFQ allows processes to **move between queues** (unlike simple multilevel queue).
- In simple **Multilevel Queue**, processes are **permanently assigned** to a queue.
- In **MLFQ**, processes can be **promoted** (aging) or **demoted** (CPU-heavy behavior).
- MLFQ is the **most flexible** scheduling algorithm.
- Modern operating systems (Linux CFS, Windows) use variants of MLFQ.
- CPU-bound processes get **demoted** to lower queues; I/O-bound stay in **higher queues**.

---

## 3.6 Multiprocessor Scheduling

### Definition
**Multiprocessor scheduling** deals with scheduling processes on systems with **multiple CPUs/cores**. It introduces additional complexity compared to single-processor scheduling.

### Detailed Explanation

#### Approaches

**1. Asymmetric Multiprocessing (AMP)**
- One processor (master) handles all scheduling decisions and system activities.
- Other processors (slaves) only execute user processes assigned by the master.
- Simple but the **master can become a bottleneck**.

**2. Symmetric Multiprocessing (SMP)**
- Each processor is **self-scheduling** — all processors can access the common ready queue.
- More complex (requires synchronization) but better performance.
- Two approaches:
  - **Common ready queue**: All processors share one queue. Requires locking (contention).
  - **Per-processor queue**: Each CPU has its own ready queue. Needs **load balancing**.

#### Processor Affinity
- A process may have an **affinity** for a particular processor (because its data is in that processor's cache).
- **Soft Affinity**: OS tries to keep a process on the same processor but doesn't guarantee it.
- **Hard Affinity**: Process is bound to a specific processor (guaranteed).

#### Load Balancing
- Ensures work is **evenly distributed** across all processors.
- **Push migration**: A periodic task checks load and pushes processes from overloaded to idle processors.
- **Pull migration**: Idle processors pull tasks from busy processors.

### Key Points / Highlights
- SMP is the most common multiprocessor approach in modern systems.
- **Processor affinity** improves cache performance.
- **Load balancing** ensures even distribution of work.

### MCQ Focus Section
- In **SMP**, all processors are peers — each can run OS and user code.
- In **AMP**, only the master processor makes scheduling decisions.
- **Processor affinity** keeps a process on the same CPU for **cache efficiency**.
- **Load balancing** distributes work evenly — uses push and pull migration.
- SMP requires **synchronization** to access the shared ready queue.

---

## 3.7 Real-Time Scheduling

### Definition
**Real-time scheduling** is designed for systems where tasks must be completed within **strict time deadlines**. Missing a deadline can have serious consequences.

### Detailed Explanation

- **Hard Real-Time**: Deadlines MUST be met. Missing a deadline = system failure. Examples: aircraft control, medical monitoring, nuclear plant control.
- **Soft Real-Time**: Deadlines SHOULD be met, but missing them causes degraded quality, not failure. Examples: multimedia playback, video conferencing.

#### Real-Time Scheduling Algorithms
- **Rate Monotonic Scheduling (RMS)**: Static priority. Tasks with **shorter periods get higher priority**. Preemptive. Optimal among static-priority algorithms.
- **Earliest Deadline First (EDF)**: Dynamic priority. The task with the **earliest deadline** gets highest priority. Preemptive. Optimal — can achieve 100% CPU utilization.

### Key Points / Highlights
- Real-time scheduling prioritizes **meeting deadlines** over fairness or throughput.
- **RMS** = static priority (shorter period = higher priority).
- **EDF** = dynamic priority (earliest deadline first).

### MCQ Focus Section
- **Hard real-time**: Deadline failure = system failure.
- **Soft real-time**: Deadline failure = degraded quality.
- **RMS** is optimal for **static priority** scheduling.
- **EDF** is optimal overall for **dynamic priority** scheduling.
- EDF can achieve **100% CPU utilization**; RMS can guarantee only up to **~69%** (ln2).
- Real-time systems require **preemptive** scheduling with **priority-based** dispatch.

---

## 3.8 Thread Scheduling

### Definition
**Thread scheduling** determines how threads are scheduled on the CPU. The approach depends on whether threads are **user-level** or **kernel-level**.

### Detailed Explanation

- **Process Contention Scope (PCS)**: Used in **many-to-one** and **many-to-many** models. Thread library schedules user-level threads onto available **LWPs (Lightweight Processes)**. Competition is among threads **within the same process**.
- **System Contention Scope (SCS)**: Used in **one-to-one** model. The OS kernel schedules kernel-level threads directly onto CPUs. Competition is among **all threads in the system**.

### Key Points / Highlights
- **PCS** = competition among threads within the same process (user-level scheduling).
- **SCS** = competition among all threads in the system (kernel-level scheduling).
- Linux and Windows use **SCS** (one-to-one model — each user thread maps to a kernel thread).

### MCQ Focus Section
- **PCS** schedules threads within a process; **SCS** schedules threads system-wide.
- **One-to-one** threading model uses **SCS**.
- **Many-to-one** model uses **PCS** (thread library handles scheduling).
- Modern OS (Linux, Windows) use **SCS** with the one-to-one model.

---

---

# UNIT 4: PROCESS SYNCHRONIZATION

---

## 4.1 Critical Section Problem

### Definition
The **Critical Section** is a segment of code in which a process accesses **shared resources** (variables, files, data structures) that must not be concurrently accessed by other processes. The **Critical Section Problem** is to design a protocol that ensures mutual exclusion, progress, and bounded waiting when multiple processes access shared resources.

### Detailed Explanation

#### Structure of a Process (w.r.t. Critical Section)

```
do {
    [Entry Section]      ← Request permission to enter CS
    [Critical Section]   ← Access shared resources
    [Exit Section]       ← Release permission
    [Remainder Section]  ← Non-critical code
} while (true);
```

#### Three Requirements for a Correct Solution

**1. Mutual Exclusion**
- If a process is executing in its critical section, **no other process** can be in its critical section simultaneously.
- At most **one process** can be in the critical section at any time.

**2. Progress**
- If no process is in the critical section and some processes wish to enter, only the processes **not in their remainder section** can participate in the decision of who enters next.
- The selection cannot be **postponed indefinitely** — a decision must be made in finite time.

**3. Bounded Waiting**
- There must be a **limit** on the number of times other processes can enter their critical section after a process has requested to enter and before that request is granted.
- Prevents **starvation**.

### Key Points / Highlights
- Three requirements: **Mutual Exclusion, Progress, Bounded Waiting**.
- Mutual Exclusion = only one process in CS at a time.
- Progress = no deadlock in deciding who enters.
- Bounded Waiting = no starvation.

### MCQ Focus Section
- **Mutual exclusion** ensures only **one process** is in the critical section at a time.
- **Progress** means the decision about who enters CS cannot be delayed forever.
- **Bounded waiting** prevents **starvation**.
- A solution to the critical section problem must satisfy **all three** conditions.
- The critical section problem arises only when processes **share data/resources**.
- **Race condition** = outcome depends on the order of process execution → need for synchronization.

---

## 4.2 Classical Two-Process and N-Process Solutions

### Definition
Early software-based solutions to the critical section problem for two or more processes, before the introduction of hardware support and semaphores.

### Detailed Explanation

#### Peterson's Solution (Two-Process)
- Software-based solution for **two processes** (P0 and P1).
- Uses two shared variables:
  - `flag[2]`: flag[i] = true means process i wants to enter CS.
  - `turn`: Indicates whose turn it is to enter CS.
- **Algorithm** (for process i):
  ```
  flag[i] = true;
  turn = j;          // Give turn to the other process
  while (flag[j] && turn == j);  // Wait
  // Critical Section
  flag[i] = false;
  // Remainder Section
  ```
- Satisfies all three requirements: mutual exclusion, progress, bounded waiting.
- **Limitation**: Only works for **two processes**. Assumes atomic load/store operations.

#### Bakery Algorithm (N-Process) — by Lamport
- Software solution for **N processes**.
- Based on the analogy of a bakery: each process takes a **number (ticket)** before entering. The process with the **smallest number** enters the CS.
- If two processes have the same number, the one with the **smaller PID** goes first.
- Satisfies all three conditions for N processes.
- **Limitation**: Not practical for large N due to complexity.

### Key Points / Highlights
- **Peterson's** = two-process solution. Simple and correct.
- **Bakery Algorithm** = N-process solution by Lamport.
- Both are **software-only** solutions (no hardware support needed).

### MCQ Focus Section
- **Peterson's solution** works for **two processes** only.
- Peterson's satisfies **mutual exclusion, progress, and bounded waiting**.
- **Bakery Algorithm** works for **N processes**.
- In Bakery, the process with the **lowest ticket number** enters the CS.
- Peterson's uses **flag[]** and **turn** variables.
- These solutions assume **sequential consistency** of memory operations.
- Software solutions are generally **slow** — hardware solutions are preferred.

---

## 4.3 Hardware Primitives for Synchronization

### Definition
**Hardware primitives** are special atomic instructions provided by the CPU to support synchronization. They execute as a **single, uninterruptible (atomic) operation**.

### Detailed Explanation

#### 1. Test-and-Set (TAS)
- Atomically reads the current value of a variable, sets it to TRUE, and returns the old value.
- ```
  boolean TestAndSet(boolean *target) {
      boolean rv = *target;
      *target = TRUE;
      return rv;
  }
  ```
- Usage for mutual exclusion:
  ```
  while (TestAndSet(&lock)); // Wait (busy-wait/spinlock)
  // Critical Section
  lock = FALSE;
  ```
- Ensures **mutual exclusion** but does NOT guarantee **bounded waiting**.

#### 2. Compare-and-Swap (CAS)
- Atomically compares the value of a variable with an expected value. If they match, it swaps in a new value. Returns the original value.
- ```
  int CompareAndSwap(int *value, int expected, int new_value) {
      int temp = *value;
      if (*value == expected)
          *value = new_value;
      return temp;
  }
  ```
- More flexible than TAS. Used in modern lock-free algorithms.

#### 3. Disabling Interrupts
- The simplest hardware approach.
- Disable all interrupts → no other process can preempt → execute CS → re-enable interrupts.
- **Problem**: Only works on **single-processor** systems. Disabling interrupts on multiprocessors is impractical and dangerous.
- **Problem**: Gives user processes too much power (could disable interrupts and never re-enable).

#### Spinlocks
- A lock that uses **busy waiting** (spinning in a loop) until the lock becomes available.
- Based on TAS or CAS.
- **Advantage**: No context switch overhead (good if wait time is short).
- **Disadvantage**: Wastes CPU cycles while spinning (bad if wait time is long).

### Key Points / Highlights
- Hardware atomic instructions: **Test-and-Set, Compare-and-Swap**.
- **Disabling interrupts** works only on single-processor systems.
- **Spinlocks** use busy waiting — efficient for short critical sections.
- Hardware solutions are faster than software solutions.

### MCQ Focus Section
- **Test-and-Set** and **Compare-and-Swap** are **atomic** (indivisible) instructions.
- **Spinlock** = **busy waiting** using atomic instructions.
- **Disabling interrupts** only works on **uniprocessor** systems.
- Test-and-Set ensures **mutual exclusion** but NOT **bounded waiting** (unless modified).
- **Busy waiting** wastes CPU — also called a **spinlock**.
- **CAS** is used in modern **lock-free** and **wait-free** data structures.

---

## 4.4 Semaphores

### Definition
A **Semaphore** is a **synchronization tool** (integer variable) with two atomic operations: **wait (P / down)** and **signal (V / up)**. It is used to solve the critical section problem and coordinate process/thread execution.

### Detailed Explanation

#### Types of Semaphores

**1. Binary Semaphore (Mutex)**
- Can only be **0 or 1**.
- Acts like a **lock**: 1 = available, 0 = acquired.
- Used for **mutual exclusion**.

**2. Counting Semaphore**
- Can take any **non-negative integer** value.
- Used to control access to a resource with a **finite number of instances**.
- Example: A semaphore initialized to 5 allows up to 5 processes to access the resource concurrently.

#### Semaphore Operations

**wait(S) / P(S) / down(S):**
```
wait(S) {
    while (S <= 0);  // Busy wait (or block)
    S--;
}
```

**signal(S) / V(S) / up(S):**
```
signal(S) {
    S++;
}
```

- Both operations must be **atomic** (indivisible).
- P = **Proberen** (to test, in Dutch). V = **Verhogen** (to increment, in Dutch).

#### Busy Waiting vs Blocking
- **Busy-wait (Spinlock) semaphore**: Process loops in the wait operation, wasting CPU.
- **Blocking semaphore**: Process is placed in a **waiting queue** when it can't acquire the semaphore. It is **woken up** by a signal operation. More efficient — no CPU waste.

#### Common Uses
- **Mutual exclusion**: Binary semaphore initialized to 1.
- **Process ordering**: Ensure process A executes before process B.
- **Resource counting**: Counting semaphore tracks available instances.

### Key Points / Highlights
- **Binary semaphore** = 0 or 1 (like a mutex). **Counting semaphore** = 0 to N.
- Two operations: **wait (P)** and **signal (V)**, both atomic.
- Blocking semaphore avoids busy waiting.
- Semaphores can solve mutual exclusion, ordering, and resource management.

### MCQ Focus Section
- **wait(S)** decrements S; **signal(S)** increments S.
- A **binary semaphore** is equivalent to a **mutex lock**.
- A **counting semaphore** controls access to resources with **multiple instances**.
- **P** and **V** operations must be **atomic**.
- **Busy-wait** semaphore wastes CPU; **blocking** semaphore uses a wait queue.
- Improper use of semaphores can cause **deadlock** (e.g., two processes each waiting for the other's semaphore).
- Semaphores can also cause **starvation** if the waiting queue is not fair (e.g., LIFO order).
- **Mutex** = **mutual exclusion** lock. Only the process that locked it can unlock it.
- A semaphore initialized to **N** allows **N** processes to access the resource concurrently.

---

## 4.5 Monitors

### Definition
A **Monitor** is a **high-level synchronization construct** that encapsulates shared data, functions, and synchronization into a single module. Only **one process** can be active inside a monitor at any time — mutual exclusion is guaranteed by the compiler/language runtime.

### Detailed Explanation

#### Key Features
- A monitor is like a **class** with:
  - **Shared data variables** (accessible only within the monitor).
  - **Procedures/methods** that operate on the data.
  - **Condition variables** for synchronization beyond mutual exclusion.
- Only **one thread/process** can execute inside a monitor at any time — the compiler enforces mutual exclusion.
- **Condition Variables**: Variables used for waiting and signaling within a monitor.
  - **wait(c)**: The process is suspended and placed in the queue for condition c. It releases the monitor lock.
  - **signal(c)**: Wakes up one process waiting on condition c (if any). If no process is waiting, the signal is **lost** (no effect).

#### Signal Semantics
- **Hoare Monitor**: When signal(c) is called, the signaling process is **immediately suspended**, and the awakened process runs.
- **Mesa Monitor** (used in practice): When signal(c) is called, the awakened process is **placed in the ready queue** (not guaranteed to run immediately). The signaling process continues. The awakened process must **re-check the condition** using a `while` loop.

### Key Points / Highlights
- Monitor = shared data + procedures + automatic mutual exclusion.
- Only **one process** active inside a monitor at a time.
- **Condition variables** (wait/signal) provide synchronization beyond mutual exclusion.
- Monitors are **higher-level** and **safer** than semaphores (less error-prone).

### MCQ Focus Section
- In a monitor, mutual exclusion is **automatic** — guaranteed by the language/compiler.
- **Condition variables** are NOT the same as regular boolean variables — they have no stored value.
- `wait(c)` always suspends the calling process; `signal(c)` is lost if no process is waiting.
- **Hoare monitors**: signaling process suspends immediately.
- **Mesa monitors**: signaling process continues, awakened process must re-check condition.
- Monitors are **less error-prone** than semaphores because mutual exclusion is built in.
- Java's `synchronized` keyword provides monitor-like behavior.
- Monitors prevent errors like **forgetting to release a lock** (which semaphores are prone to).

---

## 4.6 Classic Synchronization Problems

### 4.6.1 Producer-Consumer Problem (Bounded Buffer)

#### Definition
Two processes share a **bounded buffer** (fixed-size). The **producer** creates data items and places them in the buffer. The **consumer** removes items from the buffer. They must synchronize to prevent buffer overflow and underflow.

#### Detailed Explanation
- If the buffer is **full**, the producer must **wait**.
- If the buffer is **empty**, the consumer must **wait**.
- Both must not access the buffer **simultaneously** (mutual exclusion).

**Solution using Semaphores**:
- `mutex` (binary, init 1): For mutual exclusion on the buffer.
- `empty` (counting, init N): Counts empty slots. Producer waits if 0.
- `full` (counting, init 0): Counts full slots. Consumer waits if 0.

- **Producer**: wait(empty) → wait(mutex) → add item → signal(mutex) → signal(full)
- **Consumer**: wait(full) → wait(mutex) → remove item → signal(mutex) → signal(empty)

#### MCQ Focus Section
- The bounded buffer problem uses **3 semaphores**: mutex, empty, full.
- **Deadlock** occurs if the order of wait operations is wrong (e.g., wait(mutex) before wait(empty)).
- The order of semaphore operations is **critical** — always wait on counting semaphore before mutex.

---

### 4.6.2 Reader-Writer Problem

#### Definition
Multiple processes share a data resource. **Readers** only read the data; **Writers** modify it. Multiple readers can read simultaneously, but a writer must have **exclusive access** (no other readers or writers).

#### Detailed Explanation

**First Readers-Writers Problem** (Readers preference):
- Readers get priority. A writer must wait until all readers finish.
- **Problem**: Writers may **starve** if readers keep arriving.

**Second Readers-Writers Problem** (Writers preference):
- Once a writer is waiting, no new readers are allowed to start reading.
- **Problem**: Readers may **starve**.

**Solution uses**:
- `mutex` (binary, init 1): Protects the reader count variable.
- `wrt` (binary, init 1): Ensures exclusive access for writers.
- `read_count` (integer, init 0): Tracks number of active readers.

#### MCQ Focus Section
- Multiple **readers** can access data simultaneously — no conflict between readers.
- A **writer** needs **exclusive** access — no readers or other writers.
- **First problem**: Readers have priority → **writers may starve**.
- **Second problem**: Writers have priority → **readers may starve**.
- `read_count` tracks how many readers are currently reading.

---

### 4.6.3 Dining Philosophers Problem

#### Definition
**Five philosophers** sit around a circular table. Each has a plate and a fork (chopstick) between each pair of adjacent philosophers (5 forks total). A philosopher alternates between **thinking** and **eating**. To eat, a philosopher needs **both adjacent forks**.

#### Detailed Explanation
- This is a classic problem demonstrating **deadlock** and **starvation** in concurrent systems.
- **Naive solution**: Each philosopher picks up the left fork, then the right fork. But if all five pick up their left fork simultaneously → **deadlock** (each waiting for the right fork, which is held by a neighbor).
- **Solutions to avoid deadlock**:
  1. Allow at most **4 philosophers** to sit at the table simultaneously.
  2. Allow a philosopher to pick up forks only if **both are available** (using a critical section).
  3. Use an **asymmetric solution**: Odd-numbered philosophers pick up left first; even-numbered pick up right first.
  4. Use a **monitor** or **semaphore** with proper state management.

#### MCQ Focus Section
- The Dining Philosophers problem illustrates **deadlock** and **resource allocation**.
- If all philosophers pick up the **left fork** first → **deadlock**.
- There are **5 philosophers** and **5 forks** (shared resources).
- The problem demonstrates that a correct local behavior (each philosopher acts rationally) can lead to a **global problem** (deadlock).
- The problem can be solved using **semaphores, monitors, or asymmetric algorithms**.

---

## 4.7 Precedence Graph

### Definition
A **Precedence Graph** is a **directed acyclic graph (DAG)** that represents the order in which statements or processes must be executed. An edge from node A to node B means A must complete before B can start.

### Detailed Explanation
- Used to represent **dependencies** between tasks.
- Helps identify which tasks can run **in parallel** (independent tasks with no precedence relationship).
- Used in conjunction with **fork/join** or **semaphores** to implement concurrent execution.
- Example: If S1 → S2 and S1 → S3, then S2 and S3 can run in **parallel** after S1 completes.

### MCQ Focus Section
- A precedence graph must be a **DAG** (no cycles).
- If there's a cycle in the precedence graph → **deadlock** potential.
- Independent nodes (no path between them) can execute **concurrently**.
- Precedence graphs help in **task scheduling** and **parallel execution** planning.

---

## 4.8 Hierarchy of Processes

### Definition
**Process Hierarchy** refers to the parent-child relationships among processes, forming a **tree structure**. In UNIX, every process (except init) is created by another process, forming a hierarchical tree.

### Detailed Explanation
- The root of the process hierarchy is the **init** process (PID 1).
- Each process can create children using `fork()`, and those children can create their own children.
- The hierarchy affects:
  - **Resource allocation**: Children may inherit resources from parents.
  - **Termination**: Cascading termination may kill all descendants.
  - **Signal delivery**: Signals can be sent to process groups.
- **Process Group**: A collection of related processes. Used for signal delivery and job control.
- **Session**: A collection of process groups. Created by `setsid()`.

### MCQ Focus Section
- UNIX processes form a **tree** rooted at **init (PID 1)**.
- Process hierarchy determines **parent-child relationships**.
- **Process groups** allow signals to be sent to multiple related processes.
- A **session** is a collection of process groups, usually associated with a terminal.

---

---

# UNIT 5: THREADS

---

## 5.1 Overview

### Definition
A **Thread** (also called a **Lightweight Process — LWP**) is the **basic unit of CPU execution**. It is a flow of control within a process. A process can have multiple threads that share the same address space but execute independently.

### Detailed Explanation

#### Thread vs Process

| Feature | Process | Thread |
|---------|---------|--------|
| Address Space | Own **separate** address space | Shares address space **with other threads** of same process |
| Creation Overhead | **High** (allocate memory, resources) | **Low** (shares resources of the process) |
| Context Switch | **Slow** (switch page tables, memory) | **Fast** (only switch registers, stack, PC) |
| Communication | Through **IPC** (pipes, sockets, shared memory) | Through **shared variables** (same address space) |
| Independence | Independent of other processes | Dependent on parent process |
| Failure Impact | One process crash doesn't affect others | One thread crash can bring down the **entire process** |

#### What Threads Share (within a process)
- **Code section** (text)
- **Data section** (global variables)
- **Heap**
- **Open files and signals**
- **Process ID and address space**

#### What Each Thread Has Independently
- **Thread ID**
- **Program Counter (PC)**
- **Register set**
- **Stack**
- **Thread state** (running, ready, waiting)

#### Benefits of Multithreading
1. **Responsiveness**: A process can continue running even if one thread is blocked (e.g., UI thread stays responsive while worker thread processes data).
2. **Resource Sharing**: Threads share the address space — no need for IPC mechanisms.
3. **Economy**: Thread creation and context switching is **much cheaper** than process creation and switching.
4. **Scalability**: Threads can run on different CPUs/cores in parallel — true parallelism.

### Key Points / Highlights
- A thread is the **smallest unit of CPU execution**.
- Threads of the same process share **code, data, heap, files** but have separate **stack, PC, registers**.
- Thread creation is much **faster** and **cheaper** than process creation.
- Threads enable **concurrency within a process**.

### MCQ Focus Section
- A thread is also called a **Lightweight Process (LWP)**.
- Threads share: **code, data, heap, files, PID**. Do NOT share: **stack, PC, registers**.
- Thread context switch is **faster** than process context switch.
- If one thread in a process calls `exit()`, **all threads** in that process are terminated.
- Creating a thread is **faster** than creating a process because threads **share resources**.
- Threads communicate via **shared memory** (shared address space) — no IPC needed.
- **Multiprocessing** = multiple processes; **Multithreading** = multiple threads within a process.

---

## 5.2 Multithreading Models

### Definition
**Multithreading Models** define the mapping between **User-Level Threads (ULT)** managed by the thread library and **Kernel-Level Threads (KLT)** managed by the OS kernel.

### Detailed Explanation

#### User-Level Threads (ULT)
- Created and managed by a **user-level thread library** (e.g., POSIX Pthreads in user space).
- The **kernel is unaware** of these threads — it sees only the process.
- Fast to create and switch (no kernel involvement).
- **Problem**: If one thread blocks (e.g., I/O), the **entire process** blocks (because the kernel doesn't know about the other threads).

#### Kernel-Level Threads (KLT)
- Created and managed by the **OS kernel**.
- The kernel is **aware** of each thread and can schedule them independently.
- If one thread blocks, the kernel can schedule **another thread** of the same process.
- **Problem**: Slower to create and switch (kernel involvement).

#### Three Models

**1. Many-to-One Model**
- Many user threads mapped to **one kernel thread**.
- Thread management in user space — fast.
- If one thread blocks → **entire process blocks**.
- **No true parallelism** on multiprocessors (only one kernel thread).
- Examples: Green threads (early Java), GNU Portable Threads.

**2. One-to-One Model**
- Each user thread mapped to **one kernel thread**.
- If one thread blocks, others can still run.
- **True parallelism** on multiprocessors.
- **Overhead**: Creating a user thread requires creating a kernel thread (may limit number of threads).
- Examples: **Linux, Windows** (most modern OS).

**3. Many-to-Many Model**
- Many user threads mapped to **many kernel threads** (M ≥ N; fewer or equal kernel threads).
- Best of both worlds: true concurrency + fewer kernel threads.
- The user can create as many threads as needed.
- Most flexible but most **complex** to implement.
- Variation: **Two-Level Model** — similar to many-to-many but also allows binding a user thread to a kernel thread.
- Example: Solaris (earlier versions).

### Key Points / Highlights
| Model | Mapping | Parallelism | Blocking Behavior |
|-------|---------|-------------|-------------------|
| Many-to-One | M:1 | No | One blocks → all block |
| One-to-One | 1:1 | Yes | One blocks → others continue |
| Many-to-Many | M:N | Yes | Flexible |

### MCQ Focus Section
- **Many-to-One**: No parallelism. One thread blocks → all block. Fast but limited.
- **One-to-One**: True parallelism. One thread blocks → others run. Used by Linux, Windows.
- **Many-to-Many**: Most flexible. True parallelism with fewer kernel threads.
- **Linux** and **Windows** use the **One-to-One** model.
- The **One-to-One** model creates one kernel thread per user thread.
- **Many-to-One** model cannot utilize **multiple CPUs**.
- User-level threads are **invisible to the kernel**.
- Kernel-level threads are **slower to create** but enable independent scheduling.

---

## 5.3 Scheduler Activations

### Definition
**Scheduler Activations** is a mechanism that provides **communication between the user-level thread library and the kernel** to achieve the benefits of both user-level and kernel-level thread management.

### Detailed Explanation
- The kernel provides each process with a set of **virtual processors** (called **Lightweight Processes — LWPs**).
- The user-level thread library schedules user threads onto these LWPs.
- When a kernel event occurs (e.g., a thread blocks due to I/O), the kernel performs an **upcall** — notifying the user-level thread library so it can schedule another thread on the available LWP.
- This avoids the "one blocks → all block" problem of the Many-to-One model without the overhead of One-to-One.
- Used in the **Many-to-Many** model and the **Two-Level** model.

### Key Points / Highlights
- Scheduler activations use **upcalls** from kernel to user-level thread library.
- The kernel provides **LWPs (virtual processors)** to the process.
- Combines efficiency of user-level threads with flexibility of kernel-level scheduling.

### MCQ Focus Section
- **Upcall** = kernel notifies the user-level thread library of an event.
- Scheduler activations are used with the **Many-to-Many** model.
- **LWPs** are the interface between user-level and kernel-level threads.
- Scheduler activations solve the **blocking problem** of user-level threads.

---

## 5.4 Examples of Threaded Programs

### Definition
Threaded programs use multiple threads within a single process to perform concurrent tasks. Common examples include web servers, web browsers, and word processors.

### Detailed Explanation

**1. Web Server**
- A multithreaded web server creates a **new thread** (or uses a thread pool) for each incoming client request.
- Main thread listens for connections; worker threads handle individual requests.
- **Benefits**: Responsive to multiple clients simultaneously.

**2. Web Browser**
- One thread for **UI rendering** (displaying the page).
- Another thread for **network requests** (downloading images, CSS, JavaScript).
- Another thread for **JavaScript execution**.
- User can scroll while the page is still loading.

**3. Word Processor**
- One thread for **user input** (typing).
- Another for **spell checking** in the background.
- Another for **auto-saving** periodically.
- Another for **formatting/layout**.

**4. Thread Pool**
- Instead of creating a new thread for each task, a **pool of pre-created threads** is maintained.
- Tasks are submitted to the pool; an available thread picks up the task.
- **Advantages**: Reduces thread creation overhead, limits resource usage, improves response time.

### Key Points / Highlights
- Multithreading enables **responsive** and **efficient** applications.
- **Thread pools** reduce overhead of thread creation/destruction.
- Real-world applications heavily use multithreading for performance and responsiveness.

### MCQ Focus Section
- A **thread pool** pre-creates threads to avoid repeated creation/destruction overhead.
- A web server uses threads to handle **multiple client requests** concurrently.
- In a web browser, separate threads handle **UI, network, and JavaScript** independently.
- Thread pools limit the **maximum number** of concurrent threads (prevents resource exhaustion).
- **Pthreads** (POSIX Threads) is the standard threading API on UNIX/Linux systems.
- Java provides built-in threading support via the **Thread class** and **Runnable interface**.

---

---

# UNIT 6: DEADLOCK

---

## 6.1 Deadlock Characterization

### Definition
A **Deadlock** is a situation where a set of processes are **permanently blocked** because each process is holding a resource and waiting for a resource held by another process in the set. No process can proceed — the system is stuck.

### Detailed Explanation

#### Necessary Conditions for Deadlock (Coffman Conditions)
**All four** conditions must hold simultaneously for a deadlock to occur:

**1. Mutual Exclusion**
- At least one resource must be held in a **non-shareable** mode — only one process can use it at a time.
- Example: A printer can only be used by one process at a time.

**2. Hold and Wait**
- A process is **holding** at least one resource while **waiting** to acquire additional resources held by other processes.

**3. No Preemption**
- Resources cannot be **forcibly taken** from a process — a process must voluntarily release its resources only when it's done.

**4. Circular Wait**
- A set of processes {P1, P2, …, Pn} exists such that P1 is waiting for a resource held by P2, P2 is waiting for P3, …, and Pn is waiting for P1 — forming a **cycle**.

#### Resource Allocation Graph (RAG)
- A directed graph used to represent resource allocation and requests.
- **Vertices**: Processes (circles) and Resources (rectangles with dots representing instances).
- **Request Edge**: Process → Resource (process is requesting the resource).
- **Assignment Edge**: Resource → Process (resource is allocated to the process).
- **Cycle Detection**:
  - If there is **no cycle** → **no deadlock**.
  - If there is a **cycle** and each resource has **one instance** → **deadlock exists**.
  - If there is a **cycle** and resources have **multiple instances** → deadlock **may or may not** exist.

### Key Points / Highlights
- Deadlock requires **all four** Coffman conditions simultaneously.
- Removing **any one** condition prevents deadlock.
- RAG with a cycle and single-instance resources → definite deadlock.
- RAG with a cycle and multi-instance resources → possible but not certain deadlock.

### MCQ Focus Section
- All **four conditions** (Mutual Exclusion, Hold & Wait, No Preemption, Circular Wait) must hold for deadlock.
- If **any one** condition is broken, deadlock **cannot** occur.
- A **cycle in RAG** is a necessary condition for deadlock, but not always sufficient (multi-instance resources).
- For **single-instance** resources, a cycle in RAG = **deadlock**.
- Deadlock is different from **starvation** — starvation is indefinite waiting but the system is not stuck.
- **Livelock** = processes keep changing state but make no progress (not stuck, but no useful work).
- In a RAG, a **request edge** goes from process to resource; an **assignment edge** goes from resource to process.

---

## 6.2 Deadlock Prevention

### Definition
**Deadlock Prevention** ensures that at least one of the four necessary conditions for deadlock **cannot hold**, thereby making deadlock structurally impossible.

### Detailed Explanation

**1. Preventing Mutual Exclusion**
- Make resources **shareable** where possible.
- **Impractical** for most resources — printers, files in write mode, etc. cannot be shared simultaneously.

**2. Preventing Hold and Wait**
- **Option A**: A process must request **all resources at once** before execution. If all are available, allocate; otherwise, the process waits with no resources.
- **Option B**: A process can request resources **only if it holds none** — must release all resources before requesting new ones.
- **Problems**: Low resource utilization, possible starvation (a process needing many resources may never get all at once).

**3. Preventing No Preemption (Allow Preemption)**
- If a process holding resources is waiting for another resource, its held resources are **preempted** (taken away) and added to the resource pool.
- The process is restarted only when it can get all needed resources.
- **Practical** only for resources whose state can be saved/restored (e.g., CPU registers, memory). **Impractical** for printers.

**4. Preventing Circular Wait**
- Impose a **total ordering** on all resource types. Each resource type is assigned a unique number.
- A process can only request resources in **increasing order** of their numbers.
- If a process holds resource Ri, it can only request Rj where j > i.
- **Most practical** prevention strategy.
- **Problem**: Determining the ordering can be difficult; may lead to resource under-utilization.

### Key Points / Highlights
- Prevention breaks **one of the four conditions** — makes deadlock impossible.
- **Circular wait prevention** (resource ordering) is the most practical approach.
- Prevention is **conservative** — may reduce resource utilization and concurrency.

### MCQ Focus Section
- **Preventing circular wait** using resource ordering is the most commonly used prevention technique.
- Preventing **hold and wait** requires requesting all resources upfront — leads to **low utilization**.
- Preventing **no preemption** (allowing preemption) works only for resources whose state can be saved (e.g., CPU, memory).
- Preventing **mutual exclusion** is generally **impractical** (most resources are non-shareable).
- Deadlock prevention is **more restrictive** than deadlock avoidance — reduces system efficiency.

---

## 6.3 Deadlock Avoidance

### Definition
**Deadlock Avoidance** allows the system to allocate resources dynamically, but **checks each request** to ensure the system will remain in a **safe state**. If granting a request would lead to an unsafe state, the request is denied (the process must wait).

### Detailed Explanation

#### Safe State
- A state is **safe** if the system can allocate resources to each process in some order and avoid deadlock.
- There exists a **safe sequence** of processes where each process can get its maximum needed resources, finish, and release resources for the next.
- **Safe state → no deadlock**. **Unsafe state → deadlock is possible** (but not certain).
- Safe → Unsafe is possible. Unsafe → Deadlock is possible.

#### Banker's Algorithm (by Dijkstra)
- Used for **multiple instance** resources.
- Each process declares its **maximum** resource needs upfront.
- When a request is made, the algorithm checks if granting it keeps the system in a safe state.
- If safe → grant. If unsafe → process waits.

**Data Structures**:
- `Available[m]`: Number of available instances of each resource type.
- `Max[n][m]`: Maximum demand of each process for each resource.
- `Allocation[n][m]`: Currently allocated resources for each process.
- `Need[n][m]`: Remaining needs. **Need = Max − Allocation**.

**Safety Algorithm** (checks if a state is safe):
1. Let `Work = Available` and `Finish[i] = false` for all i.
2. Find a process i where `Finish[i] == false` and `Need[i] <= Work`.
3. `Work = Work + Allocation[i]`, set `Finish[i] = true`. Go to step 2.
4. If all `Finish[i] == true`, the system is in a **safe state**. Otherwise, it's unsafe.

**Resource Request Algorithm**:
1. If `Request[i] > Need[i]` → Error (process exceeded its claim).
2. If `Request[i] > Available` → Process must wait.
3. Pretend to allocate: update Available, Allocation, Need.
4. Run the Safety Algorithm. If safe → allocate. If unsafe → rollback and make the process wait.

### Key Points / Highlights
- Avoidance checks **before granting** a request — ensures safe state.
- **Banker's Algorithm** = the key avoidance algorithm (by Dijkstra).
- **Need = Max − Allocation**.
- Safe state guarantees **no deadlock**. Unsafe state means deadlock is **possible**.
- More flexible than prevention but requires **advance knowledge** of maximum resource needs.

### MCQ Focus Section
- **Safe state** = there exists a **safe sequence** where all processes can finish.
- **Unsafe state ≠ deadlock** — it means deadlock is **possible**.
- Banker's Algorithm requires each process to declare its **maximum resource needs** in advance.
- **Need[i] = Max[i] − Allocation[i]**.
- Banker's Algorithm has time complexity of **O(m × n²)** where m = resource types, n = processes.
- Banker's Algorithm is for **multiple instance** resources.
- Banker's Algorithm was designed by **Dijkstra**.
- If `Request > Need` → the process has **exceeded its maximum claim** (error).
- Avoidance is **less restrictive** than prevention but more computationally expensive.

---

## 6.4 Deadlock Detection

### Definition
**Deadlock Detection** allows the system to enter a deadlock state and then **detects** the deadlock using an algorithm. Once detected, a **recovery** mechanism is applied.

### Detailed Explanation

#### Detection with Single-Instance Resources
- Use a **Wait-For Graph**: Node = process. Edge Pi → Pj means Pi is waiting for a resource held by Pj.
- The Wait-For Graph is derived from the RAG by removing resource nodes.
- If there's a **cycle** in the Wait-For Graph → **deadlock exists**.

#### Detection with Multiple-Instance Resources
- Use an algorithm similar to the Banker's Safety Algorithm.
- Checks if there exists a sequence to finish all processes with available resources.
- If no such sequence exists → **deadlock**.

#### When to Invoke Detection
- **Every time** a resource request cannot be granted — expensive but detects immediately.
- **Periodically** (at fixed intervals) — less overhead but delayed detection.
- **When CPU utilization drops** below a threshold — indicates possible deadlock.

### Key Points / Highlights
- Detection allows deadlock to occur and then identifies it.
- **Wait-For Graph** (cycle detection) for single-instance resources.
- Algorithm similar to Banker's for multi-instance resources.

### MCQ Focus Section
- **Wait-For Graph**: If a **cycle** exists → **deadlock**.
- Wait-For Graph is for **single-instance** resources.
- Detection for **multi-instance** resources uses an algorithm similar to the **Safety Algorithm**.
- Detection has **overhead** — must balance frequency of invocation.
- Detection does **not prevent** deadlock — it identifies it after it occurs.

---

## 6.5 Deadlock Recovery

### Definition
Once a deadlock is **detected**, the system must recover by breaking the deadlock. Recovery involves either **terminating processes** or **preempting resources**.

### Detailed Explanation

#### 1. Process Termination

**Option A: Abort ALL deadlocked processes**
- Simple and effective — immediately breaks the deadlock.
- **Problem**: Expensive — all work done by terminated processes is lost.

**Option B: Abort one process at a time**
- Abort one process, re-run detection algorithm. If deadlock still exists, abort another.
- **Problem**: Overhead of running detection after each termination.
- **Selection criteria** (which process to abort first):
  - Priority of the process.
  - How much computation has been done (and how much is left).
  - Number of resources the process is holding.
  - How many more resources the process needs.
  - Number of processes that need to be terminated.
  - Whether the process is interactive or batch.

#### 2. Resource Preemption
- Take resources from some processes and give them to others.
- Three issues:
  1. **Selecting a victim**: Choose a process with the minimum cost.
  2. **Rollback**: The victim process must be rolled back to a **safe state** (or completely restarted).
  3. **Starvation**: The same process might always be selected as the victim. **Solution**: Include the number of rollbacks in the cost factor.

### Key Points / Highlights
- Recovery options: **Process termination** or **Resource preemption**.
- Aborting all deadlocked processes is simplest but most wasteful.
- Resource preemption requires **rollback** and must avoid **starvation**.

### MCQ Focus Section
- Two recovery methods: **process termination** and **resource preemption**.
- Aborting **all** deadlocked processes breaks deadlock immediately but is **expensive**.
- **Victim selection** for preemption should minimize **cost** (resources held, computation done, etc.).
- **Rollback** restores a process to a previous **safe state**.
- **Starvation** in recovery can be prevented by including **rollback count** in cost.

---

## 6.6 Starvation

### Definition
**Starvation** (also called **Indefinite Blocking**) occurs when a process waits **indefinitely** because other processes are continuously preferred over it. The process never gets the resources or CPU time it needs.

### Detailed Explanation

#### Starvation vs Deadlock
| Feature | Deadlock | Starvation |
|---------|----------|-----------|
| Processes stuck? | Yes — all are blocked | No — process can run but never gets a chance |
| Cycle required? | Yes (circular wait) | No |
| All four conditions? | Required | Not required |
| Solution | Detection + Recovery, Prevention, Avoidance | **Aging** |
| Progress | NONE — system stuck | Others progress, victim doesn't |

#### Causes of Starvation
- **Priority scheduling** without aging — low-priority processes never run.
- **SJF scheduling** — long processes may starve if short processes keep arriving.
- **Resource allocation** that always favors certain processes.
- Unfair **deadlock recovery** that always selects the same victim.

#### Solution: Aging
- Gradually **increase the priority** of processes that have been waiting a long time.
- Ensures that eventually every process gets a turn.

### Key Points / Highlights
- Starvation ≠ Deadlock. In starvation, the system makes progress but one process doesn't.
- **Aging** is the primary solution to starvation.

### MCQ Focus Section
- **Starvation** = indefinite waiting; **Deadlock** = permanent blocking with no progress.
- Starvation does **not** require all four Coffman conditions.
- **Aging** increases priority over time to prevent starvation.
- **SJF** and **Priority Scheduling** can cause starvation; **FCFS** and **Round Robin** do not.
- Starvation can occur in **resource allocation** and **CPU scheduling**.

---

---

# UNIT 7: PROTECTION AND SECURITY

---

## 7.1 Need for Security

### Definition
**Security** in an operating system involves protecting system resources and data from **unauthorized access, malicious attacks, and accidental damage**. It ensures **confidentiality, integrity, and availability** (the CIA triad).

### Detailed Explanation

#### CIA Triad
- **Confidentiality**: Only authorized users can access data.
- **Integrity**: Data can only be modified by authorized users in authorized ways.
- **Availability**: Data and services are available to authorized users when needed.

#### Why Security is Needed
- Protect **user data** (personal files, financial information).
- Prevent **unauthorized access** to system resources.
- Defend against **malware** (viruses, worms, trojans, ransomware).
- Ensure **system stability** and uptime.
- Protect against **data breaches** and **data theft**.
- Support **multi-user environments** where users must be isolated from each other.

### Key Points / Highlights
- Security addresses **external threats** (hackers, viruses).
- Protection addresses **internal access control** (which process can access what resource).
- Both are needed for a secure system.
- **CIA triad** = Confidentiality, Integrity, Availability.

### MCQ Focus Section
- **Confidentiality** prevents unauthorized reading of data.
- **Integrity** prevents unauthorized modification of data.
- **Availability** ensures resources are accessible when needed.
- **Security** = defending against external attacks. **Protection** = controlling internal resource access.
- A **DoS (Denial of Service)** attack targets **availability**.
- A **man-in-the-middle** attack targets **confidentiality** and **integrity**.

---

## 7.2 Security Vulnerabilities

### Definition
**Security vulnerabilities** are weaknesses in software, hardware, or protocols that can be exploited by attackers to gain unauthorized access, execute malicious code, or disrupt services.

### Detailed Explanation

#### 1. Buffer Overflow
- Occurs when a program writes **more data** to a buffer than it can hold, overwriting adjacent memory.
- Attackers exploit this to overwrite the **return address** on the stack, redirecting execution to malicious code.
- One of the most common and dangerous vulnerabilities.
- **Prevention**: Bounds checking, use of safe functions (e.g., `strncpy` instead of `strcpy`), stack canaries, ASLR (Address Space Layout Randomization), DEP (Data Execution Prevention).

#### 2. Trapdoors (Backdoors)
- **Trapdoor**: A hidden entry point in a program, intentionally left by the developer for debugging or maintenance. Can be exploited if discovered.
- **Backdoor**: Similar to a trapdoor — a secret vulnerability that bypasses normal authentication. Can be malicious (planted by attackers) or accidental.
- **Risk**: Allows unauthorized access without going through normal security checks.

#### 3. Cache Poisoning
- Corrupting the data stored in a **cache** (e.g., DNS cache, web cache) so that future requests return **incorrect/malicious data**.
- **DNS Cache Poisoning**: Modifying the DNS cache to redirect domain name queries to a malicious IP address.
- Users are redirected to **fraudulent websites** without knowing.
- **Prevention**: DNSSEC (DNS Security Extensions), encrypted connections (HTTPS).

#### 4. Other Vulnerabilities
- **SQL Injection**: Inserting malicious SQL code into input fields to manipulate database queries.
- **Cross-Site Scripting (XSS)**: Injecting malicious scripts into web pages viewed by other users.
- **Privilege Escalation**: Exploiting a vulnerability to gain higher privileges than intended.
- **Race Conditions**: Exploiting timing dependencies in concurrent processes to gain unauthorized access (TOCTOU — Time of Check to Time of Use).

### Key Points / Highlights
- **Buffer overflow** is a critical vulnerability — overruns buffer to inject malicious code.
- **Backdoors** bypass normal authentication.
- **Cache poisoning** corrupts cached data (especially DNS).
- Prevention involves secure coding, input validation, and system-level defenses.

### MCQ Focus Section
- **Buffer overflow** overwrites memory beyond the buffer boundary — can redirect execution to malicious code.
- **Stack-based buffer overflow** is the most common type.
- **ASLR** randomizes memory addresses to make exploitation harder.
- **DEP** prevents execution of code in non-executable memory regions.
- A **trapdoor/backdoor** allows bypassing normal authentication.
- **DNS cache poisoning** redirects users to fake websites.
- **TOCTOU** is a race condition vulnerability.

---

## 7.3 Authentication

### Definition
**Authentication** is the process of verifying the **identity** of a user, process, or system. It answers the question: "Who are you?"

### Detailed Explanation

#### Password-Based Authentication
- The most common form of authentication.
- User provides a **username** and **password**; the system checks against stored credentials.
- Passwords are stored as **hashes** (not plain text) using algorithms like SHA-256, bcrypt, scrypt.
- **Salting**: Adding a random value (salt) to the password before hashing to prevent rainbow table attacks.

#### Password Maintenance
- **Password policies**: Minimum length, complexity requirements (uppercase, lowercase, numbers, symbols), expiration periods.
- **Account lockout**: Lock account after N failed login attempts to prevent brute force.
- **Multi-Factor Authentication (MFA/2FA)**: Combines two or more factors:
  - **Something you know**: Password, PIN.
  - **Something you have**: Phone, hardware token, smart card.
  - **Something you are**: Fingerprint, retina scan, face recognition (biometrics).

#### Secure Communication
- **Encryption**: Convert plaintext to ciphertext using encryption algorithms.
  - **Symmetric encryption**: Same key for encryption and decryption (AES, DES). Fast.
  - **Asymmetric encryption**: Public key for encryption, private key for decryption (RSA). Slower but more secure for key exchange.
- **Digital Signatures**: Verify the authenticity and integrity of a message.
- **SSL/TLS**: Secure communication over the Internet (HTTPS).
- **VPN (Virtual Private Network)**: Encrypted tunnel for secure remote access.

### Key Points / Highlights
- Authentication verifies **identity**. Authorization verifies **permissions**.
- Passwords should be stored as **salted hashes**, never plain text.
- **MFA** significantly improves security by requiring multiple factors.
- **Symmetric encryption** is faster; **Asymmetric encryption** is more secure for key exchange.

### MCQ Focus Section
- **Authentication** = "Who are you?" **Authorization** = "What can you do?"
- **Hashing** is one-way — you cannot retrieve the original password from the hash.
- **Salting** prevents **rainbow table** attacks.
- **Brute force attack** tries all possible passwords — prevented by account lockout and rate limiting.
- **MFA/2FA** combines multiple authentication factors for stronger security.
- **Symmetric encryption** (AES) uses **one key**; **Asymmetric** (RSA) uses **two keys** (public/private).
- **Digital certificates** bind a public key to an identity (issued by Certificate Authorities — CAs).
- **Dictionary attack** tries common passwords — prevented by complexity requirements.

---

## 7.4 Application Security — Viruses and Program Threats

### Definition
**Program threats** are malicious programs designed to cause harm to systems, steal data, or disrupt operations. They exploit vulnerabilities in software to achieve their goals.

### Detailed Explanation

#### Types of Program Threats

**1. Virus**
- A program that **attaches itself** to a legitimate program and spreads when the infected program is executed.
- Requires **user action** (executing the infected file) to spread.
- Types: File virus, boot sector virus, macro virus, polymorphic virus, stealth virus.

**2. Worm**
- A **self-replicating** program that spreads **automatically** across networks without user action.
- Does NOT attach to other programs — it is a standalone program.
- Can cause network congestion and system resource exhaustion.
- Example: Morris Worm (1988), WannaCry (2017).

**3. Trojan Horse**
- A program that **appears legitimate** but contains **hidden malicious code**.
- Does NOT replicate itself.
- Example: A "free game" that secretly installs a keylogger.

**4. Ransomware**
- Malware that **encrypts** the user's files and demands a **ransom** payment for the decryption key.
- Example: WannaCry, Petya.

**5. Spyware**
- Software that **secretly monitors** user activity (keystrokes, browsing patterns, passwords).
- Example: Keyloggers.

**6. Logic Bomb**
- Malicious code that activates when a **specific condition** is met (e.g., a particular date, a file being deleted).

**7. Rootkit**
- Software that provides **privileged (root) access** to an attacker while hiding its presence.
- Very difficult to detect — modifies OS components.

### Key Points / Highlights
| Threat | Replicates? | Needs User Action? | Standalone? |
|--------|------------|--------------------| ------------|
| Virus | Yes (attaches to programs) | Yes | No (attaches) |
| Worm | Yes (spreads via network) | No | Yes |
| Trojan | No | Yes (runs it thinking it's safe) | Yes |
| Ransomware | May | May | Yes |

### MCQ Focus Section
- **Virus** attaches to programs; **Worm** is standalone and spreads via network.
- **Worm** does NOT need user action to spread — it self-replicates.
- **Trojan** does NOT replicate — disguises as legitimate software.
- **Ransomware** encrypts data and demands payment.
- **Logic bomb** activates on a **trigger condition**.
- **Rootkit** hides itself and provides root access.
- The **Morris Worm** (1988) was the first widely known worm on the Internet.
- **Antivirus** software detects and removes viruses using signature-based and heuristic-based detection.

---

## 7.5 Goals and Principles of Protection

### Definition
**Protection** refers to the set of mechanisms that control the access of processes and users to system resources. Its goal is to ensure that each component of the system uses resources only as authorized.

### Detailed Explanation

#### Goals of Protection
- Ensure each shared resource is used **only in accordance with system policies**.
- Prevent unauthorized access to resources.
- Detect and prevent **accidental** misuse by authorized users.
- Enforce the **principle of least privilege**.
- Provide a framework for **access control**.

#### Principle of Least Privilege
- Each process/user should operate with the **minimum set of privileges** needed to complete its task.
- Reduces the damage that can result from accidents, errors, or security breaches.
- Example: A web server process should not have root access.

#### Principle of Need-to-Know
- A user should have access only to the information **necessary for their job**.
- Extends least privilege to data access.

### Key Points / Highlights
- Protection is about **internal access control** (who can access what resource).
- **Least privilege** = minimum privileges needed. Reduces attack surface.
- Protection mechanisms should be **flexible** (policy-independent) — the mechanism should not dictate the policy.

### MCQ Focus Section
- **Principle of least privilege** reduces the potential damage from security incidents.
- Protection deals with **internal** threats; security deals with **external** threats.
- Protection mechanisms should be **separated from policy** (mechanism vs policy).
- Protection ensures **authorized use** of system resources.

---

## 7.6 Domain of Protection

### Definition
A **protection domain** specifies a set of **objects** (resources) and the **access rights** (operations: read, write, execute) that a process operating in that domain has on those objects.

### Detailed Explanation

- Each process operates in a protection domain.
- A domain defines **what resources** a process can access and **what operations** it can perform.
- Domain can be associated with:
  - **User**: All processes of a user share a domain.
  - **Process**: Each process has its own domain.
  - **Procedure/Function**: Domain changes when entering a different procedure.
- **Domain switching**: A process can switch from one domain to another (e.g., a system call switches from user domain to kernel domain).

### MCQ Focus Section
- A **domain** = set of (object, rights) pairs.
- A **system call** is an example of **domain switching** (user mode → kernel mode).
- Different users operate in **different domains** with different access rights.
- Protection domains determine **what a process is allowed to do**.

---

## 7.7 Access Matrix

### Definition
The **Access Matrix** is a model for representing the **protection state** of a system. It is a matrix where **rows** represent domains (users/processes), **columns** represent objects (resources), and **entries** specify the **access rights**.

### Detailed Explanation

#### Structure
| | File1 | File2 | Printer | Memory |
|----------|-------|-------|---------|--------|
| **Domain1 (UserA)** | read, write | read | print | — |
| **Domain2 (UserB)** | read | read, write | — | read |
| **Domain3 (Root)** | read, write | read, write | print | read, write |

- Each entry `Access(Di, Oj)` defines the operations domain Di can perform on object Oj.
- An **empty entry** means no access.

#### Implementation of Access Matrix

**1. Global Table**
- Store all (domain, object, rights) triples in one table.
- Simple but very large and wastes space (many empty entries).

**2. Access Control List (ACL) — Column-wise**
- Each **object** has a list of (domain, access rights) pairs.
- When a process requests access, check the ACL of the object.
- **Used by**: File systems (UNIX permissions, Windows NTFS).
- Efficient for answering: "Who can access this object?"

**3. Capability List (C-List) — Row-wise**
- Each **domain/process** has a list of (object, access rights) pairs — called **capabilities**.
- A capability is like a **ticket** or **token** granting access to an object.
- Efficient for answering: "What can this process access?"
- **Problem**: Capabilities can be forged or copied if not protected.

**4. Lock-Key Mechanism**
- Each **object** has a lock (bit pattern); each **domain** has a key (bit pattern).
- Access is granted if the key **matches** the lock.
- Combination of ACL and Capability approaches.

### Key Points / Highlights
- Access matrix is a **conceptual model** — not implemented directly (too large and sparse).
- **ACL** = per-object list. **Capability List** = per-domain list.
- UNIX file permissions are a simplified ACL (owner, group, others × read, write, execute).

### MCQ Focus Section
- **Access Matrix**: rows = domains, columns = objects, entries = access rights.
- **ACL** is stored per **object** (column-wise). Good for object-centric access control.
- **Capability List** is stored per **domain/process** (row-wise). Good for process-centric access control.
- **UNIX permissions** (rwx for user, group, others) are a form of simplified **ACL**.
- The access matrix is **sparse** in practice — direct implementation wastes space.
- **Capabilities** can be distributed like tokens — must be **unforgeable**.
- **Lock-Key** combines ACL and capability concepts.
- The access matrix model was introduced by **Lampson**.

---

## 7.8 System and Network Threats

### Definition
**System and network threats** are attacks targeting the OS, system services, and network infrastructure to gain unauthorized access, disrupt services, or steal data.

### Detailed Explanation

#### Common Attacks

**1. Denial of Service (DoS)**
- Overwhelms a system or network with excessive traffic, making it **unavailable** to legitimate users.
- **DDoS** (Distributed DoS): Uses multiple compromised machines (botnet) to launch the attack.

**2. Man-in-the-Middle (MITM)**
- Attacker intercepts communication between two parties, reading or modifying messages.
- **Prevention**: End-to-end encryption, HTTPS, digital certificates.

**3. Phishing**
- Fraudulent attempt to obtain sensitive information by disguising as a trustworthy entity (e.g., fake bank website, deceptive emails).

**4. Port Scanning**
- Scanning a system's network ports to find **open ports** and **running services** — used as reconnaissance before an attack.
- Tools: Nmap.

**5. IP Spoofing**
- Forging the **source IP address** of a packet to impersonate another system.

**6. Replay Attack**
- Capturing and retransmitting valid data (e.g., login credentials) to gain unauthorized access.
- **Prevention**: Timestamps, nonces, session tokens.

### Key Points / Highlights
- **DoS/DDoS** targets availability.
- **MITM** targets confidentiality and integrity.
- **Phishing** targets user trust.
- Prevention involves encryption, firewalls, intrusion detection, and user education.

### MCQ Focus Section
- **DoS** makes a service **unavailable** by overwhelming it with requests.
- **DDoS** uses a **botnet** (network of compromised computers).
- **MITM** sits between sender and receiver to eavesdrop or modify messages.
- **Phishing** tricks users into revealing sensitive information.
- A **firewall** filters network traffic based on security rules.
- An **IDS (Intrusion Detection System)** monitors for suspicious activity.
- An **IPS (Intrusion Prevention System)** detects and **blocks** attacks automatically.

---

---

# UNIT 8: MEMORY MANAGEMENT

---

## 8.1 Logical and Physical Address Space

### Definition
- **Logical Address (Virtual Address)**: The address generated by the **CPU** during program execution. It is the address the process "sees."
- **Physical Address**: The actual address in **main memory (RAM)** where data is stored.
- The **Memory Management Unit (MMU)** performs the mapping from logical to physical addresses at runtime.

### Detailed Explanation

#### Compile-Time and Load-Time Binding
- If addresses are fixed at compile or load time → logical = physical address.
- If addresses are bound at **execution time** → logical ≠ physical. MMU translates at runtime.
- **Execution-time binding** is the most flexible — used in modern OS.

#### Address Spaces
- **Logical Address Space**: The set of all logical addresses generated by a process.
- **Physical Address Space**: The set of all physical addresses in main memory.
- The MMU (with base register or page table) maps logical → physical.

#### Base and Limit Registers (Simple Scheme)
- **Base Register**: Holds the starting physical address of the process.
- **Limit Register**: Holds the size of the process's address space.
- Physical Address = Base + Logical Address.
- If Logical Address > Limit → **trap** (memory protection error).

### Key Points / Highlights
- Logical address = CPU-generated; Physical address = actual RAM location.
- **MMU** translates logical → physical.
- **Base and Limit registers** provide memory protection.

### MCQ Focus Section
- **Logical address** is generated by the **CPU**; **Physical address** is seen by the **memory**.
- The **MMU** maps logical addresses to physical addresses.
- In **execution-time binding**, logical ≠ physical address.
- **Base register** provides relocation; **Limit register** provides protection.
- Physical address = **Base + Logical address** (in contiguous allocation).

---

## 8.2 Swapping

### Definition
**Swapping** is the process of temporarily moving a **process from main memory to disk (backing store)** and bringing it back later for continued execution. It allows more processes than can fit in physical memory.

### Detailed Explanation

- **Swap Out**: Move a process from RAM to disk.
- **Swap In**: Move a process from disk to RAM.
- The **medium-term scheduler** manages swapping.
- The **backing store** (swap space) is a fast, large enough disk area.
- Swapping allows the OS to maintain a higher **degree of multiprogramming**.
- **Swapping is expensive** — transfer time is proportional to the amount of memory swapped.

### Key Points / Highlights
- Swapping moves **entire processes** between memory and disk.
- Managed by the **medium-term scheduler**.
- **Transfer time** = main cost of swapping.
- Modern OS use **virtual memory** (demand paging) instead of full swapping.

### MCQ Focus Section
- **Swap out** = memory to disk; **Swap in** = disk to memory.
- The **backing store** must be large enough to hold all swapped processes.
- Swapping increases the **degree of multiprogramming**.
- **Transfer time** depends on the size of the process being swapped.
- Modern systems use **demand paging** instead of full process swapping.

---

## 8.3 Contiguous Memory Allocation

### Definition
In **Contiguous Memory Allocation**, each process is allocated a **single contiguous block** of memory. The memory is divided into partitions, and each partition is assigned to a process.

### Detailed Explanation

#### Fixed-Size Partitions
- Memory is divided into **fixed-size** partitions.
- Each partition holds one process.
- Simple to implement.
- **Internal Fragmentation**: If a process is smaller than the partition, the remaining space within the partition is **wasted**.

#### Variable-Size Partitions
- Partitions are created **dynamically** based on process size — no fixed boundaries.
- No internal fragmentation.
- **External Fragmentation**: After processes are loaded and removed, free memory is scattered in **small, non-contiguous holes** that cannot satisfy a large request even though total free memory is sufficient.

#### Memory Allocation Strategies (for Variable Partitions)

| Strategy | Description | Pros | Cons |
|----------|-------------|------|------|
| **First Fit** | Allocate the **first** hole large enough | Fast (stops at first match) | May waste space at the start |
| **Best Fit** | Allocate the **smallest** hole large enough | Minimizes wasted space in the allocated hole | Produces many tiny leftover holes; slow |
| **Worst Fit** | Allocate the **largest** hole | Leaves larger remainder (potentially usable) | Wastes largest block; slow |

#### Compaction
- **Compaction** = moving all processes together in memory to merge all free holes into **one large block**.
- Solves **external fragmentation** but is **expensive** (requires moving all processes, updating addresses).
- Only possible if relocation is **dynamic** (execution-time binding).

### Key Points / Highlights
- **Internal fragmentation** = wasted space within an allocated partition (fixed partitions).
- **External fragmentation** = wasted space as scattered holes (variable partitions).
- **First Fit** is generally fastest; **Best Fit** produces smallest leftover.
- **Compaction** solves external fragmentation but is costly.

### MCQ Focus Section
- **First Fit** is generally the **fastest** and often the best in practice.
- **Best Fit** produces the **smallest leftover** but creates many small holes.
- **Worst Fit** produces the **largest leftover** — least efficient.
- **Internal fragmentation** occurs in **fixed-size** partitions.
- **External fragmentation** occurs in **variable-size** partitions.
- **Compaction** eliminates external fragmentation but requires **dynamic relocation**.
- **50% Rule** (for First Fit): Given N allocated blocks, approximately **N/2 blocks** will be lost to external fragmentation.

---

## 8.4 Paging

### Definition
**Paging** is a memory management scheme that eliminates the need for **contiguous allocation**. It divides:
- **Logical memory** into fixed-size blocks called **pages**.
- **Physical memory** into fixed-size blocks called **frames**.
- Pages are mapped to frames using a **page table**.

### Detailed Explanation

#### Key Concepts
- **Page size = Frame size** (typically 4 KB).
- A page can be placed in **any available frame** — no need for contiguous allocation.
- **Page Table**: A data structure maintained by the OS for each process. Maps page numbers to frame numbers.
- **Logical address** = **Page Number (p)** + **Page Offset (d)**.
  - Page Number = index into the page table.
  - Page Offset = position within the page.
- **Physical address** = **Frame Number (f)** + **Frame Offset (d)**.
  - Frame Number = obtained from the page table.
  - Offset remains the same.
- Page table is stored in **main memory**. Its base address is stored in the **Page Table Base Register (PTBR)**.

#### Address Translation
1. Logical address = (page number p, offset d).
2. Look up page table at index p → get frame number f.
3. Physical address = f × page_size + d.

#### Advantages
- **No external fragmentation** — any frame can hold any page.
- Simplifies memory allocation — no need to find contiguous space.
- Easy **sharing**: Multiple processes can share pages by pointing to the same frame.

#### Disadvantages
- **Internal fragmentation**: Last page of a process may not be fully utilized.
- **Page table overhead**: Page table can be very large (for large address spaces).
- **Extra memory access**: One access for page table + one for actual data = **two memory accesses**.

#### Translation Lookaside Buffer (TLB)
- A **hardware cache** that stores **recent page-to-frame mappings**.
- If the page number is found in the TLB → **TLB hit** → get frame number directly (fast).
- If not in TLB → **TLB miss** → access page table in memory, then update TLB.
- **Effective Access Time (EAT)** = hit_ratio × (TLB + memory) + (1 − hit_ratio) × (TLB + 2 × memory).
- TLB significantly reduces the average memory access time.

### Key Points / Highlights
- Paging eliminates **external fragmentation**.
- May have **internal fragmentation** in the last page.
- Uses a **page table** for address translation.
- **TLB** caches recent translations for speed.
- Page size is typically **4 KB**.

### MCQ Focus Section
- Paging eliminates **external fragmentation** but may have **internal fragmentation**.
- Logical address = **Page Number + Offset**. Physical address = **Frame Number + Offset**.
- **Page size = Frame size** (always).
- Number of pages = Logical address space / Page size.
- Number of frames = Physical memory / Frame size.
- **TLB hit** avoids the extra memory access for the page table.
- **Two memory accesses** without TLB (one for page table, one for data).
- **PTBR** (Page Table Base Register) holds the base address of the page table.
- **Page offset** is the **same** in both logical and physical addresses.
- If page size = 2^n bytes, the last n bits of the logical address = offset.

---

## 8.5 Multi-Level Paging

### Definition
**Multi-level paging** divides the page table itself into pages, creating a **hierarchy of page tables**. This avoids storing a huge, contiguous page table in memory.

### Detailed Explanation

#### Problem with Single-Level Page Table
- For a 32-bit address space with 4 KB pages: Number of pages = 2^32 / 2^12 = 2^20 = ~1 million entries.
- If each entry = 4 bytes → page table size = 4 MB per process — too large to keep contiguous.

#### Two-Level Paging
- The page table is itself broken into pages.
- Logical address is divided into: **Outer Page Number + Inner Page Number + Offset**.
- First, lookup the outer page table → get the base of the inner page table.
- Then, lookup the inner page table → get the frame number.
- Requires **3 memory accesses** (outer table + inner table + actual data).

#### General Multi-Level
- For 64-bit systems, even two levels may not be sufficient — may need 3 or 4 levels.
- Each additional level adds **one more memory access**.
- **TLB** is essential to keep performance acceptable with multi-level paging.

### Key Points / Highlights
- Multi-level paging breaks a large page table into smaller pages.
- Reduces memory needed for page tables (only pages of page table that are needed are kept in memory).
- Adds **more memory accesses** per translation (mitigated by TLB).

### MCQ Focus Section
- **Two-level paging** requires **3 memory accesses** (without TLB).
- **Three-level paging** requires **4 memory accesses** (without TLB).
- Multi-level paging solves the problem of **large page tables**.
- In a **k-level page table**, **k+1 memory accesses** are needed (without TLB).
- **TLB** is critical for multi-level paging performance.

---

## 8.6 Segmentation

### Definition
**Segmentation** is a memory management scheme that divides the logical address space into **variable-sized segments**, each representing a logical unit of the program (e.g., main code, functions, stack, heap, data, symbol table).

### Detailed Explanation

#### Key Concepts
- Unlike paging (fixed-size pages), segments are **variable-sized** — they match the **logical structure** of the program.
- **Logical address** = **Segment Number (s)** + **Offset (d)**.
- **Segment Table**: Maps segment numbers to physical addresses.
  - Each entry has: **Base** (starting physical address) + **Limit** (length of the segment).
- Address translation: Physical Address = Segment_Base + Offset. If Offset > Limit → **trap** (protection error).

#### Paging vs Segmentation

| Feature | Paging | Segmentation |
|---------|--------|--------------|
| Division | Fixed-size **pages** | Variable-size **segments** |
| View | Physical view (not visible to programmer) | Logical view (visible to programmer) |
| Internal Fragmentation | Yes (last page) | No |
| External Fragmentation | No | **Yes** (variable-size segments) |
| Address | Page number + offset | Segment number + offset |
| Table | Page table | Segment table |
| Sharing | Harder (page-level) | Easier (segment-level: share a procedure or data segment) |

#### Segmentation with Paging
- Combines both approaches: segments are further divided into **pages**.
- Eliminates **external fragmentation** of segmentation.
- Used in systems like **Intel x86** (in older modes).
- Each segment has its own **page table**.

### Key Points / Highlights
- Segmentation matches the **logical structure** of programs.
- Segments are **variable-sized** → external fragmentation.
- Segmentation with paging combines benefits of both — no external fragmentation.

### MCQ Focus Section
- Paging → **internal** fragmentation. Segmentation → **external** fragmentation.
- Segmentation with paging → **no** external fragmentation, **minimal** internal fragmentation.
- Segment table has **base** and **limit** entries for each segment.
- If **offset > limit** → memory protection error (trap).
- Segmentation supports **logical sharing** (share a function, data segment).
- **Intel Pentium** used segmentation with paging.

---

## 8.7 Overlays

### Definition
**Overlays** is a technique used to run programs that are **larger than available main memory**. The idea is to keep in memory only the parts of the program that are currently needed, and swap other parts in from disk when needed.

### Detailed Explanation
- The programmer manually divides the program into **overlays** (modules).
- At any time, only the **needed overlay** is in memory; others remain on disk.
- When a new module is needed, it **replaces (overlays)** the current one in memory.
- **No OS support needed** — the programmer handles everything.
- Largely **obsolete** now — replaced by **virtual memory** (which provides automatic overlay management by the OS).

### Key Points / Highlights
- Overlays allow running programs **larger than physical memory**.
- **Programmer's responsibility** to manage overlays (manual).
- Predecessor to **virtual memory** — now obsolete.

### MCQ Focus Section
- Overlays are managed by the **programmer**, NOT the OS.
- Overlays were used when physical memory was too **small** for the entire program.
- Replaced by **virtual memory** and **demand paging** (automatic, OS-managed).
- Overlays are a **manual** technique; virtual memory is **automatic**.

---

## 8.8 Virtual Memory Concept

### Definition
**Virtual Memory** is a memory management technique that provides the illusion of having more memory than what is physically available. It allows processes to use memory addresses that don't correspond to physical RAM addresses, with the OS and hardware handling the mapping.

### Detailed Explanation

#### Key Concepts
- Each process has its own **virtual address space** (much larger than physical memory).
- Only the **needed pages** of a process are kept in physical memory; the rest reside on **disk (swap space/page file)**.
- The OS loads pages **on demand** — when a page not in memory is accessed.
- Virtual memory is implemented using **demand paging** (or demand segmentation).
- Provides **process isolation** — each process has its own virtual address space.

#### Benefits
- Processes can be **larger than physical memory**.
- **More processes** can reside in memory (only active pages are loaded).
- **Less I/O** for loading/swapping — only needed pages are loaded.
- **Process isolation** — one process cannot access another's memory.
- **Shared libraries/pages** — multiple processes can share common pages (e.g., libc).

### Key Points / Highlights
- Virtual memory decouples **logical memory** from **physical memory**.
- Implemented using **demand paging**.
- Allows programs larger than physical RAM to execute.
- Each process has its own **virtual address space**.

### MCQ Focus Section
- Virtual memory allows a process to execute even if it is **not entirely in memory**.
- Virtual memory is implemented using **demand paging**.
- Virtual memory uses both **RAM** and **disk** (swap space).
- **Locality of reference** makes virtual memory efficient — programs tend to access a small set of pages repeatedly.
- The **page file / swap space** on disk holds pages not currently in RAM.
- Virtual memory provides **process isolation** and supports **shared libraries**.

---

## 8.9 Demand Paging

### Definition
**Demand Paging** is a virtual memory technique where pages are loaded into physical memory **only when they are needed** (referenced), not in advance. It is a **lazy evaluation** strategy — don't load a page until it must be used.

### Detailed Explanation

#### How It Works
1. When a process starts, **no pages** are loaded into memory (pure demand paging).
2. When the process accesses a page not in memory, a **page fault** occurs.
3. The OS handles the page fault:
   1. Check page table — is the reference valid? If invalid → abort.
   2. Find a **free frame** in physical memory.
   3. **Read the page** from disk into the free frame.
   4. **Update the page table** to reflect the new mapping.
   5. **Restart** the instruction that caused the page fault.
4. Subsequent accesses to the same page are served from physical memory (no page fault).

#### Valid/Invalid Bit
- Each page table entry has a **valid/invalid bit**.
- **Valid (v)**: Page is in physical memory — access is normal.
- **Invalid (i)**: Page is NOT in physical memory — accessing it causes a **page fault**.

#### Page Fault Rate and EAT
- **Page Fault Rate (p)**: Fraction of accesses that cause a page fault (0 ≤ p ≤ 1).
- **Effective Access Time (EAT)** = (1 − p) × memory_access_time + p × page_fault_service_time.
- Page fault service time includes: OS overhead + disk I/O (very slow) + restart. Typically **8–10 ms**.
- Memory access time is typically **10–200 ns**.
- Even a small p significantly increases EAT → page faults must be minimized.

### Key Points / Highlights
- Demand paging loads pages **only when needed** — reduces I/O and memory usage.
- **Page fault** = accessing a page not in memory → OS loads it from disk.
- **EAT** depends on page fault rate — low p is critical for performance.
- Pure demand paging = start with no pages in memory.

### MCQ Focus Section
- **Page fault** = accessing a page with valid/invalid bit set to **invalid**.
- **EAT** = (1-p) × memory_time + p × page_fault_time.
- **Pure demand paging**: No pages loaded initially; all loaded on demand via page faults.
- Page fault handling involves **disk I/O** — the most expensive step.
- The OS uses the **page table valid/invalid bit** to detect page faults.
- After a page fault, the instruction is **restarted** (not continued from the next instruction).
- If p = 0 → no page faults → EAT = memory access time (optimal).
- **Thrashing** occurs when the page fault rate is extremely high (too many page faults).

---

## 8.10 Page Replacement Algorithms

### Definition
When a **page fault** occurs and there are **no free frames** in physical memory, the OS must select a page to **remove (replace)** to make room for the new page. **Page replacement algorithms** determine which page to evict.

### Detailed Explanation

#### Goal
- **Minimize the number of page faults** (minimize page fault rate).

#### 1. FIFO (First In, First Out)
- Replace the **oldest** page in memory (the one that was loaded first).
- Simple to implement (use a queue).
- **Belady's Anomaly**: Increasing the number of frames can **increase** page faults (counterintuitive). FIFO is the only common algorithm that suffers from this.

#### 2. Optimal (OPT / MIN)
- Replace the page that will **not be used for the longest time** in the future.
- Produces the **minimum number of page faults** — theoretically optimal.
- **Not implementable** in practice — requires future knowledge of page references.
- Used as a **benchmark** to compare other algorithms.

#### 3. LRU (Least Recently Used)
- Replace the page that has **not been used for the longest time** (look backward, not forward).
- Based on **temporal locality**: if a page hasn't been used recently, it's unlikely to be used soon.
- **Approximation of Optimal** — generally performs well.
- **Implementation**:
  - **Counter-based**: Each page table entry has a timestamp. Replace the page with the oldest timestamp.
  - **Stack-based**: Maintain a stack of page numbers. On access, move the page to the top. Bottom = LRU.
- **Does NOT** suffer from Belady's Anomaly (it is a **stack algorithm**).

#### 4. LRU Approximation Algorithms
- True LRU requires hardware support — approximations are used in practice.
- **Reference Bit Algorithm**: Each page has a reference bit (set to 1 when accessed). Periodically, replace a page with reference bit = 0.
- **Second Chance (Clock Algorithm)**: FIFO with a modification. If the oldest page has reference bit = 1, give it a "second chance" — set bit to 0 and move to the end. If bit = 0, replace it. Uses a circular queue (clock hand).
- **Enhanced Second Chance**: Uses both reference bit and dirty bit (modified). Preference: (0,0) > (0,1) > (1,0) > (1,1). Replace the page with the lowest class first.

#### 5. Counting-Based Algorithms
- **LFU (Least Frequently Used)**: Replace the page with the **smallest access count**.
- **MFU (Most Frequently Used)**: Replace the page with the **largest access count** (based on the reasoning that a page with a small count was probably just brought in).
- Less common — LRU-based algorithms are preferred.

### Key Points / Highlights
| Algorithm | Strategy | Belady's Anomaly? | Practical? |
|-----------|---------|-------------------|------------|
| FIFO | Oldest page | **Yes** | Yes (simple) |
| Optimal (OPT) | Page not used for longest future time | No | **No** (needs future knowledge) |
| LRU | Page not used for longest past time | No | Yes (approximated) |
| Second Chance | FIFO + reference bit | No (approx) | Yes |

### MCQ Focus Section
- **FIFO** suffers from **Belady's Anomaly** — more frames can cause more page faults.
- **Optimal (OPT)** gives the **minimum page faults** but is **not practical** (requires future knowledge).
- **LRU** is the best practical algorithm — approximates Optimal using past behavior.
- **LRU** does NOT suffer from Belady's Anomaly.
- **Second Chance** = modified FIFO using reference bits — a practical LRU approximation.
- **Dirty bit (modified bit)**: If set, the page has been modified and must be **written back to disk** before replacement.
- **Stack algorithms** (LRU, OPT) never exhibit Belady's Anomaly.
- **FIFO** is the simplest but often the **worst** performing algorithm.

---

## 8.11 Fragmentation — Internal and External

### Definition
**Fragmentation** is wasted memory space that reduces the effective usable memory.
- **Internal Fragmentation**: Wasted space **within** an allocated memory block (allocated block is larger than needed).
- **External Fragmentation**: Wasted space **outside** allocated blocks — total free memory exists but is scattered in non-contiguous holes.

### Detailed Explanation

| Type | Cause | Occurs In | Solution |
|------|-------|-----------|----------|
| Internal | Fixed-size allocation | Paging (last page), Fixed partitions | Reduce allocation unit size |
| External | Variable-size allocation | Segmentation, Variable partitions | **Compaction** or **Paging** |

- **Paging**: Eliminates external fragmentation (any frame works). Has small internal fragmentation in the last page.
- **Segmentation**: Variable-sized segments → external fragmentation. No internal fragmentation.
- **Segmentation with Paging**: Eliminates external fragmentation. Small internal fragmentation.

### MCQ Focus Section
- **Paging** → only **internal** fragmentation (in the last page).
- **Segmentation** → only **external** fragmentation.
- **Contiguous allocation (variable)** → **external** fragmentation.
- **Contiguous allocation (fixed)** → **internal** fragmentation.
- **Compaction** solves external fragmentation but is expensive.
- **Best Fit** allocation creates the most external fragmentation (many small unusable holes).
- Average internal fragmentation per process = **half a page** (page_size / 2).

---

## 8.12 Thrashing

### Definition
**Thrashing** occurs when a process spends **more time paging (swapping pages in and out) than executing** — the system is busy doing I/O for page faults but no useful work is being done.

### Detailed Explanation

#### Causes
- Too many processes in memory → each gets too few frames → frequent page faults → pages are constantly swapped in/out → CPU utilization **drops**.
- The OS may interpret low CPU utilization as needing more processes → admits more → makes thrashing **worse** (vicious cycle).

#### Solution: Working Set Model
- The **Working Set** of a process = the set of pages it actively uses in a recent time window (Δ).
- If the OS provides enough frames to hold each process's working set, thrashing is avoided.
- If total working set demand > available frames → suspending some processes is necessary.

#### Solution: Page Fault Frequency (PFF)
- Monitor the **page fault rate** of each process.
- If page fault rate is **too high** → give the process more frames.
- If page fault rate is **too low** → take frames away.
- If no free frames are available → suspend a process.

### Key Points / Highlights
- Thrashing = too many page faults → CPU utilization drops → system degrades.
- Caused by **too many processes with too few frames each**.
- Solutions: **Working Set Model** and **Page Fault Frequency (PFF)**.
- The OS should not admit more processes when thrashing is detected.

### MCQ Focus Section
- **Thrashing** = more time paging than executing.
- During thrashing, **CPU utilization drops** dramatically.
- The OS may worsen thrashing by admitting **more processes** (thinking CPU is idle).
- **Working Set** = pages actively used in recent window Δ.
- **PFF** adjusts frame allocation based on page fault rate.
- **Locality of reference** prevents thrashing under normal conditions.
- **Thrashing** can be reduced by **reducing the degree of multiprogramming** (suspending processes).

---

---

# UNIT 9: FILE MANAGEMENT

---

## 9.1 File Concepts

### Definition
A **File** is a named collection of related information stored on secondary storage (disk). It is the smallest unit of persistent storage managed by the OS. A file can contain data (text, binary, images) or programs (executables).

### Detailed Explanation

#### File Attributes
| Attribute | Description |
|-----------|-------------|
| **Name** | Human-readable identifier (e.g., report.pdf) |
| **Identifier** | Unique tag (number) used by the OS internally |
| **Type** | File extension/type (.txt, .exe, .jpg, .c) |
| **Location** | Pointer to file's location on disk |
| **Size** | Current file size (in bytes) |
| **Protection** | Access control information (read, write, execute permissions) |
| **Timestamps** | Creation, last modification, last access times |
| **Owner** | User who owns the file |

#### File Operations
- **Create**: Allocate space, create directory entry.
- **Open**: Find directory entry, load metadata into memory (returns file descriptor).
- **Read**: Read data from current file position.
- **Write**: Write data at current file position.
- **Seek (Reposition)**: Move the file pointer to a specific position.
- **Delete**: Remove directory entry, deallocate disk space.
- **Truncate**: Erase file contents but keep attributes.
- **Close**: Release memory buffers, update directory entry.

#### File Types
- **Regular files**: Contain user data (text or binary).
- **Directory files**: Contain information about other files.
- **Special files**: Represent I/O devices (character special, block special).
- **Links**: Pointers to other files (hard links, symbolic links).

### Key Points / Highlights
- A file is the basic unit of **persistent storage**.
- Files have attributes: name, type, size, location, protection, timestamps.
- The OS provides operations: create, open, read, write, seek, delete, close.
- A **file descriptor** (or file handle) is returned by `open()` for subsequent operations.

### MCQ Focus Section
- A **file descriptor** is an integer that identifies an open file within a process.
- **File extension** indicates the type but is NOT enforced by all OS (UNIX doesn't enforce; Windows does to some extent).
- `open()` returns a **file descriptor** in UNIX or a **file handle** in Windows.
- Standard file descriptors in UNIX: **0 = stdin, 1 = stdout, 2 = stderr**.
- **Truncate** removes content but keeps the file (resets size to 0).
- The **file pointer** tracks the current position for read/write operations.

---

## 9.2 Access Methods

### Definition
**Access Methods** determine how data in a file is accessed and read. The two primary methods are **sequential access** and **direct (random) access**.

### Detailed Explanation

#### 1. Sequential Access
- Data is read/written in **order**, one record after another.
- The file pointer moves forward automatically after each read/write.
- Can only go forward; to go back, must **rewind** to the beginning.
- **Most common** access method (e.g., text editors, compilers, log files).

#### 2. Direct Access (Random Access)
- Data can be read/written at any **arbitrary position** — no need to process preceding records.
- Uses a **block/record number** to directly access the desired data.
- File is viewed as a numbered sequence of blocks.
- Useful for **databases**, where records need to be accessed in any order.
- **seek()** operation is used to move the file pointer to the desired position.

#### 3. Indexed Access
- An **index** is built on top of the file, containing pointers to various blocks/records.
- To access a record, first search the index for its pointer, then directly access the block.
- Used for large files with frequent search operations.
- Like a **book index** — look up the topic, find the page number, go to that page.

### Key Points / Highlights
- **Sequential**: Read in order. Simple. Most common.
- **Direct (Random)**: Read any position. Uses block numbers. Good for databases.
- **Indexed**: Uses an index for fast lookup. Best for search-heavy applications.

### MCQ Focus Section
- **Sequential access** reads data in order — most common for **text files and logs**.
- **Direct access** allows jumping to any position — uses **block/record numbers**.
- **Indexed access** uses an **index** for efficient searching.
- Magnetic **tapes** only support **sequential access**.
- Magnetic **disks** support both **sequential and direct access**.
- **seek()** changes the file position pointer for direct access.

---

## 9.3 Directory Structure

### Definition
A **Directory** is a special file that contains information (name, type, location, size, etc.) about other files. The **directory structure** organizes all files on a disk.

### Detailed Explanation

#### 1. Single-Level Directory
- All files are in **one directory**.
- Simple but impractical for many files — **naming conflicts** (no two files can have the same name).

#### 2. Two-Level Directory
- Each user has their own **separate directory** (User File Directory — UFD).
- A **Master File Directory (MFD)** points to each user's directory.
- **No naming conflict** between different users.
- **Problem**: Users cannot group files; no subdirectories.

#### 3. Tree-Structured Directory (Hierarchical)
- Generalization of two-level — arbitrary depth of subdirectories.
- Each directory can contain files and other directories.
- Uses **absolute path** (from root) and **relative path** (from current directory).
- **Most commonly used** structure (UNIX, Windows).
- Efficient searching and organization.

#### 4. Acyclic Graph Directory
- Allows **sharing** of files or directories between users.
- A file/directory can have **multiple paths** to it (hard links, symbolic links).
- **No cycles allowed** — avoids infinite loops in traversal.
- **Problem**: Dangling pointers when the shared file is deleted.

#### 5. General Graph Directory
- Allows **cycles** — a directory could point back to an ancestor.
- **Problem**: Cycles complicate traversal, searching, and deletion (can cause infinite loops).
- **Solution**: Limit the number of links followed, or use **garbage collection** to detect unreachable files.

### Key Points / Highlights
- **Tree structure** is the most common — hierarchical with subdirectories.
- **Acyclic graph** allows sharing via links (hard/symbolic) without cycles.
- **General graph** allows cycles but introduces complexity.

### MCQ Focus Section
- **Single-level** directory has **naming conflict** problems.
- **Two-level** directory separates users but no subdirectories.
- **Tree-structured** is the most widely used (UNIX, Windows).
- **Acyclic graph** supports file sharing via **links**, no cycles.
- **Hard link**: Points directly to the file's inode. File is deleted only when **all hard links are removed**.
- **Symbolic (soft) link**: Points to the file's **path name**. Can cross file systems. Becomes **dangling** if the target is deleted.
- **Absolute path**: Starts from the **root** directory (e.g., /home/user/file.txt).
- **Relative path**: Starts from the **current working directory** (e.g., ./file.txt).

---

## 9.4 File System Mounting and Sharing

### Definition
**Mounting** is the process of making a file system accessible at a specific point (mount point) in the existing directory tree. **File Sharing** allows multiple users or systems to access the same files.

### Detailed Explanation

#### Mounting
- Before accessing files on a storage device, its file system must be **mounted** on the OS's directory tree.
- The **mount point** is an existing empty directory where the new file system is attached.
- In UNIX: `mount /dev/sdb1 /mnt/usb` mounts the USB drive's file system at /mnt/usb.
- The root file system is mounted at boot time at `/` (root).

#### File Sharing
- **Local sharing**: Multiple users on the same system access shared files. Managed by **permissions** (owner, group, others).
- **Remote sharing**: Files shared across a network. Protocols:
  - **NFS (Network File System)**: UNIX/Linux standard for network file sharing.
  - **SMB/CIFS**: Windows standard (also used by Samba on Linux).
- **Client-Server model**: A file server provides files; clients access them remotely.
- **Consistency issues**: When multiple users modify the same file simultaneously. Solutions: file locking, version control.

### Key Points / Highlights
- Mounting attaches a file system to the directory tree at a **mount point**.
- File sharing uses **permissions** locally and **NFS/SMB** for network sharing.

### MCQ Focus Section
- **Mount** = attach a file system to the directory tree.
- **Unmount** = detach a file system before removing the device.
- **NFS** is the standard for file sharing on UNIX/Linux.
- **SMB/CIFS** is the standard for file sharing on Windows.
- A **mount point** is a directory where the new file system becomes accessible.
- The **root file system** is mounted at **/** during boot.

---

## 9.5 Protection

### Definition
**File protection** mechanisms control **who** can access a file and **what** operations they can perform (read, write, execute).

### Detailed Explanation

#### UNIX File Permissions
- Three categories of users: **Owner (u)**, **Group (g)**, **Others (o)**.
- Three permissions per category: **Read (r)**, **Write (w)**, **Execute (x)**.
- Represented as: `rwxr-xr--` (owner: rwx, group: r-x, others: r--).
- **Numeric representation**: r=4, w=2, x=1. Example: `755` = rwxr-xr-x.
- Changed using `chmod` command.
- **Ownership** changed using `chown` (change owner) and `chgrp` (change group).

#### Access Control List (ACL)
- More fine-grained than UNIX permissions.
- Specifies permissions for **individual users** and **groups** (not just owner/group/others).
- Used in **Windows NTFS** and optionally in UNIX.

### Key Points / Highlights
- UNIX uses **rwx permissions** for owner, group, others.
- **chmod 755** = owner: full, group: read+execute, others: read+execute.
- ACLs provide finer-grained control than traditional UNIX permissions.

### MCQ Focus Section
- UNIX permission `rwxr-xr--` in numeric = **754**.
- `chmod 644 file` = owner: rw-, group: r--, others: r--.
- **r=4, w=2, x=1** — add values for combined permissions.
- **setuid** bit allows a program to run with the **owner's privileges** (not the caller's).
- **ACL** provides per-user/per-group permissions beyond the basic three categories.
- Default permissions are set using the **umask** command.

---

## 9.6 Allocation Methods

### Definition
**File allocation methods** determine how disk blocks are allocated to files. The three main methods are **contiguous, linked, and indexed allocation**.

### Detailed Explanation

#### 1. Contiguous Allocation
- Each file occupies a **contiguous set of blocks** on disk.
- **Directory entry**: File name, start block, length.
- **Advantages**: Simple. Fast **sequential** and **direct access** (block n = start + n).
- **Disadvantages**: **External fragmentation** (as files are created/deleted). Difficult to grow files (no room to extend).

#### 2. Linked Allocation
- Each file is a **linked list of blocks**. Each block contains a pointer to the next block.
- **Directory entry**: File name, start block, end block.
- **Advantages**: No external fragmentation. Files can grow easily.
- **Disadvantages**: Only **sequential access** (no direct access — must follow pointers). Pointer space overhead in each block. Reliability issues (one broken pointer → rest of file lost).
- **FAT (File Allocation Table)**: A variation where all pointers are stored in a **central table** in memory rather than in each disk block. Improves random access. Used in **FAT12, FAT16, FAT32** file systems.

#### 3. Indexed Allocation
- Each file has an **index block** (like a page table) containing pointers to all its data blocks.
- **Directory entry**: File name, index block number.
- **Advantages**: Supports both **sequential and direct access**. No external fragmentation.
- **Disadvantages**: Overhead of the index block (wastes space for small files). For large files, need **multi-level index** or **combined scheme**.
- **UNIX inode** uses a combined scheme: direct blocks + single indirect + double indirect + triple indirect.

### Key Points / Highlights
| Method | External Frag. | Direct Access | Expansion |
|--------|---------------|---------------|-----------|
| Contiguous | Yes | Yes (fast) | Difficult |
| Linked | No | No (sequential only) | Easy |
| Indexed | No | Yes | Easy |

### MCQ Focus Section
- **Contiguous**: Fast access but suffers from **external fragmentation** and **file growth** issues.
- **Linked**: No fragmentation, **sequential access only**, pointer overhead.
- **FAT** improves linked allocation by putting pointers in a central table.
- **Indexed**: Supports **both sequential and direct access**. Used in UNIX (inode).
- **UNIX inode** uses: 12 direct + single indirect + double indirect + triple indirect blocks.
- **FAT32** uses linked allocation with a **File Allocation Table**.
- **NTFS** uses a **Master File Table (MFT)** (indexed-like approach).
- Indexed allocation wastes an index block even for **very small files**.

---

## 9.7 Free-Space Management

### Definition
The OS must track which disk blocks are **free** (available for allocation). **Free-space management** techniques track unused blocks efficiently.

### Detailed Explanation

#### 1. Bit Vector (Bitmap)
- A **bitmap** where each bit represents a block: **0 = free**, **1 = allocated** (or vice versa).
- Easy to find contiguous free blocks.
- **Space**: For a disk with n blocks, requires n bits.
- Example: 1 TB disk with 4 KB blocks → ~256 million bits = 32 MB.

#### 2. Linked List
- All free blocks are linked together in a **linked list**.
- The head pointer is stored in a known location.
- **Inefficient** for finding contiguous free blocks. Space-efficient (uses free blocks themselves for pointers).

#### 3. Grouping
- First free block stores pointers to **n** other free blocks.
- Last block in that group points to another group.
- More efficient than simple linked list — can find multiple free blocks quickly.

#### 4. Counting
- Store (start block, count) pairs — indicating a contiguous group of free blocks.
- Efficient when there are many large contiguous free regions.

### Key Points / Highlights
- **Bitmap** is the most common method — simple and fast.
- **Linked list** is space-efficient but slow for finding contiguous blocks.
- **Grouping** and **Counting** improve on the linked list approach.

### MCQ Focus Section
- **Bitmap**: Each bit = one block. Efficient for finding contiguous free space.
- **Linked list**: Free blocks linked together. Hard to find contiguous space.
- **Bitmap** requires **n bits** for n blocks.
- In bitmap: 0 = free, 1 = allocated (convention may vary).
- **FAT** doubles as a free-space management system (unused entries = free blocks).
- **Bitmap** is used in **ext2/ext3/ext4** and **NTFS** file systems.

---

## 9.8 Directory Implementation

### Definition
**Directory implementation** refers to how the OS internally stores and organizes directory entries (file names, attributes, block locations) on disk.

### Detailed Explanation

#### 1. Linear List
- A **list of file names** with metadata (pointers to data blocks, attributes).
- **Simple** to implement.
- **Slow** for search — requires **linear scan** (O(n)) to find a file.
- Can be improved with **sorting** or **caching**.

#### 2. Hash Table
- A **hash function** maps file names to positions in the table.
- **Fast** search — average O(1) lookup.
- **Collisions** must be handled (chaining, open addressing).
- Fixed table size — may need resizing.

### Key Points / Highlights
- **Linear list** is simple but slow (O(n) search).
- **Hash table** provides fast (O(1)) lookup but needs collision handling.
- Most modern file systems use **B-trees** or **hash trees** for efficient directory management.

### MCQ Focus Section
- **Linear list** search time is **O(n)** — inefficient for large directories.
- **Hash table** provides **O(1)** average lookup — much faster.
- **B-tree** (used in NTFS, ext4, HFS+) provides **O(log n)** search — good balance.
- **Collisions** in hash tables can degrade performance to O(n).

---

---

# UNIT 10: DEVICE MANAGEMENT

---

## 10.1 Types of Devices

### Definition
I/O devices can be classified based on their **sharing characteristics** and **access method**. The OS manages these devices differently based on their type.

### Detailed Explanation

#### Based on Sharing

**1. Dedicated Devices**
- Assigned to a **single process** for the entire duration it needs the device.
- No sharing — the device is exclusively allocated.
- Example: **Printer**, **tape drive**, **plotter**.
- **Disadvantage**: Low utilization if the process doesn't use the device continuously.

**2. Shared Devices**
- Can be used by **multiple processes** simultaneously (or with rapid switching).
- Example: **Disk drive** — multiple processes can read/write (with scheduling).
- **Advantage**: Better utilization.

**3. Virtual Devices**
- Physical devices made to **appear as multiple virtual devices**.
- Achieved using **spooling** (Simultaneous Peripheral Operations On-Line).
- Example: A single printer is made virtual through print spooling — multiple users submit print jobs to a queue, and the spooler sends them to the printer one at a time.
- **Converts** a dedicated device into a shared device.

#### Based on Access Method

**1. Serial Access (Sequential Access) Devices**
- Data is accessed **sequentially** — must pass through preceding data to reach the desired data.
- Example: **Magnetic tape**.
- Slow for random access. Good for **backup and archival** storage.

**2. Direct Access (Random Access) Devices**
- Data can be accessed at any **arbitrary position** directly without passing through other data.
- Example: **Hard disk (HDD)**, **SSD**, **CD-ROM**.
- Much faster for random access than serial devices.

### Key Points / Highlights
- **Dedicated** = one process at a time. **Shared** = multiple processes. **Virtual** = spooled.
- **Serial** = sequential access (tape). **Direct** = random access (disk).
- **Spooling** converts dedicated devices into shared devices.

### MCQ Focus Section
- **Printer** is a **dedicated** device — managed via **spooling** to make it virtual.
- **Disk** is a **shared** device — multiple processes can use it with scheduling.
- **Spooling** queues I/O jobs — allows a dedicated device to serve multiple users.
- **Magnetic tape** is a **serial access** device.
- **Hard disk** is a **direct access** device.
- **SSD** is a direct access device with **no seek time** (no moving parts).
- Spooling uses a **buffer/queue on disk** to hold pending jobs.

---

## 10.2 Disk Scheduling Methods

### Definition
**Disk scheduling algorithms** determine the order in which disk **I/O requests** are serviced by the disk head. The goal is to minimize the **total head movement** (seek time), thereby improving disk performance.

### Detailed Explanation

#### Key Disk Access Time Components
- **Seek Time**: Time to move the disk head to the desired **track/cylinder**. **Most significant** component.
- **Rotational Latency**: Time for the desired **sector** to rotate under the head. Average = half a rotation.
- **Transfer Time**: Time to actually read/write the data.
- **Total Access Time** = Seek Time + Rotational Latency + Transfer Time.
- Disk scheduling focuses on minimizing **seek time**.

#### 1. FCFS (First Come First Served)
- Requests are serviced in **arrival order** — simple and fair.
- **Problem**: Can result in **wild head movement** (arm moves back and forth across the disk).
- **Advantage**: Simple, fair, no starvation.
- **Disadvantage**: High total seek time (not optimized).

#### 2. SSTF (Shortest Seek Time First)
- Services the request **closest** to the current head position.
- Reduces total seek time compared to FCFS.
- **Like SJF** — greedy, selects nearest.
- **Problem**: **Starvation** — requests far from the head may wait indefinitely.
- **Advantage**: Lower average seek time than FCFS.

#### 3. SCAN (Elevator Algorithm)
- The disk head moves in **one direction** (e.g., toward higher tracks), servicing all requests along the way. When it reaches the **end**, it **reverses direction** and services requests on the way back.
- Like an **elevator** — goes up, then comes down.
- **No starvation** — every request is eventually serviced.
- **Problem**: Requests just visited must wait for the head to come back (nearly full scan).

#### 4. C-SCAN (Circular SCAN)
- Head moves in **one direction** only, servicing requests. When it reaches the **end**, it **jumps back** to the beginning without servicing (like a circular sweep).
- Provides more **uniform wait time** than SCAN.
- After reaching the end, the head moves **quickly** to the start without servicing intermediate requests.

#### 5. LOOK
- Like SCAN, but the head reverses direction at the **last request** in that direction (not at the physical end of the disk).
- More efficient than SCAN — avoids unnecessary movement to the end.

#### 6. C-LOOK (Circular LOOK)
- Like C-SCAN, but the head goes only to the **last request** in one direction, then jumps back to the **first request** in the other direction.
- Most efficient variant in practice.

### Key Points / Highlights
| Algorithm | Movement Pattern | Starvation? | Notes |
|-----------|-----------------|-------------|-------|
| FCFS | Arrival order | No | Simple, high seek time |
| SSTF | Nearest first | **Yes** | Like SJF; good avg seek time |
| SCAN | Sweep back-and-forth | No | Elevator algorithm |
| C-SCAN | One-direction sweep + jump back | No | Uniform wait time |
| LOOK | Like SCAN, stops at last request | No | More efficient than SCAN |
| C-LOOK | Like C-SCAN, stops at last request | No | Most practical |

### MCQ Focus Section
- **FCFS** is simplest but has the **highest total seek time**.
- **SSTF** produces the **lowest seek time** but can cause **starvation**.
- **SCAN** is called the **Elevator algorithm** — moves in one direction, reverses at the end.
- **C-SCAN** provides more **uniform wait time** than SCAN.
- **LOOK** and **C-LOOK** are practical improvements over SCAN and C-SCAN — they stop at the **last request** instead of going to the disk edge.
- **Seek time** is the most significant component of disk access time.
- **SSTF** is like **SJF** for disks — greedy selection of nearest request.
- **SCAN** and **C-SCAN** do not cause starvation.
- For **SSDs**, disk scheduling is less important because there is **no mechanical head movement** (seek time ≈ 0).

---

## 10.3 Direct Access Storage Devices — Channels and Control Units

### Definition
**Direct Access Storage Devices (DASD)** are storage devices that allow data to be accessed **directly** at any location without reading through all preceding data. **Channels** and **control units** are hardware components that manage I/O operations between the CPU and DASD.

### Detailed Explanation

#### DASD Examples
- **Hard Disk Drives (HDD)**: Magnetic platters with read/write heads.
- **Solid State Drives (SSD)**: Flash memory-based storage.
- **Optical disks**: CD, DVD, Blu-ray.

#### I/O Architecture

**1. I/O Channel**
- A dedicated **hardware processor** that handles I/O operations independently of the CPU.
- The CPU initiates an I/O operation and the channel takes over — freeing the CPU for other work.
- Types:
  - **Selector Channel**: Handles one high-speed device at a time (e.g., disk, tape).
  - **Multiplexer Channel**: Handles multiple low-speed devices simultaneously (e.g., terminals, printers).
  - **Block Multiplexer Channel**: Handles multiple high-speed devices by interleaving blocks.

**2. Control Unit (Device Controller)**
- An intermediary between the channel and the physical device.
- Translates channel commands into device-specific signals.
- Contains **local buffers** and **registers** for data transfer.
- Manages device-specific operations (e.g., positioning the disk head, spinning the platter).

#### I/O Flow
CPU → Channel → Control Unit → Device → Data

### Key Points / Highlights
- **DASDs** support direct (random) access — example: HDD, SSD.
- **Channels** offload I/O processing from the CPU.
- **Control units** interface between channels and physical devices.
- **Selector channel** = one device at a time; **Multiplexer channel** = multiple devices.

### MCQ Focus Section
- A **channel** is an I/O processor that handles data transfer **independently of the CPU**.
- **Selector channel**: One **high-speed** device at a time.
- **Multiplexer channel**: Multiple **low-speed** devices simultaneously.
- **Block multiplexer**: Multiple **high-speed** devices interleaved.
- The **control unit** translates commands for specific devices.
- DASD allows **direct/random access** (unlike sequential access devices like tape).
- **DMA (Direct Memory Access)** transfers data directly between devices and memory without CPU involvement.

---

---

# UNIT 11: INTER-PROCESS COMMUNICATION (IPC)

---

## 11.1 Introduction to IPC Methods

### Definition
**Inter-Process Communication (IPC)** refers to mechanisms provided by the OS that allow processes to **exchange data** and **synchronize** their actions. IPC is essential for cooperating processes.

### Detailed Explanation

#### Why IPC?
- Processes may need to **share data** (e.g., a web server and a database).
- Processes may need to **coordinate** their execution (e.g., producer and consumer).
- Processes may need to **communicate** results or status information.

#### Two Fundamental IPC Models

**1. Shared Memory**
- Processes share a **common region of memory**.
- Fast (no kernel involvement after setup).
- Requires **synchronization** (semaphores, mutexes).
- Example: POSIX shared memory (`shmget`, `shmat`, `shmdt`, `shmctl`).

**2. Message Passing**
- Processes communicate by **sending and receiving messages** through the OS.
- Slower (kernel involved in every message).
- No shared memory required — works across machines.
- Operations: `send(message)` and `receive(message)`.
- Can be **direct** (specify process ID) or **indirect** (use a mailbox/port).
- Can be **synchronous (blocking)** or **asynchronous (non-blocking)**.

#### IPC Mechanisms in UNIX/Linux
- **Pipes** (anonymous and named)
- **Shared Memory**
- **Message Queues**
- **Semaphores** (for synchronization)
- **Sockets** (for network communication)
- **Signals** (for notifications)

### Key Points / Highlights
- Two models: **Shared Memory** (fast) and **Message Passing** (flexible).
- UNIX provides: **Pipes, Shared Memory, Message Queues, Semaphores, Sockets**.
- Shared memory needs **synchronization**; message passing is handled by the kernel.

### MCQ Focus Section
- **Shared memory** is **faster** because it avoids kernel involvement after setup.
- **Message passing** works across **different machines** (distributed systems).
- **Synchronous (blocking)**: Sender waits until receiver gets the message. Receiver waits until a message is available.
- **Asynchronous (non-blocking)**: Sender sends and continues. Receiver checks and continues if no message.
- **Direct communication**: Send/receive specifies the process ID. **Indirect**: Uses a mailbox/port.
- UNIX IPC mechanisms include: **Pipes, FIFOs, Shared Memory, Message Queues, Semaphores, Sockets**.

---

## 11.2 Pipes

### Definition
A **Pipe** is a unidirectional IPC mechanism that allows data to flow from one process to another in a **FIFO (first-in, first-out)** manner. Data written by one process can be read by another process.

### Detailed Explanation

#### Anonymous (Unnamed) Pipe
- Created using the `pipe()` system call.
- Returns two file descriptors: `fd[0]` (read end) and `fd[1]` (write end).
- **Unidirectional**: Data flows in one direction only. For bidirectional communication, use **two pipes**.
- Can only be used between **related processes** (parent-child, created via `fork()`).
- Data exists only in **kernel memory** — no disk file is involved.
- The pipe has a **finite buffer** (typically 64 KB in Linux).
- Used in **shell pipelines**: `ls | grep .txt | wc -l`.

#### Named Pipe (FIFO)
- Created using `mkfifo()` or `mknod()`.
- Has a **name in the file system** — appears as a special file.
- Can be used between **unrelated processes** (any process can open the FIFO by name).
- Still **unidirectional** per FIFO. For bidirectional, use two FIFOs.
- Data does not persist — it exists only while processes are communicating.

#### popen() and pclose()
- **`popen()`**: A higher-level library function that creates a pipe **and** forks a child process to execute a shell command. Returns a `FILE*` pointer for reading or writing.
  - `FILE *fp = popen("ls -l", "r");` — runs `ls -l` and lets the parent read its output.
- **`pclose()`**: Closes the pipe opened by `popen()`, waits for the child process to finish, and returns the exit status.
- Simplifies common pipe usage patterns — combines pipe + fork + exec.

### Key Points / Highlights
- **Anonymous pipe**: Unidirectional, related processes only, `pipe()`.
- **Named pipe (FIFO)**: Unidirectional, any processes, has a file system name, `mkfifo()`.
- **popen/pclose**: High-level library functions for running shell commands via pipes.
- Pipes are **byte streams** — no message boundaries.

### MCQ Focus Section
- **Anonymous pipe** can only be used between **related (parent-child)** processes.
- **Named pipe (FIFO)** can be used between **unrelated** processes.
- `pipe()` returns **two file descriptors**: fd[0] for read, fd[1] for write.
- Pipes are **unidirectional** — data flows in one direction.
- **popen()** creates a pipe and executes a **shell command** in a child process.
- **pclose()** closes the pipe and returns the child's **exit status**.
- In the shell, `|` (pipe symbol) creates an anonymous pipe between two commands.
- Pipes are **FIFO** — data is read in the same order it was written.
- If the read end is closed and a process tries to write → **SIGPIPE** signal (broken pipe).
- Named pipes appear in the file system but data does **not persist** on disk.

---

## 11.3 Shared Memory

### Definition
**Shared Memory** IPC allows two or more processes to share a **common region of physical memory**. Processes can read and write to this shared region, enabling fast data exchange.

### Detailed Explanation

#### How It Works
1. One process creates a shared memory segment using `shmget()`.
2. Each process **attaches** the shared memory to its address space using `shmat()`.
3. Processes **read/write** to the shared memory directly (like accessing a regular array/struct).
4. When done, each process **detaches** using `shmdt()`.
5. The segment is **removed** using `shmctl()` with `IPC_RMID`.

#### POSIX Shared Memory System Calls
| Call | Function |
|------|----------|
| `shmget()` | Create or access a shared memory segment |
| `shmat()` | Attach the segment to the process's address space |
| `shmdt()` | Detach the segment |
| `shmctl()` | Control operations (remove, stat, etc.) |

#### Synchronization Requirement
- Shared memory does **not** provide built-in synchronization.
- Processes must use **semaphores**, **mutexes**, or other synchronization mechanisms to prevent **race conditions**.
- Without synchronization, simultaneous reads and writes can corrupt data.

### Key Points / Highlights
- **Fastest IPC method** — no kernel involvement during read/write (after initial setup).
- Requires **explicit synchronization** (semaphores, mutexes).
- System calls: `shmget()`, `shmat()`, `shmdt()`, `shmctl()`.

### MCQ Focus Section
- Shared memory is the **fastest** IPC mechanism.
- `shmget()` creates or accesses a shared memory segment.
- `shmat()` attaches the segment to the process's address space.
- `shmdt()` detaches (does NOT delete) the segment.
- `shmctl(shmid, IPC_RMID, NULL)` deletes the shared memory segment.
- Shared memory requires **explicit synchronization** — the OS does NOT provide automatic mutual exclusion.
- **POSIX** also provides `shm_open()` + `mmap()` as a newer shared memory API.

---

## 11.4 FIFOs (Named Pipes)

### Definition
A **FIFO (First In, First Out)**, also called a **Named Pipe**, is a special type of pipe that has a **name in the file system**, allowing **unrelated processes** to communicate. It provides unidirectional, byte-stream communication.

### Detailed Explanation

- Created using `mkfifo()` system call or `mkfifo` command.
- Appears as a **special file** in the file system.
- Any process can open the FIFO by its **file path** for reading or writing.
- Behaves like a pipe — data written by one process can be read by another.
- **Blocking behavior**: By default, `open()` on a FIFO blocks until the other end is also opened.
- Data is **not stored on disk** — travels through the kernel buffer.
- Once data is read, it is **removed** from the FIFO (consumed).

### Key Points / Highlights
- FIFO = Named Pipe = `mkfifo()`.
- Allows communication between **unrelated processes**.
- Data is transient — exists only in the kernel buffer.
- **Blocking** by default when opening (waits for both ends to be open).

### MCQ Focus Section
- FIFOs allow IPC between **unrelated** processes (unlike anonymous pipes).
- `mkfifo()` creates a named pipe with a **file system path**.
- FIFOs are **unidirectional** — for bidirectional, use two FIFOs.
- Data in a FIFO **does not persist** — it's not stored on disk.
- FIFOs follow **FIFO** ordering — data read in the order written.
- `open()` on a FIFO blocks until another process opens the other end (default behavior).

---

## 11.5 Message Queues

### Definition
A **Message Queue** is an IPC mechanism that allows processes to exchange **discrete messages** through a queue managed by the OS kernel. Unlike pipes (byte streams), message queues preserve **message boundaries**.

### Detailed Explanation

#### How It Works
1. Create/access a message queue using `msgget()`.
2. Send a message using `msgsnd()` — specify the queue, message type, and data.
3. Receive a message using `msgrcv()` — specify the queue and desired message type.
4. Remove the queue using `msgctl()` with `IPC_RMID`.

#### Key Features
- Messages have a **type** (long integer) — allows selective retrieval (receive only messages of a specific type).
- Messages are **discrete** (with boundaries) — unlike pipes which are byte streams.
- Queue has a **maximum capacity** — sends block if full (by default).
- Messages persist in the queue until **read or queue is deleted** — even if the sender terminates.
- **Multiple processes** can send to and receive from the same queue.

#### System Calls
| Call | Function |
|------|----------|
| `msgget()` | Create or access a message queue |
| `msgsnd()` | Send a message |
| `msgrcv()` | Receive a message |
| `msgctl()` | Control operations (remove, stat, etc.) |

### Key Points / Highlights
- Message queues preserve **message boundaries** (unlike pipes).
- Messages have **types** for selective retrieval.
- Messages persist in the queue until read.
- Kernel-managed — slower than shared memory but no need for explicit synchronization.

### MCQ Focus Section
- **Message queues** maintain **message boundaries**; **pipes** do not (byte stream).
- Messages have a **type** field allowing selective reception.
- `msgget()` creates or accesses a message queue.
- `msgsnd()` sends a message; `msgrcv()` receives.
- Message queues are **kernel-managed** — require system calls for every operation.
- **Pipes** = byte stream, FIFO order only. **Message queues** = discrete messages with type-based retrieval.
- Message queues are **slower** than shared memory but provide **structured communication**.
- Messages remain in the queue until **explicitly read** (even if the sender terminates).

---

### IPC Mechanisms Comparison

| Mechanism | Communication | Directionality | Related Processes Only? | Message Boundaries? | Speed |
|-----------|--------------|---------------|----------------------|--------------------| ------|
| Anonymous Pipe | Byte stream | Unidirectional | Yes | No | Fast |
| Named Pipe (FIFO) | Byte stream | Unidirectional | No | No | Fast |
| Shared Memory | Memory region | Bidirectional | No | No | **Fastest** |
| Message Queue | Messages | Bidirectional | No | **Yes** | Moderate |
| Socket | Byte stream / Datagram | Bidirectional | No (works over network) | Depends | Slowest (network) |

---

---

> **— End of Book —**
>
> *This comprehensive guide covers all topics as per the Operating Systems syllabus.*
> *Use it for concept building, exam revision, placement preparation, and technical interviews.*
> *Good luck!* 🎓
