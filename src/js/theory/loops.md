![](../../assets/Logo_Yellow.png)

# Loops

## Definición
Los `loops` o `bucles` son formas de repetir la misma acción durante un determiando número de veces. Puede parecer banal, pero es una herramienta fundamental en programación. Imagina que tienes que mostrar por consola los números del `1` al `100`. ¿Cuánto tardarías haciéndolo con `console.log()`? Tendrías que escribirlo `100` veces... ¿No sería más fácil si pudieras automatizar el proceso para que se repita `100` veces? Para eso están los `loops`.

### Bucle `for`
El bucle `for` tiene la siguiente sintaxis:
```javascript
for ([expresión inicial]; [condición que debe ser verdadera]; [incremento]) {
	// código que se va a ejecutar en cada iteración del bucle
}
```

Tenemos los siguientes elementos:
1. Expresión inicial: una variable con un valor inicial.
2. Condición a evaluar: si la expresión inicial cumple esta condición, el bucle continuará ejecutándose; si no, se detendrá.
3. Incremento: incremento de la expresión inicial para que en algún momento deje de cumplir la condición y el bucle se detenga.

Veámoslo con un ejemplo:
```javascript
for (let i = 0; i < 10; i++) {
	console.log(i);
}
```

Este bucle muestra por consola los números del `0` al `9`. ¿Cómo lo hace?

1. En primer lugar, el bucle declara una variable: `let i = 0;`. Esta es la condición inicial.
2. A continuación se evalúa la condición: `i < 10`. ¿Es `i` menor que `10`? Sí, porque de momento `i = 0`. Por lo tanto, como la condición es `true`, el bucle continúa ejecutándose.
3. Se ejecuta la instrucción `console.log(i)` que en este caso es `0`.
4. Cuando se ha ejecutado la instrucción, se incrementa la variable tal y como se le ha indicado: `i++`. Ahora `i = 1`, y comienza una nueva iteración del bucle.

El bucle parará cuando `i < 10` sea `false`, o sea, cuando `i === 10`.

### Bucle `while`
El bucle `while` se ejecutará siempre que la condición definida sea `true`:
```javascript
while (condición) {
	// ejecuta este código
}
```

Siempre que la condición evaluada sea verdadera, es decir, evalue como `true`, se ejecutará el bloque de código especificado:
```javascript
let i = 0;

while (i < 10) {
	console.log(i);
	i++;
}
```

Este bucle también muestra por consola los números del `0` al `9`. ¿Por qué? En cada iteración se muestra por consola el valor de `i`, que es `0` en un primer momento, y luego se aumenta el valor de `i` en `1`. Cuando `i === 10`, el bucle se detendrá.

### Bucle `do while`
El bucle `do while` es igual que el bucle `while`, pero ejecuta al menos una iteración, aunque la condición no se cumpla:
```javascript
let i = 0;
do {
    console.log(i);
} while (i > 0)
```

En este caso, la condición no se cumple, pero se ejecuta el código al menos una vez.