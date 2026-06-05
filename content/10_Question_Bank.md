# 📝 OS Exam Question Bank

## How to Use This Section
This question bank covers all topics in the OS syllabus and is organized to help you test your understanding of the core concepts:
- **Part 1 — Multiple Choice (MCQ):** Questions organized by chapter.
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
**B) To manage hardware resources and provide services for applications** — The OS is an intermediary between the user and hardware, allocating resources like CPU and memory.
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

---

### 📘 Chapter 2: OS Structures

**Q4.** A system call is typically invoked through a:
- A) Hardware interrupt
- B) Software interrupt (trap)
- C) Reboot sequence
- D) Direct memory access (DMA)

<details><summary>✅ Answer</summary>
**B) Software interrupt (trap)** — Programs execute a special instruction to trigger a trap, switching the CPU to kernel mode to perform the OS service.
</details>

**Q5.** The system call interface maintains a table indexed by:
- A) Process IDs
- B) System call numbers
- C) Memory addresses
- D) File sizes

<details><summary>✅ Answer</summary>
**B) System call numbers** — Each system call (like read, write, exit) is assigned a unique number. The table maps these numbers to the kernel implementation.
</details>

**Q6.** Which of the following is NOT a category of system calls?
- A) Process control
- B) File management
- C) Application UI design
- D) Device management

<details><summary>✅ Answer</summary>
**C) Application UI design** — The categories include process control, file management, device management, information maintenance, communications, and protection.
</details>

---

### 📘 Chapter 3: Processes

**Q7.** Which of the following is NOT a valid process state?
- A) Ready
- B) Waiting
- C) Compiling
- D) Running

<details><summary>✅ Answer</summary>
**C) Compiling** — The five standard process states are: New, Ready, Running, Waiting, and Terminated.
</details>

**Q8.** What does the Process Control Block (PCB) store?
- A) The source code of the program
- B) Process state, program counter, CPU registers, and scheduling info
- C) User passwords
- D) The compiler logs

<details><summary>✅ Answer</summary>
**B)** — The PCB is the data structure the OS uses to represent and track a process.
</details>

**Q9.** Context switching involves:
- A) Deleting the old process
- B) Saving the state of the current process and loading the state of the next process
- C) Re-compiling the program
- D) Moving the process to disk

<details><summary>✅ Answer</summary>
**B)** — During a context switch, the OS saves the PCB of the current process and restores the PCB of the next process to be scheduled. This takes time and is considered overhead.
</details>

---

### 📘 Chapter 4: Threads & Concurrency

**Q10.** The main difference between a process and a thread is that:
- A) Threads cannot run on multiple cores
- B) Threads share the memory and resources of their parent process
- C) Processes are faster to create
- D) Threads do not have their own program counter

<details><summary>✅ Answer</summary>
**B) Threads share the memory and resources of their parent process** — While processes have entirely separate address spaces, threads within the same process share code, data, and open files.
</details>

**Q11.** Distributing subsets of the same data across multiple cores and performing the same operation on each is called:
- A) Task parallelism
- B) Data parallelism
- C) Serial execution
- D) Concurrency

<details><summary>✅ Answer</summary>
**B) Data parallelism** — For example, splitting a large array into four chunks and having four threads process them simultaneously. Task parallelism is when different threads perform completely different tasks.
</details>

**Q12.** In the Many-to-One multithreading model:
- A) Each user thread maps to its own kernel thread
- B) Many user threads map to a single kernel thread
- C) There are no kernel threads
- D) Threads are created automatically by the compiler

<details><summary>✅ Answer</summary>
**B)** — In Many-to-One, if one user thread makes a blocking system call, all threads are blocked because there is only one kernel thread handling them.
</details>

---

### 📘 Chapter 5 & 6: CPU Scheduling

**Q13.** The CPU scheduler is also known as the:
- A) Long-term scheduler
- B) Short-term scheduler
- C) Disk scheduler
- D) Network scheduler

