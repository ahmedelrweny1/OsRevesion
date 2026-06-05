# Memory Management (Brief Overview)

## What is Memory Management?
Memory management is the functionality of an operating system which handles or manages primary memory. It moves processes back and forth between main memory and disk during execution.

## Key Responsibilities
1. **Tracking:** Keeping track of each and every memory location, regardless of either it is allocated to some process or it is free.
2. **Protection & Isolation:** Ensuring that processes cannot access each other's memory unless explicitly shared.
3. **Allocation:** Deciding which process will get memory at what time and how much.
4. **Translation:** Mapping logical addresses (used by the CPU) to physical addresses (actual RAM locations) using the Memory Management Unit (MMU).

## Paging and Virtual Memory
* **Paging:** A memory management scheme that eliminates the need for contiguous allocation of physical memory. Physical memory is divided into fixed-size blocks called **frames**, and logical memory is divided into blocks of the same size called **pages**.
* **Virtual Memory:** A technique that gives the illusion of a very large main memory. It allows the execution of processes that are not completely in memory by swapping pages in and out of the disk (Demand Paging).

> [!tip] Key Concept
> Virtual memory allows programs to be larger than actual physical RAM, providing flexibility and better system utilization.
