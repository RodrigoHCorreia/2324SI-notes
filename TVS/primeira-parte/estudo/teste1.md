# Teste tvs parcial 1 22/23

## 1.

### 1.a

18
19
21
output1.txt

77
78
79
80
output2.txt

### 1.b

fork para correr o ex1 com os parametros 18
pipe do STDOUT do ex1 para o pipe, de seguida outro fork para 

cria pipe

## 2.

### 2.a

64

17		1	9	3(9 bits PD)	0 (12 bits offset)

0x088041203000
0000 1000 1000 0000 0100 0001 0010 0000 0011 	0000 0000 0000

### 2.b

É possível ler mas proibido escrever em todos os endereços (512). Isto porque a PTE que referencia o indice 9 da tabela tem o bit R/W a 0, a tabela completa que está nesse índice é Read only.

## 3.

### 3.a

Se esta biblioteca for carregada com dlopen, iremos criar duas novas regiões no espaço de endereçamento do processo, uma na secção .text para código, e outra na secção .data para dados, com 4KB cada.

### 3.b

Ao chamar a função func em 4 processos distintos, iremos ler do .data, Como esta região tem 4KB, o Pss irá ser 4kb / 4 = 1KB.

## 4.

Exceções são interrupções do processador, e sempre que estamos a lidar com exceções, temos de estar em modo priveligiado.
Exemplo de um Erro: Um processo tenta aceder a um processo não permitido (Fora da gama permitida).
Exemplo de um não erro: Page fault. Um processo tenta aceder a uma página não mapeada o que causa uma page fault exception. No entanto esta exceção é utilizada para implementar o paging, pelo que não se trata de um erro.

## 5

### 5.a

O backing storage de uma página pertencente ao mapeamento da secção de código de um ficheiro executável é o próprio ficheiro executável.

### 5.b

Se a página foi modificada, a mesma irá encontrar-se na swap partition.

### 5.c

Swap partition.

### 5.d

Ficheiro.

### 5.e

Zero page.
