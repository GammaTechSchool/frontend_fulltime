![](../../assets/Logo_Yellow.png)

# DOM - Events

## Qué es un evento
Los eventos son acciones que realiza el usuario en nuestra web, tales como hacer click, hacer scroll, cambiar el tamaño de la pantalla, mover el ratón, etc.
Podemos programar nuestra web para que *escuche* o esté a la espera de ciertos eventos por parte del usuario, y que realice ciertas tareas cuando ocurran. Es una manera de automatizar los cambios que queramos hacer en el DOM cuando el usuario haga determinadas acciones, como hacer click sobre un botón, hacer scroll, etc.

Lo primero que debemos entender es que el escuchador de evento (el `event listener`) se coloca sobre un elemento de nuestra web, es decir, sobre un elemento HTML: un botón, un link, una imagen... Ese elemento estará a la espera de que el usuario haga "algo", interactúe con el de algún modo.
Por lo tanto también debemos especificar **_qué_** tipo de interacción es la que estamos esperando, para que el `event listener` se ejecute correctamente. Hay muchos tipos de eventos, estos son algunos de los más comunes:

- `click`: cuando el usuario haga "click".
- `keydown`: cuando se pulsa una tecla.
- `keyup`: cuando se suelta una tecla.
- `mousemove`: cuando se mueve el ratón.
- `mouseover`: el ratón "entra" en el elemento (`hover`).
- `mouseout`: el ratón "sale" del elemento (fin del `hover`).
- `submit`: cuando el usario envíe el formulario.
- `load`: cuando se ha termiando de cargar la página.
- `unload`: cuando el usuario abandona la página (por ejemplo, cerrando el navegador).

Una vez hemos colocado el `event listener` sobre un elemento de HTML, y le hemos especificado el tipo de evento que debe esperar, sólo tenemos que indicar qué va a pasar cuando ese evento ocurra. Esto lo haremos, como es lógico con una función.

## Creación de eventos
Veamos ahora cómo crear un `event listener` sobre un elemento del DOM.

### Click
Supongamos que queremos que, cuando pulsemos un botón, aparezca en la consola un mensaje.
El primer paso sería colocar el `event listener` sobre el botón. Esto lo hacemos con `addEventListener()`.
```javascript
const button = document.querySelector("button");

button.addEventListener();
```

Dentro del `event listener`, debemos especificar:
1. Qué tipo de evento estamos esperando.
2. Qué se va a ejecutar cuando ese evento ocurra.

Podemos especificar el tipo de evento como uno de los parámetros de la función, en forma de `string`:
```javascript
button.addEventListener("click");
```

E indicaremos qué es lo que va a ejecutarse cuando ocurra el evento usando una función de `callback` como segundo parámetro:
```javascript
button.addEventListener("click", function (){
	console.log("Click!");
});
```

También podemos usar una `arrow function`:
```javascript
button.addEventListener("click", () => console.log("Click!"););
```

Ahora, cuando el usuario haga click sobre ese botón, veremos en nuestra consola `"Click!"`.

### Event y event.target
La función de callback que escribimos en el `event listener` recibe por defecto un parámetro que podemos, o no, usar. En el ejemplo anterior no lo necesitábamos, por lo que no hemos hecho uso de él, pero ahora sí vamos a hacerlo.
```javascript
button.addEventListener("click", (event) => console.log(event));
```

Si ejecutaras este código sobre un botón real e hicieras click, verías que el `event` es un objeto con un montón de propiedades. Esas propiedades contienen información sobre el evento en sí, es decir, sobre el "click". Por ejemplo, las coordenadas de la pantalla en donde se ha hecho click, la fecha, y un largo etc. Entre ellas, la más útil para nosotros ahora mismo es la propiedad `target`, que muestra sobre qué elemento se ha hecho click.
```javascript
button.addEventListener("click", (event) => console.log(event.target));

// <button>...</button>
```

Este es el elemento de HTML sobre el cuál se ha hecho click.

### Submit
El evento `submit` ocurre cuando se envía un **_formulario_**, y por lo tanto sólo se puede usar con `<form>`. Es el momento de repasar el HTML relativo a los formularios.

Un formulario de un único `input` luce del siguiente modo:
```html
<form action="">
<label for="name">Name</label>
<input type="text" id="name" name="name">

<label for="age">Age</label>
<input type="number" id="age" name="age">

<input type="submit">
</form>
```

