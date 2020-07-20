# Week7 Lecture Memory management

Virtual memory space -> kernel |
--- |
T |
stack |
  |
  |
  |
shared library |
  |
BSS (heap) |
Data |
Text (code) |
  |

* dereferencing a NULL ptr (segmentation fault)

* shared pages
  * share the read only code in the physical memory in practice

## mapping (translation between vm and physical memory)

* virtual memory can have resource in disk instead of physical memory

* page fault (not in the physical memory, in disk) will trigger exception -> OS get control: context switching to make system busy -> I/O from disk to get corresponding resource back to physical memory -> switch back to the process

* referencing an invalid page triggers a page fault (an exception handled by the OS)
  * illegal address (protection error)
    * signal or kill the process
  * page not resident
    * get an empty frame
    * load page from disk
    * update page (translation) table (enter frame #, set valid bit, etc)
    * restart the faulting instruction

* page table
  * array of frame numbers (index by page number)
  * each page-table entry(PTE) also has other bits
