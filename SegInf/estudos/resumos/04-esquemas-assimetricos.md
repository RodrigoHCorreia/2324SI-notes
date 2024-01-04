# Esquemas Assimétricos

**Esquemas de cifra - qual a operação privada?**

- Todos podem cifrar, apenas o recetor pode decifrar

**Esquemas de autenticação - qual a operação privada?**

- Todos podem verificar, apenas o emissor autorizado pode assinar (gerar a marca)

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
- Custo computacional significativamente maior do que os esquemas simétricos.

- assinar != decifrar; verificar != cifrar

## Assinatura digital

- Cada interveniente tem 1 par de chaves por cada identidade digital
- Processo de assinatura usa chave privada
- Processo de verificação usa chave pública
- Par de chaves usadas durante um largo período de tempo
- Chave pública difundida através de certificados digitais

Propriedades de segurança:

- falsificação seletiva - dado m, encontrar s tal que V(kv)(s,m) = true
- falsificação existencial - encontrar (s,m) tal que V(kv)(s,m) = true
- note-se que kv é conhecido.
- assinatura s (pertencente ao conjunto Signatures) tem tipicamente dimensão fixa
  - por exemplo 160, 1024, 2048 bits
  