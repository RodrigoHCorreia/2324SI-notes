# Teste Final, Época de Recurso, Semestre de Verão, 20/21

1. (6) Para cada uma das seguintes questões, selecione a opção de resposta correta. A escolha de uma opção errada contribui negativamente para o resultado final com um terço da cotação da questão.

    1. No protocolo **HTTP**, o header **Cache-Control** tem semântica definida:
        1. Apenas nas mensagens de pedido.
        2. Apenas nas mensagens de resposta.
        3. Nas mensagens de pedido e de resposta.
        4. Nenhuma das anteriores.

        ```
        ```

    2. A realização de um pedido de método **POST** para **https://example.com/projects/123/delete**, deve ser interpretado por um intermediário como sendo:
        1. Equivalente ao pedido de método **DELETE** para **https://example.com/projects/123**.
        2. Um pedido idempotente mas não *safe*.
        3. Um pedido idempotente e *safe*.
        4. Nenhuma das anteriores.

        ```
        ```

    3. Na plataforma Spring **MVC** e assumindo a configuração por omissão:
        1. Os *handlers* presentes numa classe *controller* podem ser chamados em concorrência sobre a mesma instância, por *threads* distintas.
        2. Os *handlers* presentes numa classe *controller* nunca são chamados em concorrência sobre a mesma instância, porque apenas existe uma *thread* a processar pedidos.
        3. Os *handlers* presentes numa classe *controller* nunca são chamados em concorrência sobre a mesma instância, porque existe um *lock* que protege esses acessos.
        4. Nenhuma das anteriores.

        ```
        ```
        
    4. No contexto da *framework* **React**, a utilização de [] como segundo argumento da função **useEffect**, significa que:
        1. O efeito vai ser chamado uma vez durante o tempo de vida da instância do componente.
        2. O efeito vai ser chamado uma vez durante o tempo de vida da aplicação.
        3. O efeito vai ser chamado sempre que a função que define o componente for chamada.
        4. Nenhuma das anteriores.

        ```
        ```
        
    5. No contexto de uma *single page application*, a avaliação da seguinte expressão resulta em: 
        
        **history.pushState({},'', '/projects/123')**
        
        1. Na realização de um pedido **HTTP** de método **GET** para o caminho ‘/index.html’.
        2. Na realização de um pedido **HTTP** de método **GET** para o caminho ‘/projects/123/index.html’.
        3. Na realização de um pedido **HTTP** de método **GET** para o caminho ‘/projects/123’.
        4. Nenhuma das anteriores.

        ```
        ```
        
    6. O resultado da avaliação da expressão **JSX \<div />** é:
        1. Um elemento **HTML**, do mesmo tipo do obtido na avaliação da expressão **document.createElement('div')**.
        2. O resultado da avaliação da expressão **React.createElement('div', null)**.
        3. O resultado da avaliação da expressão **React.createElement(div, null)**.
        4. Nenhuma das anteriores.

        ```
        ```
        
2. (2) No contexto da plataforma Spring **MVC**, indique duas formas distintas para a definição de *beans*.

    ```
    ```
        
3. (2) No processo de desenvolvimento de aplicações para execução em *browser* usado na unidade curricular, qual a necessidade da existência de um passo de construção? Ou seja, porque é que os ficheiros fonte não são entregues diretamente para execução no *browser*?

    ```
    ```
       
4. (2) Indique o que é necessário realizar para que uma aplicação *single page application* suporte *deep-linking*.

    ```
    ```
       
5. (4) Realize um ou mais componentes para a plataforma Spring **MVC** de forma a expor um recurso no caminho **/anonymous**. Um pedido de método **GET** a este recurso deve retornar a lista contendo a contabilização de todos os acessos anônimos aos recursos da **API**. Cada elemento da lista é composto pelo **URI** do recurso e pelo número de acessos anônimos a esse recurso.

    ```
    ```
       
6. (4) Realize um componente para a *framework* **React** que implementa um cronômetro com suporte para contagem de tempos parciais. O componente apresenta dois botões **Start** e **Lap**, bem como a lista de números com as contagens parciais. 
Inicialmente o botão **Start** está ativo e o botão **Lap** está inativo. Um clique no botão **Start** reinicia o cronômetro, o que resulta na ativação do botão **Lap** e na remoção de todos os números da lista. Neste estado, um clique no botão **Lap** acrescenta à lista o valor em segundos entre o último clique em **Lap** e o último clique em **Start**. 
Se o botão **Start** receber um clique enquanto **Lap** está ativo, então **Lap** fica novamente inativo e o componente volta ao estado inicial. Note que a avaliação de **Date.now()** retorna o número de milissegundos desde 1 de janeiro de 1970.

    ```
    ```
