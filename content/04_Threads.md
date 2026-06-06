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

### User Threads
**User threads** — management is done by a **user-level thread library**. The OS kernel doesn't know about them.

Three primary thread libraries:
* **POSIX Pthreads**
* **Windows threads**
* **Java threads**

### Kernel Threads
**Kernel threads** — supported directly by the **Kernel**. The kernel manages thread creation, scheduling, and management.

Examples — virtually all general purpose operating systems support kernel threads, including:
* **Windows**
* **Solaris**
* **Linux**
* **Tru64 UNIX**
* **Mac OS X**

> [!important] Key Difference
> User threads are managed in user space without kernel involvement, which is fast but limited. Kernel threads are managed by the OS kernel, providing true parallelism on multicore systems but with more overhead for thread operations.

---

## Multithreading Models
These models describe how user threads are mapped to kernel threads:

1. **Many-to-One Model:** 
   * Many user threads map to a single kernel thread.
   * One thread blocking causes all to block.
   * Multiple threads may not run in parallel on multicore systems because only one may be in kernel at a time.
   * Few systems currently use this model.
   * *Examples:* Solaris Green Threads, GNU Portable Threads.
2. **One-to-One Model:** 
   * Each user thread maps to its own kernel thread.
   * Creating a user-level thread creates a kernel thread.
   * More concurrency than many-to-one.
   * Number of threads per process sometimes restricted due to overhead.
   * *Examples:* Windows, Linux, Solaris 9 and later.
3. **Many-to-Many Model:** 
   * Many user threads map to many kernel threads (flexible mapping).
   * Allows the operating system to create a sufficient number of kernel threads.
   * *Examples:* Solaris prior to version 9, Windows with the ThreadFiber package.

---

## Multitasking in Mobile Systems
Mobile operating systems handle multitasking differently from desktop systems due to screen size and resource constraints.

### iOS Multitasking
* Some mobile systems (e.g., early versions of iOS) allowed only **one process to run**, while others were suspended.
* Due to screen real estate, user interface limits iOS provides for a:
  * **Single foreground process** — controlled via user interface
  * **Multiple background processes** — in memory, running, but not on the display, and with limits
* Background process limits include: single, short task; receiving notification of events; specific long-running tasks like audio playback.

### Android Multitasking
* Android runs **foreground and background** processes, with **fewer limits** than iOS.
* Background process uses a **service** to perform tasks.
* Service can keep running even if the background process is suspended.
* Service has **no user interface** and uses **small memory**.

> [!tip] Key Comparison
> iOS is more restrictive with background processes to save battery and resources, while Android is more permissive, using services to enable background work even when processes are suspended.

---

## Thread Libraries & Implicit Threading
A thread library provides the programmer with an API for creating and managing threads.

### Two Primary Implementation Approaches
* **Library entirely in user space** — no kernel involvement
* **Kernel-level library** supported by the OS

### Main Thread Libraries

#### Pthreads (POSIX Threads)
* A **POSIX standard** (IEEE 1003.1c) API for thread creation and synchronization.
* It is a **specification**, not an implementation — the API specifies behavior; implementation is up to each system.
* May be provided either as user-level or kernel-level.
* Common in UNIX operating systems: Solaris, Linux, Mac OS X.
* Key functions: `pthread_create()`, `pthread_join()`, `pthread_exit()`

#### Windows Threads
* Windows provides its own thread API using `CreateThread()`, `WaitForSingleObject()`, and `CloseHandle()`.

#### Java Threads
* Java threads are managed by the **JVM**.
* Typically implemented using the thread model provided by the underlying OS.
* Java threads may be created by:
  * Extending the **Thread** class
  * Implementing the **Runnable** interface

### Implicit Threading
As programs use more threads, managing them manually becomes complex and error-prone. **Implicit threading** means the system (compiler or library) handles threads automatically instead of the programmer doing it manually. It hides the complexity of thread management.

> [!important] Why Implicit Threading?
> As the number of threads grows, so does the difficulty of correctly managing them. Implicit threading transfers the responsibility of thread creation and management from the programmer to compilers and run-time libraries.
