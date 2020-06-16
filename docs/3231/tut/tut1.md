# Tutorial Week 2

email: z5210220

## Operating Systems Intro

### Q1 What are some of the differences between a processor running in privileged mode (also called kernel mode) and user mode? Why are the two modes needed?

1. user mode can't make dirct system call while kernel mode can.

2. kernel mode can interact with hardware while user mode can't.

### Q2 What are the two main roles of an Operating System?

1. intermediate between user and hardware.

2. resource allocator and dispatch.

### Q3 Given a high-level understanding of file systems, explain how a file system fulfills the two roles of an operating system?

1. if user want to use a program, just run the file then operating system will do the rest of the work.

2. Operating system is responsible for loading the machine code from file to memory to create a process, and dispatch the process to run.

### Q4 Which of the following instructions (or instruction sequences) should only be allowed in kernel mode?

1. *Disable all interrupts.*
2. *Read the time of day clock.*
3. *Set the time of day clock.*
4. *Change the memory map.*
5. *Write to the hard disk controller register.*
6. *Trigger the write of all buffered blocks associated with a file back to disk (fsync).*

**MyAnswer: 1, 3, 4, 5, 6**

## OS system call interface

### Q5 The following code contains the use of typical UNIX process management system calls: fork(), execl(), exit() and getpid(). If you are unfamiliar with their function, browse the man pages on a UNIX/Linux machine get an overview, e.g: man fork

*Answer the following questions about the code below.*

*What is the value of i in the parent and child after fork.
What is the value of my_pid in a parent after a child updates it?
What is the process id of /bin/echo?
Why is the code after execl not expected to be reached in the normal case?
How many times is Hello World printed when FORK_DEPTH is 3?
How many processes are created when running the code (including the first process)?*

**MyAnswer: **

```cpp
#include <sys/types.h>
#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>

#define FORK_DEPTH 3

main()
{
  int i, r;
  pid_t my_pid;

  my_pid = getpid();
  
  for (i = 1; i <= FORK_DEPTH; i++) {

    r = fork();

    if (r > 0) {
      /* we're in the parent process after
         successfully forking a child */

      printf("Parent process %d forked child process %d\n",my_pid, r);  

    } else if (r == 0) {

      /* We're in the child process, so update my_pid */
      my_pid = getpid();

      /* run /bin/echo if we are at maximum depth, otherwise continue loop */
      if (i == FORK_DEPTH) { 
        r = execl("/bin/echo","/bin/echo","Hello World",NULL);

        /* we never expect to get here, just bail out */
        exit(1);
      }
    } else { /* r < 0 */
      /* Eek, not expecting to fail, just bail ungracefully */
      exit(1);
    }
  }
}
```