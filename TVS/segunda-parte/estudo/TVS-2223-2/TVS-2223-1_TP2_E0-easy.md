# Tecnicas de Virtualizacao de sistemas - Teste Parcial #2 - Exemplo 1

1. Para implementar um serviço para operar como *daemon* pondera-se receber os pedidos através de um *named pipe* (ou *fifo*, com tipo **p** no sistema de ficheiros) ou através de um *socket* de domínio Unix (tipo **s** no sistema de ficheiros) de tipo *stream*. Qual seria a principal desvantagem para o *named pipe*?

```
```

2. Um dos mecanismos previstos para comunicação entre processos (IPC) em sistemas da família Unix é a memória partilhada. No entanto, a utilização de memória partilhada geralmente implica a utilização de outros mecanismos de comunicação entre processos. Porquê?

```
```

3. Um serviço *systemd* pode estar: *enabled*, *disabled*, *active*, *inactive*.
    1. O que indica cada um destes quatro estados?

    ``` 
    ```

    2. Indique os pares destes quatro estados que são legítimos de ocorrer (compatíveis entre si).

    ```
    ```

4. No âmbito do *systemd*, explique sucintamente o que é um ficheiro de unidade do tipo **.socket** e o que se entende por *socket activation*.

```
```

5. Explique sucintamente o que se entende por paravirtualização e qual a sua principal desvantagem.

```
```

6. Explique sucintamente o que se entende por máquinas virtuais de processo. Dê exemplos práticos da utilização deste tipo de virtualização no cenário particular do *set* de instruções da arquitetura do *host* ser distinto do existente no ambiente virtualizado.

```
```

7. Comente a seguinte afirmação: 
> *«Um dos custos incontornáveis do sistema de contentores Docker é o de manter múltiplas versões do kernel Linux para que, por exemplo, as imagens baseadas em Ubuntu 22.04 usem o kernel 5.15 enquanto as imagens baseadas em Red Hat Enterprise Linux 8 precisam do kernel 4.18.»*

```
```

8. Considere a operação **docker build** guiada por um **Dockerfile**.

    1. Que condições dão origem a uma nova camada de *overlay* na imagem resultante do *build*?

    ```
    
    ```

    2. Na reconstrução de uma imagem, que condições permitem o reaproveitamento das imagens intermédias (em *cache*) do *build* anterior?

    ```
    ```

9. Um ficheiro **docker-compose.yml**, para especificação de uma solução composta com o nome **tp2**, contém três serviços: **svca**, **svcb** e **svcc**, todos colocados na mesma rede, **svcnet**, de tipo **bridge**. Os serviços **svca** e **svcc** têm apenas uma instância cada um, mas o serviço **svcb** foi lançado com **scale=4**. Executando um *shell* (/bin/sh) no contentor do serviço **svca**, qual é a diferença observável entre executar **ping svcb** ou **ping tp2-svcb-1** ?

```
```
