# Teste Final, Época Normal, Semestre de Verão, 21/22

1. (6) Para cada uma das seguintes questões, selecione a opção de resposta correta. A escolha de uma opção errada contribui negativamente para o resultado final com um terço da cotação da questão.

    1. No protocolo **HTTP**, o conceito de interface uniforme significa que:
        1. A semântica de um *header* de resposta não depende do recurso alvo.
        2. Os identificadores de recurso estão presentes no caminho e não na *query string*.
        3. O mesmo *media type* tem de ser usado em todas as respostas.
        4. Os únicos métodos que podem ser usados são o **POST** e **GET**.

        ```
        1
        ```

    2. No protocolo **HTTP**, uma mensagem de resposta de *status code* 400:
        1. Não pode ter *payload*.
        2. Pode ter um *payload* usando um qualquer *media type*.
        3. Tem de ter um *payload* usando o *media type* **application/problem+json**.
        4. Tem de ter um *payload* usando o *media type* **application/json**.

        ```
        ```

    3. Uma mensagem de pedido com método **GET** para o recurso **https://example.com/projects/123.json**:
        1. Tem de resultar numa mensagem de resposta com *Content-Type* igual a **application/json**.
        2. Tem de resultar numa mensagem de resposta com *Content-Type* igual a **text/json**.
        3. Tem de resultar numa mensagem de resposta com *Content-Type* igual a **application/json** ou **application/problem+json**.
        4. Pode resultar numa mensagem de resposta com qualquer valor de **Content-Type**.

        ```
        ```

    4. Na plataforma Spring **MVC**, por omissão, uma classe anotada com **@RestController** vai ter as seguintes instâncias criadas pelo contexto Spring:
        1. Uma única instância.
        2. Uma instância distinta por pedido.
        3. Uma instância distinta por cada ligação de um cliente.
        4. O menor número de instâncias de forma a que nunca exista uma instância a ser usada simultaneamente por *threads* diferentes.

        ```
        ```

    5. No contexto de uma *single page application*, a avaliação da seguinte expressão resulta em:

        **window.location.pathname = '/projects'**
        
        1. Em nenhum pedido **HTTP** executado.
        2. Na execução de um pedido de método **GET** para o caminho /index.html.
        3. Na execução de um pedido de método **GET** para o caminho /projects.
        4. Na execução de um pedido de método **GET** para o caminho /projects.html.

        ```
        ```

    6. A avaliação da seguinte expressão **JSX \<Example a="b"/>** é:
        1. Equivalente à avaliação da expressão **React.createElement(Example)({a:"b"})**.
        2. Equivalente à avaliação da expressão **React.createElement(Example {a:"b"})**.
        3. Equivalente à avaliação da expressão **React.createElement(Example({a:"b"}))**.
        4. Nenhuma das anteriores.

        ```
        ```

2. (2) No *media type* **Siren**, quais as diferenças na estrutura e no propósito dos *links* e das *actions*.

    ```
    ```

3. (2) No contexto de uma aplicação que usa as bibliotecas **React** e **React Router**, qual a diferença entre a utilização dos elementos `<a />` e `<Link />`?

    ```
    ```

4. (2) Descreva os elementos do processo de construção de aplicações usado nesta unidade curricular que permitem a utilização de bibliotecas fornecidas pelo **NPM** em aplicações para execução no *browser*.

    ```
    ```

5. (4) Realize um ou mais componentes para a plataforma Spring **MVC** de forma a que um recurso seja exposto no caminho **/pending**. Um pedido de método **GET** para esse recurso deve retornar uma mensagem com uma representação contendo um objeto **JSON**. Esse objeto deve representar o número de pedidos atualmente em processamento (i.e., iniciados e não concluídos) agrupados por método **HTTP**.

    ```
    ```

6. (4) Realize um componente **React** com as seguintes propriedades: um *array* de *strings* **messages**, um número **period** e um componente **component**.

    Este componente deve apresentar cada mensagem do *array* **messages** durante **period** milissegundos, avançando automaticamente para a próxima mensagem depois de decorrido esse tempo. A seguir à última mensagem, o processo deve recomeçar na primeira mensagem.

    A apresentação das mensagens deve ser feita com recurso ao componente **component**, nomeadamente através da sua propriedade **text** com tipo *string*.

    O componente realizado deve reagir corretamente a mudanças nas suas propriedades.

    ```
    ```
