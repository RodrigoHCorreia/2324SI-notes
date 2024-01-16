# Técnicas de Virtualização de Sistemas - Época Normal — Teste Parcial #2 — Teste Global, parte 2

6. [3] Num sistema Linux, considere um serviço que atende os processos clientes através de um único *socket* de domínio Unix do tipo *stream*. É possível atender múltiplos clientes em simultâneo? Se sim, como se distingue cada um dos clientes no serviço (por exemplo, no momento de receber/enviar dados de/para cada um dos clientes)? Se não, como se pode desenhar uma solução para suportar este requisito?

    ```
    Sim, é possível atender múltiplos clientes em simultâneo através de um único socket de domínio Unix do tipo stream. Cada cliente irá fazer um pedido de conexão ao socket, e quando o servidor aceita esse pedido, o mesmo recebe um novo file descript referente a esse cliente. Este file descriptor lê e escreve para o file descriptor do processo cliente.
    ```

7. [2.5] Alguns processos ativos num sistema Linux correspondem a serviços a operar como *daemons*. Indique três características associadas a este tipo de processos (não específicas de um gestor de serviços).

    ```
    Três características dos processos que operam como daemons são:

    - Habilidade de correr em background.
    - Não possuem um terminal associado, o que significa que não recebem ou escrevem dados para o terminal.
    - Não tem interação direta com o utilizador. 
    ```

8. [2.5] Num sistema Linux com *systemd*, o ficheiro **/etc/systemd/system/tp2.service**, na sua secção [Unit] tem a linha **Requires=tp2.socket**.
    1. [1.5] Tendo em conta esta linha, que funcionalidade do *systemd* deverá estar a ser usada no serviço **tp2** e porque aparece esta diretiva **Requires** no ficheiro **.service**?

        ```
        A funcionalidade do systemd que está a ser usada é o socket activation. Esta diretoria aparece no ficheiro .service porque o serviço tp2 depende do socket tp2.socket, ou seja, o serviço tp2 só irá ser iniciado se o socket estiver ativo.
        ```

    2. [1] Deverá o ficheiro **.socket** ter uma linha equivalente (**Requires=tp2.service**)? Porquê?

        ```
        Não, porque o socket não depende do serviço, mas sim o contrário. O socket deve ser iniciado primeiro, habitualmente no boot da máquina, e só depois é que o serviço deve ser iniciado.
        ```

9. [3] A empresa **VMware** vende um produto, descrito como um hipervisor, cujas instruções de instalação contêm o seguinte texto:
> *«In a typical interactive installation, you boot the ESXi installer and respond to the installer prompts to install ESXi to the local host disk. The installer reformats and partitions the target disk and installs the ESXi boot image. If you have not installed ESXi on the target disk before, all data on the drive is overwritten, including hardware vendor partitions, operating system partitions, and associated data.»* in VMware vSphere 8.0 Product Documentation, Installing ESXi Interactively
- Este é um hipervisor de tipo 1 ou de tipo 2? Justifique a sua afirmação com base no texto acima.

    ```
    Este é um hipervisor de tipo 1 (bare metal), o que significa que o hypervisor corre diretamente no hardware. Isto pode ser concluído pelo facto de o texto mencionar que o ESXi é instalado diretamente no disco local.
    ```

10. [2.5] Apresente duas vantagens que resultam da organização das imagens *docker* em camadas, suportadas por sistemas de ficheiros do tipo *overlay*. Apresente também uma possível desvantagem.

    ```
    Duas vantagens da organização das imagens docker em camadas são:

    - Possibilidade de criar imagens baseadas em outras imagens.
    - Reaproveitamento de camadas de imagens intermédias, o que permite que o docker não tenha que reconstruir camadas que já existem em cache.
    
    Uma possível desvantagem é que se o docker tiver que reconstruir uma camada, por o seu contexto ter mudado comparando com o armazenado em cache, então o docker tem que reconstruir todas as camadas abaixo desse layer, incluindo o próprio, mesmo que o contexto de algumas das camadas abaixo não tenha mudado.
    ```

11. [4] Considere o **Dockerfile** apresentado ao lado e três ficheiros: **package.json** e **app.js**, com uma aplicação para **Node.js**, e um **README.md**

    ```dockerfile
    FROM node:alpine
    WORKDIR /home/node
    COPY package.json .
    RUN npm install
    COPY app.js .
    COPY README.md .
    RUN chown -R node.node /home/node
    USER node
    EXPOSE 80
    CMD ["node", "app,js"]
    ```

- Indique que camadas de *overlay* são criadas sobre a imagem base **node:alpine**
- Modifique o **Dockerfile** para minimizar o número de camadas de *overlay*
- Indique as camadas de *overlay* criadas sobre a base, considerando as alterações

    ```
    As camadas de overlay criadas sobre a imagem base node:alpine, dado o Dockerfile apresentado, são:

    - WORKDIR /home/node
    - COPY package.json .
    - RUN npm install
    - COPY app.js .
    - COPY README.md .
    - RUN chown -R node.node /home/node
    
    Ficheiro modificado:

    FROM node:alpine
    WORKDIR /home/node
    COPY package.json README.md app.js .
    RUN npm install && \ chown -R node.node /home/node
    USER node
    EXPOSE 80
    CMD ["node", "app,js"]

    As camadas de overlay criadas sobre a imagem base node:alpine, dado o Dockerfile modificado, são:

    - WORKDIR /home/node
    - COPY package.json README.md app.js .
    - RUN npm install && \ chown -R node.node /home/node
    ```



12.  [2.5] Um ficheiro **docker-compose.yml**, para especificação de uma solução composta com o nome **tp2**, contém três serviços: **svca**, **svcb** e **svcc**, todos colocados na mesma rede, **svcnet**, de tipo **bridge**. Os serviços **svca** e **svcc** têm apenas uma instância cada um, mas o serviço **svcb** foi lançado com **scale=4**. Executando um *shell* (/bin/sh) no contentor do serviço **svca**, qual é a diferença observável entre executar **nslookup svcb ou nslookup tp2-svcb-1** ?
    
        ```
        ```
        