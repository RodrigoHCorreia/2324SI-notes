# Java Cryptography Architecture (JCA)

## Princípios de desenho

- Independência dos algoritmos e expansibilidade
  - Utilização de esquemas criptográficos, como a assinatura digital e a cifra simétrica, independentemente dos algoritmos que os implementam
  - Capacidade de acrescentar novos algoritmos para os mecanismos criptográficos considerados
- Independência da implementação e interoperabilidade
  - Várias implementações para o mesmo algoritmo
  - Interoperabilidade entre várias implementações
    - Por exemplo, assinar com uma implementação e verificar com outra
  - Acesso normalizado a características próprias dos algoritmos

