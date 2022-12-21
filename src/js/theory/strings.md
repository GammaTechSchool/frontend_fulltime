![](../../assets/Logo_Yellow.png)

# Strings
Los `strings` son cadenas o secuencias de caracteres que se declaran poniéndolos entre comillas dobles (`""`), simples (`''`) o backticks (\`\`). Los `strings` son útiles para almacenar información que puede ser representada en forma de texto.
Podemos realizar diversas operaciones con los `strings`, como comprobar su longitud, concatenar dos o más `strings`, extraer partes de un `string`, etc.

## Creación de strings
Podemos crear `strings` usando `string literals`:
```javascript
const string1 = "A string primitive";
const string2 = "Also a string primitive";
const string3 = `Yet another string primitive`;
```

O podemos crear un `string` usando el `constructor`:
```javascript
const string4 = new String("A String object");
```

## Accediendo a los caracteres dentro de un string
Los `strings` tienen un orden, y cada caracter dentro de él tendrá una posición, representada por el número de su `índice` o `index`.
```javascript
const name = "John";
```

En el `string` `name` que acabamos de declarar, los caracteres (las *letras* en este caso), tienen un orden y un número de índice. Los `string` tienen base `0`, lo cual quiere decir que el primer caracter está en la posición `0`, y el resto se ordena en orden ascendente. Estos son los `índices` o posiciones de los caracteres de `name`:
```javascript
0 : "J"
1 : "o"
2 : "h"
3 : "n"
```

Podemos acceder a cada caracter presente en un string usando `[]`:
```javascript
let name = "John";
console.log(name[0]); // "J"
console.log(name[1]); // "o"
console.log(name[3]); // "n"
```

También podemos acceder a la longitud de un string con el método `.length`:
```javascript
const name = "John";
console.log(name.length) // 4
console.log(name[3]) // "n"
console.log(name[4]) // undefined
```

El método `.length` nos devuelve la longitud de un `string`. La longitud del `string` "John" es de `4` (tiene `4` caracteres), pero el `índice` de su último caracter es `3`, porque los `strings` tienen base `0` (comienzan en `0`). Es importante recordar esto para no solicitar un caracter en una posición que no existe, ya que entonces obtendremos `undefined`.

## Métodos de string
Hay ciertos métodos que podemos aplicar a un `string` para realizar operaciones con ellos. Veamos algunos de ellos:

### `concat()`
El método **`concat()`** combina dos o más cadenas de texto y devuelve una cadena de texto nueva:
```javascript
const str1 = 'Hello';
const str2 = 'World';

const result1 = str1.concat(str2);
console.log(result1); // "HelloWorld"

const result2 = str1.concat(' ', str2);
console.log(result2); // "Hello World"
```

### `includes()`
El método **`includes()`** determina si una cadena de texto o caracter puede ser encontrado dentro de otra cadena de texto, devolviendo **`true`** o **`false`** según corresponda:
```javascript
let name = 'John';
console.log(name.includes('o')); // true
console.log(name.includes('a')); // false
console.log(name.includes('ohn')); // true
```

### `indexOf()` / `lastIndexOf()`
El método **`indexOf()`** devuelve el índice de la primera ocurrencia del valor especificado, empezando por el principio, o `-1` si no se encuentra dicho valor:
```javascript
let name = 'John';
console.log(name.indexOf('o')); // 1
console.log(name.includes('a')); // -1
console.log(name.includes('hn')); //
```

Como habrás intuido, el método `lastIndexOf()` devuelve el índice de la última ocurrencia del valor específicado en el `string`:
```javascript
let name = 'Peter';
console.log(name.lastIndexOf('e')); // 3
```

### `charAt()`
El método **`charAt()`** devuelve en un nuevo `string` el carácter de una cadena que esté en la posición que se le indique. Es el método inverso a `indexOf()`:
```javascript
let name = "John";
console.log(name.charAt(0)); // "J"
console.log(name.charAt(1)); // "o"
console.log(name.charAt(5)); // undefined
```

### `toUpperCase()` / `toLowerCase()`
Devuelve el valor en `mayúsculas` o en `minúsculas`, respectivamente, del `string` sobre el que se aplica el método:
```javascript
let name = 'John';
let lastName = "DOE";
console.log(name.toUpperCase()); // "JOHN"
console.log(lastName.toLowerCase()); // "doe"
```

### `replace()` / `replaceAll()`
El método `replace()` sustituye la **primera** ocurrencia de un caracter o cadena de caracteres por lo que indiquemos, y nos devuelve un nuevo `string` con la modificación:
```javascript
let name = "Peter";
let newName = name.replace("e", "a");
console.log(newName); // "Pater";
```

Como podrás imaginar, `replaceAll()` sustituye no sólo la primera ocurrencia, sino todas:
```javascript
let string = "Peter is not Peter, but Peter's brother";
let newString = string.replaceAll("Peter", "Mark");
console.log(newString); // "Mark is not Mark, but Mark's brother";
```

Es importante recalcar que el `string` original no es modificado, sino que `replace()` crea un nuevo `string`.

### `slice()`
El método **`slice()`** extrae una sección de un `string` y devuelve un `string` nuevo. El `string` original no es modificado.
Admite `2` parametros: posición de inicio y posición de parada (no incluida). Si sólo se da `1`, se agarrará desde esa posición hasta el final del `string`:
```javascript
let sentence = "Hello World";
console.log(sentence.slice(3)); // lo World
console.log(sentence.slice(0, 5)); // Hello
console.log(sentence.slice(8, 11)); // rld
```

