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

Exceções são interrupções do processador, e sempre que estamos a lidar com exceções, temos de estar 