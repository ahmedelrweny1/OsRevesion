## 1. FCFS — First-Come, First-Served

The simplest CPU scheduling algorithm. Processes are executed in the **order they arrive** in the ready queue — just like a queue at a grocery store.

**Properties:**
* **Non-preemptive** — once a process gets the CPU, it runs until it finishes
* Implemented using a **FIFO queue**
* Easy to understand and implement, but often **poor performance**

### Example 1: Arrival Order P1 → P2 → P3

| Process | Burst Time |
| :--- | :--- |
| P1 | 24 ms |
| P2 | 3 ms |
| P3 | 3 ms |

**Gantt Chart:**

| P1 | P2 | P3 |
| :---: | :---: | :---: |
| 0 ————— 24 | 24 —— 27 | 27 —— 30 |

**Calculations:**

| Process | Completion | Turnaround | Waiting Time |
| :--- | :--- | :--- | :--- |
| P1 | 24 | 24 − 0 = 24 | 24 − 24 = **0** |
| P2 | 27 | 27 − 0 = 27 | 27 − 3 = **24** |
| P3 | 30 | 30 − 0 = 30 | 30 − 3 = **27** |

$$
\text{Average Waiting Time} = \frac{0 + 24 + 27}{3} = \frac{51}{3} = \mathbf{17 \text{ ms}}
$$

### Example 2: Arrival Order P2 → P3 → P1

Same processes, but now **P2 arrives first**, then P3, then P1.

**Gantt Chart:**

| P2 | P3 | P1 |
| :---: | :---: | :---: |
| 0 —— 3 | 3 —— 6 | 6 ————— 30 |

**Calculations:**

| Process | Completion | Turnaround | Waiting Time |
| :--- | :--- | :--- | :--- |
| P1 | 30 | 30 − 0 = 30 | 30 − 24 = **6** |
| P2 | 3 | 3 − 0 = 3 | 3 − 3 = **0** |
| P3 | 6 | 6 − 0 = 6 | 6 − 3 = **3** |

$$
\text{Average Waiting Time} = \frac{6 + 0 + 3}{3} = \frac{9}{3} = \mathbf{3 \text{ ms}}
$$

> [!important] Dramatic Difference!
> Same processes, different arrival order: **17 ms vs 3 ms** average waiting time. This shows FCFS is highly sensitive to arrival order.

### The Convoy Effect

The **Convoy Effect** occurs when a single long (CPU-bound) process blocks many short (I/O-bound) processes behind it, like a slow truck blocking a lane of fast cars.

* All short processes must **wait** for the long process to finish
* Results in **lower CPU utilization** and **lower throughput**
* This is the primary weakness of FCFS

---

## 2. SJF — Shortest Job First (Nonpreemptive)

Schedule the process with the **shortest CPU burst** next. Among all processes in the ready queue, pick the one that will finish the fastest.

**Properties:**
* **Nonpreemptive** — once a process starts, it runs to completion
* **Optimal** — gives the minimum average waiting time for any set of processes
* **Challenge:** We can't know the exact future burst length! Must estimate/predict it

### SJF Example

| Process | Arrival Time | Burst Time |
| :--- | :--- | :--- |
| P1 | 0 | 6 |
| P2 | 2 | 8 |
| P3 | 4 | 7 |
| P4 | 5 | 3 |

**Step-by-step trace:**
* **t=0:** Only P1 has arrived → P1 starts running
* **t=6:** P1 finishes. Ready queue: P2 (burst=8), P3 (burst=7), P4 (burst=3). Shortest = **P4** → runs
* **t=9:** P4 finishes. Ready queue: P2 (burst=8), P3 (burst=7). Shortest = **P3** → runs
* **t=16:** P3 finishes. Ready queue: P2 (burst=8). **P2** → runs
* **t=24:** P2 finishes. All done.

**Gantt Chart:**

| P1 | P4 | P3 | P2 |
| :---: | :---: | :---: | :---: |
| 0 —— 6 | 6 —— 9 | 9 —— 16 | 16 —— 24 |

