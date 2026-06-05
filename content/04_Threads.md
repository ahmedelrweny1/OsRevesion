# Threads & Concurrency

## What is a Thread?
A **thread** is the smallest unit of execution inside a program that the operating system can schedule and run. Simply put, a thread is a path of execution inside a process.

| Feature | Process | Thread |
|---------|---------|--------|
| **Definition** | A running program with its own separate memory. | A smaller unit inside a process that shares memory with other threads. |
| **Weight** | Heavyweight — requires full OS resources. | Lightweight — shares resources of parent process. |
| **Communication** | Via shared memory or message passing (complex). | Via shared memory directly (simple & fast). |
| **Context Switch** | Expensive and slow. | Thread switch has much lower overhead. |

> [!tip] Analogy
> Think of a process as a factory (the whole application), and threads as the individual workers inside it.

---

## Why Do We Use Threads?
Threads are primarily used for:
* **Parallelism:** Performing more than one task at the same time.
* **Better performance & Faster application response.**
* **Improving user experience:** For example, in a web browser, one thread downloads a file in the background while the main thread keeps the user interface responsive and clickable.

### The 4 Major Benefits of Threads
1. **Responsiveness:** Threading allows continued execution if part of a process is blocked (crucial for UIs).
2. **Resource Sharing:** Threads inherently share the memory and resources of the process they belong to. No need to copy data or use complex IPC.
3. **Economy:** Thread creation is cheaper than process creation. Context-switching between threads is much faster.
4. **Scalability:** Threads can run truly in parallel across multiple CPU cores on multiprocessor architectures.

---

## Multithreaded Server Architecture
In a multithreaded server, each incoming client request is handled by a dedicated thread:
1. Client sends a request to the server.
2. Server creates a new thread specifically to service that request.
3. Server immediately resumes listening for additional client requests.

---

## Multicore Programming
Multicore systems introduce two key concepts:
* **Concurrency:** More than one task makes progress (can happen on a single core via a scheduler).
* **Parallelism:** A system performs multiple tasks simultaneously (requires multiple cores).

### Types of Parallelism
* **Data Parallelism:** Distributes subsets of the *same data* across multiple cores, performing the *same operation* on each (e.g., splitting a 1000-item array across 4 threads).
* **Task Parallelism:** Distributes *different threads* across cores, each performing a *unique operation* (e.g., one thread renders UI, another handles the network).

### The 5 Challenges of Multicore Programming
1. **Dividing Activities:** Breaking the program into smaller independent tasks.
2. **Balance:** Ensuring work is evenly distributed so no CPU core sits idle.
3. **Data Splitting:** Data must be divided correctly so each thread works on its own part.
4. **Data Dependency:** Managing tasks that depend on results from other tasks.
5. **Testing & Debugging:** Bugs like race conditions and deadlocks are hard to reproduce.

---

## User Threads vs Kernel Threads
* **User Threads:** Management is done by a user-level thread library (e.g., POSIX Pthreads, Windows threads, Java threads). The OS kernel doesn't know about them.
* **Kernel Threads:** Supported directly by the kernel. Almost all general-purpose OSes support them (Windows, Linux, macOS).

---

## Multithreading Models
These models describe how user threads are mapped to kernel threads:

1. **Many-to-One Model:** 
   * Many user threads map to a single kernel thread.
   * *Pros:* Simple to implement.
   * *Cons:* One blocking thread blocks ALL threads; no true parallelism on multicore systems.
2. **One-to-One Model:** 
   * Each user thread maps to its own kernel thread.
   * *Pros:* More concurrency; one blocking thread doesn't affect others.
   * *Cons:* Creating a user thread requires creating a kernel thread, adding overhead.
3. **Many-to-Many Model:** 
   * Many user threads map to a smaller or equal number of kernel threads.
   * *Pros:* Best flexibility; OS creates sufficient kernel threads.

---

## Thread Libraries & Implicit Threading
A thread library provides the programmer with an API for creating and managing threads. The three main libraries are:
* **Pthreads (POSIX Threads):** A standard specification (not an implementation).
* **Windows Threads:** Managed by the Windows OS.
* **Java Threads:** Managed by the JVM.

### Implicit Threading
As programs use more threads, managing them manually becomes complex and error-prone. **Implicit threading** means the system (compiler or library) handles threads automatically instead of the programmer doing it manually. It hides the complexity of thread management.
