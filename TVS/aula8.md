# X86-64 Continuation

- **Virtual Memory Address:**

- 12 bits offset
- 9 bits PTI (page table index)
- 9 bits PDI (page directory index)
- 9 bits PDPI (page directory pointer index)
- 9 bits PML4I (page map level 4 index)
- 16 bits unused (all are 0's or 1's depending on the last used bit in PML4I)

> 2^48 = 256TB
> This means that the maximum amount of memory that can be addressed per process is 256TB.

2^9 = 512 entries in each table that are going to be indexed by the PTI, PDI, PDPI, PML4I.

in the PTI, the 40 bits in the table entry are called PFN (page frame number), that are going to be used to access the page frame.

Every translation is stored in a cache and is going to be used in the next translation.

- **Principal of locality**: if you access a memory location, you are going to access it again in the near future.

- **Executable Files (program)**
H - admin info
.text - code (allocate as many entries as needed to fix the code in memory)
.rodata - read only data (this will also be allocated in memory with ur x flags (read and execute))
.data - initialized data ( this will also be allocated in memory with ur w flags (read and write))

the proccess needs at least a thread to run, and a thread needs a stack.

- **Stack**
- grows down

**Address space org.**

- **Initial:**

  - executable file
  - dynamic libraries
  - 1 stack(initial thread)

- **Dynamic:**

  - create new threads (needs more stack)
  - malloc(dynamic memory allocation)
  - dynamic libraries
  - memory mapping files
