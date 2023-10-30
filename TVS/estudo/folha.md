# Coisas a por na folha

range de bits e o que significam

bits relevantes das tabelas

file descriptor table   

## Redirection

* The redirection is a way to **connect the output of one command to a file**;
* It is done using the `>` character;
* It is possible to connect the input of a command to a file using the `<` character;
* Examples:

```bash
$ cat abc.txt > def.txt  # Redirects the output of cat abc.txt to def.txt
...
$ cat < abc.txt          # Redirects the input of cat to abc.txt
...
# Executes the program and redirects the stdout to the file out.txt
$ ./a.out > out.txt # Its the same as ./a.out 1> out.txt
...
$ ./a.out 2> error.txt # Redirects the stderr to the file out.txt
...
$ ./a.out 3>&1 # Redirects the file descriptor 3 to the file descriptor 1
...
$ ./a.out 1> result.txt 2>&1 # Redirects the stdout and stderr to the file result.txt
```

dup vs dup2

fork and how it works
getpid - get process id
geppid - get parent pid
wait function

exec family of functions 
exec is a sys call function that replaces the current process with a new one
execlp - exec with a list of arguments
execvp - exec with a vector of arguments
execve - exec with a vector of arguments and environment variables
file permissions
open and the flags
read and write 
pipe and their functions
kill process
root directories
privilege levels
protection bits
system calls
process memory consumption

segmentation fault and exceptions.

