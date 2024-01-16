# Técnicas de Virtualização de Sistemas - Época de Recurso — Teste Parcial #2 — Teste Global, parte 2

6. [3] Considere o código, apresentado abaixo, de um programa cliente que comunica com um servidor que atende pedidos no *socket* de domínio Unix localizado em **/run/tp2-server.sock** Não contando com a falta das diretivas de **#include** nem com a falta do tratamento de erros, indique os erros notórios no código apresentado, justificando devidamente porque motivo são erros.

    ```c
    struct sockaddr_un cli_addr;
    int main(int argc, char * argv[]) {
        int conn_fd = socket(AF_UNIX, SOCK_STREAM, 0);
        cli_addr.sun_family = AF_UNIX;
        sprintf(cli_addr.sun_path, "/run/tp2-client-%d.sock", getpid());
        cli_addr.sun_port = 5600;
        connect(conn_fd, (struct sockaddr *)&cli_addr, sizeof (cli_addr));
        /* utilização de conn_fd */
        close(conn_fd);
        return 0;
    }
    ```

    ```
    O erro notório no código apresentado é que o cliente está a tentar fazer connect ao socket /run/tp2-client-%d.sock, quando o correto seria fazer connect ao socket /run/tp2-server.sock, visto que essa é a localização do socket do servidor, onde o mesmo está a atender pedidos.
    ```

7. [2.5] A especificação de um serviço *systemd* pode incluir opcionalmente a diretiva **ExecStop**, geralmente omissa, para especificar um comando explícito para terminar o serviço. No entanto, mesmo sem esta diretiva, o comando **systemctl stop *nome_do_serviço*** consegue geralmente terminá-lo. Como?

    ```
    ```

8. [2.5] Na secção de instalação do ficheiro que descreve um serviço em *systemd*, explique porque razão é preferível usar **WantedBy**, em vez de **RequiredBy**, para associar esse serviço a um *target*.

    ```
    ```

9. [3] O código fonte do *kernel* Linux pode ser compilado com diversas opções de configuração. Uma dessas opções está documentada com o seguinte texto:
> *«This changes the kernel so it can modify itself when it is run under* a hypervisor, potentially improving performance significantly over full virtualization. However, when run without a hypervisor the kernel is theoretically slower and slightly larger.»* in https://github.com/torvalds/linux/blob/master/arch/x86/Kconfig
> *neste contexto significa “sobre” ou “debaixo do controlo de”

Que nome se dá ao tipo de solução de virtualização que está implícito neste texto? Na sua resposta, refira as partes relevantes do texto acima que permitem identificar o tipo de solução/otimização em causa.

    ```
    ```

10. [2.5] Descreva sucintamente 5 a 7 passos que considera relevantes na compreensão do que acontece num sistema Linux desde que se executa o comando **docker run -it ubuntu:latest** até que o respetivo contentor está em execução. NOTA: Existem múltiplas respostas válidas.

    ```
    ```

11. [2.5] Um ficheiro **docker-compose.yml**, para especificação de uma solução composta com o nome **tp2**, contém, entre outros elementos, a especificação de um serviço com o nome **svc**, associado a uma rede **tp2net** de tipo *bridge*. Ao levantar a solução com up, este serviço poderá ter associado mais do que 1 contentor? <u>Se sim</u>, como? <u>Se não</u>, o que poderia ser feito para que isso fosse possível? <u>Em qualquer caso</u>, que nome ou nomes podem ser usados na rede **tp2net** para chegar a esse(s) contentor(es)?

    ```
    Este serviço poderá estar associado a mais do que um contentor, utilizando --scale, por exemplo, docker-compose up --scale svc=3 irá criar 3 contentores com o nome tp2_svc_1, tp2_svc_2 e tp2_svc_3, e todos eles irão pertencer à rede tp2net. Os nomes que podem ser usados para chegar a esses contentores na rede tp2net são os mesmos, tp2_svc_1, tp2_svc_2 e tp2_svc_3.
    ```

12. [4] Considere o **Dockerfile** apresentado ao lado, os ficheiros **package.json** e **app.js**, com uma aplicação para **Node.js**, o ficheiro **README.md**, e uma pasta **images** com ficheiros de suporte à interface de utilizador da aplicação. Pretende-se que no sistema de ficheiros das instâncias da imagem todos os ficheiros e pastas abaixo de **/home/node/webapp** tenham como dono o utilizador node. Considera-se que há grande probabilidade de alterar o ficheiro **app.js**, o porto da aplicação e os ficheiros da pasta **images**. Pretende-se ainda, prioritariamente, otimizar a reutilização da *cache* de imagens intermédias e, dentro do possível, minimizar o número de camadas de *overlay*.

    ```dockerfile
    FROM node:alpine
    WORKDIR /home/node/webapp
    COPY README.md .
    COPY images/* ./images
    USER node
    ENV PORT=80
    COPY package.json app.js .
    RUN chown -R node.node /home/node
    RUN npm install
    EXPOSE $PORT
    CMD ["node", "app,js"]
    ```

- Identifique problemas no **Dockerfile** que contrariam os objetivos enunciados atrás.
- Corrija o **Dockerfile** de modo a concretizar os objetivos enunciados.

    ```
    Os argumentos passado para o COPY estão incorretos, o primeiro argumento é o caminho para o ficheiro ou diretoria no host, e o segundo argumento é o caminho para o ficheiro ou diretoria no container, como o segundo argumento deve ser uma diretoria, e não um ficheiro, o COPY README.md . assim como o COPY package.json app.js . deve ser substituído por COPY README.md ./ e COPY package.json app.js ./, respetivamente.
    De salientar que no RUN para colocar como dono de /home/node/webapp o utilizador node, o mesmo está a separar o utilizador e o grupo com um ponto, quando o correto é separar com dois pontos, e apesar de não contrariar o enunciado, estamos a definir que o dono de toda a diretoria /home/node é o utilizador node, quando o pretendido é /home/node/webapp
    O comando CMD ["node", "app,js"] está incorreto, pois está a passar como argumento para o node o ficheiro app,js, quando o correto é app.js.
    (Não sei se o que está para trás era suposto ser de proposito ou se foi uma gralha na escrita do enunciado, uma vez que o mesmo foi copiado diretamente do tp2-en e se calhar ninguém reparou)

    Passando aos problemas de otimização, tanto de reutilização das imagens em cache, como minimização do número de layers, podemos concatenar no início do Dockerfile os copy de README.md com o package.json, uma vez que os mesmos não têm grande probabilidade de serem alterados, e devemos colocar assim como podemos concatenar o COPY das images com o COPY do app.js, uma vez que ambos têm grande probabilidade de serem alterados, conseguindo assim reduzir o número de camadas de overlay.
    Era ainda possível concatenar os RUN chown -R node:node /home/node/webapp com o RUN npm install, e colocá-los também no início do Dockerfile, uma vez que ambos são menos propensos a alteração. O ficheiro ficava assim:
    ```

    ```
    FROM node:alpine
    WORKDIR /home/node/webapp
    COPY README.md package.json ./
    RUN npm install && \
        chown -R node:node /home/node/webapp    

    COPY --chown=node:node images/* ./images
    COPY --chown=node:node app.js ./
    USER node
    ENV PORT=80
    EXPOSE $PORT
    CMD ["node", "app.js"]
    ``` 
