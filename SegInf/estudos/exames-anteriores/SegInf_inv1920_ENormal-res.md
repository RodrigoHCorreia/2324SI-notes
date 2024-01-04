# SegInf Inverno 1920 Época Normal - Resolução

## 1

As limitações da sollução de padding em que os bytes em falta são preenchido com zeros, é que na decifra, não é possível distinguir entre os zeros de padding e zeros que pertencem à mensagem original.

## 2

Se o atacante conhecer a função de hash H utilizada pelo sistema, então é possível ao atacante gerar uma mensagem m tal que AEe(m) = m || H(m) irá passar a verificação de integridade, visto que o hash h corresponde ao hash da mensagem m.

## 3

### 3.1

A assinatura de um certificado folha apenas tem em conta o certificado emissor, visto que este certificado é assinado com a chave privada do emissor e verificado com a chave pública deste.

### 3.2

Não existem campos de um certificado X.509 que estejam protegidos por um esquema de cifra, dado que o objetivo do certificado é certificar que a entidade é confiável, pelo que para este efeito é usada uma assinatura digital.

## 4

A JCA disponibiliza várias classes para interagir com os esquemas criptográficos existentes. Através destas classes é possível obter o esquema desejado através do método getInstance que devolve uma implementação do esquema criptográfico. Por exemplo, se o objetivo for assinar um documento digitalmente pode-se usar a classe Signature através da qual podemos chamar o método getInstance, passando como parâmetro o algoritmo desejado.

## 5

### 5.1

A alteração de mensagens durante o handshake é detetada através da mensagem Finished, que garante que o cliente e o servidor receberam mensagem fidedignas.

### 5.2

A troca do pre-master secret através de esquemas assimétricos é insegura, pois se a chave privada for comprometida, então todas as futuras mensagens e anteriores estão também comprometidas, podendo ser decifradas pelo atacante, ou seja, a proprietade de perfect forward secrecy não é garantida. com o uso de esquemas assimétricos.

## 6

Dado que o atacante sabe a construção, este pode simplesmente aplicar um ataque de dicionário em que, neste dicionário, as chaves são os hashes pré-calculados e os valores as palavras passes resultantes. Este ataque é prático, pois basta ao atacanta calcular novamente os hashes para todas as passwords, com base na construção, que não introduz aleatoriedade na construção do hash.

Ainda mais, o uso do algoritmo SHA-1 não é recomendado devido a colisões de hashes, sendo que o atacante também poderia explorar esta vertente.