<details><summary>✅ Answer</summary>
**B) Short-term scheduler** — It selects which process should execute next from the ready queue and allocates the CPU to it.
</details>

**Q14.** Preemptive scheduling means:
- A) A process runs until it voluntarily yields the CPU
- B) The OS can forcibly take the CPU away from a running process
- C) Only the longest jobs get the CPU
- D) Processes cannot be interrupted

<details><summary>✅ Answer</summary>
**B) The OS can forcibly take the CPU away from a running process** — This usually happens when a timer interrupt goes off (like in Round Robin) or a higher priority process arrives.
</details>

**Q15.** Which algorithm minimizes average waiting time but is difficult to implement because it requires knowing the future burst length?
- A) First-Come, First-Served (FCFS)
- B) Shortest Job First (SJF)
- C) Round Robin (RR)
- D) Priority Scheduling

<details><summary>✅ Answer</summary>
**B) Shortest Job First (SJF)** — SJF is provably optimal for minimizing average waiting time, but predicting the exact length of the next CPU burst is challenging.
</details>

**Q16.** Aging is used to prevent:
- A) Thrashing
- B) Starvation
- C) Context switching
- D) High CPU utilization

<details><summary>✅ Answer</summary>
**B) Starvation** — Aging gradually increases the priority of a process the longer it waits in the ready queue, ensuring that low-priority processes eventually get to run.
</details>

---

### 📘 Chapter 7 & 8: Memory Management & Deadlocks

**Q17.** Virtual memory allows:
- A) The CPU to run twice as fast
- B) The execution of processes that are larger than the physical RAM
- C) The hard drive to spin faster
- D) Deletion of cache memory

<details><summary>✅ Answer</summary>
**B)** — By keeping only the actively used "pages" of a program in RAM and swapping the rest to the disk, virtual memory creates the illusion of infinite memory.
</details>

**Q18.** Which of the following is NOT one of the four necessary conditions for a deadlock?
- A) Mutual exclusion
- B) Hold and wait
- C) Preemption
- D) Circular wait

<details><summary>✅ Answer</summary>
**C) Preemption** — The condition is actually **No Preemption** (resources cannot be forcibly taken). If preemption is allowed, deadlocks can be resolved.
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

---


## Part 3: Scheduling Problems (Fully Worked)

## Part 4: Scheduling Problems (Fully Worked)

---

### 📊 Problem 1: FCFS (First-Come, First-Served)

**Problem Statement:**

Consider the following set of processes with their arrival times and CPU burst times:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 8          |
| P2      | 1           | 4          |
| P3      | 2           | 9          |
| P4      | 3           | 5          |

**Using FCFS scheduling, calculate the Gantt chart, waiting time, and turnaround time for each process.**

<details><summary>✅ Answer</summary>

**Step 1: Determine the order of execution**

FCFS serves processes in the order they arrive:
- P1 arrives at time 0 → runs first
- P2 arrives at time 1 → runs second
- P3 arrives at time 2 → runs third
- P4 arrives at time 3 → runs fourth

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

Turnaround Time = Completion Time − Arrival Time

| Process | Completion | Arrival | Turnaround Time |
|---------|-----------|---------|-----------------|
| P1      | 8         | 0       | 8 − 0 = **8**  |
| P2      | 12        | 1       | 12 − 1 = **11**|
| P3      | 21        | 2       | 21 − 2 = **19**|
| P4      | 26        | 3       | 26 − 3 = **23**|

**Step 5: Calculate Waiting Times**

Waiting Time = Turnaround Time − Burst Time

| Process | Turnaround | Burst | Waiting Time    |
|---------|-----------|-------|-----------------|
| P1      | 8         | 8     | 8 − 8 = **0**  |
| P2      | 11        | 4     | 11 − 4 = **7** |
| P3      | 19        | 9     | 19 − 9 = **10**|
| P4      | 23        | 5     | 23 − 5 = **18**|

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

