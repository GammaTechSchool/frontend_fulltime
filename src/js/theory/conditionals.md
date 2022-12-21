![](../../assets/Logo_Yellow.png)

# Conditionals

## If / else
Las sentencias (*statements*) `if...else` son una instrucción que nos permite manejar la toma de decisiones de nuestro código. Podemos pensar en ellos como en controladores de toma de decisioines.

En una sentencia `if...else`, decidiremos si un bloque de código va a ejecutarse en función de una condición (`if`), que debe ser siempre verdadera (`true`). En caso de que sea falsa (`false`), no se ejecutará ese bloque, y podremos decidir qué se ejecuta en su lugar (`else`).

```javascript
if (condicion es verdadera) {
   // el código se ejecuta
} else {
   // el código se ejecuta
}
```

### Ejemplos
En este ejemplo, al ser la nota mayor o igual que 5, se ejecutará la instrucción que se encuentra dentro del bloque `if`. De lo contrario, se ejecutaría la instrucción presente en `else`.

```javascript
const grade = 7;

if (grade >= 5) {
    console.log('Has aprobado!')
}
else {
    console.log('Has suspendido...')
}
```

### Else if
Puedes concatenar multiples condiciones usando `else if`.

```javascript
if (la condición 1 es verdadera) {
   // el código se ejecuta
} else if (la condición 1 NO es verdadera, pero la condición 2 es verdadera) {
  // el código se ejecuta
} else {
   // el código se ejecuta
}
```

Ejemplo:
```javascript
const grade = 9.5;

if (grade >= 5 && grade <= 8) {
    console.log("Has aprobado!");
}
else if (grade >= 9) {
    console.log("Has sacado muy buena nota!!");
}
else {
    console.log("Has suspendido");
}
```

En este caso, la condición del primer `if` no se cumple, por lo que pasa al `else if`. Al cumplirse esta condición, se ejecutaría ese bloque de código.

## Operador ternario
Si tienes una sentencia `if...else` simple, quizás quieras usar el operador ternario, ya que simplifica mucho la forma de escribir los condicionales. Su forma es la siguiente:

```
condicion ? si la condicion es verdadera : si la condicion es falsa
```

Ejemplo:
```javascript
let number = 5;
number > 0 ? console.log("Número mayor que 0") : console.log("Número menor que 0");
```

Ten en cuenta que puede usarse para declarar variables también:
```javascript
const age = 23;
const ciudadano = age >= 18 ? true : false;

console.log(ciudadano); // true
```

## Switch
`switch` es una manera alternativa de hacer condicionales `if / else`. A un `switch` le pasaremos un valor, y a continnuación escribiremos qué instrucción se va a evaluar dependiendo de cuál sea ese valor. A diferencia de `if / else`, no le pasaremos una condición que pueda ser `true` o `false`, sino un valor:
```javascript
let number = 2;

switch (number) {
	case 1:
		console.log("El número es 1");
		break
	case 2:
		console.log("El número es 2");
		break
	case 3:
		console.log("El número es 3");
		break
	default: 
		console.log("En caso de que no se cumpla ninguno de los casos anteriores, se ejecuta esta línea por defecto.");
}
```

Como ves, después de cada bloque de código, hay que ordenarle a `switch` que se detenga usando `break`. Si no lo hacemos, en cuanto se cumpla alguno de los `cases`, se ejecutará todo el código hasta el final del `switch` o hasta el siguiente `break`, independientemente de las condiciones. 

Al final de `switch`, podemos poner un caso por defecto, que sería el equivalente al `else`: se ejecutará si no se cumplen los casos anteriores.

## Links útiles:

-   [Sentencias condicionales en JS](https://www.freecodecamp.org/espanol/news/javascript-if-else-y-if-then-sentencias-condicionales-en-js/#:~:text=El%20if...else%20es,false%20en%20las%20sentencias%20if%20.).
-   [MDN: if...else](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/if...else).