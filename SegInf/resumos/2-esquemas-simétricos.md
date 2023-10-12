## 1. Esquemas Simétricos:

**Características Gerais:**

- Neste esquema, a mesma chave é usada tanto para cifrar quanto para decifrar a informação.
- As suas chaves são normalmente usadas durante pouco tempo.
- A segurança do esquema depende da confidencialidade da chave compartilhada.
- Geralmente, são mais rápidos do que os esquemas assimétricos.

**Quando são usados:**

- Em sistemas onde a velocidade é crucial, como na cifragem de grandes volumes de dados.
- Em sistemas onde as duas partes podem compartilhar uma chave secreta de forma segura.

### Cifra simétrica

**Algoritmos (G,E,D)**

- **G** - função (probabiliística) de geração de chaves
  - **G: -> Keys(1 Chave do conjunto possível de chaves)**
- **E** - função (probabilística) de cifra
  - E: Keys -> {0,1}* -> {0,1}*
- **D** - função (determinística) de decifra
  - D: Keys -> {0,1}* -> {0,1}*
  
{0,1}* - Mensagem binária de qualquer dimensão

**Algoritmos Comuns:**

- AES (Advanced Encryption Standard)
- DES (Data Encryption Standard)

**Propriedades:**

- Requerem que a chave seja mantida em segredo.
- **Não garante integridade**
- É computacionalmente infazível obter a mensagem a partir do criptograma sem a chave secreta.

**Modos:**

- **Eletronic-Codebook (ECB)**
  - A primitiva garante que os padrões do bloco em claro não passam para os blocos cifrados
  - Blocos iguais de texto em claro produzem blocos iguais de texto cifrado
  - A cifra é realiza de forma independente para cada bloco
  - A ocorrência de erros num bloco de texto afeta apenas a decifra desse bloco
  - Permite acesso aleatório para decifra e recifra de múltiplos blocos

- **Cipher-Block Chaining (CBC)**
  - Sob a mesma chave e sob o mesmo vector de iniciação, duas mensagens iguais implicam criptogramas iguais
  - A cifra de um bloco depende do bloco anterior
  - A ocorrência de erros num bloco cj de texto cifrado afeta a decifra do próprio bloco e do bloco seguinte cj+1. A decifra do bloco cj+1 terá erros nas mesmas posições que cj.

![Cifra e Decifra CBC](image.png)

- **Cipher-Feedback (CFB)**

- **Output-Feedback (OFB)**

- **Counter (CTR)**
  - Sob a mesma chave e sob o mesmo vector de iniciação, duas mensagens iguais implicam criptogramas iguais
  - A ocorrência de erros num bloco de texto cifrado afeta apenas a decifra desse bloco. O bloco resultante mj resultade da decifra do bloco cj terá erros nas mesmas posições que cj.
  - Permite acesso aleatório para decifra e recifra de bits
  - É relativamente fácil de manipular um determinado bloco de texto em claro

### MAC - Message Authentication Code

**Algoritmos (G,T,V)**

- **G** - função (probabiliística) de geração de chaves
  - **G: -> Keys(1 Chave do conjunto possível de chaves)**
- **T** - função (probabilística) de geração de marcas
  - T: Keys -> {0,1}* -> **Tags**
- **V** - função (determinística) de verificação de marcas
  - V: Keys -> (Tags x {0,1}*) -> {true, false}

**Cifra autenticada:**

- Para garantir confidencialidade e simultaneamente autenticidade, tem de se usar uma combinação dos esquemas de cifra e MAC.

- Existem duas abordagens:
  - **Encrypt-then-MAC**
    - A mensagem é cifrada e depois autenticada
    - A marca indica se houve alteração ou não do criptograma
    - E(k1)(M) || T(k2)(E(k1)(M))
  - **MAC-then-Encrypt**
    - A mensagem é autenticada e depois cifrada
    - A marca é gerada sobre a mensagem, e é posteriormente tudo cifrado
    - E(k1)(M || T(k2)(M))

- Existem modos de operação cujo objetivo é produzirem uma cifra autenticada, combinando as operações num só algoritmo
  - **Galois/Counter Mode (GCM)**
  - **Offset Codebook Mode (OCB)**
  - **Counter with CBC-MAC (CCM)**
  
