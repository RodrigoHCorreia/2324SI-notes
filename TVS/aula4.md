# Pipe e Sinais

## Pipes

- O **pipe** é um objeto que vive no kernel, e é tratado como se fosse um ficheiro, apesar de ser uma **byte queue** armazenada em memória.
- a chamada da função *pipe()* devolve dois descritores de ficheiros, um para leitura e outro para escrita.
  - Para retornar dois números, usa-se um array de inteiros, que é passado como argumento.
- Só podemos utilizar o pipe entre processos que partilhem um antepassado comum, ou seja, através de um *fork()*.
  - **Porém isto pode potenciar problemas de sincronização, pois podem tentar aceder ao pipe ao mesmo tempo.**
  - Para isto não acontecer, **devemos comunicar unilateralmente**, ou seja, um processo escreve e o outro lê.
  - Se quisermos comunicar **bilateralmente**, devemos criar dois pipes, um para cada sentido.
  - **Para fecharmos as fias, devemos fazer close() dos descritores de ficheiros que não vamos utilizar.**
  - Ao fecharmos o descritor de escrita, o descritor de leitura devolve 0.


```c
int main() {
    puts("prog07a running");

    int pipefd[2];
    pipe(pipefd);

    write(pipefd[1], "Hello, World!\n", 13);

    //sleep(5); unneeded

    char msg[14];
    int n = read(pipefd[0], msg, 13);
    msg[n] = 0;

    puts(msg);
}
```

>  $? - indica o status code do último comando executado

## Sinais

- 