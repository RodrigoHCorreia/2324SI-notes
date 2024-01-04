# Seg Inf - Exame Normal 2021/2022 - Resolução

## 1 - Verdadeiro ou Falso (Cifras de Bloco)

- A mesma primitiva pode ser usada com diferentes modos de operação. - **Verdadeiro**
- Estas primitivas são determinísticas, ou seja, usando a mesma chave k, e o mesmo bloco b, DES(k)(b) dá o mesmo resultado - **Verdadeiro**
- Os modos de operação ECB e CBC só funcionam com chaves de dimensão superior a 64 bits - **Falso** (ECB funciona com chaves de 56 bits)
- O modo de operação GCM dá garantias de autenticidade da mensaagem cifrada, sendo possível detetar modificações antes da decifra - **Verdadeiro**

## 2 - Verdadeiro ou Falso (X.509, TLS e JCA)

- Num certificado folha ou intermédio, a assinatura desse certificado é verificada pela chave pública existente no mesmo certificado - **Falso** (é verificada pela chave pública do certificado emissor)
- A classe X509Certificate da JCA tem os métodos getPublicKey e getPrivateKey - **Falso** (não tem o método getPrivateKey)
- No handshake do TLS, cliente e servidor enviam os números client_random e server_random, sobre um canal inseguro. Se os números forem modificados no canal, tal será detetado nas mensagens finais do handshake - **Verdadeiro**
- As chaves usadas no record protocol são derivadas da chave privada do servidor - **Falso** 

## 3 - Verdadeiro ou Falso (OAuth 2.0 e OpenID Connect)

- Em ambos os protocolos, o termo aplicação cliente, ou relying party, designa o browser através do qual o utilizador acede ao serviço - **Falso** (o browser é o user-agent)
- A estrutura designada como access_token tem de ser usada nos pedidos ao servidor de recursos - **Verdadeiro**
- Em ambos os protocolos, a aplicação cliente e o servidor de autorização partilham uma chave privada de longa duração para assinar mensagens - **Falso** (não partilham nenhuma chave privada)
- Nestes protocolos, e tendo em conta o fluxo authorization code grant, o endereço designado de callback refere-se a um dos endpoints disponíveis no servidor de autorização - **Falso** (refere-se a um endpoint disponível na aplicação cliente)

## 4

Se é computacionalmente viável encontrar dois valores x e x' tal que MD5(x) = MD5(x'), então significa que existe uma colisão na função de hash MD5. se esta função fosse usada para gerar a assinatura digital de um certificado X.509, significaria que um atacante poderia criar um certificado fraudulento que seria aceite legítimo pois ambos teriam a mesma assinatura digital (MD5(x) = MD5(x')).

## 5 Alice quer ligar-se a C2

Cliente precisa de: Alice e respetiva chave (KSA1), Int1, CA2.
Servidor precisa de: C2 e respetiva chave (KSC2), Int2, CA1.

## 6 JCA

Dois motivos para existirem os métodos update e doFinal e não apenas o método update é que:
- Caso haja necessidade de acrescentar padding à mensagem, e isto só pode ser feito se se souber que é o último bloco da mensagem.
- Finaliza o processo de cifra, e devolve o resultado final

## 7

Uma aplicação que guarde passwords usando salt diferente por utilizador e uma função de hash, tem vantagens comparando com uma solução que usa cifra simétrica ou assimétrica para guardar as passwords:
- Proteção contra ataques de dicionário e de força bruta, pois o salt faz com que mesmo que dois utilizadores tenham a mesma password, o hash seja diferente. Isto faz com que o atacane não consiga simplesmente pre-computar um dicionário de valores hash conhecidos e compará-los com os hashes das passwords.
- Mesmo em caso da base de dados ser comprometida, o atacante não consegue obter as passwords dos utilizadores, pelo facto do salt ser único e as funções de hash serem unidirecionais, ao contrário de uma cifra simétrica ou assimétrica, em que o atacante pode simplesmente usar a chave para decifrar as passwords.

## 8

As vantagens em usar um esquema de MAC ou um de assinatura digital para garantir a autenticidade dos cookies que se usa para manter estado de sessão entre um browser e um servidor HTTP é que com MAC, a rapidez de computação é maior do que com assinatura digital, pois o MAC usa cifra simétrica, enquanto que a assinatura digital usa cifra assimétrica. No entanto, a assinatura digital garante a propriedade de não-repúdio, enquanto que o MAC não garante.
A assinatura digital é mais robusto e completo, porém com MAC só temos de gerir uma chave secreta que se encontra no servidor para gerar e verificar o MAC.

## 9 RBAC

A relação UA é uma associação estática entre utilizadores e roles, sobre quais roles um utilizador tem acesso. porém no na sessão, é que o utilizador efetivamente os ativa. Por exemplo, apesar de um utilizador ter um role muito elevado, o mesmo pode querer ativar um role mais baixo para por exemplo verificar o que um utilizador com esse role tem acesso.

## 10 OAuth 2.0 e OpenID C\onnect

### 10.1 Como é obtido o client_id e o client_secret?

- O client_id e o client_secret são obtidos através do registo na aplicação cliente no servidor de autorização. O servidor de autorização gera um client_id e um client_secret para a aplicação cliente, e envia-os para a aplicação cliente.

## 1.2 Qual o mecanismo que permite à aplicação cliente relacionar um pedido de autorização com a resposta entregue pelo servidor de autorização, e como é usado?

- O mecanismo que permite à aplicação cliente relacionar um pedido de autorização com a resposta entregue pelo servidor de autorização é o state. O state é um parâmetro que é enviado no pedido de autorização, e que é devolvido na resposta do servidor de autorização. A aplicação cliente pode usar este parâmetro para relacionar o pedido com a resposta. Ele é usado para evitar ataques CSRF.