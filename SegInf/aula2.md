# Fundamentos de Segurança Informática

**Três pilares da segurança informática:**

- Confidencialidade
- Integridade
- Disponibilidade

- **Criptografia:** ciência de escrever mensagens cifradas.
- **Criptoanálise:** ciência de quebrar códigos e decifrar mensagens.
- **Criptologia:** ciência que reúne criptografia e criptoanálise.

| | Simétricos | Assimétricos |
| --- | --- | --- |
| **Confidencialidade** | Cifra | Cifra |
| **Integridade** | Message Authentication Code (MAC) | Assinatura Digital |

## Criptografia Simétrica

Processo de proteção e desproteção usando a mesma chave
A chave deve ser regularmente atualizada

### Esquema de cifra simétrica

- Algoritmos (G, E, D)
  - **G** - função (probabiliística) de geração de chaves
    - **G: -> Keys(1 Chave do conjunto possível de chaves)**
  - **E** - função (probabilística) de cifra
    - E: Keys -> {0,1}* -> {0,1}*
  - **D** - função (determinística) de decifra
    - D: Keys -> {0,1}* -> {0,1}*
  
{0,1}* - Mensagem binária de qualquer dimensão