**Calculations:**

| Process | Arrival | Completion | Turnaround | Waiting Time |
| :--- | :--- | :--- | :--- | :--- |
| P1 | 0 | 6 | 6 − 0 = 6 | 6 − 6 = **0** |
| P2 | 2 | 24 | 24 − 2 = 22 | 22 − 8 = **14** |
| P3 | 4 | 16 | 16 − 4 = 12 | 12 − 7 = **5** |
| P4 | 5 | 9 | 9 − 5 = 4 | 4 − 3 = **1** |

$$
\text{Average Waiting Time} = \frac{0 + 14 + 5 + 1}{4} = \frac{20}{4} = \mathbf{5 \text{ ms}}
$$

> [!note] SJF is Optimal
> SJF is **provably optimal** — it gives the minimum average waiting time for a given set of processes. Moving a shorter process before a longer one decreases the shorter process's wait time more than it increases the longer one's.

---

## 3. SJF Preemptive — Shortest Remaining Time First (SRTF)

SRTF is the **preemptive version** of SJF. Whenever a **new process arrives**, the scheduler compares its burst time with the **remaining time** of the currently running process. If the new process is shorter, it **preempts** (interrupts) the current process.

### SRTF Example — Full Step-by-Step Trace

| Process | Arrival Time | Burst Time |
| :--- | :--- | :--- |
| P1 | 0 | 8 |
| P2 | 1 | 4 |
| P3 | 2 | 9 |
| P4 | 3 | 5 |

**Detailed execution trace:**

**t=0:** P1 arrives (burst=8). It's the only process → **P1 runs**.

**t=1:** P2 arrives (burst=4). P1 has run for 1 unit → remaining = 7.
Compare: P2(4) < P1(7) → **P2 preempts P1**. P1 goes back to ready queue with remaining=7.

**t=2:** P3 arrives (burst=9). P2 has run for 1 unit → remaining = 3.
Compare: P2(3) < P3(9), P2(3) < P1(7) → **P2 continues**. P3 enters ready queue.

**t=3:** P4 arrives (burst=5). P2 has run for 2 units → remaining = 2.
Compare: P2(2) < P4(5), P2(2) < P1(7), P2(2) < P3(9) → **P2 continues**.

**t=5:** P2 finishes (ran from t=1 to t=5 total). Remaining processes:
* P1: remaining = 7
* P3: remaining = 9
* P4: remaining = 5
Shortest = **P4** (5) → **P4 runs**.

**t=10:** P4 finishes. Remaining:
* P1: remaining = 7
* P3: remaining = 9
Shortest = **P1** (7) → **P1 runs**.

**t=17:** P1 finishes. Only P3 left (remaining=9) → **P3 runs**.

**t=26:** P3 finishes. **All done.**

**Gantt Chart:**

| P1 | P2 | P4 | P1 | P3 |
| :---: | :---: | :---: | :---: | :---: |
| 0 — 1 | 1 ——— 5 | 5 ——— 10 | 10 ——— 17 | 17 ——— 26 |

**Calculations:**

| Process | Arrival | Burst | Completion | Turnaround | Waiting Time |
| :--- | :--- | :--- | :--- | :--- | :--- |
| P1 | 0 | 8 | 17 | 17 − 0 = 17 | 17 − 8 = **9** |
| P2 | 1 | 4 | 5 | 5 − 1 = 4 | 4 − 4 = **0** |
| P3 | 2 | 9 | 26 | 26 − 2 = 24 | 24 − 9 = **15** |
| P4 | 3 | 5 | 10 | 10 − 3 = 7 | 7 − 5 = **2** |

$$
\text{Average Waiting Time} = \frac{9 + 0 + 15 + 2}{4} = \frac{26}{4} = \mathbf{6.5 \text{ ms}}
$$

> [!tip] SRTF Decision Rule
> At every moment a new process arrives, ask: **"Is the new process's burst SHORTER than the REMAINING time of the current process?"** If yes → preempt. If no → continue.

