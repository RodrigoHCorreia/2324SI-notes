# DockerFile

pegar no ubuntu correr os updates, instalar um conjunto de ferramentas de rede para usar ping, nslookup etc.

docker build -t ubuntu-net . -> how to build a docker image
docker run -it ubuntu-net -> how to run a docker image

no trabalho um exercício é criar uma imagem usando um dockerfile, a imagem deve corresponder à aplicação web que foi usada no trabalho 3.
é preciso o package.json o tvsapp.js, e os ficheiros com imagens e assim.
Com base nesses ficheiros devemos criar a imagem que mete a aplicação disponível na forma de contentor.

COPY command inside dockerfile should be to a directory meaning it should end in ./ and not .
>COPY src/* ./

we need ENV variables for node ports etc.

EXPOSE $NODE_PORT

## DockerCompose (Soluções compostas)

objetive: manage multiple containers in an integrated way by describing the solution(or networks or volumes)
reads the description and execute a bunch of docker comments to produce the final result.

docker compose up -d -> run the containers in the background, -d is detached meaning my command line will not get stuck waiting for the solution to come down

docker-compose.yml

Class example:

```yml
name "tvs"

services
    ariana
        image alpine # Very small linux image
        tty true # Allocate a terminal / [NOT NEEDED FOR THE WORK]
        depends_on
            - demoapp
        networks
            - alphanet
    
    ursula
        build ubuntu-net # service based on a dockerfile, with the directory for the dockerfile
        tty true
        depends_on
            - demoapp
        networks
            - upsilonnet
    
    demoapp
        build app
        restart "no" # not needed, just to let us know more commands exist
        # we can map internal ports to external ports
        ports
            - ":2345:5432"
        networks
            - alphanet
            - upsilonnet
networks
    alphanet
    upsilonnet
```

Some example:

```yml
name "tvs"

services:
  web:
    build: .
    ports:
      - "3000:3000"
    volumes:
      - .:/src
    environment:
      NODE_PORT: 3000
    depends_on:
      - db
  db:
    image: mongo
    ports:
      - "27017:27017"
    volumes:
      - ./data:/data/db
```

exec command will allow us to run some program inside a container
>docker compose exec -it ariana /bin/sh

to check the networks from a container we can use the command: ip addr | less

we can isolate networks to make hackers life's harder.

ex nginx and tvvsapp share a network but all inside is a different one.

for docker the dns server is ALWAYS 127.0.0.11

nslookup demoapp 127.0.0.11

```yml
version: '3.8'
services:
  # entry service
  entry:
    depends_on:
      - webapp
    networks:
      - abc
    # uses an nginx:alpine image
    image: nginx:alpine
    # The solution will use a single port in the host system for all incoming requests: 2023
    ports:
      - "2023:80"
    # with a modified configuration file
    volumes:
      - ./default.conf:/etc/nginx/conf.d/default.conf

  # webapp service
  webapp:
  # is built directly from the Dockerfile developed in exercise 1.
    build:
      context: .
      dockerfile: Dockerfile
    networks:
      - abc
      - dce
    environment:
      - NODE_PORT=4001
      - ELASTIC_URL=http://database:9200 # easter egg

  # database service
  database:
    # is an elasticsearch:8.11.1
    image: elastic/elasticsearch:8.11.1
    networks:
      - dce
    # with the these environment variables defined
    environment:
      - discovery.type=single-node
      - xpack.security.enabled=false
    volumes:
      - esdata:/usr/share/elasticsearch/data

# Use a volume to ensure that elasticsearch persistent data is not lost between executions. The
# relevant directory is /usr/share/elasticsearch/data
volumes:
  esdata:

# Ensure that entry can access webapp and webapp can access datastore, but entry cannot access datastore
networks:
  abc:
  dce:
```