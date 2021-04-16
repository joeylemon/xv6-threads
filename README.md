# xv6-threads

This is a copy of the [xv6 repository](https://github.com/mit-pdos/xv6-public) which implements real kernel threads in xv6, including the addition of clone and join functions which create the foundation for a thread library that defines the thread_create, thread_join, lock_init, lock_acquire, and lock_release functions.

This project was assigned in COSC361 Operating Systems taught by Dr. Micah Beck, as an assignment from the [OSTEP](https://github.com/remzi-arpacidusseau/ostep-projects) textbook.

## Changes to implement feature

### Makefile
The makefile had to be edited to add the new user programs to test the creation of threads and the concurrent execution of code. The forktest program had to be removed to get rid of errors involving malloc.

### defs.h
The declarations for clone and join were created in this file.

### proc.c
The code definitions for clone and join were added to this file. The clone function sets up a new process with the given stack arguments, and the join function scans the process table looking for a zombie child and clears them out.

### proc.h
A new property was added to the process data structure to mark the address of the thread stack, titled *threadstack.

### syscall.c
The declarations for the new functions sys_clone() and sys_join() were added to this file.

### syscall.h
This system call numbers were assigned to the new functions sys_clone() and sys_join().

### sysproc.c
This file contains the definitions of the sys_clone() and sys_join() functions which call the definitions in proc.c.

### user.h
The declarations for the new system calls clone() and join() were added to this file, as well as the new functions thread_create(), thread_join(), lock_init(), lock_acquire(), and lock_release(). A new structure was created to define a lock.

### ulib.c
The definitions for the new functions thread_create(), thread_join(), lock_init(), lock_acquire(), and lock_release() were added to this file.

### usys.S
The declarations for the new functions clone() and join() were added to this file.

### testthreads.c
This user program tests the creation of three different threads and their usage of locks to ensure concurrency is working and thread safety is achieved via locks.