---

## 4. Exponential Averaging — Predicting CPU Bursts

Since we **can't know** the exact length of the next CPU burst, we **predict** it using past behavior. The technique used is **Exponential Averaging**.

### The Formula

$$
\tau_{n+1} = \alpha \cdot t_n + (1 - \alpha) \cdot \tau_n
$$

Where:
* $\tau_{n+1}$ = predicted value for the **next** burst
* $t_n$ = **actual** length of the $n^{th}$ burst (observed)
* $\tau_n$ = **predicted** value of the $n^{th}$ burst (previous prediction)
* $\alpha$ = smoothing factor, $0 \leq \alpha \leq 1$

### Understanding Alpha ($\alpha$)

| Value | Behavior |
| :--- | :--- |
| $\alpha = 0$ | $\tau_{n+1} = \tau_n$ — Prediction **never changes**, history is ignored completely |
| $\alpha = 1$ | $\tau_{n+1} = t_n$ — Only the **last actual burst** matters, all history forgotten |
| $\alpha = 0.5$ | **Balanced** — equal weight to recent observation and past prediction |

> [!tip] Exam Tip
> $\alpha = 0.5$ is the most commonly tested value. It means each prediction is the simple **average** of the last actual burst and the last prediction.

### Worked Example: $\alpha = 0.5$, $\tau_0 = 10$

Given actual burst sequence: **6, 4, 6, 4, 13, 13, 13**

We calculate each prediction step by step using $\tau_{n+1} = 0.5 \times t_n + 0.5 \times \tau_n$:

| Step | Actual Burst ($t_n$) | Previous Prediction ($\tau_n$) | Calculation | New Prediction ($\tau_{n+1}$) |
| :--- | :--- | :--- | :--- | :--- |
| 0 | — | — | Given | $\tau_0 = \mathbf{10}$ |
| 1 | $t_0 = 6$ | $\tau_0 = 10$ | $0.5 \times 6 + 0.5 \times 10 = 3 + 5$ | $\tau_1 = \mathbf{8}$ |
| 2 | $t_1 = 4$ | $\tau_1 = 8$ | $0.5 \times 4 + 0.5 \times 8 = 2 + 4$ | $\tau_2 = \mathbf{6}$ |
| 3 | $t_2 = 6$ | $\tau_2 = 6$ | $0.5 \times 6 + 0.5 \times 6 = 3 + 3$ | $\tau_3 = \mathbf{6}$ |
| 4 | $t_3 = 4$ | $\tau_3 = 6$ | $0.5 \times 4 + 0.5 \times 6 = 2 + 3$ | $\tau_4 = \mathbf{5}$ |
| 5 | $t_4 = 13$ | $\tau_4 = 5$ | $0.5 \times 13 + 0.5 \times 5 = 6.5 + 2.5$ | $\tau_5 = \mathbf{9}$ |
| 6 | $t_5 = 13$ | $\tau_5 = 9$ | $0.5 \times 13 + 0.5 \times 9 = 6.5 + 4.5$ | $\tau_6 = \mathbf{11}$ |
| 7 | $t_6 = 13$ | $\tau_6 = 11$ | $0.5 \times 13 + 0.5 \times 11 = 6.5 + 5.5$ | $\tau_7 = \mathbf{12}$ |

> [!note] Observation
> Notice how the prediction **gradually converges** toward the actual value. When the actual bursts suddenly jumped to 13, the prediction lagged behind (9 → 11 → 12), slowly catching up. With a higher $\alpha$, it would catch up faster but be more volatile.

---

## 5. Round Robin (RR)

Each process gets a small unit of CPU time called a **time quantum** (or **time slice**, typically **10–100 milliseconds**). After the quantum expires, the process is **preempted** and placed at the **end** of the ready queue.

**Key Properties:**
* **Preemptive** — the timer interrupt forces context switches
* Fair — each process gets $\frac{1}{n}$ of the CPU time (for $n$ processes)
* **No process waits more than $(n-1) \times q$ time units** (where $q$ is the quantum)
* Designed for **time-sharing systems** — ensures responsiveness

