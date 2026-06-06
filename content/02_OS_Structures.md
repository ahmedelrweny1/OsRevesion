# OS Structures & System Calls

## Operating System Services
An operating system provides an environment for the execution of programs and services to programs and users. Core OS services include:
1. **User Interface:** Almost all operating systems have a user interface (CLI, GUI, or Batch).
2. **Program Execution:** The system must be able to load a program into memory, run it, and end its execution (normally or abnormally).
3. **I/O Operations:** A running program may require I/O (files or devices).
4. **File-System Manipulation:** Programs need to read, write, create, and delete files and directories, search them, list file information, and manage permissions.
5. **Communications:** Processes may exchange information, on the same computer or between computers over a network. Communications may be via shared memory or through message passing (packets moved by the OS).
6. **Error Detection:** The OS must constantly be aware of possible errors in CPU, memory hardware, I/O devices, or user programs. For each type of error, the OS should take the appropriate action to ensure correct and consistent computing. Debugging facilities can greatly enhance the user's and programmer's abilities to efficiently use the system.

### Services for System Efficiency
Another set of OS functions exists for ensuring the efficient operation of the system itself via resource sharing:
7. **Resource Allocation:** When multiple users or multiple jobs are running concurrently, resources must be allocated to each of them. Many types of resources include CPU cycles, main memory, file storage, and I/O devices.
8. **Accounting:** Keeping track of which users use how much and what kinds of computer resources.
9. **Protection and Security:** The owners of information stored in a multiuser or networked computer system may want to control use of that information. Concurrent processes should not interfere with each other.

---

## User Operating System Interface - GUI
* **User-friendly desktop metaphor interface**
* Usually involves mouse, keyboard, and monitor
* Icons represent files, programs, actions, etc.
* Various mouse buttons over objects in the interface cause various actions (provide information, options, execute function, open directory known as a folder)
* Invented at **Xerox PARC**

### Systems with Both CLI and GUI
* **Microsoft Windows** is GUI with CLI "command" shell
* **Apple Mac OS X** is "Aqua" GUI interface with UNIX kernel underneath and shells available
* **Unix and Linux** have CLI with optional GUI interfaces (CDE, KDE, GNOME)

---

## System Calls
**System calls** provide the programming interface to the services provided by the OS. 
* They are typically written in high-level languages like C or C++.
* They are mostly accessed by programs via a high-level **Application Programming Interface (API)** rather than direct system call use.

> [!tip] API vs System Call
> An API function may internally invoke multiple system calls on behalf of the programmer, abstracting away the low-level details.

### Example of System Calls
A system call sequence to copy the contents of one file to another file involves multiple system calls for: acquiring file names, opening source file, creating destination file, reading from source, writing to destination, closing files, and handling errors at each step.

### System Call Implementation
* A number is associated with each system call.
* The **system-call interface** maintains a table indexed according to these numbers.
* The system call interface invokes the intended system call in the OS kernel and returns the status of the system call and any return values.
* The caller needs to know nothing about how the system call is implemented.
* Just needs to obey the API and understand what the OS will do as a result of the call.
* Most details of OS interface are hidden from the programmer by the API.
* Managed by **run-time support library** (set of functions built into libraries included with compiler).

### System Call Parameter Passing
Often, more information is required than simply the identity of the desired system call. The exact type and amount of information vary according to the OS and the specific call.

> [!tip] Parameter Passing Methods
> Three general methods are used to pass parameters to the OS:
> 1. **Registers** — Pass parameters directly in CPU registers (simplest, but limited by number of registers)
> 2. **Block/Table** — Parameters stored in a block or table in memory, and the address of the block is passed as a parameter in a register
> 3. **Stack** — Parameters pushed onto the stack by the program and popped off by the OS

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
   * Dump memory if error
   * Debugger for determining bugs, single step execution
   * Locks for managing access to shared data between processes
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
   * Send, receive messages if message passing model to host name or process name
   * From client to server
   * Shared-memory model create and gain access to memory regions
   * Transfer status information
   * Attach and detach remote devices
6. **Protection:**
   * Control access to resources
   * Get/set permissions
   * Allow/deny user access

---

## Standard C Library Example
A C program invoking `printf()` library call, which internally calls the `write()` system call. This demonstrates how user programs interact with the OS through library functions rather than making direct system calls.

---

## Examples: MS-DOS vs FreeBSD

### MS-DOS
* **Single-tasking** operating system
* Shell invoked when system booted
* Simple method to run a program — **no process created**
* **Single memory space** — loads program into memory, overwriting all but the kernel
* Program exit → shell reloaded

### FreeBSD (Unix Variant)
* **Multitasking** operating system
* User login → invoke user's choice of shell
* Shell executes `fork()` system call to create process
* Executes `exec()` to load program into process
* Shell waits for process to terminate or continues with user commands
* Process exits with:
  * `code = 0` → no error
  * `code > 0` → error code

> [!tip] Key Difference
> MS-DOS is single-tasking with no process concept, while FreeBSD uses multitasking with `fork()` and `exec()` to manage processes — a fundamental UNIX design pattern.

---

## System Programs
System programs provide a convenient environment for program development and execution. Some of them are simply user interfaces to system calls; others are considerably more complex.

> [!important] User's View
> Most users' view of the operating system is defined by system programs, not the actual system calls.

System programs can be divided into:

1. **File Management:**
   * Create, delete, copy, rename, print, dump, list, and generally manipulate files and directories

2. **Status Information:**
   * Some ask the system for info — date, time, amount of available memory, disk space, number of users
   * Others provide detailed performance, logging, and debugging information
   * Typically, these programs format and print the output to the terminal or other output devices
   * Some systems implement a **registry** — used to store and retrieve configuration information

3. **File Modification:**
   * Text editors to create and modify files
   * Special commands to search contents of files or perform transformations of the text

4. **Programming-Language Support:**
   * Compilers, assemblers, debuggers, and interpreters sometimes provided

5. **Program Loading and Execution:**
   * Absolute loaders, relocatable loaders, linkage editors, and overlay-loaders
   * Debugging systems for higher-level and machine language

6. **Communications:**
   * Provide the mechanism for creating virtual connections among processes, users, and computer systems
   * Allow users to send messages to one another's screens, browse web pages, send electronic-mail messages, log in remotely, transfer files from one machine to another

7. **Background Services:**
   * Launch at boot time
   * Some for system startup, then terminate
   * Some from system boot to shutdown
   * Provide facilities like disk checking, process scheduling, error logging, printing
   * Run in user context not kernel context
   * Known as **services**, **subsystems**, **daemons**

8. **Application Programs:**
   * Don't pertain to system
   * Run by users
   * Not typically considered part of OS
   * Launched by command line, mouse click, finger poke
