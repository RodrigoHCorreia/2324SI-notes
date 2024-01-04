# Trabalho 1 SegInf

## Identificação do grupo

- Rodrigo Henriques Correia - 48335
- Carlos Guilherme Pereira - 48253
- Tiago Pardal - 47xxx

## Pergunta 1

CI(k1, m) = Es(T(k1)(m)1..L)(m) || T(k1)(m)

Dada a equação, este esquema não cumpre os objetivos de garantia de confidencialidade e autenticidade de mensagens.

Es(k)(m) é um esquema de cifra simétrica, usado para garantir a confidencialidade da mensagem.
T(k)(m) é um esquema de *message authentication code* (MAC), usado para garantir a autenticidade da mensagem.

Quando usados em conjunto de forma correta, é possível garantir a confidencialidade e a autenticidade da mensage, de uma de duas formas:

- **Encrypt-then-MAC**
  - A mensagem é cifrada e depois autenticada
  - A marca indica se houve alteração ou não do criptograma
  - E(k1)(M) || T(k2)(E(k1)(M))
- **MAC-then-Encrypt**
  - A mensagem é autenticada e depois cifrada
  - A marca indica se houve alteração ou não da mensagem
  - T(k1)(M) || E(k2)(T(k1)(M))

O esquema apresentado não irá fornecer garantia de confidencialidade pois a mensagem é encriptada com uma chave que corresponde ao MAC dos primeiros L bits da mensagem (em vez de por exemplo uma k2, diferente de k1), e depois é enviada a autenticação da mensagem com a chave k1 sem qualquer tipo de encriptação. Isto permite a um atacante decriptar a mensagem, pois a chave utilizada na encriptação está visível no canal de comunicação.

## Pergunta 2

Existem alguns motivos pelos quais é tão comum proteger e enviar chaves simétricas com esquemas de cifra assimétrica.
Como o custo computacional da cifra assimétrica é muito superior ao custo computacional da cifra simétrica, é muito mais eficiente encriptar uma mensagem grande com uma chave simétrica, e de seguida encriptar a chave simétrica com um esquema de cifra assimétrico, esquema esse que é computacionalmente mais díficil de quebrar.

## Pergunta 3

### Semelhanças

**Autenticidade**: Ambos os esquemas são usados para autenticar a origem da mensagem. Ao verificar uma assinatura ou um MAC, o receptor pode ter confiança de que a mensagem foi realmente enviada pelo remetente esperado.

**Integridade**: Tanto o esquema de assinatura digital quanto o MAC (Message Authentication Code) são usados para verificar a integridade dos dados. Eles garantem que a mensagem não foi alterada durante a transmissão.

### Diferenças

**Tipos de Chaves**: Em um esquema de assinatura digital, são usadas chaves assimétricas: o remetente assina a mensagem com sua chave privada, e o receptor verifica a assinatura usando a chave pública correspondente do remetente. Em contraste, os MACs utilizam cifra simétrica, onde o remetente e o receptor compartilham a mesma chave secreta. O remetente usa esta chave para gerar o MAC e o receptor a usa para verificar o MAC.

**Garantia de não-repúdio**: Um esquema de assinatura digital fornece a propriedade de não repúdio, isto significa que o remetente não pode negar ter enviado a mensagem, uma vez que só ele possui a chave privada que criou a assinatura. Uma vez que um MAC é gerado usando uma chave secreta que é compartilhada entre o remetente e o receptor, não se pode provar conclusivamente que foi o remetente quem enviou a mensagem.