### Round Robin Example: $q = 4$

| Process | Burst Time |
| :--- | :--- |
| P1 | 24 |
| P2 | 3 |
| P3 | 3 |

**Step-by-step trace:**

**t=0–4:** P1 runs for quantum (4 units). Remaining: P1=20. → P1 goes to end of queue.
Ready queue: [P2, P3, P1]

**t=4–7:** P2 runs for 3 units (finishes before quantum expires). **P2 done.**
Ready queue: [P3, P1]

**t=7–10:** P3 runs for 3 units (finishes before quantum expires). **P3 done.**
Ready queue: [P1]

**t=10–14:** P1 runs for quantum (4 units). Remaining: P1=16.
Ready queue: [P1]

**t=14–18:** P1 runs for quantum (4 units). Remaining: P1=12.

**t=18–22:** P1 runs for quantum (4 units). Remaining: P1=8.

**t=22–26:** P1 runs for quantum (4 units). Remaining: P1=4.

**t=26–30:** P1 runs for quantum (4 units). Remaining: P1=0. **P1 done.**

**Gantt Chart:**

| P1 | P2 | P3 | P1 | P1 | P1 | P1 | P1 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0—4 | 4—7 | 7—10 | 10—14 | 14—18 | 18—22 | 22—26 | 26—30 |

**Calculations:**

| Process | Burst | Completion | Turnaround | Waiting Time |
| :--- | :--- | :--- | :--- | :--- |
| P1 | 24 | 30 | 30 − 0 = 30 | 30 − 24 = **6** |
| P2 | 3 | 7 | 7 − 0 = 7 | 7 − 3 = **4** |
| P3 | 3 | 10 | 10 − 0 = 10 | 10 − 3 = **7** |

$$
\text{Average Waiting Time} = \frac{6 + 4 + 7}{3} = \frac{17}{3} = \mathbf{5.67 \text{ ms}}
$$

### Effect of Time Quantum Size

The quantum size $q$ has a **dramatic effect** on RR performance:

| Quantum Size | Behavior |
| :--- | :--- |
| $q$ → **very large** (∞) | Degenerates into **FCFS** — each process finishes before quantum expires |
| $q$ → **very small** | Excessive **context switches** — most CPU time spent switching, not computing |
| **Optimal range** | $q$ = **10–100 ms**, with context switch time < **10 μs** |

> [!warning] Rule of Thumb
> The time quantum should be **large enough** that ~80% of CPU bursts are shorter than the quantum. This ensures most processes finish within their quantum, reducing unnecessary context switches.
> Context switch overhead should be **< 10 μs**, while quantum is **10–100 ms** (quantum should be ~1000x the switch time).

---

## 6. Priority Scheduling

Each process is assigned a **priority number**. The CPU is allocated to the process with the **highest priority**.

**Convention:** Smallest integer = **highest** priority (e.g., priority 1 > priority 5).

**Properties:**
* Can be **preemptive** or **nonpreemptive**
* SJF is a special case of priority scheduling where $\text{priority} = \frac{1}{\text{predicted next burst time}}$

### Priority Scheduling Example (Nonpreemptive)

All processes arrive at time 0:

| Process | Burst Time | Priority |
| :--- | :--- | :--- |
| P1 | 10 | 3 |
| P2 | 1 | 1 |
| P3 | 2 | 4 |
| P4 | 1 | 5 |
| P5 | 5 | 2 |

**Execution order** (sorted by priority, smallest number = highest priority):
P2 (pri=1) → P5 (pri=2) → P1 (pri=3) → P3 (pri=4) → P4 (pri=5)

**Gantt Chart:**

| P2 | P5 | P1 | P3 | P4 |
| :---: | :---: | :---: | :---: | :---: |
| 0 — 1 | 1 ——— 6 | 6 ———— 16 | 16 —— 18 | 18 — 19 |

**Calculations:**

