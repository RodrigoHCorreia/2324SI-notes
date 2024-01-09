# Teste Final, Epoca Normal, Semestre de Verão, 20/21 

1. (6) Para cada uma das seguintes questoes, seleccione a opcão de resposta correcta. A escolha de uma opcão errada contribui negativamente para o resultado final com um terco da cotacao da quest̃ao.

    1.  No protocolo **HTTP**, o *header **Content-Location*** tem semântica definida:
        1. Apenas nas mensagens de pedido.
        2. Apenas nas mensagens de resposta.
        3. Nas mensagens de pedido e de resposta.
        4. Nas mensagens de pedido e de resposta com um metodo idempotente.

        ```
        ```

    2. A realização de um pedido de método **GET** para **https://example.com/projects/123/delete**, deve ser interpretado por um intermediário como sendo:
        1.  Equivalente ao pedido de método **DELETE** para **https://example.com/projects/123**.
        2.  Um pedido idempotente mas não *safe*.
        3.  Um pedido idempotente e *safe*.
        4.  Nenhuma das anteriores.

        ```
        ```    

    3.  Na platforma Spring **MVC**, por omissão, o construtor de uma classe anotada com **@RestController** ́e chamado:
        1.  Uma vez por cada pedido HTTP, independentemente do *handler* que processa o pedido.
        2.  Uma vez por cada pedido HTTP processado por um *handler* presente nessa classe.
        3.  Uma vez por cada utilizador distinto.
        4.  Uma vez por cada instância da aplicação.
    
        ```
        4
        ```

    4.  Assumindo o processo de construção de aplicações para execução na plataforma **browser** usando na unidade curricular, qual o resultado da avalição da seguinte expressão num módulo da aplicação:
        
        **const m = require(’utils’)**
        
        1.  Erro de execução, porque a função **require** não está definida.
        2.  Pedido HTTP de método **GET** com caminho **/utils**.
        3.  Pedido HTTP de método **GET** com caminho **/utils.js**.
        4.  Referência para um objecto, se o módulo **utils** estiver presente em **node_modules**.

        ```
        ```

    5.  No contexto de uma single page application, a avaliação da seguinte expressão resulta em:

        **window.location.pathname = ’/projects’**

        1.  Na realização de um pedido HTTP de método **GET** para o caminho ‘/index.html’.
        2.  Na realização de um pedido HTTP de método **HEAD** para o caminho ‘/index.html’.
        3.  Na realização de um pedido HTTP de método **GET** para o caminho ‘/projects’.
        4.  Na realização de um pedido HTTP de método **GET** para o caminho ‘/projects.html’.
        
        ```
        3
        ```

    6.  O resultado da avaliação da expressão **JSX\<Div />** ́e:
        1.  Um elemento **HTML**, do mesmo tipo do obtido na avaliação da expressão **document.createElement(’div’)**.
        2.  Um elemento **HTML**, do mesmo tipo do obtido na avaliação da expressâo **document.createElement(’Div’)**.
        3.  O resultado da avaliação da expressão **Div({})**.
        4.  Nenhuma das anteriores.
            
        ```
        2
        ```

2. (2) No formato Siren, quais a diferenças entre *links* e acçôes?

    ```
    ```

3. (2) No contexto do protocolo **HTTP**, descreva qual a relação entre negociação de contéudos e *caching*. Nomeadamente, indique as consequências na organização do sistema de *cache* decorrentes da existência de negociação de contéudos, bem como a informação extra que é necessário incluir nas mensagens **HTTP**.

    ```
    ```

4. (2) Tendo em consideração o modelo de construção de aplicações para a plataforma *browser* usado na unidade curricular, indique qual o propósito e forma da utilização do sistema **NPM**.

    ```
    ```
    
5. (3) Realize um ou mais componentes para a plataforma Spring **MVC** de forma a expôr um recurso no caminho **/handlers**. Um pedido de método **GET** a este recurso deve retornar um objecto **JSON**. Cada campo deste objecto representa um *handler* usado no processamento de pelo menos um pedido, sendo o valor do campo um objecto com:

    - O número de vezes que o *handler* foi utilizado.
    - O tempo médio de execução dos pedidos a esse *handler*.

    Assuma que todos os *handlers* são do tipo **HandlerMethod**. Use o método **getShortLogMessage** para obter uma representação textual do *handler*. Valorizam-se soluções em que o cálculo do tempo de processamento inclua não só o tempo de execução do *handler* mas também o da maioria dos intermediários envolvidos (e.g. filtros e interceptores).

    ```
    ```

6. (5) Realize um componente React que recebe um **URI** e que apresenta uma caixa de texto (*textarea*) e um botão. A caixa de texto deve apresentar o conteúdo do *body* presente na resposta a um pedido **HTTP** de método **GET** ao **URI** recebido, independentemente do *status code* da resposta. Caso o pedido resulte numa excepção, a caixa de texto deve apresentar o texto associado a essa excepção. Um clique no botão deve desencadear um novo pedido **HTTP** ao **URI** definido e consequente apresentação da resposta. Enquanto um pedido estiver em curso, o botão deve permanecer inactivo (*disabled*). O componente deve ser sensível a mudanças no **URI** definido. Caso o novo **URI** seja diferente do **URI** usado no último pedido (terminado ou em curso), deve ser desencadeado um pedido para o novo valor do **URI** e cancelado eventuais pedidos em curso.

    ```
    ```
