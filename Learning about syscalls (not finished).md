System calls are the way a program interacts with the operating systems's kernel, they bridge the user space applications and kernel pace operations, letting programs request services like file manipulation, process management, memory allocation, and network communication. essentially they are what is handling hardware vs software and meshing those together.

**How a syscall works
1. User space vs. Kernel space:

applications run in user space with restricted access to system resources. Whereas the kernel operates in privileged mode and manages hardware and system resources.

2. Making a syscall:

* A program invokes a syscall using a library function (like `open()` in C).
* The library wraps the syscall, placing it in a form the kernel understands.
* The processor switches to kernel mode, the syscall is executed, and the control returns to the application.

**Examples of syscalls

`read` Reads data from a file or input.
`write` Writes data to a file or output
`open` Opens a file or device
`close` Closes a file or device
`fork` Creates a new process
`execve` Executes a process 
`wait` Waits for a process to change state
`exit` Terminates a process
`mmap` Maps a file or device into memory
`socket` Creates a network socket

**Example of a basic C program with syscalls

```c
#include <unistd.h>
#include <sys/syscall.h>
#include <stdio.h>

int main() {
    long result = syscall(SYS_write, STDOUT_FILENO, "Hello, syscall!\n", 16);
    printf("Syscall returned: %ld\n", result);
    return 0;
}

```

 

[[2025-01-14 (fourth day, feeling overwhelmed)]]

