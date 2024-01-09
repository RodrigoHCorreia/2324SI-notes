# Teste Final, Época Especial, Semestre de Verão, 20/21

1. (6) Para cada uma das seguintes questões, selecione a opção de resposta correta. A escolha de uma opção errada contribui negativamente para o resultado final com um terço da cotação da questão.

    1. No protocolo **HTTP**, o *header* **Authorization** tem semântica definida:
        1. Apenas nas mensagens de pedido.
        2. Apenas nas mensagens de resposta.
        3. Nas mensagens de pedido e de resposta.
        4. Nenhuma das anteriores.

        ```
        ```

    2. A realização de um pedido de método **GET** para **https://example.com/projects/123/delete** deve ser interpretado por um intermediário como sendo:
        1. Equivalente ao pedido de método **DELETE** para **https://example.com/projects/123**.
        2. Um pedido idempotente mas não *safe*.
        3. Um pedido idempotente e *safe*.
        4. Nenhuma das anteriores.

        ```
        ```

    3. Segundo o RFC 8288 (*Web Linking*) um *link relation type* é:
        1. O identificador do recurso alvo do *link*.
        2. O identificador do recurso que define o contexto do *link*.
        3. O identificador que expressa a semântica da ligação entre dois recursos.
        4. Nenhuma das anteriores.

        ```
        ```

    4. No contexto da *framework* **React**, a utilização de **undefined** como segundo argumento da função **useEffect** significa que:
        1. O efeito vai ser chamado uma vez durante o tempo de vida da instância do componente.
        2. O efeito vai ser chamado uma vez durante o tempo de vida da aplicação.
        3. O efeito vai ser chamado sempre que a função que define o componente for chamada.
        4. Nenhuma das anteriores.

        ```
        ```

    5. No contexto de um *browser*, a avaliação da seguinte expressão resulta:
        
        **fetch('https://httpbin.org/status/404').status**
        
        1. No número 404.
        2. No número 200.
        3. No valor *null*.
        4. Nenhuma das anteriores.

        ```
        ```

    6. O resultado da avaliação da expressão **JSX \<Div>\<div /></Div>** é:

        1. Um elemento **HTML** do mesmo tipo do obtido na avaliação da expressão **document.createElement('Div')**.
        2. O resultado da avaliação da expressão **React.createElement(Div, null, document.createElement('div'))**.
        3. O resultado da avaliação da expressão **React.createElement(Div, null, React.createElement('div', null))**.
        4. O resultado da avaliação da expressão **React.createElement(Div, null, React.createElement(div, null))**.

        ```
        ```

2. (2) Indique dois motivos para a utilização de *hypermedia* nas representações dos recursos de uma **API HTTP**.

    ```
    ```
        
3. (2) No contexto da plataforma Spring **MVC**, quais os critérios que se deve ter em conta para escolher um *servlet filter* ou um *handler interceptor* como ponto de extensibilidade a usar para criar um intermediário no processamento de pedidos.

    ```
    ```
       
4. (2) Tendo em consideração o modelo de construção de aplicações para a plataforma *browser* usado na unidade curricular, indique qual o propósito e forma de utilização da ferramenta **webpack**.

    ```
    ```
       
5. (4) Realize um ou mais componentes para a plataforma Spring **MVC** de forma a que todas as respostas produzidas tenham o *header* **HTTP Debug** contendo o tempo em milissegundos que a resposta demorou a ser processada, bem como o eventual *handler* envolvido nesse processamento. Valorizam-se soluções em que o cálculo do tempo de processamento inclua não só o tempo de execução do eventual *handler* mas também o da maioria dos intermediários envolvidos (e.g., filtros e interceptores).

    ```
    ```
       
6. (4) Realize um componente para a *framework* **React** que:
    - Apresenta o valor de um contador iniciado com zero.
    - Apresenta uma caixa de texto e um botão. Sempre que o botão for premido, o valor presente na caixa de texto deve ser usado como o período em milissegundos com que o contador é incrementado. Inicialmente e sempre que o botão seja premido com a caixa de texto vazia, o período de contagem deve ser infinito.
    
    Tenha em consideração que a função de atualização de estado retornada pelo hook **setState** também pode receber uma função que recebe o valor de estado anterior e retorna o novo valor pretendido para o estado.

    ```
    ```
