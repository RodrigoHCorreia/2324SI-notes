# Continuation of spring-context, Servlets

## Bean Functions

- **@Bean** - indica que o método devolve um bean
Às vezes criar uma instância não é feita diretamente com o construtor, mas sim através de outras vias, para resolver isto utilizamos **bean functions**.
- Estas bean functions estão encapsuladas dentro de uma class de configuração BeanConfig.

```kotlin
class BeanConfig {
    @Bean
    fun cookieHandler(): CookieHandler = CookieManager()

    @Bean
    fun httpClient(cookieHandler: CookieHandler): HttpClient = 
        HttpClient
            .newBuilder()
            .cookieHandler(cookieHandler)
            .build()

}

```

## Scope

- **@Scope** - indica o scope.

### Different Scopes

- **singletons** (default scope) - apenas uma instância do componente e usada para **satisfazer todas as dependências** i.e. usada em todas as injeções.
  - Sharing - **the need to be tread-safe!**

- **prototype** - uma nova instância do componente é criada para cada injeção, **não é normalmente utilizada.**
  - No Sharing

## Recommended Practices

- Componentes devem usar inversão de controlo, contudo eles não devem depender de um container expecífico.
  - Porquê?
    - **Testabilidade** - não queremos ter de usar um container para testar um componente.
    - **Reusabilidade** - não queremos ter de usar um container para usar um componente.

- Preferir sempre **injeção de construtor** em vez de injeção de propriedades.

# Servlets

- **Servlets** são componentes Java que permitem criar aplicações web.