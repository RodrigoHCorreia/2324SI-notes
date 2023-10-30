# Aula 7 Exercícios

O **significado especial**  do index.html para o servidor, é que este é o ficheiro que é servido por omissão, sendo assim não precisa de ser especificado no URI.

O index.html no entanto, não tem qualquer tipo de significado para o browser

Document é um objeto que fornece acesso a todos os elementos html do documento.

document.getElementById("main-heading") vai buscar o elemento no documento com o id main-heading

o console.log(mainHeading) apresenta null porque o html ainda não foi carregado, e o script é executado antes do html.

Aparece um erro na consola porque a constante something já se encontra defenida no scope global, no ficheiro s1.js.

O erro já não aparece após introduzir o atributo type="module", porque o script passa a ser executado noutro scope, e a constante something já não está em conflito.

## Anotações da aula

se tivesse 100 ficheiros, tinha de fazer 100 pedidos, o que é ineficiente.

o que enviamos na rede n é o código fonte, enviamos um **bundle**.
O processo de transformar os N ficheiros num ficheiro só, chama-se **bundling**.
O programa que faz o bundling chama-se **bundler**.

