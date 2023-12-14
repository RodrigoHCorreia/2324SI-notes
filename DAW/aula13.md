# Onde manter a sessão do utilizador

O token pode ser armazenado em vários sítios:

- Memory (mas se o browser fechar ou a página for recarregada, o token é perdido, e isto é desinteressante)
- LocalStorage (torna o token vulnerável a ataques XSS)

Ataque XSS: um atacante consegue injetar código malicioso no nosso site, e esse código malicioso consegue aceder ao LocalStorage e roubar o token.

Cookie: é um mecanismo de armazenamento de dados no browser, que é enviado para o servidor em cada pedido HTTP. (o que vamos utilizar)

3 atributos que podemos meter nas bolachas para as tornar mais seguras:

- Secure: só é enviado para o servidor se a ligação for HTTPS
- HttpOnly: não é possível aceder ao cookie através de JavaScript
- SameSite: só é enviado para o servidor se o pedido for originado pelo mesmo site

**Cross-Site Request Forgery (CSRF):** um atacante consegue fazer com que o browser faça um pedido HTTP para o nosso servidor, e esse pedido é feito com as credenciais do utilizador.

## Site and Origin

Site origin:

Site: TLD+1

Exemplo:
https://example.org -> tld = org, tld+1 = example.org
example.co.uk -> tld = co.uk, tld+1 = example.co.uk

Origem: par (scheme + host + port)
neste caso seria (https, example.org, 443)

No caso dos localhost:
http://localhost:3000 -> (http, localhost, 3000)
http://localhost:5000 -> (http, localhost, 5000)

São o mesmo site, porem com origens diferentes.

## CORS

Cross Origin Resource Sharing (CORS): um atacante consegue fazer com que o browser faça um pedido HTTP para o nosso servidor, e esse pedido é feito com as credenciais do utilizador.

estamos a desenvolver e temos um webpack-dev-server no 8080
depois temos a JVM com a nossa API no 8000

A app que corre no ambito do browser está na origem (http, localhost, 8080)
Quando for feito um pedido para a API, a origem associada ao pedido é (http, localhost, 8000)

Aqui existe Cross Origin.

Por omissão estes pedidos estão protegidos.

Faz um pedido preflight (OPTIONS) para a API e envia um conjunto de informação em headers, só se a resposta for sim é que a ligaçao é feita.

Temos então de configurar CORS na nossa API.
Quais são as origens, quais os headers extras que os pedidos podem ter e os métodos que podem ser usados. (existe ainda a possibilidade de durante quanto tempo o browser pode guardar a resposta para não ter de fazer constantemente pedidos preflight).

um proxy é um intermediário entre o browser e o servidor.
Vamos configurar um proxy no webpack-dev-server para que os pedidos para a API sejam reencaminhados para a JVM.
