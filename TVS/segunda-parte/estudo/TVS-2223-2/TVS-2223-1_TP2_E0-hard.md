# Técnicas de Virtualização de Sistemas - Teste Parcial #2 - Exemplo 2

1. O código abaixo implementa um serviço, a operar como *daemon*, para guardar e recuperar 4 *bytes*. No entanto, a forma como o *named pipe* é utilizado está fundamentalmente errada. Porquê?

    ```c
    char data[4];
        int main() {
            char req[REQ_LEN];
            umask(0111); 
            mkfifo("/tmp/tp2-req", 0666);
            int fd = open("/tmp/tp2-req", O_RDWR);
            for (;;) {
                memset(req, 0, REQ_LEN);
                int len; 
                do { 
                    len = read(fd, req, REQ_LEN); 
                } while (len == 0);
                switch (req[0]) {
                    case 'S': 
                        memcpy(data, &req[1], 4); 
                        write(fd, "OK\n", 3); 
                        break;
                    case 'G': 
                        write(fd, data, 4); 
                        break;
                    case 'Q': 
                        write(fd, "OK\n", 3); 
                        unlink("/tmp/tp2-req"); 
                        exit(0);
                    default: 
                        write(fd, "ERR\n", 4); 
                        break;
                }
            }
        }
    ```

    ```
    Um named pipe, enquanto IPC, só pode ser utilizado de forma unidirecional. Isto porque, não havendo qualquer tipo de mecanismo de sincronismo ou comunicação entre os diferentes processos, não devemos utilizá-lo para fazer comunicações bi-direccionais por possíveis condições de deadlocks. Para contornar este problema, dois named pipes devem ser utilizados, um para leitura e um para escrita.
    ``` 

2. Vários processos relacionados, comunicam através de um espaço de memória partilhada. Um dos processos aloca espaço para um objeto com **malloc**, preenche devidamente todos os campos do objeto e publica o ponteiro para o objeto na zona de memória partilhada. Há processos a tentar consultar os campos do objeto publicado e a terminar a execução com indicação de *segmentation fault*. Qual é o problema?

    ```
    O problema é que apesar do ponteiro se encontrar publicado na zona de memória partilhada, o objeto para o qual ele aponta, é referente a memória não partilhada do processo que alocou o objeto com malloc. Sendo assim, após um processo tentar consultar um campo do objeto, pelo facto de não ter acesso à região da memoria por esta ser não partilhada, irá terminar a sua execução com segmentation fault.
    ```

3. No arranque do sistema, o *systemd* precisa de determinar o conjunto de serviços em estado *enabled*. Como se determina essa informação?

    ```
    Para determinar qual o conjunto de serviços que se encontram no estado enabled, o systemd procura nas diferentes target directories, por exemplo /etc/systemd/system/multi-user.target.wants, os symlinks que se encontram lá. Esses symlinks apontam para o unit file do serviço, e quando o sistema arranca em multi-user target, vai arrancar também todos esses serviços.
    ```

4. Na definição de ficheiro de unidade para o *systemd*, é possível adicionar um serviço (especificado num ficheiro **.service**) a um target (especificado num ficheiro **.target**) sem editar, <u>direta ou indiretamente</u>, o ficheiro **.target**.

    1. Indique como se pode conseguir o efeito indicado.

        ```
        O efeito indicado pode ser atingido expressando uma dependência de forma inversa através de um WantedBy=(ficheiro .target), na secção de Install do unit file do serviço.
        ```

    2. Indique qual o propósito para a existência desta funcionalidade.

        ```
        Esta funcionalidade existe para por exemplo quando instalamos um software que tem um serviço, e este serviço deve ser arrancado num determinado momento do meu sistema. Utilizando a maneira de adicionar o serviço a um determinado target sem editar o ficheiro .target, isto torna-se possível.
        ```

5. Os processadores **ARM v8** de 64 *bits* (por vezes designados por *aarch64*) suportam um modo de tradução de endereços com duas fases, em que um *endereço virtual* é primeiro traduzido para um *endereço intermédio* e a seguir passa por uma segunda tradução para se obter o *endereço físico* final. Qual é o propósito deste esquema de tradução com duas fases?

    ```
    O propósito de realizar um esquema de tradução com duas fazes, é que permite ao hypervisor controlar que memória em uma VM pode aceder, e onde é que esses recursos aparecem no espaço de endereçamento da mesma. Com este esquema de tradução com duas fases podemos garantir que uma uma VM só pode ver os recursos que lhe são alocados, e não os recursos que são alocados a outras VMs, isto é importante para garantir isolamento da VM.
    ```

6. Comente a seguinte afirmação:
> *«Um dos custos incontornáveis do sistema de contentores Docker é o de precisar de uma máquina virtual auxiliar para correr um kernel Linux, que fica em execução em simultâneo com o kernel do host, seja num sistema Windows, Mac ou Linux.»*

    ```
    A afirmação está incorreta. Num sistema Linux, o sistema de contentores Docker, utiliza o kernel do host, e não necessita de uma máquina virtual auxiliar. Nos outros sistemas operativos, o Docker pode necessitar de uma máquina virtual auxiliar. Nos sistemas Windows mais recentes, existe um suporte nativo para contentores Linux, em que não precisam de uma máquina virtual ou Hyper-V para correr. Nos sistemas Mac, o Docker ainda necessita de uma máquina virtual auxiliar, para correr o kernel Linux.
    ```

7. Considere o **Dockerfile** apresentado ao lado e dois ficheiros, **package.json** e **app.js**, com uma aplicação para **Node.js**

    ```dockerfile
    FROM ubuntu
    WORKDIR /opt/isel/tp2
    RUN cp * /opt/isel/tp2/
    RUN apt update
    RUN apt install -y npm nodejs
    RUN npm install
    EXPOSE 80
    CMD ["node", "app.js"]
    ```

- A construção da imagem falha na linha com **RUN cp**, que se pretendia que colocasse os ficheiros da aplicação Node.js na diretoria de destino. Indique porquê e corrija.
- Modifique ainda o **Dockerfile** para minimizar o número de reconstruções de camadas quando algum dos ficheiros da aplicação **Node.js** é alterado e reduza o número total de camadas.

    ```

    ```

8. Uma solução para **docker compose**, composta por múltiplos serviços, utiliza redes distintas para vários grupos de serviços dessa solução. Consequentemente, os vários contentores da solução estarão em execução com definições distintas de rede, possivelmente todas elas diferentes das definições de rede do sistema anfitrião. No entanto, todos os processos desses contentores são também processos do sistema anfitrião. Como podem coexistir no mesmo sistema operativo processos com definições de rede diferentes?

    ```
    ```
