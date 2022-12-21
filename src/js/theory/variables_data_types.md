![](../../assets/Logo_Yellow.png)

# Variables y tipos de datos

## Variables
### ¿Qué es una variable?
En programación, las `variables` son *contenedores* de datos. Usamos las variables para *almacenar* datos en la memoria del ordenador. Cuando se `declara` una variable, se le reserva un espacio en la memoria del ordenador y podemos asignarle un `valor` o `dato` que será guardado en dicha variable.

Podemos pensar en las `variables` como si fueran *cajas* dentro de las cuáles guardamos cosas. El ordenador guardará en esa caja (la variable) lo que tú le digas que guarde, y colocará la caja en algún lugar de su memoria.

Ahora bien, ¿cómo podemos recuperar lo que guardamos dentro de la variable? Muy fácil, le damos un `nombre`. Siguiendo con el símil de la caja, es como si le pusieramos una etiqueta a la caja para saber qué hay dentro. Así, más adelante, podremos buscar la caja por el nombre y obtener su contenido. 

### Declaración de variables
En JavaScript, para declarar una variable, usamos `let` o `const` seguido del nombre que le queramos dar a nuestra variable:
```javascript
let name;
let age;
let height;
```

Para asignarles un valor, usaremos el `operador de asignación` o *assignment operator* `=` junto con el valor que elijamos:
```javascript
name = "Daniel";
age = 29;
height = 180;
```

También podemos crear una variable y asignarle un valor al mismo tiempo:
```javascript
let name = "Daniel";
let age = 29;
const height = 180;
```

Nuestro ordenador guardará el dato `"Daniel"` dentro de la variable `name`. De ese modo, más adelante, podremos decirle al ordenador: "Dame lo que haya dentro de la variable `name`", y el ordenador podrá buscar en su memoria la variable con ese nombre y darnos su contenido.

Habrás notado que para asignarle un valor a una variable debemos usar `=`. A partir de ahora, en JavaScript, `=` ya no significará "igual", como en matemáticas. Es importante acostumbrarse a que `=` es un operador, es decir, realiza una operación: la de asignar un valor a una variable.

Existen ciertas reglas para nombrar variables en JavaScript:

-   No pueden empezar por un número.
-   No aceptan carácteres especiales excepto `$` y `_`.
-   No pueden contener espacios.
-   Se suele seguir la convención de nombrar las variables de JavaScript usando camelCase: `firstName`, `lastName`, `dateOfBirth`, etc.

Tampoco es posible declarar dos variables con el mismo nombre. Cada variable tiene que tener un nombre único:
```javascript
let name = "John";
let name = "Peter"; // SyntaxError: Identifier 'name' has already been declared
```

Conviene precisar que se puede asignar a una variable el resultado de una operación (como las operaciones matemáticas, pero no solamente éstas):
```javascript
let num = 2 + 2;
let name = "Daniel" + " " + "Danielson";
```

También es posible modificar el valor de una variable, salvo que sea una constante:
```javascript
let name = "Daniel";
name = "Pedro";
console.log(name);  // "Pedro"

const height = 180;
height = 190;  // TypeError: Assignment to constant variable.
```

## Tipos de datos
Todos los lenguajes de programación tienen distintos tipos de datos con los que pueden trabajar. Puedes pensar en los datos como todo aquello que puede almacenarse en una variable. En JavaScript tenemos dos grupos de datos: los `primitives` y los `objects`. 
Los `primitives` de JavaScript son:
- string
- number
- bigint
- boolean
- undefined
- symbol
- null

Veámos algunos de estos datos:

### Numbers
Números enteros (negativos, cero y positivos) y números decimales: 
```javascript
1
-3
0
5.15
```

### Strings
Los `strings` son cadenas de caracteres que van entre comillas dobles, simples o backticks. En JavaScript, los `strings` son el equivalente a texto, una serie de caracteres seguidos:
```javascript
"hello"
'goodbye'
"javascript is a great programming language"
`No, it's not, nobody thinks like that`
```

Es importante entender que todo aquello que vaya entrecomillado será un `string`. Estos ejemplos contienen `strings`, no `numbers`:
```javascript
"2"
'2022'
`14/04/1931`
```

### Booleans
El valor de un `boolean` solo puede ser `true` o `false` (verdadero o falso). Cada vez que pidas a JavaScript que realice una comparación, responderá con un `boolean`.

### Undefined
En JavaScript, si no le asignamos un valor a una variable, éste es `undefined` por defecto. También es el valor que devuelven las funcionen que no devuelven nada:
```javascript
let firstName;
console.log(firstName); // undefined
```
### Null
El valor `null` representa intencionalmente un valor vacío o nulo:
```javascript
let emptyValue = null;
```

### El operador `typeof`
Podemos comprobar el tipo de dato de una variable usando el operador `typeof`. Veamos cómo funciona:
```javascript
console.log(typeof 'JavaScript') // string
console.log(typeof 5) // number
console.log(typeof true) // boolean
console.log(typeof "23") // string
console.log(typeof false) // boolean
console.log(typeof 3.45) // number
console.log(typeof undefined) // undefined
console.log(typeof null) // object
```

Es importante tener en cuenta que el resultado que devuelve `typeof` es un `string`.