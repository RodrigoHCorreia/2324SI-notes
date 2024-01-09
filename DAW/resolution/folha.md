Idempotência é crucial para garantir: Consistência e Previsibilidade: O sistema mantêm um estado previsível, mesmo quando existem retentativas ou múltiplos pedidos, e.g. caso a comunicação com o servidor falhe antes do cliente receber a resposta do servidor, o cliente pode repetir o pedido, tendo a certeza que esse pedido extra não vai gerar efeitos colaterais indesejados, mesmo que as respostas obtidas pelo servidor sejam diferentes.

Métodos são considerados safe se a sua semãncia é essencialmente read-only, i.e., o cliente não espera que o servidor mude de estado como resultado da aplicação de um método safe a um recurso. Da mesma forma, o uso razoável de um método safe não deve causar danos no servidor.
A necessidade de distinguir entre métodos safe e unsafe é permitir que processos de recuperação automática e otimização de cache funcionem sem quaisquer riscos de causarem danos.

HttpServlet - responsible for ultimately handling an HTTP request by populating an HttpServletResponse using information from a HttpServletRequest.
HttpFilter - contributes to the handling of HTTP responses, by using the request’s information, present in an HttpServletResponse instance, and eventually mutating an HttpServletResponse before and after the request is handled by a server. Multiple filters are organized in a pipeline.

Inversão de controlo é uma técnica de design onde uma classe recebe as suas dependências em vez de as criar.
Injeção de dependências é o ato de fornecer as dependências à instância da classe que as precisa.

Siren:

```json
{
  "class": [ "order" ],
  "properties": { 
      "orderNumber": 42, 
      "itemCount": 3,
      "status": "pending"
  },
  "entities": [
    { 
      "class": [ "items", "collection" ], 
      "rel": [ "http://x.io/rels/order-items" ], 
      "href": "http://api.x.io/orders/42/items"
    },
    {
      "class": [ "info", "customer" ],
      "rel": [ "http://x.io/rels/customer" ], 
      "properties": { 
        "customerId": "pj123",
        "name": "Peter Joseph"
      },
      "links": [
        { "rel": [ "self" ], "href": "http://api.x.io/customers/pj123" }
      ]
    }
  ],
  "actions": [
    {
      "name": "add-item",
      "title": "Add Item",
      "method": "POST",
      "href": "http://api.x.io/orders/42/items",
      "type": "application/x-www-form-urlencoded",
      "fields": [
        { "name": "orderNumber", "type": "hidden", "value": "42" },
        { "name": "productCode", "type": "text" },
        { "name": "quantity", "type": "number" }
      ]
    }
  ],
  "links": [
    { "rel": [ "self" ], "href": "http://api.x.io/orders/42" },
    { "rel": [ "previous" ], "href": "http://api.x.io/orders/41" },
    { "rel": [ "next" ], "href": "http://api.x.io/orders/43" }
  ]
}
```
Explicar o que é cada cena

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

## TODOS

- Exercícios práticos resolvidos
- Exercícios teóricos (maybe)
- 