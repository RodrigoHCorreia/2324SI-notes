# Privelege Levels

- Processor provided
- Usually at least 2
- User mode (non-priveleged level)
- Kernel/Supervisor mode (Privileged level)

## Why do we need privelege levels?

- We want to protect the OS from user programs
- In kernel mode every instruction is allowed
- In user mode, some operations are forbidden or restricted

![Proccess Virtual Address Space](<proccess_virtual_address_space.jpg>)

- This is for example how we can touch hardware devices, by mapping them to a specific address in the virtual address space.

Some of the user mode restrictions are:

- Some addresses are inaccessible, and this is enforced by the system itself.
- With **intel** processors the `in` and `out` instructions to read and write to hardware devices
- inaccessible registers (e.g. x86-64: idtr, `CR3`, msr)
  - idtr: interrupt descriptor table register
  - msr: model specific register
  - cr3: control register 3 - this is the register that holds the address of the page table.

- Attending interupts (usually) requires changing privilege level
- Classic system calls performed with software interrupts
  - One interrupt line record for system calls
  - Linux: int 0x80
  - Windows: int 0x2e

When performing a system call we need to place the system call number in a specific register, and the system call number is documented in the OS documentation.
The arguments are also placed in registers.

## Assembly

_start: - entry point of the program
    - put 0's in the bss section
    - malloc memory for the stack etc.
    - etc.
main: - the main function

**<https://chromium.googlesource.com/chromiumos/docs/+/master/constants/syscalls.md>**

hello-sys.s

```c
    .text
    .global_start
_start:
    # write(1, msg, 14);

    movq $14, %rdx # length of msg
    leal msg(%rip), %rsi # address of msg
    movq $1, %rdi # file descriptor
    movq $1, %rax # system call number
    syscall

    # exit(0);
    xorq %rdi, %rdi # exit code
    movq $60, %rax # system call number
    syscall

msg: ascii "Hello, world!\n" # we do this here and not in the data section because with data section we needed 4kB of memory to be allocated for the data section, and here we only need 14 bytes.

    .end
```

> how to compile: as -o hello-sys.o hello-sys.s
> how to link: ld -o hello-sys hello-sys.o

## IA-32

**Virtual Address:**

- 32 bits
  - 10 bits PDI (page directory index)
  - 10 bits PTI (page table index)
- 12 bits offset

Every process has one Page directory table, and this page directory table has 1024 entries, and each entry points to a page table.
