# SegInf Verão 2122 - Exame Recurso - Resolução

## 1 V ou F (Primitivas de cifra simétrica)

- O modo de operação ECB não precisa de IV, cao contrário do modo de operação CBC. **Verdadeiro**
- Na prática, as chaves usadas nestas primitivas são normalmente reutilizadas várias vezes, sendo as mesmas chaves usadas ao longo de vários meses ou anos. **Falso**
- Um esquema criptográfico que use a primitiva AES pode usar modos de operação diferentes para cifrar e decifrar (ECB para cifrar e CBC para decifrar). **Falso**
- Estas primitivas usam chaves de pequenas dimensão quando comparadas com as chaves usadas em esquemas assimétricos. **Verdadeiro**

## 2 V ou F (X.509, TLS e JCA)

- Num certificado folha ou intermédio, a assinatura desse certificado é verificada pela chave pública existente no mesmo certificado. **Falso**
- A classe X509Certificate da JCA tem os métodos getPublicKey e getPrivateKey. **Falso**
- No handshake do TLS, cliente e servidor enviam os números client_random e server_random, sobre um canal inseguro. Se os números forem modificados no canal, tal será detetado nas mensagens finais do handshake. **Verdadeiro**
- As chaves usadas no record protocol são derivadas da chave privada do servidor. **Falso**

## 3 V ou F (OAuth 2.0 e OpenID Connect)

- Na framework OAuth 2.0, o valor a colocar no parâmetro scope é introduzido pelo dono de recursos. **Falso** (é introduzido pelo cliente)
- A estrutura id_token é usada pela aplicação cliente para obter mais informações sobre o utilizador (ex. foto de perfil) através do userinfo endpoint. **Falso** (é através do access_token)
- Na framework OAuth 2.0, o access_token tem informação sobre o dono dos recursos cujo objetivo é ser consultada pela aplicação cliente. **Falso**
- Nestes protocolos, e tendo em conta o fluxo authorization code grant, o endereço designado de callback refere-se a um dos endpoints da aplicação cliente **Verdadeiro**

## 4

Modo WRAP/UNWRAP é usado para cifrar e decifrar chaves, enquanto que o modo ENCRYPT/DECRYPT é usado para cifrar e decifrar mensagens.

## 5. Nos certificados X.509 a verificação de autenticidade do certificado é feita com um esquema de assinatura digital. Este objetivo poderia ser obtido com um esquema MAC aplicado ao conteúdo do certificado?

Não, Porque se usassemos MAC aplicado ao conteúdo do certificado iriamos ter uma única chave, que seria a chave privada do emissor, e esta chave seria usada para gerar o MAC e para verificar o MAC. Logo, para verificar a autenticidade do certificado seria necessário ter a chave privada do emissor.

## 6

Caso uma autoridade de certificação alternativa esteja comprometida, então os certificados emitidos por essa AC seriam considerados válidos. O atacante pode assim emitir um certificado fraudulento para o servidor S e este certificado será considerado válido. O atacante pode assim apresentar este certificado fraudulento ao cliente C e este irá aceitar o certificado como válido, pois o certificado é assinado por uma AC válida. Assim, o atacante consegue fazer-se passar pelo servidor S e obter informação confidencial do cliente C.

## 7. A utilização de um salt de 64 bits em vez de 16 bits para armazenar a informação de validação na base de dados aumenta em 4 vezes a dificuldade de realizar um ataque através da interface de autenticação

A afirmação é falsa, pois o tamanho do salt não está diretamente relacionado com a segurança do mesmo. Sim, se o salt for maior o número de possibilidades aumenta logo para realizar um ataque em dicionário ou de força bruta o atacante necessita de mais tempo. No entanto, ao realizar um ataque de força bruta ou tentando adivinhar a password, em nada irá afetar o tamanho do salt.

## 8. Considere uma aplicação web que pretende garantir a autenticidade dos cookies que usa para manter estado de sessão entre browser e servidor HTTP. É mais adequado usar um esquema de MAC, um esquema de assinatura digital, ou qualquer um deles? Porquê?

É mais adequado usar um esquema de MAC. Apesar da assinatura digital ser na globalidade, um método mais robusto e completo, para o caso em concreto é suficiente, mais eficiente e prático utilizar um MAC. Primeiro só existe um agente a validade os cookies que é o servidor, logo uma chave simétrica chega e é menos complexo de gerir do que um par de chaves assimétricas.

## 9. O conjunto designado por PA relaciona utilizadores e permissões. Através deste conjunto, uma política pode indicar que determinado utilizador é hierarquicamente superior a outro e por isso herda as suas permissões

A afirmação é falsa, pois o conjunto PA relaciona utilizadores e permissões, mas não indica que um utilizador é hierarquicamente superior a outro. A relação UA é que indica que um utilizador é hierarquicamente superior a outro.
