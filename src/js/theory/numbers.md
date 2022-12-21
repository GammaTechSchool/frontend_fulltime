![](../../assets/Logo_Yellow.png)

# Numbers
En JavaScript, `numbers` son números enteros y decimales con los cuales podemos realizar operaciones aritméticas.

## Creación de numbers
Podemos crear números directamente en una variable:
```javascript
let age = 27;
const PI = 3.15;
```

## Math Object
A la hora de operar con números, además de usar los `operadores aritméticos`, podemos usar el `Math Object`. Math es un objeto que cuenta con una series de métodos útiles a la hora de trabajar con números. La sintaxis de estos métodos es siempre la misma:
```javascript
Math.<<método>>(<<number>>);
```

Veamos algunos ejemplos:
```javascript
// Redondear:
console.log(Math.round(9.81));              // 10

// Redondear hacia abajo
console.log(Math.floor(PI));                // 3

// Redondear hacia arriba
console.log(Math.ceil(PI));                 // 4

// Encontrar el mínimo en una lista
console.log(Math.min(-5, 3, 20, 4, 5, 10)) // -5

// Encontrar el máximo en una lista
console.log(Math.max(-5, 3, 20, 4, 5, 10)) // 20

// Valor absoluto
console.log(Math.abs(-10))                 // 10

// Raíz cuadrada
console.log(Math.sqrt(100))                // 10

// Elevar a n potencia
console.log(Math.pow(3, 2))                // 9
```
