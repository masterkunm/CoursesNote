# WK2 Part1 deadlock, part2 MIPS, implementation of threads and processes, context switching

## **deadlock**

* what

* how it occur

* several approaches to prevent and fix

e.g

```cpp
semaphore res_1, res_2;

void proc_A() {
    Down(&res_1);
    Down(&res_2);
    // do something
    up(&res_2);
    up(&res_1);
}

void proc_B() {
    Down(&res_2);
    Down(&res_1);
    // do something
    up(&res_1);
    up(&res_2);
}
```

* condition to occur

    1. mutual exclusion conditoin

    2. hold and wait condition (hold resources also can request additional one)

    3. no preemption condition (assure the holding resource won't be taken)

    4. circular wait condition

## strategies for dealing with deadlocks

1. ignore the problem altogether

    * the ostrich algorithm (deadlock occurs rarely)

2. prevention

    * deadlock prevention (prevent one of the four conditions required for deadlock)
    * this strategy easily leads to live-lock (live-lock processes are not blocked, change state regularly, but never make progress)

3. detection and recovery

    * detection with one resource of each type (a cycle can be found within the graph, denoting deadlock)

4. dynamic avoidance (careful resource allocation)

    * enough information required

### safe and unsafe state

* safe
  * system is not deadlocked
  * there is a scheduling order that results in every process running to completion, even if they all request the maximum resources

* unsafe
  * cannot guarantee that the unsafe state won't have deadlock

### **Bankers Algorithm**

## Starvation

a process never receive the resource it is waiting for.

### solution -> first come, first serve

----------

## MIPS R3000

load/store instruction

arithmetic and logical operations

**all instructions are encoded in 32bits, some instructions have immediate operands. Immediate values are constants encoded in the instruction itself, only 16-bit value**.

### MIPS register

* 32 general purpose registers
  * r0 -> 0
  * r31 link register for jump and link instruction

* HI/LO

* PC
  * not directly visible
  * modified implicitly by jump and branch instructions

### branching and jumping

__the (one) instruction following the jumping and branching will executed prior to destination of jump. (branch and jump delay slot)__

__instruction partially through pipeline prior to jmp having an effect__

![image](../../../img/3231/Screen%20Shot%202020-06-17%20at%203.09.34%20pm.png)

> 5 stage pipeline is how hardware developer designed it for speed

### JAL

r31 = PC + 8

RA is used to return from function call

### compiler register conventions

![image1](../../../img/3231/Screen%20Shot%202020-06-17%20at%203.20.12%20pm.png)

#### a factorial example

![image2](../../../img/3231/Screen%20Shot%202020-06-17%20at%203.36.43%20pm.png)

## process and thread

each thread has its own stack.

* user level thread

* kernel level thread

## context switch

* switch between threads

* switch between processes

can happened by:

1. on a system call

2. on an exception

3. on an interrupt

4. between instructions

## **note**

**in assignment, don't use recursion, because the memory in os161 only about 4K**.
