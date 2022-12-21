![](../../assets/Logo_Yellow.png)

# Arrays  

## ¿Qué es un array?
Podemos pensar en un `array` como una colección de elementos que pueden almacenarse bajo una única variable (más info [aquí](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)). Los arrays tienen las siguientes propiedades, entre otras:

- Pueden albergar diferentes tipos de datos (strings, numbers, booleans, objects... u otros arrays).
- Su longitud (length) puede variarse, haciéndolo más corto o más largo.
- Los arrays tienen índices que señalan la posición de los diversos elementos que contienen. La primera posición tiene índice 0, la segunda 1, etc.
- Los arrays tienen una serie de métodos que nos permiten realizar diferentes operaciones con ellas.

### Declaración de un array
Un array puede declararse de diversas formas. La más sencilla es hacerlo asignándolo directamente a una variable:

```javascript
const myArray = ["red", 22, true];
```

También podemos usar el [constructor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/Array):
```javascript
const cities = new Array("Madrid", "Barcelona");
console.log(cities); // ["Madrid", "Barcelona"]
```

### Acceso y modificación de un array mediante su índice
Podemos acceder a cualquier elemento de un array, siempre que conozcamos su índice (su posición dentro del array), del siguiente modo:
```javascript
const cities = ["Madrid", "Barcelona"];
console.log(cities[1]); // "Barcelona"
```

De un modo similar, podemos reasignar un valor a dicha posición:
```javascript
cities[1] = "Toledo";
console.log(cities); // ["Madrid", "Toledo"]
```

## Métodos de array
Existen multitud de [métodos de array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array#instance_methods). Nos centraremos en los más usuales.

### Métodos que no modifican el array:
Estos métodos dejan intacto el array sobre el que se aplican.

#### `length`
Devuelve la longitud del array (la cantidad de elementos que contiene):
```javascript
const cities = ["Madrid", "Barcelona"];
console.log(cities.length); // 2
```

#### `indexOf()`
Devuelve la posición de un elemento en particular:
```javascript
const cities = ["Madrid", "Barcelona"];
console.log(cities.indexOf("Madrid")); // 0
```

#### `includes()`
Devuelve un booleano en función de si el array contiene, o no, el elemento por el que hemos preguntado:
```javascript
const cities = ["Madrid", "Barcelona"];
console.log(cities.includes("Madrid")); // true
console.log(cities.includes("Valencia")); // false
```

#### `slice()`
Devuelve una copia del segmento del array que le indiquemos. Para indicar el segmento, le pasaremos al método dos números: 1) la posición de inicio; 2) la posición en la que se detendrá (no incluida):
```javascript
const cities = ["Madrid", "Barcelona", "Toledo", "Valencia", "Sevilla", "Zaragoza"];
console.log(cities.slice(0, 3)); // ["Madrid", "Barcelona", "Toledo"] (posiciones del 0 al 2 (el 3 no está incluido))
console.log(cities.slice(2, 4)); // ["Toledo", "Valencia"] (posiciones del 2 al 3 (el 4 no está incluido))
```
  
### Métodos que modifican el array original
Estos métodos sí alteran el array sobre le que se aplican.
  
#### `push()`
Añade uno o más elementos al **final** del array y devuelve la nueva longitud del array:
```javascript
const cities = ["Madrid", "Barcelona"];
const count = cities.push("Valencia");

console.log(count); // 3
console.log(cities); // ["Madrid", "Barcelona", "Valencia"]
```

```javascript
const fruits = ["apple", "banana"];
const count = fruits.push("orange", "grape");

console.log(count); // 4
console.log(fruits); // ["apple", "banana", "orange", "grape"]
```

#### `pop()`
Elimina el **último** elemento de un array y devuelve dicho elemento:
```javascript
const cities = ["Madrid", "Barcelona", "Valencia"];
const removed = cities.pop();

console.log(removed); // "Valencia"
console.log(cities); // ["Madrid", "Barcelona"]
```

#### `unshift()`
Añade uno o más elementos al **comienzo** del array y devuelve la nueva longitud del array:
```javascript
const cities = ["Madrid", "Barcelona"];
const count = cities.unshift("Valencia", "Toledo");

console.log(count); // 4
console.log(cities); // ["Valencia", "Toledo", "Madrid", "Barcelona"]
```