Podemos añadirle el evento `submit` al formulario para recoger lo datos introducidos por el usuario. 
Sin embargo, una vez lanzado el evento `submit` se envía de manera automática, por lo que lo primero que tenemos que hacer es detener el envío usando `event.preventDefault()`, y luego ya podemos escribir las líneas de código que queramos:
```javascript
const form = document.querySelector("form");
form.addEventListener("submit", (event) => {
	event.preventDefault();
	console.log(event.target);
});

// <form action="">
//   <label for="name">Name</label>
//   <input type="text" id="name" name="name">
//   <label for="age">Age</label>
//   <input type="number" id="age" name="age">
//   <input type="submit">
// </form>
```

Esto nos devuelve el HTML del formulario, que es el `target` del evento. Al ser el nodo un objeto, podemos acceder a los inputs de dentro del forulario como si fueran propiedades del mismo, usando como `key` el `name` de los `inputs`.
Esto es, `event.target.name` es el `input` con `name="name"`; `event.target.age` es el `input` con el `name="age"`.
La información contenida en el input en el momento en que se envía el formulario es el `value` del `input`, y por tanto:
- `event.target.name.value` contiene la información del `input name="name"`.
- `event.target.age.value` contiene la información del `input name="age"`.

Podemos, por lo tanto, guardar las respuestas del usuario a nuestro formulario. Supongamos que el usuario `"John"` de `35` años rellena el formulario con su nombre y su edad:
```javascript
form.addEventListener("submit", (event) => {
	event.preventDefault();
	const user = {
		name: event.target.name.value,
		age: event.target.age.value	
	}
	console.log(user);
});

// {name: "John", age: 35}
```

Es de esta manera como se validan los formularios. Por ejemplo, este sería el lugar indicado para validar si el nombre cumple los requisitos que queremos (longitud, caracteres especiales, etc.), si la edad es válida (es un número)..., y ordenar los datos y enviarlos al servidor para guardarlos en la base de datos.

**Nota**: si no usamos `event.preventDefault()` como primera instrucción de nuestro código, el formulario se envía automáticamente sin ejecutar ninguna de las líneas de código que hayamos especificado dentro del `event listener`.
Si enviamos un formulario y no ocurre nada de lo que hemos ordenado, lo más probable es que se nos haya olvidado escribir el `event.preventDefault()`.

### Eventos con funciones predefinidas
Dado que `addEventListener()` acepta como segundo argumento una función, podemos tener esa función definida fuera:
```javascript
const printHello = () => console.log("Hello!");

button.addEventListener("click", printHello);
```

El resultado es el mismo que si hubieramos escrito la función directamente en el `event listener`. Esto nos permite reutilizar código para distintos elementos que tengan la misma funcionalidad.
Es importante notar que al pasarle la función al `eventListener` no debemos escribir los paréntesis `()`. Los paréntesis sirven para ejecutar una función, y si los usáramos la función se ejecutaría en el momento. Pero esto va en contra del concepto mismo de `eventListener`, que consiste en que la función se ejecute sólo cuando ocurra el evento. Por eso, lo que le pasamos es el nombre de la función, y el `event listener` la ejecutará sólo cuando ocurra el evento.

### Eventos inline
Podemos definir los `event listeners` en el HTML. Para ello, sólo necesitamos tener la funcnión definida previamente en el archivo JS. Para añadir el `event listener` en el HTML hacemos lo siguiente:
Archivo HTML:
```html
<button onClick="sayHello()">Click me!</button>
```
Archivo JS:
```javascript
const sayHello = () => console.log("Hello");
```

Cuando hagamos click en el botón, el HTML llamará a la función con el mismo nombre del JS y la ejecutará. El resultado es el mismo que si hicieramos un `addEventListener()`. Si queremos hacer otro tipo de evento que no sea `"click"`, lo haremos siguiendo el patrón `onTipoDeEvento`:
- click: `onClick`
- submit: `onSubmit`
- resize: `onResize`
etc.

Se pueden usar ambos métodos indistintamente, aunque por lo general se prefiere escribir JavaScript en el archivo JS, y no mezclar lenguajes sin motivo. Habrá momentos en los que será necesario declarar los `event listeners` en el HTML, del mismo modo que a veces es necesario escribir HTML en el JS. Cada situación tendrá su solución particular, y no habrá ningún problema siempre y cuando esté justificada.