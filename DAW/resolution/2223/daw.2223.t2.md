# Teste Final, Época de Recurso, Semestre de Inverno, 22/23

1. (6) Para cada uma das seguintes questões, indique qual a resposta correta. Cada resposta incorreta subtrai 1/3 pontos à classificação total do conjunto de questões deste grupo.

    1. A realização de um pedido de método **GET** para **https://example.com/games/create** deve ser interpretado por um intermediário como sendo:
        1. Um pedido não *safe* e não idempotente.
        2. Um pedido *safe* e não idempotente.
        3. Um pedido não *safe* e idempotente.
        4. Um pedido *safe* e idempotente.

        ```
        
        ```

    2. Uma mensagem de resposta **HTTP** com status code igual a **200** e *Content-Type* igual a **application/problem+json** deve ser interpretada por um intermediário como sendo:
        1. Uma resposta de sucesso.
        2. Uma resposta de não sucesso.
        3. Uma resposta de sucesso ou de não sucesso dependendo do valor do campo **type** presente na representação.
        4. Nenhuma das anteriores.

        ```
        ```

    3. O campo **rel** presente num *header* **Link** representa:
        1. O *media-type* potencialmente recebido na resposta a um pedido ao recurso alvo do *link*.
        2. Um valor booleano que indica se o **URI** para o destino é absoluto ou relativo.
        3. O identificador do recurso alvo do *link*.
        4. Nenhuma das anteriores.

        ```
        ```

    4. No contexto da utilização da biblioteca **Spring MVC** a execução da função **doFilter** pertencente à interface **HttpFilter**:
        1. Ocorre sempre no contexto da mesma *thread*.
        2. Ocorre sempre no contexto da *thread* associada à instância sobre a qual é chamado o método.
        3. Ocorre sempre no contexto da *thread* associada ao pedido **HTTP** que resultou nesta chamada.
        4. Ocorre sempre no contexto da *thread* associada ao *handler* que vai processar o pedido **HTTP**.

        ```
        3
        ```

    5. Considere o seguinte componente para a biblioteca React:

        ```javascript
        function Counter() {
            const [value, setValue] = useState(0);
            useEffect(() => {
                const tid = setInterval(() => setValue(value + 1), 1000);
                return () => { clearInterval(tid); }
            }, []);
            return (<div>{value}</div>);
        }
        ```

        A colocação deste componente resulta em:
        1. Na apresentação constante do valor 0.
        2. Na apresentação do valor 0 seguida do valor 1 após 1000 milissegundos.
        3. Na apresentação de um valor numérico incrementado a cada 1000 milissegundos.
        4. Nenhuma das anteriores.

        ```
        ```

    6. Quando uma *single page application* suporta *deep linking* e o utilizador introduz diretamente o **URL** **https://example.com/games?id=123** (e.g., ativando um *bookmark*), o browser faz sempre um pedido HTTP:
        1. de método **GET** usando o **URL** **https://example.com**.
        2. de método **GET** usando o **URL** **https://example.com/index.html**.
        3. de método **GET** usando o **URL** **https://example.com/games?id=123**.
        4. o browser não realiza nenhum pedido **HTTP**.

        ```
        3
        ```

2. (2) No contexto da utilização de *hypermedia* no âmbito de **APIs HTTP**, em que situações deve ser usada o *link relation* *self*?

    ```
    Onde eu tenho representações para as quais eu não tenho conhecimento do URI.
    ```

3. (2) No desenho de **APIs HTTP**, quais as vantagens da utilização de métodos idempotentes?

    ```
    ```

4. (4) Realize um ou mais componentes para uso com a biblioteca **Spring MVC** de forma a que para cada pedido **HTTP** seja emitida uma mensagem de *log* com: método **HTTP**; **URI** do recurso acedido; *status code* da resposta; tempo de processamento; identificador do *handler* que processou o pedido, caso o *handler* seja do tipo **HandlerMethod**. Valorizam-se soluções onde o cálculo do tempo de processamento tem em conta mais etapas desse processamento. Use o método **getShortLogMessage** para obter o identificador de um **HandlerMethod**.

    ```
    ```

5. (4) Realize um componente para a biblioteca **React** que recebe a propriedade **f** do tipo **() => Promise\<string>** e que apresenta o *fulfillment value* ou a *rejection reason* da *promise* resultante da avaliação de **f**. Enquanto esta *promise* estiver pendente, deve ser apresentado um contador incrementado a cada 100 milissegundos. O componente deve ser sensível a mudanças na propriedade **f**.

    ```
    ```

6. (2) Realize a função

    ```js
    useInput(initial: string): [currentValue: string, changeHandler: React.ChangeEvent<HTMLInputElement> => void]
    ```
    para ser usada como *hook* em componentes para a biblioteca **React**, tal como ilustrado no seguinte exemplo:

    ```js
    function Example() {
        const [value, handler] = useInput("");
        return (<input type="text" value={value} onChange={handler} />);
    }
    ```
    ```

    ```