### 📊 Problem 2: SJF Non-Preemptive (Shortest Job First)

**Problem Statement:**

Consider the following set of processes:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 7          |
| P2      | 2           | 4          |
| P3      | 4           | 1          |
| P4      | 5           | 4          |

**Using non-preemptive SJF scheduling, calculate the Gantt chart, waiting time, and turnaround time for each process.**

<details><summary>✅ Answer</summary>

**Step 1: Execution trace (non-preemptive SJF)**

- **Time 0:** Only P1 has arrived (AT=0). P1 starts running. Burst = 7.
- **Time 7:** P1 finishes. Ready queue contains: P2 (BT=4, arrived at 2), P3 (BT=1, arrived at 4), P4 (BT=4, arrived at 5). Shortest burst = P3 (BT=1). **P3 runs.**
- **Time 8:** P3 finishes. Ready queue: P2 (BT=4), P4 (BT=4). Tie → use FCFS (P2 arrived first). **P2 runs.**
- **Time 12:** P2 finishes. Ready queue: P4 (BT=4). **P4 runs.**
- **Time 16:** P4 finishes. All done.

**Step 2: Gantt Chart**

```
| P1              | P3  | P2      | P4      |
0                 7     8        12        16
```

**Step 3: Calculate all metrics**

| Process | AT | BT | CT | TAT = CT−AT | WT = TAT−BT |
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

> 💡 Compare this to FCFS for the same data: SJF gives lower average waiting time, confirming SJF is optimal for minimizing average waiting time.

</details>

---

### 📊 Problem 3: SRTF (Shortest Remaining Time First — Preemptive SJF)

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

<details><summary>✅ Answer</summary>

**Step-by-step execution trace at each time unit:**

