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
 

### Destructuring Assignment // atribuição de destruição

 ```js
const [firstNumber, secondNumber, thirdNumber] = [1, 2, 3]

console.log(firstNumber, secondNumber, thirdNumber);
 ```

Para ignorar qualquer item, basta usar uma vírgula no lugar:

 ```js
const [firstNumber, , thirdNumber] = [1, 2, 3]


console.log(firstNumber, thirdNumber);
 ```
 
Em objetos:

 ```js
const beer = {
    brand: 'Skol',
    age: 100,
    cold: true
}

const { brand, cold }= beer

console.log(brand, cold)
 ```
 
 Renomeando propriedades:
 
  ```js
const beer = {
    brand: 'Skol',
    age: 100,
    cold: true
}

const { brand: marca, cold: gelada }= beer

console.log(marca, gelada
 ```
 
 Propriedades em profundidade:
  ```js
 const beer = {
    brand: 'Skol',
    age: 100,
    cold: true,
    address: {
        city: 'Nova Zelândia'
    }
}

const { brand, address: { city } }= beer

console.log(brand, city)
 ```
 
 Em funções:
 
 ```js
 const cold = ({ cold }) => cold === true

console.log(cold({ cold: true }))
 ```
 
 ### Higher order functions
 > Funções de primeira ordem, no javascript, uma
> função é um dado, ou seja, eu posso receber uma função como argumento e retornar uma função de outra função.

perceba, que em todos os métodos, é passado uma função como argumento.
#### Map:
Quando usar? Quando você quer obter um novo array, com a mesma
quantidade de itens do original, só que com cada item transformado.

```js
const numbers = [1, 2, 3, 4]

/* 
  objetivo: transformar cada elemento no dobro

  1 - é um vetor
  2 - vetor final vai ter a mesma quantidade de elementos que a inicial
  3 - cada elemento será transformado

  escolha: map
*/

const doubles = numbers.map(number => number * 2)

console.log(doubles)
 ```
 
```js
const usuarios = [
  { name: 'Joao', profissao: 'Engenheiro' },
  { name: 'Pedro', profissao: 'Aviador' },
  { name: 'Ricardo', profissao: 'Computacao' },
]
/* 
  objetivo: pegar somento a profissão

  1 - é um vetor
  2 - resultado final, tem a mesma quantidade de elementos que a inicial
  3 - é uma mudança em cada elemento do vetor

  escolha: Map
  
  const usuariosProfissao = usuarios.map(({profissao}) => profissao)
  console.log(usuariosProfissao)
*/
 ```


#### Filter:

Baseado em uma condição, você quer obter um novo array, 
apenas com alguns elementos do original

```js
const idades = [20, 15, 17, 30]

const podeBeber = idades.filter(idade => idade > 18)

console.log(podeBeber)
 ```
 
 ```js
const favoriteFrameworksPerson1 = ['Vue js', 'React Native', 'React']

const favoriteFrameworksPerson2 = [ 'Vue js', 'React Native', 'Angular']

const commumFrameworks = favoriteFrameworksPerson1.filter(framework => {
   return favoriteFrameworksPerson2.includes(framework)
})

console.log(commumFrameworks);
 ```
 
 #### Reduce:

 Quando usar? Quando você quiser reduzir o array a alguma tipo de dado, ex:
 
  ```js
const numbers = [1, 2, 3]

const sum = numbers.reduce((accumulator, item) => accumulator + item, 0);

/*
 fluxo:
  1 - accumulator recebe 0 
  2- item recebe o primeiro item do array
  3 - 0 + 1 vai retornar 1 que é armazenado no accumulator
  4 - item pega o segundo item do array, que é somado com o 1 do accumulator, retornando 3
  5 - item agora vale 3 que é somado com o 3 do accumulator retornando 6

*/

console.log(sum)

// Resultado foi 6, ou seja, reduzimos o array, para um tipo numérico, por isso chama reduce
// Bom especificar o 0, ele é o início, mas também mostra qual o tipo de dados queremos retornar com o array, se por exemplo
// eu quiser retonar uma string, use '', e um objeto {}
 ```
 
 Imagina que quero pegar esse array, e transformar em uma string, apenas com o nome:
 
  ```js
const baralhos = [
  { name: 'magico', price: 50.0 },
  { name: 'sinistro', price: 44.30 },
  { name: 'ilusao', price: 32.5 }
]

1 - transformar um array numa string? Esse é um caso de uso do reduce

const nomesBaralhos = baralhos.reduce((acc, { name }) => `${acc} ${name}` , '')
                                      //                    ''    'magico'      = acc
                                      //                   ' magico'  'sinistro' = acc
                                      //                   '  magico sinistro ilusao = acc
                                      //                    'magico sinistro ilusao '
console.log(nomesBaralhos) 
 ```
 
 
 #### Propriedades de objetos com nomes dinámicos:
 
 Imagina que eu queira um objeto, com propriedades que serão
 definidas em tempo de execucação:
 
  ```js
const obj = {}

const vetor = [50, 18, 39]

vetor.forEach( v => {
  obj.v = 5
})

console.log(obj)

/* Usando a notação de ponto, ele não vai reconhecer o v passado no
parametro  apenas vai pensar "ta tem um v pra definir como nome da minha
propriedade, vou definir ele aqui v: 5 e pronto"*/
 ```
 
 Então como deixar esse nome dinâmico?
 
   ```js
const obj = {}

const vetor = [50, 18, 39]

vetor.forEach( v => {
  obj[v] = 5
})

console.log(obj)

// Usando colchetes, dai agora o nome v, será associado ao que está no parametro
 ```
 
 
 

 
 
 
 
 

