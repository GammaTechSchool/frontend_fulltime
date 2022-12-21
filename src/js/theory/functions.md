![](../../assets/Logo_Yellow.png)

# Functions

Podemos entender las `funciones` como *subprogramas*, esto es, una serie de líneas de código o sentencias (`statements`) que son llamadas para ejecutarse en otro lugar del código (o, incluso, desde otro archivo). 
Una función es un procedimiento, un conjunto de sentencias o instrucciones que, ejecutadas una detrás de otra en cierto órden, llevan a cabo una tarea, un cálculo, etc. 
Las funciones, además, pueden recibir uno o más valores o parámetrods (`input`) y devolver uno o más valores (`output`). Normalmente el `output` está relacionado con el `input` de algún modo: una transformación del mismo, un cálculo a partir del mismo, etc.

### Declaración de funciones
Declaramos una función del siguiente modo:
1. Usando la palabra `function`.
2. Dando un nombre a la función para poder recuperarla más adelante (como hacemos con las variables).
3. Poniendo entre paréntesis los `parámetros` que queramos pasarle a la función, si es que le pasamos alguno (si no, dejaremos los paréntesis vacíos).
4. Escribiendo entre corchetes las instrucciones de código que queramos que ejecute esa función.
5. Si queremos que nuestra función devuelva algún valor, deberemos usar `return` seguido del valor. De lo contrario, la función devolverá el valor por defecto, que es `undefined`.

Por ejemplo, he aquí una función que muestra por consola `"Helo World!"`:
```javascript 
function sayHello() {
	console.log("Hello World!");
}

sayHello(); // "Hello World!"
```

Esta función es igual, solo que ahora le vamos a pasar un parámetro, un nombre (`string`) que añadir a nuestro saludo:
```javascript
function sayHi(person) {
	console.log("Hi " + person);
}

sayHi("John"); // "Hi John"
sayHi("Anna"); // "Hi Anna"
```

Las dos funciones que hemos visto no devuelven ningún valor, simplemente muestran algo por consola. Para devolver un valor, debemos usar `return`:
```javascript
function sum(a, b) {
	return a + b
}

let result = sum(2, 3);
console.log(result); // 5
```

### Function scope
Todo aquello que declaremos dentro de una función, sólo existe *dentro* de la función, y no puede ser recuperado desde fuera.
```javascript
function scopeExample() {
	let localNumber = 5;
}

scopeExample();

console.log(localNumber); // ReferenceError: localNumber is not defined
```

Para acceder al valor, deberíamos retornarlo con `return`:
```javascript
function scopeExample() {
	let localNumber = 5;
	return localNumber
}

let returnedValue = scopeExample();

console.log(returnedValue); // 5
```

### Ternary operator
Dentro de una función podemos escribir el código que necesitemos, incluyendo bucles o condicionales. A la hora de hacer esto último, puede ser útil usar el `operador ternario`, que equivale a una sentencia `return`. Estas dos funciones realizan la misma operación:
```javascript
function evalNum(num) {
	if (num % 2 === 0) {
		return "El número es par"
		}
	else {
		return "El número es impar"
		}
}

function ternary(num) {
	num % 2 === 0 ? "El número es par" : "El número es impar"
}
```

### Default parameters
Cuando definamos los parámetros de nuestra función, podemos establecer el valor que tendrán por defecto, en caso de que no se le pase ninguno:
```javascript
function evalNum(num = 5) {
	return num * 2
}

evalNum(2);  // 4
evalNum();  // 10
```

En el primer caso, le pasamos el parámetro con normalidad, por lo que la función hace lo que se le pide: lo multiplica por `2`.
En el segundo caso, sin embargo, no le pasamos ningún parámetro. Para evitar que se produzca un error al intentar multiplicar `undefined * 2`, hemos establecido que, en caso de que no se pase ningún valor, el parámetro `num` será `5`. Es lo que sucede, y por eso el resultado es `5 * 2`.