| Time | Event | Ready Queue (Process: Remaining) | Running | Action |
|------|-------|----------------------------------|---------|--------|
| 0    | P1 arrives | P1:8 | P1 | P1 starts (only process) |
| 1    | P2 arrives | P1:7, P2:4 | P2 | P2 preempts P1 (4 < 7) |
| 2    | P3 arrives | P1:7, P2:3, P3:2 | P3 | P3 preempts P2 (2 < 3) |
| 3    | P4 arrives | P1:7, P2:3, P3:1, P4:1 | P3 | P3 continues (remaining 1 ≤ P4's 1, no preemption) |
| 4    | P3 done, P5 arrives | P1:7, P2:3, P4:1, P5:3 | P4 | P4 runs (shortest remaining = 1) |
| 5    | P4 done | P1:7, P2:3, P5:3 | P2 | P2 runs (tie: P2 arrived first, both have 3) |
| 6    | — | P1:7, P2:2, P5:3 | P2 | P2 continues |
| 7    | — | P1:7, P2:1, P5:3 | P2 | P2 continues |
| 8    | P2 done | P1:7, P5:3 | P5 | P5 runs (3 < 7) |
| 9–10 | — | P1:7, P5:2→1 | P5 | P5 continues |
| 11   | P5 done | P1:7 | P1 | P1 runs |
| 11–18| — | P1:7→0 | P1 | P1 runs to completion |

**Gantt Chart:**

```
| P1 | P2 | P3   | P4 | P2      | P5      | P1                     |
0    1    2      4    5         8        11                         18
```

**Calculations:**

| Process | AT | BT | CT  | TAT = CT−AT | WT = TAT−BT |
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

> 💡 SRTF gives the optimal (minimum) average waiting time among all scheduling algorithms.

</details>

---

### 📊 Problem 4: Priority Scheduling (Non-Preemptive)

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

<details><summary>✅ Answer</summary>

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

| Process | AT | BT | Priority | CT  | TAT = CT−AT | WT = TAT−BT |
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

> ⚠️ Notice P5 has the longest wait (14) due to its low priority (5). In a real system, **aging** would be used to gradually increase P5's priority and prevent starvation.

</details>

---

### 📊 Problem 5: Round Robin (RR)

**Problem Statement:**

Consider the following set of processes with **time quantum q = 3**:

| Process | Arrival Time | Burst Time |
|---------|-------------|------------|
| P1      | 0           | 7          |
| P2      | 1           | 4          |
| P3      | 2           | 2          |
| P4      | 3           | 5          |

**Using Round Robin scheduling with q = 3, show the queue state at each step and calculate all metrics.**

<details><summary>✅ Answer</summary>

**Step-by-step execution with queue tracking:**

| Time | Action | Running | Remaining Bursts | Ready Queue (order) |
|------|--------|---------|------------------|---------------------|
| 0    | P1 starts | P1 | P1:7 | — |
| 1    | P2 arrives | P1 | P1:6, P2:4 | [P2] |
| 2    | P3 arrives | P1 | P1:5, P2:4, P3:2 | [P2, P3] |
| 3    | P1 quantum expires, P4 arrives | — | P1:4, P2:4, P3:2, P4:5 | [P2, P3, P4, P1] |
| 3    | P2 starts | P2 | — | [P3, P4, P1] |
| 6    | P2 quantum expires (1 left) | — | P1:4, P2:1, P3:2, P4:5 | [P3, P4, P1, P2] |
| 6    | P3 starts | P3 | — | [P4, P1, P2] |
| 8    | P3 finishes (burst=2 < q=3) | — | P1:4, P2:1, P4:5 | [P4, P1, P2] |
| 8    | P4 starts | P4 | — | [P1, P2] |
| 11   | P4 quantum expires (2 left) | — | P1:4, P2:1, P4:2 | [P1, P2, P4] |
| 11   | P1 starts | P1 | — | [P2, P4] |
| 14   | P1 quantum expires (1 left) | — | P1:1, P2:1, P4:2 | [P2, P4, P1] |
| 14   | P2 starts | P2 | — | [P4, P1] |
| 15   | P2 finishes (1 left < q) | — | P1:1, P4:2 | [P4, P1] |
| 15   | P4 starts | P4 | — | [P1] |
| 17   | P4 finishes (2 left < q) | — | P1:1 | [P1] |
| 17   | P1 starts | P1 | — | — |
| 18   | P1 finishes | — | All done | — |

**Gantt Chart:**

```
| P1      | P2      | P3   | P4      | P1      | P2 | P4   | P1 |
0         3         6      8        11        14   15    17   18
```

**Calculations:**

| Process | AT | BT | CT  | TAT = CT−AT | WT = TAT−BT |
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

> 💡 **Observations:**
> - P3 finishes early because its burst (2) is less than the quantum (3)
> - RR has higher average waiting time than SJF/SRTF but provides better response time
> - If q were very large (e.g., q=10), this would degenerate into FCFS
> - Each process gets the CPU at most every (n−1)×q = 3×3 = 9 time units

</details>

---

---

## 🎯 Quick Reference: Algorithm Comparison

| Algorithm | Type | Starvation? | Convoy Effect? | Optimal? | Best For |
|-----------|------|-------------|----------------|----------|----------|
| FCFS | Non-preemptive | No | Yes | No | Batch systems |
| SJF | Non-preemptive | Yes | No | Yes (min avg WT) | When burst times known |
| SRTF | Preemptive | Yes | No | Yes (min avg WT) | When burst times known |
| Priority | Both | Yes | No | No | Systems with priorities |
| Round Robin | Preemptive | No | No | No | Interactive/time-sharing |
| MLFQ | Preemptive | Possible (use aging) | No | No | General purpose |

---

> 🏆 **You've reached the end of the Question Bank!** If you can answer all of these questions confidently, you're well-prepared for your OS exam. Go back and review any topics where you struggled. Good luck! 🍀
