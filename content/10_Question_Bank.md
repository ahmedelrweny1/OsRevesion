# 📝 Task Scheduling Question Bank

This section contains multiple choice questions and fully worked problems exclusively for CPU Scheduling.

### 📘 Chapter 5: CPU Scheduling Concepts

---

**Q33.** The CPU scheduler is also known as the ___?

- A) Long-term scheduler
- B) Short-term scheduler
- C) Medium-term scheduler
- D) I/O scheduler

<details><summary>✅ Answer</summary>

**B) Short-term scheduler** — The CPU scheduler (short-term scheduler) selects a process from the ready queue and allocates the CPU to it. It runs very frequently (milliseconds) and must be extremely fast.

</details>

---

**Q34.** CPU scheduling can happen in all of the following transitions EXCEPT ___?

- A) Running → Waiting
- B) Running → Ready
- C) Ready → Running
- D) New → Terminated (directly)

<details><summary>✅ Answer</summary>

**D) New → Terminated (directly)** — CPU scheduling decisions occur during four transitions: (1) Running→Waiting, (2) Running→Ready, (3) Waiting→Ready, (4) Running→Terminated. A process cannot go directly from New to Terminated.

</details>

---

**Q35.** Dispatch latency is ___?

- A) The time a process waits in the ready queue
- B) The time it takes for the dispatcher to stop one process and start another
- C) The total execution time of a process
- D) The time between process creation and termination

<details><summary>✅ Answer</summary>

**B) The time it takes for the dispatcher to stop one process and start another** — Dispatch latency is the time the dispatcher takes to stop one process and start running another. It includes context switching, switching to user mode, and jumping to the correct location in the user program.

</details>

---

**Q36.** Which scheduling criterion should be MAXIMIZED?

- A) Waiting time
- B) Turnaround time
- C) CPU utilization and throughput
- D) Response time

<details><summary>✅ Answer</summary>

**C) CPU utilization and throughput** — We want to maximize CPU utilization (keep CPU busy) and throughput (number of processes completed per time unit). We want to minimize turnaround time, waiting time, and response time.

</details>

---

**Q37.** The dispatcher does all of the following EXCEPT ___?

- A) Switching context
- B) Switching to user mode
- C) Selecting which process to run next
- D) Jumping to the proper location in the user program

<details><summary>✅ Answer</summary>

**C) Selecting which process to run next** — The dispatcher gives control of the CPU to the process selected by the short-term scheduler. It performs context switching, switching to user mode, and jumping to the correct location. The scheduler (not the dispatcher) selects which process runs next.

</details>

---

**Q38.** Preemptive scheduling means ___?

- A) A process runs until it voluntarily gives up the CPU
- B) The OS can forcibly take the CPU away from a running process
- C) Only one process can ever run
- D) Scheduling only happens at boot time

<details><summary>✅ Answer</summary>

**B) The OS can forcibly take the CPU away from a running process** — In preemptive scheduling, the OS can interrupt a running process (e.g., when a higher-priority process arrives or a time quantum expires) and allocate the CPU to another process.

</details>

---

**Q39.** Non-preemptive scheduling occurs only when a process ___?

- A) Gets a higher priority
- B) Switches from running to waiting or terminates
- C) Enters the ready queue
- D) Receives a signal

<details><summary>✅ Answer</summary>

**B) Switches from running to waiting or terminates** — Non-preemptive (cooperative) scheduling only makes scheduling decisions when a process voluntarily gives up the CPU — either by switching to the waiting state (e.g., I/O request) or by terminating.

</details>

---

**Q40.** Turnaround time is defined as ___?

- A) Time spent waiting in the ready queue
- B) Time from submission of a process to its completion
- C) Time the CPU is idle
- D) Time spent in I/O

<details><summary>✅ Answer</summary>

**B) Time from submission of a process to its completion** — Turnaround time = Completion time − Arrival time. It includes all time spent waiting in the ready queue, executing on the CPU, and doing I/O.

</details>

---

### 📘 Chapter 6: Scheduling Algorithms

---

**Q41.** FCFS (First-Come, First-Served) scheduling may cause ___?

