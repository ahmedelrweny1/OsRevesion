# 📝 OS Exam Question Bank

## How to Use This Section
This question bank covers all topics in the OS syllabus and is organized to help you test your understanding of the core concepts:
- **Part 1 — Multiple Choice (MCQ):** 40+ questions organized by chapter.
- **Part 2 — True or False:** Quick statements to test your intuition.
- **Part 3 — Scheduling Problems:** Fully worked CPU scheduling math problems with Gantt charts.

> [!tip] Tip
> Click on the **"✅ Answer"** toggle below each question to reveal the explanation!

---

## Part 1: Multiple Choice Questions (MCQ)

### 📘 Chapter 1: OS Overview

**Q1.** What is the primary purpose of an operating system?
- A) To compile source code
- B) To manage hardware resources and provide services for applications
- C) To provide internet access
- D) To render graphics

<details><summary>✅ Answer</summary>
**B) To manage hardware resources and provide services for applications**
</details>

**Q2.** The purpose of dual-mode operation (user mode and kernel mode) is to:
- A) Run the CPU twice as fast
- B) Protect the OS and hardware from errant user programs
- C) Allow two users to log in simultaneously
- D) Increase memory capacity

<details><summary>✅ Answer</summary>
**B) Protect the OS and hardware from errant user programs** — A mode bit distinguishes user mode from kernel mode. Privileged instructions can only run in kernel mode.
</details>

**Q3.** Which of the following is NOT an operating system service?
- A) Program execution
- B) Error detection
- C) File-system manipulation
- D) Compiling code

<details><summary>✅ Answer</summary>
**D) Compiling code** — A compiler is a separate application program, not an OS service.
</details>

**Q4.** A system that allows multiple jobs to be in memory at the same time, keeping the CPU always busy, is called:
- A) Multiprocessing
- B) Multiprogramming
- C) Multithreading
- D) Time-sharing

<details><summary>✅ Answer</summary>
**B) Multiprogramming** — Multiprogramming increases CPU utilization by organizing jobs so that the CPU always has one to execute.
</details>

**Q5.** Which of the following handles the transition from user mode to kernel mode?
- A) A software interrupt (trap) or hardware interrupt
- B) A compiler directive
- C) An infinite loop
- D) A standard function call

<details><summary>✅ Answer</summary>
**A) A software interrupt (trap) or hardware interrupt** — When an interrupt occurs, the hardware switches from user mode to kernel mode.
</details>

**Q6.** The concept of "time-sharing" is a logical extension of:
- A) Multiprocessing
- B) Multiprogramming
- C) Batch processing
- D) Single-user systems

<details><summary>✅ Answer</summary>
**B) Multiprogramming** — Time-sharing (multitasking) is multiprogramming where the CPU switches between jobs so frequently that users can interact with each program while it is running.
</details>

---

### 📘 Chapter 2: OS Structures

**Q7.** A system call is typically invoked through a:
- A) Hardware interrupt
- B) Software interrupt (trap)
- C) Reboot sequence
- D) Direct memory access (DMA)

<details><summary>✅ Answer</summary>
**B) Software interrupt (trap)**
</details>

**Q8.** The system call interface maintains a table indexed by:
- A) Process IDs
- B) System call numbers
- C) Memory addresses
- D) File sizes

<details><summary>✅ Answer</summary>
**B) System call numbers** — Each system call is assigned a unique number.
</details>

**Q9.** Which of the following is NOT a category of system calls?
- A) Process control
- B) File management
- C) Application UI design
- D) Device management

<details><summary>✅ Answer</summary>
**C) Application UI design**
</details>

**Q10.** The OS provides a higher-level programming interface to access system calls known as:
- A) API (Application Programming Interface)
- B) CPU registers
- C) Device drivers
- D) Graphical User Interface (GUI)

<details><summary>✅ Answer</summary>
**A) API** — An API function may internally invoke multiple system calls on behalf of the programmer, abstracting away the low-level details.
</details>

**Q11.** Which system call category includes creating and terminating processes?
- A) Device Management
- B) Information Maintenance
- C) Process Control
- D) Communications

<details><summary>✅ Answer</summary>
**C) Process Control**
</details>

---

### 📘 Chapter 3: Processes

