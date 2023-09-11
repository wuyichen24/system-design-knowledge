# Program, Process and Thread

## Program
- **Concepts**
   - An executable file containing a set of instructions and passively stored on disk.

## Process
- **Concepts**
   - A program is in execution.
   - When a program is loaded into the memory and becomes active, the program becomes one or multiple processes.
- **Characteristics**
   - Processes are usually independent.
   - Each process has its own memory space.
   - A process is a heavyweight operation. It takes more time to create and terminate.
   - Context switching is more expensive between processes.
- **Inter-process communication**

## Thread
- **Concepts**
   - The smallest unit of execution within a process.
- **Characteristics**
   - There is no universal fixed limit for the number of threads in a process.
   - Threads that belong to the same process share the same memory, data structures and variables.
- **Inter-thread communication**
