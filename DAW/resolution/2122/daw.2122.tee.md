# Teste Final, Época Especial, Semestre de Verão, 21/22

1. (6) Para cada uma das seguintes questões, selecione a opção de resposta correta. A escolha de uma opção errada contribui negativamente para o resultado final com um terço da cotação da questão.

    1. No protocolo **HTTP**, um pedido de método **GET** para o recurso **https://example.com/projects/123/delete**:
        1. Solicita a remoção do recurso com URI **https://example.com/projects/123**.
        2. Solicita uma representação do recurso com URI **https://example.com/projects/123**.
        3. Solicita uma representação do recurso com URI **https://example.com/projects/123/delete**.
        4. Deve resultar sempre numa resposta com status code 400 (bad request).

        ```
        ```

    2. No protocolo **HTTP**, uma mensagem de resposta de status code 500:
        1. Não pode ter payload.
        2. Pode ter um payload usando um qualquer media type.
        3. Tem de ter um payload usando o media type **application/problem+json**.
        4. Tem de ter um payload usando o media type **application/json**.

        ```
        ```

    3. Na norma Web Linking (RFC 8288) o atributo *rel* de um *link*:
        1. Contém o URI do recurso destino do *link*.
        2. Contém o URI do recurso contexto do *link*.
        3. Contém o *media-type* usado na representação do recurso destino do *link*.
        4. Contém o tipo da relação entre dois recursos representado eventualmente na forma de um URI.

        ```
        ```

    4. Na biblioteca Spring **MVC** e na configuração por omissão:
        1. É sempre criada uma nova instância de um *interceptor* por cada pedido.
        2. Não são criadas instâncias de *interceptors* porque todos os métodos têm de ser estáticos.
        3. Apenas são criadas novas instâncias de *interceptors* quando todas as instâncias existentes estiverem a ser usadas.
        4. Nenhuma das anteriores.

        ```
        ```

    5. A utilização de módulos **NPM** usando o sistema **CommonJS** em ficheiros **Javascript** destinados à execução em *browsers* requer:
        1. A instalação de extensões no *browser*.
        2. A utilização da ferramenta **webpack** ou similar.
        3. A utilização da biblioteca **React** ou similar.
        4. A utilização da sintaxe **JSX**.

        ```
        2
        ```

    6. O primeiro parâmetro da função **createElement** da biblioteca **React** é:
        1. Sempre uma *string*.
        2. Sempre um componente.
        3. Sempre uma instância de um componente.
        4. Nenhuma das anteriores.

        ```
        ```

2. (2) No desenho de **APIs HTTP** quais as vantagens da utilização de métodos idempotentes?

    ```
    ```

3. (2) No contexto do desenvolvimento de **Single Page Applications** qual o propósito do uso do método **preventDefault** presente em objetos *evento*?

    ```
    
    ```

4. (2) No contexto da biblioteca **React** o recurso identificado por **https://reactjs.org/docs/hooks-rules.html** (acedido a 2022-09-09) tem presente a seguinte afirmação na sua representação:

    **"Don’t call Hooks inside loops, conditions, or nested functions. Instead, always use Hooks at the top level of your React function, before any early returns."**

    Indique qual a razão para esta limitação.

    ```
    ```

5. (4) Realize um ou mais componentes para a plataforma Spring **MVC** de forma a que um recurso seja exposto no caminho **/failures**. Um pedido de método **GET** para esse recurso deve retornar uma mensagem com uma representação contendo um objeto **JSON**. Esse objeto deve representar os últimos 10 pedidos que resultaram numa resposta com status code maior ou igual a 500. A representação de cada pedido deve incluir: o método do pedido, o URI do pedido, o status code da resposta, e o nome do controlador e do método responsável pelo processamento desse pedido (caso o processamento tenha sido realizado por um controlador).

    ```
    ```

6. (4) Realize um componente para uso com a biblioteca **React** que receba uma lista de **URLs** através das suas propriedades e apresente uma lista de itens. Cada item está associado a um URL da lista e deve conter:

    - O URL e o texto “...” enquanto o pedido ao URL estiver a ser realizado.
    - O URL e o código de estado da resposta ou o erro ocorrido depois do pedido ter sido concluído com ou sem sucesso.

    A ordem dos itens deve respeitar a ordem dos URLs. A sua solução pode criar e usar componentes auxiliares. O componente realizado deve reagir corretamente a mudanças nas suas propriedades.

    ```
    ```
