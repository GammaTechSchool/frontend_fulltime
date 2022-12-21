![](../../assets/Logo_Yellow.png)

# Ejercicios JS - Loops

### Ejercicio 1
Itera del `0` al `10` usando un bucle `for` e imprime cada número por consola. Luego, haz lo mismo con un bucle `while`.

### Ejercicio 2
Itera del `10` al `0` usando un bucle `for` e imprime cada número por consola. Luego, haz lo mismo con un bucle `while`.

### Ejercicio 3
Crea la variable `number` y haz que un bucle `for` imprima la tabla de multiplicar de ese número (del `0` al `10`) en la consola, siguiento el siguiente formato:
```
num x 0 = 0
num x 1 = num * 1
num x 2 = num * 2
etc.
```

### Ejercicio 4
Imprime el siguiente patrón:
```
 i    i^2   i^3
 0    0     0
 1    1     1
 2    4     8
 3    9     27
 4    16    64
 5    25    125
 6    36    216
 7    49    343
 8    64    512
 9    81    729
 10   100   1000
 ```

### Ejercicio 5
Imprime por consola, **una sola vez**, la suma de todos los números del `0` al `10`.

### Ejercicio 6
Haz lo mismo pero con el resultado de multiplicar todos los números del `0` al `10`. Una vez estés seguro de que es el resultado correcto, explica en un comentario por qué da ese resultado.

### Ejercicio 7
Imprime le siguiente patrón por consola:
```
#
##
###
####
#####
######
#######
```

### Ejercicio 8
Pídele al usuario que introduzca un número. Ahora, imprime por consola sólo los números pares hasta ese número (incluido).

### Ejercicio 9
Pídele al usuario que introduzca un número e imprime por consola:
`"La suma de todos los números pares del 0 al <<num>> es <<result>>, y la suma de todos los números impares del 0 al <<num>> es <<result>>."`

### Ejercicio 10
Pídele al usuario que introduzca un número y muestra por consola los números múltiplos de `3` que hay desde `0` a dicho número. Hazlo sin usar `if / else`.

### Ejercicio 11
Crea la variable `str` con valor `"JavaScript"`. A continuación, pídele al usuario que introduzca un número de `0` al `10` y una letra. Debes añadir a `str` dicha letra tantas veces como el número que ha introducido el usuario.
Ejemplo:
```javascript
let num = 5;
let letter = "j";
// resultado esperado: "JavaScriptjjjjj" (5 "j" añadidas)
```

### Ejercicio 12
Itera sobre la variable `"JavaScript"` del ejercicio anterior y muestra por consola cada letra.

### Ejercicio 13
Crea la variable `filter` y dale el valor de una letra cualquiera. A continuación, itera sobre un `string` y muestra por consola cuantas veces aparece `filter` en el `string`.
Ejemplo:
```javascript
let filter = "s";
let string = "sospechoso";
// resultado esperado: 3 (la "s" aparece 3 veces en el string "sospechoso")
```

### Ejercicio 14
Usando las mismas variables del ejercicio anterior, ahora debes crear un nuevo `string` que no contenga la letra de `filter`:
```javascript
let filter = "s";
let string = "sospechoso";
// resultado esperado: "opechoo"