| Process | Completion | Turnaround | Waiting Time |
| :--- | :--- | :--- | :--- |
| P1 | 16 | 16 − 0 = 16 | 16 − 10 = **6** |
| P2 | 1 | 1 − 0 = 1 | 1 − 1 = **0** |
| P3 | 18 | 18 − 0 = 18 | 18 − 2 = **16** |
| P4 | 19 | 19 − 0 = 19 | 19 − 1 = **18** |
| P5 | 6 | 6 − 0 = 6 | 6 − 5 = **1** |

$$
\text{Average Waiting Time} = \frac{6 + 0 + 16 + 18 + 1}{5} = \frac{41}{5} = \mathbf{8.2 \text{ ms}}
$$

### Problem: Starvation

**Starvation** occurs when low-priority processes **wait indefinitely** because higher-priority processes keep arriving and jumping ahead in the queue.

* A low-priority process might **never execute** if there is always a higher-priority process ready

### Solution: Aging

**Aging** gradually **increases the priority** of processes that have been waiting for a long time.

* **Example policy:** Increase priority by 1 every **15 minutes**
* A process starting at priority 127 will eventually reach priority 0 (highest) after sufficient waiting time
* This **guarantees** that every process will eventually run

> [!important] Starvation + Aging
> Whenever you mention priority scheduling in an exam, always discuss the **starvation problem** and the **aging solution**. They are inseparable concepts.

---

## 7. Algorithm Comparison Table

| Algorithm | Type | Preemptive? | Optimal? | Starvation? | Key Advantage | Key Disadvantage |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **FCFS** | Non-preemptive | ❌ No | ❌ No | ❌ No | Simple to implement | Convoy effect |
| **SJF** | Non-preemptive | ❌ No | ✅ Yes | ✅ Yes | Minimum avg wait time | Can't know burst length |
| **SRTF** | Preemptive | ✅ Yes | ✅ Yes | ✅ Yes | Best avg wait time (preemptive) | Overhead of frequent switching |
| **Priority** | Both | Both | ❌ No | ✅ Yes | Handles urgency well | Starvation (solved by aging) |
| **Round Robin** | Preemptive | ✅ Yes | ❌ No | ❌ No | Fair, good response time | High avg wait if quantum is poor |

---

## 8. Key Formulas Summary

> [!important] Must-Know Formulas

$$
\text{Turnaround Time} = \text{Completion Time} - \text{Arrival Time}
$$

$$
\text{Waiting Time} = \text{Turnaround Time} - \text{Burst Time}
$$

$$
\text{Response Time} = \text{First Response Time} - \text{Arrival Time}
$$

$$
\text{Exponential Average: } \tau_{n+1} = \alpha \cdot t_n + (1 - \alpha) \cdot \tau_n
$$

$$
\text{RR Max Wait} = (n - 1) \times q \text{ where } n = \text{number of processes, } q = \text{quantum}
$$

---

## 9. Quick Decision Guide

Use this to quickly identify which algorithm to apply in an exam question:

| If the question says... | Use this algorithm |
| :--- | :--- |
| "First come first served" or "FIFO queue" | **FCFS** |
| "Shortest burst first" (no preemption) | **SJF** |
| "Shortest remaining time" or "preemptive SJF" | **SRTF** |
| "Predict next burst" or "exponential averaging" | **Exponential Averaging** formula |
| "Time quantum" or "time slice" | **Round Robin** |
| "Each process has a priority number" | **Priority** |

> [!tip] Exam Checklist for Scheduling Problems
> 1. ✅ Identify the algorithm from keywords in the question
> 2. ✅ List all processes with arrival time, burst time, and priority (if applicable)
> 3. ✅ Draw the **Gantt chart** step by step
> 4. ✅ Calculate completion time for each process from the Gantt chart
> 5. ✅ Apply: Turnaround = Completion − Arrival
> 6. ✅ Apply: Waiting = Turnaround − Burst
> 7. ✅ Compute averages: Sum ÷ Number of processes
