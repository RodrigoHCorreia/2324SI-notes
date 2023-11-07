# Bits relevantes das tabelas de paginas

**P** - diz se é valido ou n
**R/W** - diz se é read only ou read write
**U/S** - diz se pode ser usado pelo user
**nx** - se podemos fazer fetch de instruções

**A** - Accessed, são postos a 1 pelo próprio processador quando aquela entrada é usada com sucesso numa tradução.

**D** - Dirty, são posto a 1 pelo próprio processador, se o acesso foi de escrita.

Estes valores voltam a ser postos a 0 pelo sistema operativo.

Cria-se um array dentro da memória física com o mesmo número de entradas que as entradas da memória física, de movo a representá-la.
O que cada entrada do array tem é informação sobre o que se passa na memória, sendo ainda possível ligar um conjunto de entradas em lista, fazendo ligações entre elas.

**Active list** - aprox. ao working set, ou seja a lista dos blocos que têm sido mais usados recentemente.
**Inactive list** - páginas que não têm sido usadas recentemente, mas que já foram usadas.

Conjunto da lista ativa e inativa é o **resident set**.
**Available list** - páginas que não estão a ser usadas.

Cada página da lista tem um bit R.

O kernel tem um código que vai percorrer as listas, de baixo para cima, à procura de páginas que não estão a ser usadas para as colocar na lista de páginas disponíveis.
Isto é feito indo às Page Table Entries, consultando os bits de Accessed e Dirty, e se estes estiverem a ser usados, metem o bit R da página a 1, e os bits A e D da PTE a 0.

Como isto é um algoritmo demoroso, o kernel por omissão só percorre 1/6 da lista inativa, este algoritmo é corrido sempre que os valores esperados para cada página não estão a ser cumpridos.

Por normal a lista inativa é maior que a lista ativa.

Se o algoritmo fica com dificuldades em libertar a lista em causa, o kernel aumenta o número de páginas que o algoritmo percorre, procurando libertar mais páginas.

Quando o algoritmo vai percorrer a lista inativa e encontra duas vezes consecutivas um bit a 0, envia a página para a lista de páginas disponíveis, se encontra duas vezes consecutivas um bit a 1, a mesma transita para o topo da lista ativa, com o bit R a 0.

Se a lista de páginas ativas estiver com capacidade superior ao esperado, o algoritmo começa a percorrer a lista ativa, procurando transitar páginas para o topo da lista inativa, com o bit a 1.

Páginas novas vão para o topo da lista inativa, porque existe a probabilidade das mesmas só seres preciso uma vez.