- A) Starvation
- B) The convoy effect
- C) Deadlock
- D) Thrashing

<details><summary>✅ Answer</summary>

**B) The convoy effect** — In FCFS, if a long CPU-bound process arrives first, all shorter processes behind it must wait, causing the "convoy effect" — short processes pile up behind a long one, leading to poor average waiting time.

</details>

---

**Q42.** SJF (Shortest Job First) is optimal because ___?

- A) It is the simplest algorithm
- B) It gives the minimum average waiting time for a given set of processes
- C) It prevents deadlock
- D) It uses the most memory

<details><summary>✅ Answer</summary>

**B) It gives the minimum average waiting time for a given set of processes** — SJF is provably optimal: by scheduling the shortest jobs first, it minimizes the average waiting time. However, it requires knowing (or predicting) the next CPU burst length, which is its main challenge.

</details>

---

**Q43.** In SRTF (Shortest Remaining Time First), preemption occurs when ___?

- A) A process finishes I/O
- B) A new process arrives with a shorter remaining burst than the currently running process
- C) The time quantum expires
- D) The process voluntarily yields

<details><summary>✅ Answer</summary>

**B) A new process arrives with a shorter remaining burst than the currently running process** — SRTF is the preemptive version of SJF. When a new process arrives, if its burst time is shorter than the remaining time of the currently executing process, the current process is preempted.

</details>

---

**Q44.** In Round Robin with quantum q, the maximum waiting time for a process is ___?

- A) (n) × q
- B) (n − 1) × q
- C) q
- D) n × (q + context switch time)

<details><summary>✅ Answer</summary>

**B) (n − 1) × q** — In Round Robin, if there are n processes in the ready queue, each process waits at most (n − 1) × q time units before getting the CPU again. No process waits more than this between consecutive turns.

</details>

---

**Q45.** Aging is used to prevent ___?

- A) Deadlock
- B) Starvation
- C) Fragmentation
- D) Thrashing

<details><summary>✅ Answer</summary>

**B) Starvation** — Aging is a technique where the priority of a process is gradually increased the longer it waits in the ready queue. This prevents indefinite blocking (starvation) of low-priority processes.

</details>

---

**Q46.** Which scheduling algorithm gives the best average response time for interactive systems?

- A) FCFS
- B) SJF
- C) Round Robin
- D) Priority (non-preemptive)

<details><summary>✅ Answer</summary>

**C) Round Robin** — Round Robin is designed for time-sharing/interactive systems. By giving each process a small time quantum, it ensures all processes get regular CPU time, providing good response times.

</details>

---

**Q47.** If the time quantum q in Round Robin is very large, it degenerates into ___?

- A) SJF
- B) FCFS
- C) Priority scheduling
- D) SRTF

<details><summary>✅ Answer</summary>

**B) FCFS** — If q is very large (larger than the longest burst), no process is ever preempted by the timer, so processes run to completion in arrival order — exactly like FCFS.

</details>

---

**Q48.** The exponential averaging formula for predicting next CPU burst is ___?

- A) τ(n+1) = α × t(n) + (1 − α) × τ(n)
- B) τ(n+1) = t(n) + τ(n)
- C) τ(n+1) = t(n) × τ(n)
- D) τ(n+1) = α × τ(n)

<details><summary>✅ Answer</summary>

**A) τ(n+1) = α × t(n) + (1 − α) × τ(n)** — Where t(n) is the actual length of the nth CPU burst, τ(n) is the predicted value, and α (0 ≤ α ≤ 1) controls the weight of recent vs. past history. When α = 0, history dominates; when α = 1, only the last burst matters.

</details>

---




**Q52.** If α = 0 in exponential averaging, the predicted next burst ___?

- A) Equals the most recent burst
- B) Ignores recent history and equals the initial guess τ(0) throughout
- C) Becomes zero
- D) Doubles the previous prediction

<details><summary>✅ Answer</summary>

**B) Ignores recent history and equals the initial guess τ(0) throughout** — When α = 0, the formula becomes τ(n+1) = τ(n) = ... = τ(0). The actual burst times are never factored in, and the prediction never changes from the initial value.

</details>

---

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
