# Modelo React

**Elemento:**

Um elemento é um par para referência para componente propriedade
Ou nome nativo do elemento (div, span, etc) e propriedades

**Componente:**

No react temos componentes, componentes são funções que recebem propriedades.

Um componente tem a responsabilidade máxima de gerar uma árvore de elementos, com base nas props, e no estado interno **à colocação** do componente, que não pode gerar side effects (não pode alterar o estado da aplicação).

```tsx
function SomeComponent({}: SomeComponentProps) // Componente

<SomeComponent p1=2 p2="abc"/> // Isto é um elemento
```

Quando uma das props, ou do estado mudar, a função do componente é reavaliada.

A gestão de estado é posicional, ou seja, é feita com base na posição do componente na árvore de elementos.

O efeito vai ser executado quando o resultado do render estiver no DOM.

```tsx

observedCounter = 0

useEffect(
    () => {
        setInterval(
            () => {
                setCounter(observedCounter + 1), 2000
            })
    },[])
```

Array de dependências, se for vazio, o efeito é executado apenas uma vez.
ESLint - Linter para Typescript

Se o array de dependências mudar o efeito volta a ser executado.

```tsx
useEffect(
    () => {
        setInterval(
            () => {
                setCounter(observedCounter + 1), 2000
            })
    },[observedCounter])
```

O problema desta abordagem é que os efeitos anteriores não são cancelados, e o efeito é executado novamente passado os 2 segundos.

O react permite cancelar o efeito anterior retornando uma função de cancelamento do efeito.

```tsx
useEffect(
    () => {
        const intervalId = setInterval(
            () => {
                setCounter(observedCounter + 1), 2000
            })
        return () => clearInterval(intervalId)
    },[observedCounter])
```

a função de cancelamento pode ser chamada em duas ocasiões:

- Quando o componente é desmontado
- Quando um novo efeito é executado

Isto continua a não estar correto porque o valor não vai ser atualizado de 2000 em 2000 milissegundos, mas sim de 2000 em 2000 milissegundos + o tempo que demorou a cancelar o efeito, e a criar um novo.

Para isto devemos tirar partido do primeiro argumento do setCounter ser polimórfico, e receber uma função que recebe o valor anterior e retorna o novo valor.

```tsx
useEffect(
    () => {
        const intervalId = setInterval(
            () => {
                setCounter((prevCounter) => prevCounter + 1), 2000
            })
        return () => clearInterval(intervalId)
    },[])
```
O código acima é uma função (useEffect) que recebe uma função, que chama uma função(setInterval) que recebe uma função que chama uma função (setCounter) que recebe uma função.
A função retorna uma função que chama uma função (clearInterval) que vai ser executada quando o componente for desmontado ou um novo efeito ser executado.

De acordo com a filha do Felix é lidar, de acordo com o Felix o código é legível.

**Controlled Input:**

```tsx
<input type="text" name="username" value={someState}/>
```

O input deixou de ser autónomo e passou a ser controlado.

Através de um onChange podemos alterar o estado do componente, e o input vai ser atualizado.
