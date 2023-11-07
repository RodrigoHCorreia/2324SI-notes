# Aula 9

**Resident Set:**

- RAM ocupada
- Subconjunto do espaço de endereçamento que efetivamente está mapeado para memória

**Working Set:**

- Endereços de memória necessários que serão usados num determinado tempo

**Nota:** Somar o resident set de diferentes processos que possam ter páginas de endereçamento partilhadas não irá dar efetivamente o valor que as mesmas ocupam em memória.

**Pss** - dá-nos um número mais apróximado da contribuição que cada processo tem para a total RAM ocupada.

Se tiver um bloco de memória física com dados que já n esteja a ser usada e queiramos libertar, guardamos o conteudo do bloco na **swap partition** no disco, e libertamos aquela gama de endereços, se mais tarde houver um acesso aquela gama de endereços vai ocorrer um page fault, e vai ser preciso ir ao disco buscar os dados para os trazer novamente para a RAM.

O nome da técnica de guardar dados secundários noutro espaço sem ser a RAM, onde estão os swap partitions designa-se de memória virtual

**O QUE FAZ APARECER O ESPAÇO DE ENDEREÇAMENTO VIRTUAL:**

- Ele nasce do **ficheiro executável**, de seguida vem das **bibliotecas dinâmicas** que podem ser carregadas, Temos ainda de ter **pelo menos um Stack**, e um **Heap**. A execução do programa pode ainda dar origem a **ficheiros mapeados em memória**.

**Backing storage:**

- Zona de memória secundária que armazena dados de uma página virtual quando esta não está mapeada para RAM.
- Responde pelos dados quando ocorre um page fault por falta de mapeamento.

backing storage é um elemento em disco onde ficam os dados quando retiramos uma página física de memória
**ou a mesma está clean e o backing storage é o sítio em disco original**
**ou está dirty e o backing storage passa a ser o swap file**
para sitios como bss, entre outros, vem sempre o swap file
em código e constantes, é sempre o ficheiro de onde vieram

Zero page - página na memória física que está toda com 0s.

ro CoW - alocamos a apontar para a zero page, e quando escrevemos nessa página, ai é que vai ser alocada a página na memória física, vai ser feita a escrita ai e o backing file aqui passa a ser o swap partition.
