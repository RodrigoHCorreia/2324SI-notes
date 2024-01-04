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
- Nestes protocolos, e tendo em conta o fluxo authorization code grant, o endereço designado de callback refere-se a um dos endpoints disponíveis no servidor de autorização. **Falso** (refere-se a um endpoint disponível na aplicação cliente)