![](../../assets/Logo_Yellow.png)

# ES6

## Arrow functions
Las `arrow functions` o *funciones flecha* son una forma distinta y más abreviada de escribir funciones en JavaScript.
Veamos la siguiente `función` tradicional:
```javascript
function double(num) {
	return num * 2
}
```

Podemos convertirla en una `arrow function` del siguiente modo:
```javascript
const double = num => num * 2;
```

Una `arrow function` se declara como una variable normal, pero en vez de asignarle un `string`, `number`, etc., se le asigna como valor una función.

Si sólo hay un parámetro, no hace falta escribir los paréntesis, pero si no hay ninguno, o hay, más de uno, sí son necesarios:
```javascript
const sum = (a, b) => a + b;
const greet = () => console.log('Hello!');
```

Las llaves `{}` y el `return` no son necesarios si escribes la función en la misma línea. Pero si quieres escribir varias líneas, sí son necesarias:
```javascript
const sum = (a, b) => {
	return a + b
}
```

## Array methods
Los `arrays` tienen varios métodos incorporados para iterar sobre ellos. Todos funcionan más o menos de la misma forma. Supongamos que tenemos un `array` de números y queremos sacar el doble de cada número:

1. Se aplica el método:
```javascript
array.map();
```
2. El método va a iterar por el `array`, y lo único que necesita es que le digamos qué hacer con cada elemento de la lista en cada iteración. Para ello, le pasaremos como argumento una función, lo que se llama una función `callback`:
```javascript
array.map(function() {
	return 
});
```
3. El método `map`, como el resto de métodos que vamos a ver, proporcionan a la función `callback` cada elemento de la lista. Simplemente tenemos que pasárselo a la `callback` como argumento:
```javascript
array.map(function(num) {
	return num * 2
});
```

Podemos escribir la operación anterior de manera más abreviada usando `arrow functions`:
```javascript
array.map(num => num * 2);
```

### `forEach()`
El método `forEach` itera sobre un array y aplica la función que le pasemos al método sobre cada elemento. Este método no devuelve nada:
```javascript
const numbers = [1, 2, 3, 4, 5];
const doubles = numbers.forEach(num => console.log(num));  
// 1
// 2 
// 3 
// 4 
// 5
```

### `map()`
El método `map` itera sobre el array, permite que operemos coon cada valor como queramos, y devuelve un nuevo array con las modificaciones.
```javascript
const numbers = [1, 2, 3, 4, 5];
const doubles = numbers.map(num => num * 2);
console.log(doubles);  // [2, 4, 6, 8, 10]
```

### `filter()`
Este método nos permite filtrar ciertos elementos de un array. Para ello, itera sobre cada elemento del array y le aplica una condición. Si esta condición se cumple, extrae el elemento y lo introduce en un nuevo array, que devuelve al final:
```javascript
const numbers = [1, 2, 3, 4, 5];
const evens = numbers.filter(num => num % 2 === 0);
console.log(evens);  // [2, 4]
```

### `reduce()`
El método `reduce` también itera por el array, pero devuelve un "reductor", el resultado de operar con todos los elementos en orden. En cada iteración te provee de dos parámetros:
1. Un "acumulador" donde se acumula el resultado de cada operación.
2. Cada elemento del array.
```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, element) => accumulator + element);
console.log(sum);  // [15]
```

### `sort()`
Este método sirve para ordenar un `array`. Si no se le pasa ningún argumento, lo ordenará siguiendo su valor `UTF-16` (puedes ver la lista [aquí](https://asecuritysite.com/coding/asc2)), por lo que los `strings` se ordenarán alfabéticamente, aunque con las mayúsculas teniendo prioridad sobre las minúsculas. Por esto mismo, no funcionará con números.
```javascript
const strings = [ 'elephant', 'dog', 'cat', 'bee', 'ant' ];
const orderedStrings = string.sort();
console.log(orderedStrings);  // [ 'ant', 'bee', 'cat', 'dog', 'elephant' ]
```

El método `sort` admite una función de comparación entre cada dos elementos del array:
- si la comparación da `-1`, el primer elemento se coloca primero.
- si la comparación da `1`, el segundo elemento se coloca primero.
- si la comparación da `0`, se dejan los elementos en el mismo orden.
```javascript
let numbers = [5, 8, 2, 4, 1];
const ascendingList = numbers.sort((a, b) => a - b);
const descendingList = numbers.sort((a, b) => b - a);

console.log(ascendingList);   // [1, 2, 4, 5, 8]
console.log(descendingList);  // [8, 5, 4, 2, 1]
```

[Link: ES6 - Métodos de array](https://scandiweb.com/blog/javascript-array-methods-explained/)

