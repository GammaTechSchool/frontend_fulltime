![](../../assets/Logo_Yellow.png)

# Ejercicios JS - Arrays

### Ejercicio 1
1. Crea una variable que tenga como valor un array vacío.
2. Crea una variable que tenga como valor un array con al menos 3 tipos de datos distintos.
3. Crea un array vacío y añádele dos valores usando `push()`, dos valores usando `unshift()` y luego usa `pop()` y `shift()` una vez. A constinuación muestra por consola la longitud del array.
4. Crea el siguiente array: `const names = ["Carlos", "María", "Isidro", "Elizondo", "Molina"]`. A continuación, muestra por consola los nombres `["María, Isidro"]` usando `slice()`. Luego, sustituye `"Elizondo"` por `"Parma"` usando `splice()`.
5. Convierte el array anterior (`names`) en un string de nombres separados por espacios.
6. Crea la variable `const sentence = "El perro de San Roque no tiene rabo"`. A continuación, conviértela en un `array` de palabras, y luego en otro de letras.

### Ejercicio 2
Crea el array `months` con valor: `["January", "February", "Marj", "April", "Mei"]`.

1. Hay dos meses mal escritos: `March` y `May`. Modifica el array usando `[]` para solucionarlo.
2. Crea la variable `newMonths` y asígnale el siguiente array:`["June", "July", "August", "September"]`. A continuación, crea una variable llamada `totalMonths` que sea la concatenación de `months` y `newNonths`.
3. Añade los siguientes 3 meses (`"October"`, `"November"`, `"December"`) al final del array anterior (`totalMonths`) usando `push()`.

### Ejercicio 3
Crea `3` variables (`num1`, `num2` y `num3`), que contendrán números, pero no les des valor todavía. Vamos a trabajar con el array `totalMonths` del ejercicio anterior:

Escribe un condicional en el que:
- Si el primer número es mayor que el segundo, elimine el último elemento del array.
- O bien, si el segundo número es mayor que el tercero, pero menor que `10`, elimine el primer elemento del array.
- O bien, si el segundo número es mayor que el tercero o que el primero, añada el string `"October"` al final del array.
- Si nada de lo anterior es verdadero, print `"Bad luck!"`.

Ahora dale los siguientes valores a `num1`, `num2` y `num3`, y comprueba los resultados:
- `num1 = 9`, `num2 = 7`, `num3 = 5` debe dar como resultado `['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November']
- `num1 = 4`, `num2 = 7`, `num3 = 5` debe dar como resultado `['February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December']
- `num1 = 5`, `num2 = 24`, `num3 = 8` debe dar como resultado `['January', 'February', 'March', 'April', 'May', 'June', 'July', 'August', 'September', 'October', 'November', 'December', 'October']
- `num1 = 7`, `num2 = 7`, `num3 = 7` debe dar como resultado `"Bad luck!"`

### Ejercicio 4
Dado el siguiente array: `['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Saturday']`:

1. Encuentra la posición del string `"Wednesday"` y si la longitud de ese string es mayor que el número de su posición, dale la vuelta al array.
2. Compara la longitud de los elementos en primera y segunda posición, y si el primero es más corto que el segundo, muestra los tres primeros elementos del array (usa el método apropiado para cortar un trozo del array).
3. Comprueba si el array incluye el string Sunday. Si es así, print `"That's nice!"`, si no, print `"Oh no!"` y añade `"Sunday"` al final del array.

### Ejercicio 5
Escribe un script que le dé la vuelta a cualquier `array`. Usa primero el método de array apropiado para ello, y después inténtalo sin usar ningún método, sólo con un bucle `for`.

### Ejercicio 6
Crea un array vacío llamado `numbers`:
1. Crea un bucle `for` que llene el array con los números de `0` al `10` (incluido).
2. Crea un bucle `for` que sume los números de `numbers`y guarde el resultado en la variable `results`.
3. Crea dos arrays vacíos: `evens` y `odds`. A continuación crea un único bucle `for` que itere sobre el array `numbers` y, si el número es par, lo añada a `evens`, y si es impar a `odds`.

### Ejercicio 7
Dados estos dos `arrays`:
```javascript
const fruits = ["pera", "banana", "mandarina", "frambuesa"];
const colors = ["verde", "amarilla", "naranja", "roja"];
```

Crea un programa que muestr por consola cada fruta con su color siguiendo el siguiente modelo:
```javascript
"La pera es verde"
"La banana es amarilla"
etc.
```

### Ejercicio 8
Dado el siguiente `array bidimensional`:
```javascript
const array = [["David", "Fernández"], ["Ana", "García"], ["Manuel", "Herrera"]];
```

Escribe un programa que, usando bucles `for`,  devuelva un array `unidimensional` con el nombre y apellidos de cada persona en un único `string`:
```javascript
["David Fernández", "Ana García", "Manuel Herrera"]
```

### Ejercicio 9
Calcula la media del siguiente array, y redonde su resultado a la baja:
```javascript
const grades = [5, 7, 7, 4, 8, 5, 3, 9];
```