**Q12.** Which of the following is NOT a valid process state?
- A) Ready
- B) Waiting
- C) Compiling
- D) Running

<details><summary>✅ Answer</summary>
**C) Compiling** — The five standard process states are: New, Ready, Running, Waiting, and Terminated.
</details>

**Q13.** What does the Process Control Block (PCB) store?
- A) The source code of the program
- B) Process state, program counter, CPU registers, and scheduling info
- C) User passwords
- D) The compiler logs

<details><summary>✅ Answer</summary>
**B)** — The PCB is the data structure the OS uses to represent and track a process.
</details>

**Q14.** Context switching involves:
- A) Deleting the old process
- B) Saving the state of the current process and loading the state of the next process
- C) Re-compiling the program
- D) Moving the process to disk

<details><summary>✅ Answer</summary>
**B)** — During a context switch, the OS saves the PCB of the current process and restores the PCB of the next process to be scheduled. This takes time and is considered overhead.
</details>

**Q15.** When a process is waiting for an I/O event to complete, what state is it in?
- A) Ready
- B) Running
- C) Waiting (Blocked)
- D) Terminated

<details><summary>✅ Answer</summary>
**C) Waiting (Blocked)**
</details>

**Q16.** The Ready Queue contains processes that:
- A) Are waiting for an I/O device
- B) Have completed their execution
- C) Reside in main memory and are waiting to execute on the CPU
- D) Are currently executing on the CPU

<details><summary>✅ Answer</summary>
**C)** — Processes in the ready queue are fully loaded in memory and are just waiting for the CPU scheduler to pick them.
</details>

**Q17.** A zombie process is:
- A) A process that consumes all CPU time
- B) A terminated process whose parent has not yet collected its exit status
- C) A process that has no memory allocated to it
- D) A process running in an infinite loop

<details><summary>✅ Answer</summary>
**B)** — A zombie process has finished execution but still has an entry in the process table because its parent hasn't collected its exit status.
</details>

**Q18.** An orphan process is:
- A) A process whose parent has terminated before it
- B) A process that has no memory allocated to it
- C) A process running in an infinite loop
- D) A process that consumes all CPU time

<details><summary>✅ Answer</summary>
**A)** — When a parent terminates without collecting the child's status, the child becomes an orphan and is typically adopted by the init process.
</details>

---

### 📘 Chapter 4: Threads & Concurrency

**Q19.** The main difference between a process and a thread is that:
- A) Threads cannot run on multiple cores
- B) Threads share the memory and resources of their parent process
- C) Processes are faster to create
- D) Threads do not have their own program counter

<details><summary>✅ Answer</summary>
**B) Threads share the memory and resources of their parent process** — While processes have entirely separate address spaces, threads within the same process share code, data, and open files.
</details>

**Q20.** Distributing subsets of the same data across multiple cores and performing the same operation on each is called:
- A) Task parallelism
- B) Data parallelism
- C) Serial execution
- D) Concurrency

<details><summary>✅ Answer</summary>
**B) Data parallelism** — For example, splitting a large array into four chunks and having four threads process them simultaneously. Task parallelism is when different threads perform completely different tasks.
</details>

**Q21.** In the Many-to-One multithreading model:
- A) Each user thread maps to its own kernel thread
- B) Many user threads map to a single kernel thread
- C) There are no kernel threads
- D) Threads are created automatically by the compiler

<details><summary>✅ Answer</summary>
**B)** — In Many-to-One, if one user thread makes a blocking system call, all threads are blocked because there is only one kernel thread handling them.
</details>

**Q22.** Which of the following is NOT a benefit of multithreading?
- A) Resource sharing
- B) Economy (cheaper than creating processes)
- C) Increased memory isolation between threads
- D) Responsiveness

<details><summary>✅ Answer</summary>
**C) Increased memory isolation between threads** — Threads actually *share* memory; they do not isolate memory from one another.
</details>

**Q23.** The One-to-One multithreading model provides:
- A) Better concurrency than the Many-to-One model
- B) Less concurrency than the Many-to-One model
- C) No kernel threads
- D) Only a single user thread

<details><summary>✅ Answer</summary>
**A) Better concurrency** — Because each user thread maps to its own kernel thread, one thread blocking does not block the others.
</details>

