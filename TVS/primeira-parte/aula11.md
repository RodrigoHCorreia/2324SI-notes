# Inter-process Communication (IPC)

## Pipe

Half-duplex communication between two processes.
Synchronized byte buffer
**Limitations:** The processes must be related to each-other somehow in the hierarchy.

## Memory Mapping

mmap using MAP_SHARED flag, allows two processes to share the same memory.
Same limitation as pipe, and also hald-duplex.

## Shared Memory (shm)

shm_open(const char *name, int oflag, mode_t mode);
ftruncate(int fd, off_t length);
mmap(void* addr, size_t length, int prot, int flags, int fd, off_t offset);

## Named Pipes (FIFO)

mkfifo - creates a named pipe
open - opens a named pipe (works like a regular file)
unlink - removes a named pipe
read/write - reads and writes like a pipe, returning 0 when there are no more writers or readers.
unlike regular pipes, named pipes will wait for the first writer to appear before returning from the open call.
