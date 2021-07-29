# Javascript ES6

### Const, let and var

**Prefer to use const, this adds less complexity to the code, and constants have a single purpose.**

```html
let userName = Pedro
let userName = 25 // do not do it ❌

const userName = Pedro 😎🎇

```

### Arrow function
  
| Conventional | Arrow functions |
| -------- | -------- | 
| function () { }     | () => { }     | 
| function () { return { } }     | () => ( { } )   
| function double(num) { return num * 2 }     | num  => num * 2   
| function sum(num1, num2) { return num1 + num2 }     | (num1, num2) => { return num1 + num2}  

### Spread Operator

**Notação:** . . . (sim, são 3 pontos)

> **Objeto iterável:** Qualquer objeto que você pode iterar por ele.
**ex:** Array e String
Você pode iterar por cada elemento do array, ou por cada letra da string.

Oque faz spread Operator? Ele pega o objeto iterável e desmembra em parte individuais.

Exemplos de spread:

```js
const food = 'hamburguer'
console.log(...food); // h a m b u r g u e r
```

```js
const equipment = ['mouse', 'keyboard', 'monitor']
console.log(...equipment); // mouse keyboard monitor
```

> **Math.max:** retorna o maior número.
Ex: Math.max(1, 2, 3) => 3

```js
const numbers = [1, 2, 3];
Math.max(...numbers); => 3
/* Por baixo dos panos, o spread operator pega esse
array(que é um objeto iterável), e desmembra cada item,
ele espalha os valores, como se fossem passados um a um */
```
**Antes do spread operator**

```js
 const superGMs = ['Magnus', 'MVL']
 const GMS = ['Krikor', 'Leitão']
 
 GMS.concat(superGMs) //["Krikor", "Leitão", "Magnus", "MVL"]
```

**Depois do spread operator**
```js
const superGMs = ['Magnus', 'MVL']
const GMS = ['Krikor', 'Leitão'].concat(superGMs) // [ 'Krikor', 'Leitão', 'Magnus', 'MVL' ]
```
**Com spread operator**
```js
const superGMs = ['Magnus', 'MVL']
const GMS = ['Krikor', ...superGMs, 'Leitão'] // [ 'Krikor', 'Magnus', 'MVL', 'Leitão' ]
```

**Com spread operator**
O spread também espalha propriedades de objetos dentro de outro objeto


### Rest Parameters
 Usa também a notação de 3 pontos (...), mas agora é chamado de rest parameters,
 ele é usado quando eu quero transformar os parâmetros passados numa função, em um array,
 isso é útil quando eu não sei quantos argumentos vão ser passados, ex:
 
 ```js
 sum(1, 2, 3, 4, 5)   // podem ter um monte de argumentos aqui.
  
function sum(...sum) {   // tudo vai dentro do array sum
  sum.reduce((acc, curr) => acc + curr, 0)
}
```

O rest sempre ficará no parâmetro de uma função, ele transforma os argumentos em vetor, já o spread fica no argumento, ele espalha um a um os valores.
 


