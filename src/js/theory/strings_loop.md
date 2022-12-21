![](../../assets/Logo_Yellow.png)

# Guía: iterar un `string` 

Uno de los usos más comunes de los bucles es iterar una lista de elementos ordenados, como un `string` o un `array`. Supongamos el siguiente `string`:
```javascript
let name = "John";
```

En los `strings` los elementos (las *letras* en este caso) tienen un orden y un número de índice. Los `string` tienen base `0`, lo cual quiere decir que el primer caracter está en la posición `0`, y el resto se ordena en orden ascendente. Estos son los `índices` o posiciones de los caracteres de `name`:
```javascript
0 : "J"
1 : "o"
2 : "h"
3 : "n"
```

Ahora bien, si evaluáramos la longitud del `name`, obtendríamos lo siguiente:
```javascript
console.log(name.length); // 4
```

`name` tiene `4` elementos (letras, en este caso), por lo que su `length` es `4`. Sin embargo, el último elemento de `name` no está en la posición `4`. De hecho, dicho índice no existe en `name`:
```javascript
console.log(name[name.length]); // undefined
```

Por lo tanto, el último elemento de un `string` se encuentra en `string.length - 1`:
```javascript
let name = "John";
console.log(name[name.length - 1]); // "n"
```

Teniendo esto en cuenta, ¿cómo iteramos por un `string`?
```javascript
let name = "John";

for (let i = 0; i < string.length; i++) {
	console.log(name[i]);
}
```

El bucle irá desde `0` hasta `string.length - 1` porque la condición de parada es que `i` sea *menor* que `string.length`, es decir, `string.length - 1`. Si quisiéramos usar `<=`, entonces:
```javascript
let name = "John";

for (let i = 0; i <= string.length - 1; i++) {
	console.log(name[i]);
}
```
