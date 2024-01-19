# Teste Final, Época Normal, Semestre de Inverno, 22/23

1. (6) Para cada uma das seguintes questões, selecione a opção de resposta correta. Cada resposta incorrecta subtrai 1/3 pontos da questão à classificação total do conjunto de questões deste grupo.

    1. No protocolo **HTTP**, o método **DELETE** é:
        1. Não *safe* e não idempotente.
        2. *Safe* e não idempotente.
        3. Não *Safe* e idempotente.
        4. *Safe* e idempotente.

        ```
        3 - Não Safe e idempotente. Um método é safe se não alterar o estado do servidor e é idempotente se o resultado de executar o método uma ou mais vezes for o mesmo.
        ```

    2. No protocolo **HTTP**, o conceito de *interface uniforme* significa que:
        1. Os **URIs** têm de ter sempre a mesma estrutura tal como usar nomes pluralizados (e.g., **/games/123** em vez de **/game/123**) e ter sempre os identificadores da base de dados no caminho e não na q*uery string*(e.g. **/games/123** em vez de **/games?id=123**).
        2. O significado dos *status codes* nas mensagens de resposta não depende do recurso acedido.
        3. Devem ser usados *media types* baseados em **JSON** em todas as representações (e.g., **application/json e application/problem+json**).
        4. Não podem ser usados métodos não definidos no **RFC 7231** - *Hypertext Transfer Protocol (HTTP/1.1): Semantics and Content*.

        ```
        2
        ```

    3. No contexto de **APIs HTTP** qual a forma que sugere para comunicar informação de erro específica da aplicação em resposta a pedidos **HTTP**.
        1. Definindo e usando um novo *status code* nas mensagens de resposta.
        2. Colocando essa informação no *payload* da mensagem de resposta.
        3. Definindo e usando um novo *header* nas mensagens de resposta.
        4. Retornando uma exceção criada especificamente para representar esse tipo de informação.

        ```
        2
        ```

    4. Para se suportar *deep-linking* no contexto de uma *single page application* é necessário configurar o servidor que serve essa aplicação da seguinte forma.
        1. Caso o caminho presente num pedido **GET** não esteja associado a um ficheiro então é retornada uma resposta de sucesso com o conteúdo de **index.html** em vez de uma resposta com *status code* **404**.
        2. Caso o caminho presente num pedido **GET** não esteja associado a um ficheiro então é retornada uma resposta de redireção para o caminho **/index.html.**
        3. O servidor usar a **API** de história para navegar para o *deep-link*.
        4. O servidor usar React Router para navegar para o *deep-link*.

        ```
        1
        ```

    5. A avaliação da expressão **JSX \<A>\<p>Hello\</p>\</A>** é equivalente a qual das seguintes expressões:
        1. **A({children=[document.createElement("p"), "hello"]})**
        2. **React.createElement("A", null, React.createElement("p", null, "Hello"))**
        3. **React.createElement(A, null, document.createElement("p", null, "Hello"))**
        4. **React.createElement(A, null, React.createElement("p", null, "Hello"))**

        ```
        4
        ```

    6. No contexto da biblioteca **React** uma função *hook*:
        1. Pode ser chamada dentro de um *callback* associado a um evento.
        2. Pode ser chamada dentro da função passada ao **useEffect**.
        3. Pode ser chamada dentro de outra função *hook*.
        4. Nenhuma das anteriores.

        ```
        
        ```

2. (2) No âmbito da biblioteca Spring indique qual a consequência de anotar classes com a anotação **@Component**.

    ```
    A consequência de anotar classes com a anotação @Component é que o Spring vai criar uma instância dessa classe e vai registar essa instância no contentor de injeção de dependências.
    ```

3. (2) Tendo em conta que os *browsers* modernos já suportam o sistema de módulos **ECMAScript Modules (ESM)**, qual a relevância de se ainda usar uma ferramenta como o *webpack*?

    ```
    No caso de utilizarmos js, 
    apesar de não ser preciso, é relevante. evitamos 1 pedido http por modulo, conseguindo num só pedido
    podemos n querer fornecer o código fonte diretamente, ou minimizamos com o bundle normal (para reduzir a sua dimensão), ou para compilar de ts para js.
    ```

