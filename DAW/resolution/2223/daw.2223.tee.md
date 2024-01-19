# Teste Final, Época Especial, Semestre de Inverno, 22/23

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

    4. Na biblioteca **Spring MVC** e na configuração por omissão:
        1. Ocorre sempre no contexto da mesma *thread*.
        2. Ocorre sempre no contexto da *thread* associada à instância sobre a qual é chamado o método.
        3. Ocorre sempre no contexto da *thread* associada ao pedido **HTTP** que resultou nesta chamada.
        4. Ocorre sempre no contexto da *thread* associada ao *handler* que vai processar o pedido **HTTP**.
        ```
        ```

    5. Considere o seguinte componente para a biblioteca **React**:
        ```javascript
        function Counter() {
            const [value, setValue] = useState(0);
            useEffect(() => {
                const tid = setInterval(() => setValue((x) => x + 1), 1000);
                //return () => { clearInterval(tid); }
            }, [setValue]);
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

    6. Quando uma *single page application* suporta *deep linking* e o utilizador introduz diretamente o **URL** **https://example.com/games?id=123** (e.g., ativando um *bookmark*), o browser faz sempre um pedido **HTTP**:
        1. de método **GET** usando o **URL** **https://example.com/index.html**.
        2. de método **GET** usando o **URL** **https://example.com/**.
        3. de método **GET** usando o **URL** **https://example.com/games**.
        4. de método **GET** usando o **URL** **https://example.com/games?id=123**.

        ```
        ```

2. (2) No contexto da utilização de *hypermedia* no âmbito de **APIs HTTP**, em que situações deve ser usada o *link relation* *self*?

    ```

    ```

3. (2) No desenho de **APIs HTTP**, quais as vantagens da utilização de métodos idempotentes?

    ```

    ```

4. (5) Realize um ou mais componentes para a plataforma **Spring MVC** de forma a que um recurso seja exposto no caminho **/errors**. Um pedido de método **GET** para esse recurso deve retornar uma mensagem com uma representação contendo um objeto **JSON**. Esse objeto deve representar os pedidos processados nos últimos 10 minutos e que resultaram numa resposta com status code igual a **500**. A representação de cada pedido deve incluir: o momento em que o pedido foi recebido; o método do pedido; o **URI** do pedido; e o nome do controlador e do método responsável pelo processamento desse pedido (caso o processamento tenha sido realizado por um controlador).

    /errors -> {pedidos nos ultimos 10 minutos com resposta igual a 500} RequestInfo(momento, method, uri, nome_do_controlador, methodo do controlador)
    ```kotlin
    data class RequestInfo(
    val initialTime: Long,
    val method: String,
    val uri: String,
    val controllerName: String? = null,
    val methodName: String? = null
    )

    @Service
    class RequestService {
        private val requests = mutableListOf<RequestInfo>()
        private val lock = ReentrantLock()

        fun get(): List<RequestInfo> {
            lock.withLock {
                val tenMinutes = 10000 * 600
                return requests.filter { System.currentTimeMillis() - it.initialTime < tenMinutes}
            }
        }

        fun add(request: RequestInfo) {
            requests.add(request)
        }
    }

    @Component
    class Interceptor(private val service: RequestService): HandlerInterceptor {
        override fun preHandle(request: HttpServletRequest, response: HttpServletResponse, handler: Any): Boolean {
            request.setAttribute("initialTime", System.currentTimeMillis())
            return true
        }

        override fun postHandle(
            request: HttpServletRequest,
            response: HttpServletResponse,
            handler: Any,
            modelAndView: ModelAndView?
        ) {
            if (response.status != 500) return
            val handlerMethod = handler
            val initialTime = request.getAttribute("initialTime") as Long
            val method = request.method
            val uri = request.requestURI
            if(hander is HandlerMethod){
                service.add(RequestInfo(initialTime, method, uri, handler.beanType.simpleName, handlerMethod.method.name))
            } else {
                service.add(RequestInfo(initialTime, method, uri))
            }
        }
    }

    @RestController
    class MyController(private val service: RequestService) {

        @GetMapping("/errors")
        fun getErrors(): ResponseEntity<*> {
            return ResponseEntity.status(200).body(service.get())
        }
    }
    ```

5. (5) Realize um componente para a biblioteca **React** que recebe a propriedade **f** do tipo **() => Promise<string>** e que apresenta o *fulfillment value* ou a *rejection reason* da *promise* resultante da avaliação de **f**. O componente deve também apresentar um botão que promove a reavaliação da função **f** sempre que premido. Este botão deve estar desabilitado enquanto a promessa retornada pela última avaliação não se tiver completado. O componente deve ser sensível a mudanças na propriedade **f**.

    ```ts
    function PromiseWatcher({f}: {f: () => Promise<string>}) {
    const [waiting, setWaiting] = useState(false)
    const [content, setContent] = useState("")

    const awaitPromise = async () => {
        setWaiting(true)
        try {
            const text = await f()
            setContent(text)
        } catch (e) {
            setContent(e.message)
        } finally {
            setWaiting(false)
        }
    }

    useEffect(() => {
        awaitPromise()
        return () => {}
    }, [f])

    return (
        <div>
            <button onClick={awaitPromise} disabled={waiting}> await </button>
            <textarea value={content}></textarea>
        </div>
    )
    }

    export function demo(){
        const root = createRoot(document.getElementById("container"))
        root.render(<PromiseWatcher f={async () => {
            const response = await fetch('https://httpbin.org/delay/6')
            return response.text()
        }} />)    
    ```
