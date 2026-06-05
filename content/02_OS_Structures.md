# OS Structures & System Calls

## Operating System Services
An operating system provides an environment for the execution of programs and services to programs and users. Core OS services include:
1. **User Interface:** Almost all operating systems have a user interface (CLI, GUI, or Batch).
2. **Program Execution:** The system must be able to load a program into memory, run it, and end its execution (normally or abnormally).
3. **I/O Operations:** A running program may require I/O (files or devices).
4. **File-System Manipulation:** Programs need to read, write, create, and delete files and directories.
5. **Communications:** Processes may exchange information via shared memory or message passing.
6. **Error Detection:** The OS must constantly be aware of possible errors in CPU, memory, I/O devices, or user programs and take appropriate action.
7. **Resource Allocation:** For simultaneous jobs, resources (CPU cycles, memory, file storage) must be allocated.
8. **Accounting:** Keeping track of which users use how much and what kinds of computer resources.
9. **Protection and Security:** Controlling access to system resources and defending against external I/O devices.

---

## System Calls
**System calls** provide the programming interface to the services provided by the OS. 
* They are typically written in high-level languages like C or C++.
* They are mostly accessed by programs via a high-level **Application Programming Interface (API)** rather than direct system call use.

> [!tip] API vs System Call
> An API function may internally invoke multiple system calls on behalf of the programmer, abstracting away the low-level details.

### System Call Implementation
* A number is associated with each system call.
* The system-call interface maintains a table indexed according to these numbers.
* The system call interface invokes the intended system call in the OS kernel and returns the status of the system call and any return values.
* The caller needs to know nothing about how the system call is implemented.

---

## Types of System Calls
System calls can be grouped roughly into six major categories:

1. **Process Control:**
   * Create process, terminate process
   * End, abort
   * Load, execute
   * Get/set process attributes
   * Wait for time, wait event, signal event
   * Allocate and free memory
2. **File Management:**
   * Create file, delete file
   * Open, close
   * Read, write, reposition
   * Get/set file attributes
3. **Device Management:**
   * Request device, release device
   * Read, write, reposition
   * Get/set device attributes
   * Logically attach or detach devices
4. **Information Maintenance:**
   * Get/set time or date
   * Get/set system data
   * Get/set process, file, or device attributes
5. **Communications:**
   * Create, delete communication connection
   * Send, receive messages
   * Transfer status information
   * Attach or detach remote devices
6. **Protection:**
   * Control access to resources
   * Get/set permissions
   * Allow/deny user access
