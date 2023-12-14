# Load Balancing, Docker && SSE

## Load Balancing

### Porquê?

- Aumento de capacidade computacional (Horizontal Scaling)
- Aumento de disponibilidade (High Availability)
- Critério de distribuição
  - Round Robin (cada pedido vai para um servidor diferente)
  - Menor Tempo
  - Menos pedidos pendentes
  - Afinidade (o mesmo utilizador vai sempre para o mesmo servidor, isto pode ser verificado por exemplo através do token)

nginx.

## Docker

docker compose, é a forma que temos de coordenar a criação de vários containers.

8080:8080 -> faz com que o porto 8080 do anfitrião (máquina) seja mapeado para o porto 8080 do container.

## SSE (Server Sent Events)

Formato:

Content-Type: text/event-stream

Um evento é costituido por um id, um evento, e um data para o conteudo do evento.

API Standard do browser: EventSource

API do spring: SseEmitter
