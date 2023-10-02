## When to use DTOs, Input/OutputModels, DAOs and Domain Models

### Input/Output Models

- Utilizado pelos **controllers**, pelo facto de terem uma estrutura ligada diretamente aos pedidos e respostas da API.
- Input Models para os pedidos
- Output Models para as respostas

### DTOs: Data Transfer Objects

- Utilizados para enviar objetos entre camadas da aplicação, por exemplo, entre o controller e o service.

### DAOs: Data Access Objects

- Utilizados para aceder à base de dados, por exemplo, para fazer queries nos repositórios.
- Utilizado para guardar a interface abstrata de algum tipo na base de dados.
- Usamos para fazer testes com mocking.

### Domain Models

- Utilizados pelos **services** e às vezes pelos **repositórios**.
- Representam os objetos do **domínio da aplicação**, com as suas regras de negócio.

### How do they interact?

#### Controller

- Aceitam input na forma de **Input models**.
- Podem ransformam este input em **DTOs** para passar para os **Services**.
- Recebem **DTOs** como output dos **Services** e convertem-nos em **Output models** para a resposta.

#### Service

- Aceitam e retornam **DTOs** quando comunicam com os **Controllers**.
- Usam **Domain Models** para encapsular a lógica de negócio.
- Podem converter entre **Domain Models** e **DTOs** quando interagem com os **Repositories**.

#### Repository

- Trabalham com **Domain Models**.