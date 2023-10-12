## 2. Esquemas Assimétricos:

**Características Gerais:**

- Utilizam um par de chaves: uma pública (para cifrar ou verificar assinaturas) e uma privada (para decifrar ou assinar).
- A segurança baseia-se na dificuldade de derivar a chave privada a partir da chave pública.

**Quando são usados:**

- Em sistemas onde as partes não podem compartilhar uma chave secreta previamente.
- Para assinaturas digitais, que garantem a autenticidade e integridade de uma mensagem.

**Algoritmos Comuns:**

- RSA (Rivest-Shamir-Adleman)
- DSA (Digital Signature Algorithm)
- ECC (Elliptic Curve Cryptography)

**Propriedades:**

- Permite que as partes se comuniquem de forma segura sem precisar compartilhar uma chave secreta previamente.
- Geralmente mais lentos do que os esquemas simétricos.
- Vulneráveis a ataques se os parâmetros (como tamanho