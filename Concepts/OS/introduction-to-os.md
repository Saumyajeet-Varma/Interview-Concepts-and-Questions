# Operating System

An operating system (OS) is a software that manages computer hardware and software resources and provides common services for computer programs. It acts as an intermediary between the user and the computer hardware.

## Key Functions

- **Process Management** – Starts, stops, and schedules programs (processes) for execution.
- **Memory Management** – Allocates and frees RAM for running programs.
- **File System Management** – Creates, reads, writes, and deletes files in storage.
- **Device Management** – Controls input/output devices (keyboard, printer, etc.) via drivers.
- **Security and Access Control** – Protects data and resources from unauthorized access.
- **User Interface** – Provides GUI (Graphical User Interface) or CLI (Command Line Interface).

## Core Components of Operating System

### Kernel

- The core of the OS.
- Always running in memory.
- Directly interacts with hardware.
- Responsible for CPU scheduling, memory allocation, and device control.
- Types:
    - Monolithic Kernel (Linux) – All core services run in one large program.
    - Microkernel (Minix) – Core is small; other services run separately for better stability.
    - Hybrid Kernel (Windows, macOS) – Combination of both.

### Process Management

- The OS runs multiple programs at the same time (multitasking).
- It:
    - Creates and terminates processes.
    - Schedules which process uses the CPU.
    - Uses context switching to switch between processes in microseconds.

### Memory Management

- Keeps track of which memory is used by which process.
- Allocates/deallocates memory.
- Handles virtual memory (gives programs more memory than physically available by using disk as backup).

### File System

- Organizes data into files and directories.
- Manages reading/writing from storage devices.
- Provides permissions (who can read/write a file).

### Device Management

- Uses device drivers to talk to hardware (keyboard, mouse, printer, etc.).
- Acts as translator between applications and hardware.

### Security and Protection

- User authentication (passwords, biometrics).
- Permissions for files and devices.
- Data encryption.

## Types of Operating System

- **Batch OS** – Jobs processed in batches without user interaction (old mainframes).
- **Time-Sharing OS** – Multiple users share the system (Unix, Linux servers).
- **Real-Time OS (RTOS)** – Very fast response, used in embedded systems (aircraft, robots).
- **Distributed OS** – Manages multiple computers as one (cluster computing).
- **Mobile OS** – Android, iOS for smartphones.