**Q24.** Implicit threading means:
- A) Programmers must manually write code to create and manage each thread
- B) The compiler and libraries automatically manage thread creation and synchronization
- C) Threads are completely hidden from the CPU
- D) Only kernel threads are used

<details><summary>✅ Answer</summary>
**B)** — Implicit threading hides the complexity of multithreading from the programmer by relying on compilers and libraries (e.g., OpenMP).
</details>

---

### 📘 Chapter 5 & 6: CPU Scheduling

**Q25.** The CPU scheduler is also known as the:
- A) Long-term scheduler
- B) Short-term scheduler
- C) Disk scheduler
- D) Network scheduler

<details><summary>✅ Answer</summary>
**B) Short-term scheduler** — It selects which process should execute next from the ready queue and allocates the CPU to it.
</details>

**Q26.** Preemptive scheduling means:
- A) A process runs until it voluntarily yields the CPU
- B) The OS can forcibly take the CPU away from a running process
- C) Only the longest jobs get the CPU
- D) Processes cannot be interrupted

<details><summary>✅ Answer</summary>
**B)** — This usually happens when a timer interrupt goes off (like in Round Robin) or a higher priority process arrives.
</details>

**Q27.** Which algorithm minimizes average waiting time but is difficult to implement because it requires knowing the future burst length?
- A) First-Come, First-Served (FCFS)
- B) Shortest Job First (SJF)
- C) Round Robin (RR)
- D) Priority Scheduling

<details><summary>✅ Answer</summary>
**B) Shortest Job First (SJF)** — SJF is provably optimal for minimizing average waiting time, but predicting the exact length of the next CPU burst is challenging.
</details>

**Q28.** Aging is used to prevent:
- A) Thrashing
- B) Starvation
- C) Context switching
- D) High CPU utilization

<details><summary>✅ Answer</summary>
**B) Starvation** — Aging gradually increases the priority of a process the longer it waits in the ready queue, ensuring that low-priority processes eventually get to run.
</details>

**Q29.** In Round Robin (RR) scheduling, if the time quantum is extremely large, the algorithm behaves exactly like:
- A) Shortest Job First (SJF)
- B) First-Come, First-Served (FCFS)
- C) Priority Scheduling
- D) Shortest Remaining Time First (SRTF)

<details><summary>✅ Answer</summary>
**B) FCFS** — If the time quantum is larger than the longest CPU burst, no process will ever be preempted, so it behaves just like FCFS.
</details>

**Q30.** The time from the submission of a process to its completion is called:
- A) Waiting time
- B) Response time
- C) Turnaround time
- D) CPU utilization

<details><summary>✅ Answer</summary>
**C) Turnaround time** — Turnaround time is the total time spent waiting to get into memory, waiting in the ready queue, executing on the CPU, and doing I/O.
</details>

**Q31.** The time it takes for the dispatcher to stop one process and start another running is known as:
- A) Turnaround time
- B) Dispatch latency
- C) CPU burst
- D) Response time

<details><summary>✅ Answer</summary>
**B) Dispatch latency** — This is pure overhead that system designers try to minimize.
</details>

**Q32.** First-Come, First-Served (FCFS) scheduling can suffer from:
- A) The Convoy Effect
- B) Starvation
- C) Excessive context switching
- D) High dispatch latency

<details><summary>✅ Answer</summary>
**A) The Convoy Effect** — Short processes get stuck waiting behind a long process, severely decreasing average waiting time.
</details>

**Q33.** Shortest Remaining Time First (SRTF) is the preemptive version of:
- A) FCFS
- B) SJF
- C) Priority Scheduling
- D) Round Robin

<details><summary>✅ Answer</summary>
**B) SJF** — If a new process arrives with a CPU burst shorter than the remaining time of the currently executing process, the current process is preempted.
</details>

---

### 📘 Chapter 7 & 8: Memory Management & Deadlocks

**Q34.** Virtual memory allows:
- A) The CPU to run twice as fast
- B) The execution of processes that are larger than the physical RAM
- C) The hard drive to spin faster
- D) Deletion of cache memory

<details><summary>✅ Answer</summary>
**B)** — By keeping only the actively used "pages" of a program in RAM and swapping the rest to the disk, virtual memory creates the illusion of infinite memory.
</details>

