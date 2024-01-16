# Notas

https://unix.stackexchange.com/questions/159462/what-is-systemds-target-service-and-socket/159488#159488
https://unix.stackexchange.com/questions/159174/differences-between-inactive-vs-disabled-and-active-vs-enabled-services
https://securitywing.com/types-virtualization-technology/
https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files
https://developer.arm.com/documentation/102142/0100/Stage-2-translation

1. quando fazendo um docker build guiado por um dockerfile, que condições dão origem a uma nova camada de overlay na imagem resultante:

- Cada condição que representa uma possível mudança no sistema de ficheiros do container, dá origem a uma nova camada de overlay na imagem resultante.

2. Na reconstrução de uma imagem, que condições permitem o reaproveitamento das imagens intermédias (em *cache*) do *build* anterior?

- Se o contexto de um layer não mudou (ficheiros e diretorias que o mesmo depende), então o Docker utiliza o layer em cache em vez de o reconstruir.


- ver umask e daemon

Devemos ordenar os layers do nosso Dockerfile de forma a que os layers que mudam menos frequentemente estejam mais acima no ficheiro, para que sejam reutilizados mais vezes. Uma vez que o docker no processo de reconstrução de uma imagem, vai percorrendo o Dockerfile de cima para baixo, e quando encontra um layer que o seu contexto mudou, comparando com o que está em cache, reconstrói todos os layers abaixo desse, incluindo o próprio. 

https://docs.docker.com/build/cache/

Não copiar ficheiros desnecessários.
Minimizar o número de layers, por exemplo concatenar comandos RUN em apenas um, caso faça sentido, com &&.
Usar multi-stage builds, para que não sejam incluídos ficheiros desnecessários na imagem final.

Multi-stage builds - https://docs.docker.com/develop/develop-images/multistage-build/

## alguns tópicos a não esquecer de estudar

- Multi-stage builds
- Paravirtualization
  - The major drawback of paravirtualization is the requirement of modifying guest operating system to execute and communicate with the hypervisor. You must modify the kernel of the guest OS before installation.

| | Processo | Sistema
| --- | --- | --- |
| Instruction Set == | Processo de S.O. | Virtual Box, VMware, Parallels (tem um Hypervisor)|
| Instruction Set != | JVM, .NET, Node.js, qemu-user (Virtual Execution Environment)| Emuladores de Plataforma, quemu-system |  

> RUN <<EOF
> set -e // exit on error
> echo "the first command"
> echo "the second command"
> EOF

Dizer o que é o install section

(targets são os runlevels do systemd)

**Níveis de operacionalidade da máquina bottom-up:**

sysinit
basic
multi-user
graphical

```bash
[Unit]
Description=My Service

[Install]
WantedBy=multi-user.target
```

**Hypervisors**

- Tipo 1 - Bare Metal - Significa que o hypervisor corre diretamente no hardware, sem um sistema operativo a correr por baixo.
- Tipo 2 - Hosted - Significa que o hypervisor corre sobre um sistema operativo, que por sua vez corre sobre o hardware.

OsGuests - São os sistemas operativos que correm sobre o hypervisor.