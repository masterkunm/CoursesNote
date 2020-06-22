# Wk3 lecture

## System call

```bash
application
system libraries
    |
    |
    |   system call
    |
    V
    OS
```

* process management

* file management

...

> system call transitions triggered by special processor instruction

* system call

* return

* processor mode

* stack pointer

* program counter

* registers

## MIPS R2000/R3000

the processor control registers are located in CP0

* exception/interrupt management register
  * c0_cause, status, epc, badvaddr.



* translation management registers

* CP0 is manipulated using mtc0 (move to) and mfc0 (move from) instruction. (these two only can access in kernel mode)


![image](../../../img/3231/Screen%20Shot%202020-06-17%20at%203.09.34%20pm.png)