**Q35.** Which of the following is NOT one of the four necessary conditions for a deadlock?
- A) Mutual exclusion
- B) Hold and wait
- C) Preemption
- D) Circular wait

<details><summary>✅ Answer</summary>
**C) Preemption** — The condition is actually **No Preemption** (resources cannot be forcibly taken). If preemption is allowed, deadlocks can be resolved.
</details>

**Q36.** Paging is a memory management scheme that:
- A) Eliminates the need for contiguous allocation of physical memory
- B) Guarantees no deadlocks will occur
- C) Prevents all page faults
- D) Only works for kernel threads

<details><summary>✅ Answer</summary>
**A)** — Paging divides physical memory into fixed-size frames and logical memory into pages, allowing non-contiguous allocation.
</details>

**Q37.** In the context of deadlocks, "Hold and Wait" means:
- A) A process is holding at least one resource and waiting to acquire additional resources held by other processes
- B) A process holds the CPU and waits for a user
- C) The OS holds all memory and waits for a reboot
- D) A thread is holding its PCB and waiting for I/O

<details><summary>✅ Answer</summary>
**A)** — This is one of the four necessary conditions for deadlock.
</details>

---

## Part 2: True or False Questions

**T/F 1.** Multitasking requires a computer to have multiple CPU cores.
<details><summary>✅ Answer</summary>**False** — Multitasking can happen on a single CPU core via rapid time-sharing (context switching), giving the illusion of simultaneous execution.</details>

**T/F 2.** Creating a new thread is generally faster and consumes less resources than creating a completely new process.
<details><summary>✅ Answer</summary>**True** — Threads are lightweight and share their parent process's memory space, avoiding the massive overhead of process creation.</details>

**T/F 3.** FCFS scheduling can suffer from the "convoy effect", where short processes get stuck waiting behind a very long CPU-bound process.
<details><summary>✅ Answer</summary>**True** — Because FCFS is non-preemptive, a long process will hold the CPU until it finishes, forcing all others to wait.</details>

**T/F 4.** A process in the "Ready" state is waiting for an I/O event to complete.
<details><summary>✅ Answer</summary>**False** — A process waiting for I/O is in the **Waiting** state. The **Ready** state means it is fully loaded in memory and just waiting for the CPU to be assigned to it.</details>

**T/F 5.** In the One-to-One multithreading model, if one thread is blocked waiting for I/O, other threads in the same process can continue to execute.
<details><summary>✅ Answer</summary>**True** — Because each user thread maps to a distinct kernel thread, the kernel can simply schedule another thread from the same process.</details>

**T/F 6.** The time it takes for the dispatcher to stop one process and start another is called "Dispatch Latency".
<details><summary>✅ Answer</summary>**True** — This is pure overhead that system designers try to minimize.</details>

**T/F 7.** The OS sits between application programs and the computer hardware.
<details><summary>✅ Answer</summary>**True** — The OS acts as the critical middle layer that abstracts hardware complexity.</details>

**T/F 8.** Each thread within a process has its own program counter, stack, and register set.
<details><summary>✅ Answer</summary>**True** — While threads share code and data, they must have their own execution state (stack and registers).</details>

