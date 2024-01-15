# Notas

https://unix.stackexchange.com/questions/159462/what-is-systemds-target-service-and-socket/159488#159488
https://unix.stackexchange.com/questions/159174/differences-between-inactive-vs-disabled-and-active-vs-enabled-services
https://securitywing.com/types-virtualization-technology/

1. quando fazendo um docker build guiado por um dockerfile, que condições dão origem a uma nova camada de overlay na imagem resultante:

- Cada condição que representa uma possível mudança no sistema de ficheiros do container, dá origem a uma nova camada de overlay na imagem resultante.

2. Na reconstrução de uma imagem, que condições permitem o reaproveitamento das imagens intermédias (em *cache*) do *build* anterior?

- Se o contexto de um layer não mudou (ficheiros e diretorias que o mesmo depende), então o Docker utiliza o layer em cache em vez de o reconstruir.

Devemos order os layers do nosso Dockerfile de forma a que os layers que mudam menos frequentemente estejam mais acima no ficheiro, para que sejam reutilizados mais vezes. Uma vez que o docker no processo de reconstrução de uma imagem, vai percorrendo o Dockerfile de cima para baixo, e quando encontra um layer que não está em cache, reconstrói todos os layers abaixo desse, incluindo o layer que não está em cache. 

https://docs.docker.com/build/cache/

Não copiar ficheiros desnecessários.
Minimizar o número de layers, por exemplo concatenar comandos RUN em apenas um, caso faça sentido, com &&.
Usar multi-stage builds, para que não sejam incluídos ficheiros desnecessários na imagem final.

Multi-stage builds - https://docs.docker.com/develop/develop-images/multistage-build/

## alguns tópicos a não esquecer de estudar

- Multi-stage builds
- Paravirtualization


> RUN <<EOF
> set -e // exit on error
> echo "the first command"
> echo "the second command"
> EOF