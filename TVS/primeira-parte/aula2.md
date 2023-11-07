# Aula 2 - Processos

## Um Processo contém

- Espaço de endereçamento virtual
- 1 ou mais fios de execução (threads)
- tabela de descritores de ficheiros
- (e mais...)

example:

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    write(1, "Hello World!\n", 13); // 1 = stdout, base unix write

    puts("DONE!"); // also writes to stdout 
    return 0;
}
```

other example:

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    write(1, "prog1 running!\n", 13); // 1 = stdout, base unix write

    int res = write(3, "Hello, World\n", 13); // 3 = file descriptor 3
    if (res == -1){
        perror("write to 3 failed") 
    } else {
        printf("write to 3 succeeded");
    }
    puts("DONE!"); // also writes to stdout 
    return 0;
}
```
