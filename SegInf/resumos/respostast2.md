# Respostas téoricas - Trabalho 2

## 1. 

### a)

A propriedade *perfect forward secrecy* é a propriedade do handshake que garante que se a chave privada for comprometida, não é possível decifrar
master secret anteriores.
O motivo pelo qual a propriedade *perfect forward secrecy* não é garantida usando o processo base com RSA para estabelecer o **master_secret** é porque caso um atacante consiga obter a chave privada do servidor em algum momento no futuro, é possível decifrar todas as comunicações passadas, que foram protegidas com essa chave, isto viola a propriedade *perfect forward secrecy*.

### b)

Dois possíveis ataques ao *record protocol* são:

- Um ataque de **repetições de mensagens**, que é quando um atacante tenta sobrecarregar o sistema enviando um grande número de mensagens repetidas, que podem ser prevenidas através do número de sequência.

## 2.

O uso da tecnica de CAPTCHA contribui sim para mitigar ataques de dicionário à informação de validação, porque aumentamos o custo dos pedidos para o cliente, pois este exige que o cliente resolva um desafio computacional que é difícil para computadores, dificultando assim ataques automatizados de dicionário.

## 3.

Para detetar se o conteúdo do cookie, que armazena um JWT com o identificador do utilizador foi adulterado no browser, a aplicação servidor pode utilizar o o mecanismo de verificação de integridade do JWT. O JWT é constituido pelo header, payload e signature, sendo que a signature é gerada usando o header e o payload codificados em base64 e uma chave secreta do servidor através de um HMAC. Assim, a integridade do JWT é assegurada e qualquer modificação no conteúdo do token será detetada pelo servidor através do processo de verificação da assinatura.

## 4.

### a)

No contexto do OpenID Connect, está previsto o uso da estrutura JWT para um ID token. Este, é um conjunto de asserções sobre um utilizador autenticado e é estruturado como um JSON Web Token (JWT) assinado pelo fornecedor de identidade​​. O objetivo do ID token é fornecer informações de autenticação do usuário de uma forma que possa ser facilmente validada e confiável, devido à sua natureza assinada.

### b)

Após o dono do recurso ter autorizado e consentido o uso de um recurso, a aplicação cliente realiza as seguintes ações para conseguir fazer pedidos ao servidor de recursos:
Envia um pedido POST para o token endpoint do servidor de autorização, incluindo o tipo de concessão (grant_type) como código de autorização (authorization_code), o código de autorização obtido e o URI de redirecionamento.
Recebe uma resposta do servidor de autorização que contém o access token, o tipo de token, um refresh token (opcional), a duração de validade do token (expires_in) e o id_token (no caso do OpenID Connect)​​.
De seguida utiliza o access token obtido para fazer pedidos ao servidor de recursos, incluindo o token no cabeçalho de autorização das requisições HTTP.

## 5.

Para determinar o conjunto total de permissões para o utilizador u4 no modelo de controlo de acessos RBAC1, podemos utilizar as informações fornecidas e as fórmulas associadas ao RBAC. Vamos considerar os seguintes elementos:

1. **Utilizadores (U):** {u1, u2, u3, u4}
2. **Hierarquia de Papéis (RH):** {M ⪯ T, M ⪯ D, D ⪯ S, T ⪯ S, T ⪯ T2, D ⪯ D2}
3. **Atribuições de Utilizador para Papéis (UA):** {(u1, M), (u2, T2), (u3, D2), (u4, S)}
4. **Atribuições de Papéis para Permissões (PA):** {(M, p1), (D, p2), (T, p3), (D2, p5), (T2, p4)}

Dado que u4 está atribuído ao papel de Supervisor, precisamos considerar todas as permissões associadas a este papel, bem como as permissões dos papéis júnior a ele na hierarquia, ou seja, Developer Tester e Member.
O conjunto total de permissões para o utilizador u4 numa sessão é a união das permissões associadas aos seus papéis na sessão:

- Permissões de Member (M): p1
- Permissões de Developer (D): p2
- Permissões de Tester (T): p3

Portanto, o conjunto total de permissões para u4 é: {p1, p2, p3}. As permissões D2 e T2 não são incluídas, pois não fazem parte da hierarquia direta de Supervisor.