**T/F 9.** Priority scheduling can lead to starvation if a continuous stream of higher priority processes arrive.
<details><summary>✅ Answer</summary>**True** — This is why aging (gradually increasing a waiting process's priority) is used.</details>

**T/F 10.** A deadlock can occur even if the "Circular Wait" condition is prevented.
<details><summary>✅ Answer</summary>**False** — Deadlock requires ALL four conditions to be met simultaneously. If you break one, you prevent deadlock.</details>


## Part 3: Scheduling Problems (Fully Worked)

---

### ≡ƒôè Problem 1: FCFS (First-Come, First-Served)

**Problem Statement:**

Consider the following set of processes with their arrival times and CPU burst times:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 8          |
| P2      | 1           | 4          |
| P3      | 2           | 9          |
| P4      | 3           | 5          |

**Using FCFS scheduling, calculate the Gantt chart, waiting time, and turnaround time for each process.**

<details><summary>Γ£à Answer</summary>

**Step 1: Determine the order of execution**

FCFS serves processes in the order they arrive:
- P1 arrives at time 0 ΓåÆ runs first
- P2 arrives at time 1 ΓåÆ runs second
- P3 arrives at time 2 ΓåÆ runs third
- P4 arrives at time 3 ΓåÆ runs fourth

**Step 2: Gantt Chart**

```
| P1          | P2      | P3              | P4        |
0             8        12                21          26
```

**Step 3: Calculate Completion Times**

| Process | Arrival | Burst | Completion Time |
|---------|---------|-------|-----------------|
| P1      | 0       | 8     | 0 + 8 = **8**  |
| P2      | 1       | 4     | 8 + 4 = **12** |
| P3      | 2       | 9     | 12 + 9 = **21**|
| P4      | 3       | 5     | 21 + 5 = **26**|

**Step 4: Calculate Turnaround Times**

Turnaround Time = Completion Time ΓêÆ Arrival Time

| Process | Completion | Arrival | Turnaround Time |
|---------|-----------|---------|-----------------|
| P1      | 8         | 0       | 8 ΓêÆ 0 = **8**  |
| P2      | 12        | 1       | 12 ΓêÆ 1 = **11**|
| P3      | 21        | 2       | 21 ΓêÆ 2 = **19**|
| P4      | 26        | 3       | 26 ΓêÆ 3 = **23**|

**Step 5: Calculate Waiting Times**

Waiting Time = Turnaround Time ΓêÆ Burst Time

| Process | Turnaround | Burst | Waiting Time    |
|---------|-----------|-------|-----------------|
| P1      | 8         | 8     | 8 ΓêÆ 8 = **0**  |
| P2      | 11        | 4     | 11 ΓêÆ 4 = **7** |
| P3      | 19        | 9     | 19 ΓêÆ 9 = **10**|
| P4      | 23        | 5     | 23 ΓêÆ 5 = **18**|

**Step 6: Calculate Averages**

- **Average Waiting Time** = (0 + 7 + 10 + 18) / 4 = **35 / 4 = 8.75**
- **Average Turnaround Time** = (8 + 11 + 19 + 23) / 4 = **61 / 4 = 15.25**

**Final Summary:**

| Process | AT | BT | CT | TAT | WT |
|---------|----|----|----|----|-----|
| P1      | 0  | 8  | 8  | 8  | 0   |
| P2      | 1  | 4  | 12 | 11 | 7   |
| P3      | 2  | 9  | 21 | 19 | 10  |
| P4      | 3  | 5  | 26 | 23 | 18  |
| **Avg** |    |    |    | **15.25** | **8.75** |

</details>

---

### ≡ƒôè Problem 2: SJF Non-Preemptive (Shortest Job First)

**Problem Statement:**

Consider the following set of processes:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 7          |
| P2      | 2           | 4          |
| P3      | 4           | 1          |
| P4      | 5           | 4          |

**Using non-preemptive SJF scheduling, calculate the Gantt chart, waiting time, and turnaround time for each process.**

<details><summary>Γ£à Answer</summary>

**Step 1: Execution trace (non-preemptive SJF)**

- **Time 0:** Only P1 has arrived (AT=0). P1 starts running. Burst = 7.
- **Time 7:** P1 finishes. Ready queue contains: P2 (BT=4, arrived at 2), P3 (BT=1, arrived at 4), P4 (BT=4, arrived at 5). Shortest burst = P3 (BT=1). **P3 runs.**
- **Time 8:** P3 finishes. Ready queue: P2 (BT=4), P4 (BT=4). Tie ΓåÆ use FCFS (P2 arrived first). **P2 runs.**
- **Time 12:** P2 finishes. Ready queue: P4 (BT=4). **P4 runs.**
- **Time 16:** P4 finishes. All done.

**Step 2: Gantt Chart**

```
| P1              | P3  | P2      | P4      |
0                 7     8        12        16
```

**Step 3: Calculate all metrics**

| Process | AT | BT | CT | TAT = CTΓêÆAT | WT = TATΓêÆBT |
|---------|----|----|-----|-------------|--------------|
| P1      | 0  | 7  | 7   | 7           | 0            |
| P2      | 2  | 4  | 12  | 10          | 6            |
| P3      | 4  | 1  | 8   | 4           | 3            |
| P4      | 5  | 4  | 16  | 11          | 7            |

**Step 4: Calculate Averages**

- **Average Waiting Time** = (0 + 6 + 3 + 7) / 4 = **16 / 4 = 4.0**
- **Average Turnaround Time** = (7 + 10 + 4 + 11) / 4 = **32 / 4 = 8.0**

**Final Summary:**

| Process | AT | BT | CT  | TAT | WT |
|---------|----|----|-----|-----|----|
| P1      | 0  | 7  | 7   | 7   | 0  |
| P2      | 2  | 4  | 12  | 10  | 6  |
| P3      | 4  | 1  | 8   | 4   | 3  |
| P4      | 5  | 4  | 16  | 11  | 7  |
| **Avg** |    |    |     | **8.0** | **4.0** |

> ≡ƒÆí Compare this to FCFS for the same data: SJF gives lower average waiting time, confirming SJF is optimal for minimizing average waiting time.

</details>

---

### ≡ƒôè Problem 3: SRTF (Shortest Remaining Time First ΓÇö Preemptive SJF)

**Problem Statement:**

Consider the following set of processes:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 8          |
| P2      | 1           | 4          |
| P3      | 2           | 2          |
| P4      | 3           | 1          |
| P5      | 4           | 3          |

**Using SRTF (Preemptive SJF) scheduling, show the step-by-step execution trace, Gantt chart, and calculate all metrics.**

<details><summary>Γ£à Answer</summary>

**Step-by-step execution trace at each time unit:**

| Time | Event | Ready Queue (Process: Remaining) | Running | Action |
|------|-------|----------------------------------|---------|--------|
| 0    | P1 arrives | P1:8 | P1 | P1 starts (only process) |
| 1    | P2 arrives | P1:7, P2:4 | P2 | P2 preempts P1 (4 < 7) |
| 2    | P3 arrives | P1:7, P2:3, P3:2 | P3 | P3 preempts P2 (2 < 3) |
| 3    | P4 arrives | P1:7, P2:3, P3:1, P4:1 | P3 | P3 continues (remaining 1 Γëñ P4's 1, no preemption) |
| 4    | P3 done, P5 arrives | P1:7, P2:3, P4:1, P5:3 | P4 | P4 runs (shortest remaining = 1) |
| 5    | P4 done | P1:7, P2:3, P5:3 | P2 | P2 runs (tie: P2 arrived first, both have 3) |
| 6    | ΓÇö | P1:7, P2:2, P5:3 | P2 | P2 continues |
| 7    | ΓÇö | P1:7, P2:1, P5:3 | P2 | P2 continues |
| 8    | P2 done | P1:7, P5:3 | P5 | P5 runs (3 < 7) |
| 9ΓÇô10 | ΓÇö | P1:7, P5:2ΓåÆ1 | P5 | P5 continues |
| 11   | P5 done | P1:7 | P1 | P1 runs |
| 11ΓÇô18| ΓÇö | P1:7ΓåÆ0 | P1 | P1 runs to completion |

**Gantt Chart:**

```
| P1 | P2 | P3   | P4 | P2      | P5      | P1                     |
0    1    2      4    5         8        11                         18
```

**Calculations:**

| Process | AT | BT | CT  | TAT = CTΓêÆAT | WT = TATΓêÆBT |
|---------|----|----|-----|-------------|--------------|
| P1      | 0  | 8  | 18  | 18          | 10           |
| P2      | 1  | 4  | 8   | 7           | 3            |
| P3      | 2  | 2  | 4   | 2           | 0            |
| P4      | 3  | 1  | 5   | 2           | 1            |
| P5      | 4  | 3  | 11  | 7           | 4            |

**Averages:**

- **Average Waiting Time** = (10 + 3 + 0 + 1 + 4) / 5 = **18 / 5 = 3.6**
- **Average Turnaround Time** = (18 + 7 + 2 + 2 + 7) / 5 = **36 / 5 = 7.2**

**Final Summary:**

| Process | AT | BT | CT  | TAT | WT |
|---------|----|----|-----|-----|----|
| P1      | 0  | 8  | 18  | 18  | 10 |
| P2      | 1  | 4  | 8   | 7   | 3  |
| P3      | 2  | 2  | 4   | 2   | 0  |
| P4      | 3  | 1  | 5   | 2   | 1  |
| P5      | 4  | 3  | 11  | 7   | 4  |
| **Avg** |    |    |     | **7.2** | **3.6** |

> ≡ƒÆí SRTF gives the optimal (minimum) average waiting time among all scheduling algorithms.

</details>

---

### ≡ƒôè Problem 4: Priority Scheduling (Non-Preemptive)

**Problem Statement:**

Consider the following set of processes with their arrival times, burst times, and priorities (**lower number = higher priority**):

| Process | Arrival Time | Burst Time | Priority |
|---------|-------------|------------|----------|
| P1      | 0           | 6          | 3        |
| P2      | 1           | 3          | 1        |
| P3      | 2           | 8          | 4        |
| P4      | 3           | 2          | 2        |
| P5      | 5           | 4          | 5        |

**Using non-preemptive priority scheduling, calculate the Gantt chart and all metrics.**

<details><summary>Γ£à Answer</summary>

**Step 1: Execution trace (non-preemptive priority)**

- **Time 0:** Only P1 (Priority 3) has arrived. P1 starts. (Non-preemptive: P1 runs to completion.)
- **Time 6:** P1 finishes. Ready queue: P2 (Pri=1, AT=1), P3 (Pri=4, AT=2), P4 (Pri=2, AT=3), P5 (Pri=5, AT=5). Highest priority = P2 (Pri=1). **P2 runs.**
- **Time 9:** P2 finishes. Ready queue: P3 (Pri=4), P4 (Pri=2), P5 (Pri=5). Highest priority = P4 (Pri=2). **P4 runs.**
- **Time 11:** P4 finishes. Ready queue: P3 (Pri=4), P5 (Pri=5). Highest priority = P3 (Pri=4). **P3 runs.**
- **Time 19:** P3 finishes. Ready queue: P5 (Pri=5). **P5 runs.**
- **Time 23:** P5 finishes. All done.

**Step 2: Gantt Chart**

```
| P1          | P2      | P4   | P3               | P5       |
0             6         9     11                   19        23
```

**Step 3: Calculate all metrics**

| Process | AT | BT | Priority | CT  | TAT = CTΓêÆAT | WT = TATΓêÆBT |
|---------|----|----|----------|-----|-------------|--------------|
| P1      | 0  | 6  | 3        | 6   | 6           | 0            |
| P2      | 1  | 3  | 1        | 9   | 8           | 5            |
| P3      | 2  | 8  | 4        | 19  | 17          | 9            |
| P4      | 3  | 2  | 2        | 11  | 8           | 6            |
| P5      | 5  | 4  | 5        | 23  | 18          | 14           |

**Step 4: Averages**

- **Average Waiting Time** = (0 + 5 + 9 + 6 + 14) / 5 = **34 / 5 = 6.8**
- **Average Turnaround Time** = (6 + 8 + 17 + 8 + 18) / 5 = **57 / 5 = 11.4**

**Final Summary:**

| Process | AT | BT | Pri | CT  | TAT  | WT  |
|---------|----|----|-----|-----|------|-----|
| P1      | 0  | 6  | 3   | 6   | 6    | 0   |
| P2      | 1  | 3  | 1   | 9   | 8    | 5   |
| P3      | 2  | 8  | 4   | 19  | 17   | 9   |
| P4      | 3  | 2  | 2   | 11  | 8    | 6   |
| P5      | 5  | 4  | 5   | 23  | 18   | 14  |
| **Avg** |    |    |     |     | **11.4** | **6.8** |

> ΓÜá∩╕Å Notice P5 has the longest wait (14) due to its low priority (5). In a real system, **aging** would be used to gradually increase P5's priority and prevent starvation.

</details>

---

### ≡ƒôè Problem 5: Round Robin (RR)

**Problem Statement:**

Consider the following set of processes with **time quantum q = 3**:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 7          |
| P2      | 1           | 4          |
| P3      | 2           | 2          |
| P4      | 3           | 5          |

**Using Round Robin scheduling with q = 3, show the queue state at each step and calculate all metrics.**

<details><summary>Γ£à Answer</summary>

**Step-by-step execution with queue tracking:**

| Time | Action | Running | Remaining Bursts | Ready Queue (order) |
|------|--------|---------|------------------|---------------------|
| 0    | P1 starts | P1 | P1:7 | ΓÇö |
| 1    | P2 arrives | P1 | P1:6, P2:4 | [P2] |
| 2    | P3 arrives | P1 | P1:5, P2:4, P3:2 | [P2, P3] |
| 3    | P1 quantum expires, P4 arrives | ΓÇö | P1:4, P2:4, P3:2, P4:5 | [P2, P3, P4, P1] |
| 3    | P2 starts | P2 | ΓÇö | [P3, P4, P1] |
| 6    | P2 quantum expires (1 left) | ΓÇö | P1:4, P2:1, P3:2, P4:5 | [P3, P4, P1, P2] |
| 6    | P3 starts | P3 | ΓÇö | [P4, P1, P2] |
| 8    | P3 finishes (burst=2 < q=3) | ΓÇö | P1:4, P2:1, P4:5 | [P4, P1, P2] |
| 8    | P4 starts | P4 | ΓÇö | [P1, P2] |
| 11   | P4 quantum expires (2 left) | ΓÇö | P1:4, P2:1, P4:2 | [P1, P2, P4] |
| 11   | P1 starts | P1 | ΓÇö | [P2, P4] |
| 14   | P1 quantum expires (1 left) | ΓÇö | P1:1, P2:1, P4:2 | [P2, P4, P1] |
| 14   | P2 starts | P2 | ΓÇö | [P4, P1] |
| 15   | P2 finishes (1 left < q) | ΓÇö | P1:1, P4:2 | [P4, P1] |
| 15   | P4 starts | P4 | ΓÇö | [P1] |
| 17   | P4 finishes (2 left < q) | ΓÇö | P1:1 | [P1] |
| 17   | P1 starts | P1 | ΓÇö | ΓÇö |
| 18   | P1 finishes | ΓÇö | All done | ΓÇö |

**Gantt Chart:**

```
| P1      | P2      | P3   | P4      | P1      | P2 | P4   | P1 |
0         3         6      8        11        14   15    17   18
```

**Calculations:**

| Process | AT | BT | CT  | TAT = CTΓêÆAT | WT = TATΓêÆBT |
|---------|----|----|-----|-------------|--------------|
| P1      | 0  | 7  | 18  | 18          | 11           |
| P2      | 1  | 4  | 15  | 14          | 10           |
| P3      | 2  | 2  | 8   | 6           | 4            |
| P4      | 3  | 5  | 17  | 14          | 9            |

**Averages:**

- **Average Waiting Time** = (11 + 10 + 4 + 9) / 4 = **34 / 4 = 8.5**
- **Average Turnaround Time** = (18 + 14 + 6 + 14) / 4 = **52 / 4 = 13.0**

**Final Summary:**

| Process | AT | BT | CT  | TAT | WT  |
|---------|----|----|-----|-----|-----|
| P1      | 0  | 7  | 18  | 18  | 11  |
| P2      | 1  | 4  | 15  | 14  | 10  |
| P3      | 2  | 2  | 8   | 6   | 4   |
| P4      | 3  | 5  | 17  | 14  | 9   |
| **Avg** |    |    |     | **13.0** | **8.5** |

> ≡ƒÆí **Observations:**
> - P3 finishes early because its burst (2) is less than the quantum (3)
> - RR has higher average waiting time than SJF/SRTF but provides better response time
> - If q were very large (e.g., q=10), this would degenerate into FCFS
> - Each process gets the CPU at most every (nΓêÆ1)├ùq = 3├ù3 = 9 time units

</details>

---

---

## ≡ƒÄ» Quick Reference: Algorithm Comparison

| Algorithm | Type | Starvation? | Convoy Effect? | Optimal? | Best For |
|-----------|------|-------------|----------------|----------|----------|
| FCFS | Non-preemptive | No | Yes | No | Batch systems |
| SJF | Non-preemptive | Yes | No | Yes (min avg WT) | When burst times known |
| SRTF | Preemptive | Yes | No | Yes (min avg WT) | When burst times known |
| Priority | Both | Yes | No | No | Systems with priorities |
| Round Robin | Preemptive | No | No | No | Interactive/time-sharing |
| MLFQ | Preemptive | Possible (use aging) | No | No | General purpose |

---

> ≡ƒÅå **You've reached the end of the Question Bank!** If you can answer all of these questions confidently, you're well-prepared for your OS exam. Go back and review any topics where you struggled. Good luck! ≡ƒìÇ
