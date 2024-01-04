# Autenticação

## Informação de autenticação

- Algo que se conhece (password, PIN, passphrases, etc.)
- Algo que se possui (ex. tokens, RSA SecurID)
- Algo que se é (ex. características biométricas)
- Algo que se faz (ex. assinatura manuscrita)
  
## Vulnerabilidades de passwords textuais

- **Ataque de dicionário** - Atacante usa uma lista de palavras-passe conhecidas, ou prováveis, e tenta exaustivamente as entradas da lista, em 1 ou mais utilizadores
- Estes ataques têm como alvo a interface de autenticação dos sistemas ou o local onde está guardada a informação de validação

Para aumentar a proteção contra ataques de dicionário podemos:

- Aumentar a incerteza da password
  - Passwords aleatórias
  - Seleção proativa
  - Verificação offline
- Controlar o acesso à informação de verificação
- Aumentar o tempo de processamento da função f

- Salt

- Limitar o acesso à função de autenticação g(v) após a deteção de tentativas de autenticação erradas
- Técnicas:
  - Backoff: O tempo de execução de g(v) depende do número anterior de tentativas erradas
  - Terminação da ligação
  - Bloqueamento
  - Jailing: Acesso ao serviço com funcionalidade limitada
- Porém é preciso garantir a disponibilidade do serviço.

- Aumentar o custo dos pedidos, diminuindo o número de pedidos realizados através do aumento do seu custo para o cliente, por exemplo através de um captcha (Completely Automated Public Turing test to tell Computers and Humans Apart), que é um teste de desafio-resposta, que permite distinguir humanos de máquinas.

- **Ataques com pré-computação**

- Baseia-se no facto da função f ser igual para todos os utilizadores
- seja D um dicionário de palavras prováveis e M um array associativo
- Pré-computação
  - Para todos a' em D, calcular e armazenar o par (f(a'i), a'i) em M (tal que M[f(a'i)]=a'i)
- A pré-computação é usada para obter a password de qualquer utilizador