#### `shift()`
Elimina el **primer** elemento de un array y devuelve dicho elemento:
```javascript
const cities = ["Madrid", "Barcelona", "Valencia"];
const removed = cities.shift();

console.log(removed); // "Madrid"
console.log(cities); // ["Barcelona", "Valencia"]
```

#### `splice()`
El método splice() cambia el contenido de un array eliminando elementos existentes y/o agregando nuevos elementos.

El `primer parámetro` indica la posición (índice) en el que realizar el cambio.

El `segundo parámetro` indica cuántos elementos (si hay alguno) deben eliminarse a partir de la posición indicada en el anterior parámetro.

El `tercer parámetro` indica qué elemento se va a introducir en el array en el índice indicado pior el primer parámetro.
```javascript
const months = ['Jan', 'March', 'April', 'June'];

// inserta 'Feb' en el índice 1
months.splice(1, 0, 'Feb');
console.log(months); // ["Jan", "Feb", "March", "April", "June"]

// introduce 'May' en el índice 4, y elimina 1 elemento en dicho índice
months.splice(4, 1, 'May');
console.log(months); // ["Jan", "Feb", "March", "April", "May"]
```

### Métodos de conversión
Una array puede convertirse en un string, y un string en array, del siguiente modo:

#### `join()`
El método join() une todos los elementos de un array en un string y devuelve este string. Puede especificarse qué carácter va a separar cada elemento (o no especificar ninguno):

```javascript
const elements = ['Fire', 'Air', 'Water'];

console.log(elements.join()); // "Fire,Air,Water"
console.log(elements.join('')); // "FireAirWater"
console.log(elements.join('-')); // "Fire-Air-Water"
```
  
#### `split()`
Realiza el proceso inverso a join(). Este método acepta como parámetro un patrón y convierte un string en un array buscando dicho patrón. El método devuelve el nuevo array:

```javascript
const str = "Pedro es un chico muy alto.";

// separa el string por espacios
const words = str.split(' ');
console.log(words); // ["Pedro", "es", "un", "chico", "muy", "alto."]

// separa el string por letras
const chars = str.split('');
console.log(chars); // ['P', 'e', 'd', 'r', 'o', ' ', 'e', 's', ' ', 'u', 'n', ' ', 'c', 'h', 'i', 'c', 'o', ' ', 'm', 'u', 'y', ' ', 'a', 'l', 't', 'o', '.']

// no separa el string
const strCopy = str.split();
console.log(strCopy); ["Pedro es un chico muy alto."]
```


## Arrays bidimensionales
Un `array` puede almacenar cualquier tipo de dato, ¡también otros arrays! Cuando un array contiene otros arrays dentro, decimos que es un `array bidimensional`:
```javascript
const persons = [["David", "Fernández"], ["Ana", "García"]];
```

Para acceder a sus valores, primero hay que entrar en la primera *capa* del array, y luego en la segunda. Podemos hacerlo con `[]`, como haríamos con un array normal. Supongamos que queremos acceder al string `Fernández`.
```javascript
console.log(persons[0][1]);  // "Fernández"
```

Primero accedermos al array que se encuentra en primera posición (índice `0`, y luego a la segunda posición de ese array (índice `1`).

Del mismo modo, puede haber arrays dentro de arrays dentro de arrays, etc. En ese caso, estaremos ante arrays tridimensionales, tetradimensionales, etc. Puedes acceder a ellas del mismo modo.


## Guía: como iterar un array bidimensional
Podemos iterar cualquier array con un bucle `for`. Pero, ¿cómo iterar un `array bidimensional`?
```javascript
const persons = [["David", "Fernández"], ["Ana", "García"]];
for (let i = 0; i < persons.length; i++) {
	console.log(persons[i]);
}

// ["David", "Fernández"]
// ["Ana", "García"]
```

Esto sólo nos muestra cada array al completo, no cada elemento. Para ello tenemos que hacer otra cosa. Para iterar un array dentro de un array, debemos hacer un bucle dentro de un bucle.
El primer bucle iterará por el primer array, y el segundo por cada elemento de dicho array.
```javascript
const persons = [["David", "Fernández"], ["Ana", "García"]];
for (let i = 0; i < persons.length; i++) {
	for (let j = 0; j < persons[i].length; j++) {
		console.log(persons[i][j]);
	}
}

// "David"
// "Fernández"
// "Ana"
// "García"
```