4. (4) Realize um ou mais componentes para uso com a biblioteca **Spring MVC** de forma a expor recursos nos caminhos **/handlers** e **/handlers/{handler-id}**. Um pedido de método **GET** a **/handlers** retorna uma representação **JSON** contendo uma lista de *links* para caminhos com a forma **/handlers/{handler-id}** um para cada *handler* que tenha sido executado até ao momento. Um pedido para **/handlers/{handler-id}** retorna uma representação com o número de vezes que o *handler* foi executado caso **handler-id** seja o identificador de um *handler* executado pelo menos uma vez. Assuma que todos os *handlers* são do tipo **HandlerMethod** e use o método **getShortLogMessage** para obter o identificador de um *handler*.

    ```kotlin
    data class HandlerInfo(val id: String, var count: Int = 0)

    @Service
    class HandlerService {
        private val handlers = mutableMapOf<String, HandlerInfo>() 

        private val lock = ReentrantLock()

        fun executeHandler(id: String) = lock.withLock {
            val handler = handlers.getOrPut(id) { HandlerInfo(id) }
            handler.count++
        }

        fun getHandler(id: String): HandlerInfo? = lock.withLock { handlers[id] }

        fun getAllHandlers(): List<HandlerInfo> = lock.withLock { handlers.values.toList() }
    }

    @Component
    class HandlerInterceptor(private val handlerService: HandlerService) : HandlerInterceptor {

        override fun postHandle(request: HttpServletRequest, response: HttpServletResponse, handler: Any, modelAndView: ModelAndView?) {
            if (handler is HandlerMethod) {
                val handlerId = handler.method.getShortLogMessage()
                handlerService.executeHandler(handlerId)
            }
        }
    }

    @RestController
    @RequestMapping("/handlers")
    class HandlerController(private val handlerService: HandlerService) {

        @GetMapping
        fun getAllHandlers(): ResponseEntity<List<String>> {
            val handlers = handlerService.getAllHandlers()
            val links = handlers.map { "/handlers/${it.id}" }
            return ResponseEntity.ok(links)
        }

        @GetMapping("/{handlerId}")
        fun getHandler(@PathVariable handlerId: String): ResponseEntity<Any> {
            val handler = handlerService.getHandler(handlerId)
            return if (handler != null) {
                ResponseEntity.ok(mapOf("id" to handler.id, "count" to handler.count))
            } else {
                ResponseEntity.notFound().build()
            }
        }
    }
    ```

5. (4) Realize um componente para uso com a biblioteca **React** recebendo um **URI** e um período temporal em milissegundos. O componente deve realizar periodicamente um pedido de método **GET** para esse **URI** e apresentar ou atualizar o conteúdo (*payload*) textual da resposta numa caixa de texto (*textarea*) independentemente do *status code* da resposta. Caso a realização do pedido resulte numa exceção, a caixa de texto deve apresentar o texto associado a essa exceção. O componente deve ser sensível a mudanças no **URI** ou no período temporal.

    ```tsx
    import React, { useState, useEffect } from 'react';

    interface Props {
        uri: string;
        interval: number;
    }

    function PeriodicRequest({ uri, interval }: Props) {
        const [content, setContent] = useState('');

        useEffect(() => {
            const fetchData = async () => {
                try {
                    const response = await fetch(uri);
                    const text = await response.text();
                    setContent(text);
                } catch (error) {
                    setContent(error.toString());
                }
            };

            // Executa imediatamente e depois em intervalos
            fetchData();
            const intervalId = setInterval(fetchData, interval);

            // Limpeza no desmonte do componente
            return () => clearInterval(intervalId);
        }, [uri, interval, setContent]); // Dependências: uri e interval

        return <textarea value={content} readOnly />;
    }

    export default PeriodicRequest;
    ```

6. (2) Realize a função

    **useCounter(initial: number): [observed: number, inc: () => void, dec: () => void]** 

    para ser usado como *hook* em componentes para a biblioteca **React**. Este *hook* serve para gerir um contador retornando a função um *array* com três elementos: o valor atual do contador, uma função para incrementar o contador e uma função para decrementar o contador.

    ```ts
    function useCounter(initial: number): [observed: number, inc: () => void, dec: () => void] {
        const [counter, setCounter] = useState(initial)

        const inc = (() => {
            setCounter(prev => prev + 1)
        })
          
        const dec = (() => {
            setCounter(prev => prev - 1)
        })

        return [observed: counter, inc: inc, dec:dec]
    }
    ```
