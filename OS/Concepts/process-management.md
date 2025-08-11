# Process Management

A process is basically a program in execution — it’s a running instance of some code along with everything it needs to run.

- A program is just a set of instructions stored on disk (inactive).
- A process is when the OS loads that program into memory and starts executing it.

## Program vs Process

| **Aspect**               | **Program**                                                                               | **Process**                                                         |
| ------------------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------- |
| **Definition**           | A **passive** collection of instructions stored on disk (like `.exe`, `.py`, `.c` files). | An **active** instance of a program in execution.                   |
| **State**                | Static (does nothing until executed).                                                     | Dynamic (has a life cycle — created, running, waiting, terminated). |
| **Storage Location**     | Stored in **non-volatile storage** (HDD, SSD).                                            | Loaded into **RAM** during execution.                               |
| **Lifespan**             | Exists until deleted from disk.                                                           | Exists until the program finishes or is stopped.                    |
| **Needs OS Management?** | No — it’s just a file.                                                                    | Yes — OS allocates CPU time, memory, and resources.                 |
| **Example**              | `chrome.exe` file on disk.                                                                | The running Chrome browser you’re using right now.                  |

> **Analogy**: Think of a program as a recipe written in a cookbook — it just sits there until someone decides to cook. <br> A process is you actually cooking the dish using the recipe, using resources like a stove, ingredients, and utensils.

## What makes up a process?

When a process is running, it’s not just the code. It includes:

- **Program Code (Text Section)** – The actual instructions to execute.
- **Program Counter (PC)** – Keeps track of which instruction to execute next.
- **Stack** – Stores temporary data like function calls, parameters, and local variables.
- **Heap** – Stores dynamically allocated memory during runtime.
- **Data Section** – Stores global and static variables.
- **Registers** – Small, fast storage in the CPU holding current working data.
- **Process Control Block (PCB)** – A data structure maintained by the OS that stores:
    - Process ID (PID)
    - State (Running, Ready, Waiting, etc.)
    - CPU registers
    - Scheduling information
    - Memory management info
    - I/O status

## States of Process

A process doesn’t always run — it moves between states

- New – Process is being created.
- Ready – Waiting for CPU time.
- Running – Currently executing instructions.
- Waiting (Blocked) – Waiting for some event (like I/O completion).
- Terminated – Finished execution.

<!-- Img for states flow -->

## Context Switching

Context Switching is when the CPU pauses one process and switches to another, saving the state of the first so it can resume later exactly where it left off

This is necessary because:
- The CPU is much faster than I/O devices.
- Multiple processes need to share CPU time (multitasking).
- It gives the illusion that all processes are running at once (time-sharing).

> Analogy: Imagine you’re reading Book A but get interrupted to read Book B. <br> You bookmark your page in Book A (save state) → pick up Book B where you left off (load state) → later return to Book A at the bookmark.

### How it Works ? 

When switching from Process A to Process B:

- Save State of Process A
    - The OS stores all important information about Process A in its Process Control Block (PCB):
    - CPU registers
    - Program counter (next instruction)
    - Memory management info
    - Open files, etc.
- Load State of Process B
    - The OS retrieves Process B’s saved state from its PCB.
    - Restores CPU registers and program counter.
- Start Execution of Process B
    - CPU resumes Process B from where it was last paused.

### When Does Context Switching Happen ?

- Time slice expiry (in Round Robin scheduling)
- I/O wait (process waiting for data from disk/network)
- Higher priority process arrives
- System calls (process requests OS service)
- Interrupts (hardware signals CPU)

### Overhead

- Context switching takes time (no useful work is done during the switch).
- Too many switches → thrashing (system spends more time switching than running processes).