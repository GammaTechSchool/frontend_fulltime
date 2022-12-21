![](../../assets/Logo_Yellow.png)

# Ejercicios Puente Diciembre

## Conditionals
### Ejercicio 1
Tienes las siguientes variables:
```javascript
let angulo1 = 72;
let angulo2 = 36;
let angulo3 = 72;
```
Escribe un programa que:
- Compruebe si el triángulo es válido (la suma de los ángulos de un triángulo es siempre `180`).
- Clasifique el triángulo en: acutángulo, obstusángulo o rectángulo.

Cambia los valores de las variables y asegúrate de que funcionan.

### Ejercicio 2
Escribe un condicional que procese las notas de un examen:
- Si la nota está entre `0` y `59` (incluido), debe devolver `"Suspenso"`.
- Si la nota está entre `60` y `79` (ambos incluidos), debe devolver `"Aprobado"`.
- Si la nota está entre `80` y `89` (ambos incluidos), debe devolver `"Notable"`.
- Si la nota está entre `90` y `100` (ambos incluidos), debe devolver `"Sobresaliente"`.
- Cualquier otro número devolvera `"Formato de nota incorrecto"`.

### Ejercicio 3
Escribe un condicional que traduzca `"Hello World"` a diferentes idiomas basándose en la variable `language`.
- Si `language` es `es`, mostrará `"Hola mundo!"`.
- Si `language` es `fr`, mostrará `"Bonjour tout le monde!"`.
- Si `language` es `en`, mostrará `"Hello World!"`.
- Si `language` es `de`, mostrará `"Hallo Welt!"`.
- Cualquier otro valor deberá devolver `"Sorry, language not available"`.

### Ejercicio 4
Escribe un condicional que evalúe dos variables, `"age"` y `"nationality"`, y compruebe si la persona en cuestión puede o no votar en las elecciones. Las condiciones y los `outputs` quedan a tu imaginación.

