# Esquemas, Primitivas, siméticas

- As **primitivas** são **determinísticas**. (Ex. DES, AES)
- **Modo ECB (Electronic Code Book)** é também **determinístico**.
- **Modo CBC (Cipher Block Chaining)** é **probabilístico**, sendo assim já é possível fazer a cifra caso haja blocos repetidos.
  - Em cada bloco é feito um XOR com o criptograma anterior.
  - O primeiro bloco é feito um XOR com um vetor de inicialização (IV) aleatório, fornecido no momento em que vamos fazer a cifra.


```bash
openssl end -des-ecb -e -in msg.txt -out msg.cif -K 18047f5e9778ee41
```
