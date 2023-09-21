# Pipeline, Spring-MVC

- O objetivo da implementação de servlet que o spring-mvc fornece, é oferecer um tipo de programação com base em controllers e em handlers. para isto existe um pipeline de processamento de pedidos.
- O pipeline é composto por vários componentes, que são chamados de **interceptors**.

- A grande diferença entre filter e intercepter é que **o filtro não tem qualquer tipo de conhecimento sobre spring-mvc**. nomeadamente o routing de qual handler vai ser usado.

Na saida:

- **ArgumentResolver** - entidade responsável por fornecer os argumentos necessários para o handler, tipicamente a partir da mensagem.

Na entrada:

- **MessageConverter** - entidade responsável por converter o retorno do handler para o tipo de mensagem que o cliente pediu.

- **MultiValueMap** - é um mapa que permite extrair todos os os valores de uma chave.
  - permite ter várias chaves com o mesmo nome.