### Ejercicio 5
Escribe un programa que convierta una palabra en plural (en castellano). Para ello, deberás comprobar la última letra de la palabra, ya que si ésta es una *consonante*, el plural se formará con `es`, pero si es una *vocal*, será solo una `s`. 
**Ojocuidao**: debe valer para cualquier palabra que le pasemos, sin que tengamos que modificar ni una línea de nuestro código.
Ejemplo:
- Si el input no es un `string`, se devolverá `"Input inválido: sólo se aceptan strings"`.
- Si la palabra es `"mesa"`, devolverá `"mesas".
- Si la palabra es `"camión"`, devolverá `"camiones"`.
- Si la palabra acaba en `"s"` y no es la palabra `"crisis"`, ni `"tesis"`, ni la palabra `"bíceps"`, se devolverá `"Esta palabra ya está en plural"`.
- Si la palabra acaba en `"s"` y es `"crisis"`, o `"tesis"`, o `"tórax"`, se devolverá `"El plural coincide con el singular"`.
- Si la palabra es `"sed"`, `"salud"` o `"caos"`, se devolverá `"Esta palabra no tiene forma plural"`.


## Strings
### Ejercicio 6
Escribe un programa que quite los espacios de las frases. Por ejemplo, debería convertir `"Hello World"` en `"HelloWorld"`.

### Ejercicio 7
Dado el string `"pámpano"`, muestra por consola su inverso: `"onapmáp"`. Recuerda que los `string` son *inmutables*: deberás crear una variable nueva donde ir guardando el resultado.

### Ejercicio 8
Crea un programa que detecte si una palabra es un palíndromo o no. Un palíndromo es una palabra que se lee igual del derecho que del revés: "ojo", "asa", etc.

### Ejercicio 9
Dado el siguiente `string`:
```javascript
let str = "Capitalize";
```

Escribe un programa que devuelva un nuevo `string` con el mismo valor, pero con la primera letra en minúsculas y la última en mayúsculas. 
Recuerda que los `string` son *inmutables*: deberás crear una variable nueva donde ir guardando el resultado.

### Ejercicio 10
Escribe un programa que acepte una dirección de email en formato `string` y devuelva el dominio de dicho mail (a partir de la `@`).

El programa debe hacer tres cosas:
1. Comprobar si el `string` contiene el caracter `@`.
2. Si no lo tiene debe devolver `"Dirección de correo incorrecta"`.
3. Si lo tiene, debe devolver el dominio.

Ejemplo:
- Si el email es `"teacher@gammatech.school"`, debe devolver `"gammatech.school"`.
- Si el email es `"fakemail@gmail.com"`, debe devolver `"gmail.com"`.
- Si el email es `"wrongmail.com"`, debe devolver `"Dirección de correo incorrecta"`.


## Loops
### Ejercicio 11
Escribe un bucle que compruebe si un número es primo o no.

### Ejercicio 12
Tienes un bote con 25 galletas. Te gustan mucho las galletas, así que te comes `3` cada día. Sin embargo, cada `2` días (los días pares) tu abuela te da `1` galleta más que puedes meter en tu bote. 
Usa un bucle `for` que devuelva el número de días que tardarás en quedarte sin galletas.

### Ejercicio 13
Escribe un bucle que imprima, del `0` al `100`, cada `3` números.

### Ejercicio 14
Haz un bucle `for` dentro de un bucle `for` (qué locura, ¿no?). 
- El bucle externo debe tener `3` iteraciones, y en cada iteración logeará `"Índice del bucle externo: <<índice del bucle externo>>"`. 
- El bucle interno debe tener `5` iteraciones, y en cada iteración logeará `"Bucle interno: <<índice del bucle interno>>"`. 
Ten en cuenta de que no puedes llamar a los índices de ambos bucles `i`. La convención es llamar al índice del segundo bucle `j`.
El resultado debería ser el siguiente:
```javascript
Índice del bucle externo: 0
Bucle interno: 0
Bucle interno: 1
Bucle interno: 2
Bucle interno: 3
Bucle interno: 4
Índice del bucle externo: 1
Bucle interno: 0
Bucle interno: 1
Bucle interno: 2
Bucle interno: 3
Bucle interno: 4
Índice del bucle externo: 2
Bucle interno: 0
Bucle interno: 1
Bucle interno: 2
Bucle interno: 3
Bucle interno: 4
```

### Ejercicio 15
Usa tus recién adquiridos conocimientos de bucles dobles para programar un reloj. Pero este reloj tendrá minutos con 10 segundos cada uno. Queremos ver los primeros 5 minutos:
```javascript
0 : 0
0 : 1
0 : 2
0 : 3
0 : 4
0 : 5
0 : 6
0 : 7
0 : 8
0 : 9
1 : 0
1 : 1
1 : 2
1 : 3
1 : 4
1 : 5
1 : 6
1 : 7
1 : 8
1 : 9
2 : 0
etc...
```


## Mix
### Ejercicio 16
Escribe un programa que acepte un `string` cualquiera y una letra. Si el `string` contiene dicha letra, deberás mostrar por consola cada caracter hasta dicha letra, usando un bucle `for`. Si no, mostrará `"La palabra no contiene dicha letra"`.

Pasos:
1. Comprueba que el `string` *incluya* la letra.
2. Si no la incluye, devuelve el mensaje de error.
3. Si la inluye, *itera* por el `string` hasta la *posición* de dicha letra.

Ejemplo:
- `"JavaScript"`, `"S"` -> `"J"`, `"a"`, `"v"`, `"a"`.
- `"Gammatech"`, `"t"` -> `"G"`, `"a"`, `"m"`, `"m"`, `"a"`.
- `"Patata"`, `"j"` -> `"La palabra no contiene dicha letra"`.

### Ejercicio 17
Escribe un programa que acepte un `string` y lo devuelva alternando mayúsculas y minúsculas. Debes comprobar antes que el input sea un `string`.
Recuerda que los `string` son *inmutables*: deberás crear una variable nueva donde ir guardando el resultado.
Ejemplo:
- `"JavaScript"` -> `"jAvAsCrIpT"`.
- `2342` -> `"Input inválido"`.

### Ejercicio 18
Escribe un programa que acepte un `string` y, si éste tiene una longitud superior a `8` caracteres, lo corte hasta esa longitud. El programa debe modificar la variable original, no devolver una nueva.
Ejemplo:
- `"JavaScript"` -> `"JavaScri"`.
- `"Paralelepípedo"` -> `"Paralele"`.
- `"Casa"` -> `"Casa"`.
