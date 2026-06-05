# Deadlocks (Brief Overview)

## What is a Deadlock?
A **deadlock** is a situation where a set of processes are blocked because each process is holding a resource and waiting for another resource acquired by some other process in the set.
Since no process can proceed, they remain stuck indefinitely.

## The Four Necessary Conditions
For a deadlock to occur, **all four** of the following conditions must hold simultaneously:

1. **Mutual Exclusion:** At least one resource must be held in a non-sharable mode. Only one process can use the resource at any given time.
2. **Hold and Wait:** A process is holding at least one resource and is waiting to acquire additional resources held by other processes.
3. **No Preemption:** Resources cannot be forcibly taken away from a process; a resource can be released only voluntarily by the process holding it.
4. **Circular Wait:** There exists a circular chain of processes, where each process is waiting for a resource held by the next process in the chain.

## Handling Deadlocks
Operating systems typically handle deadlocks in one of four ways:
1. **Prevention:** Structuring the system to ensure that at least one of the four necessary conditions cannot hold.
2. **Avoidance:** The OS uses an algorithm (like the Banker's Algorithm) to assess whether granting a resource will leave the system in a "safe state."
3. **Detection and Recovery:** Letting deadlocks occur, detecting them, and taking action to recover (such as terminating a process or preempting resources).
4. **Ignorance:** The OS ignores the problem altogether and assumes deadlocks rarely happen. (This is the approach taken by most modern operating systems like Windows and Linux).
