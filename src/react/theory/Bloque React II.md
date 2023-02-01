### Contenido
 - [State Hooks y Events](#state-hooks-y-events)
	- [State](#state)
	- [Usando State Hook - useState()](#usando-state-hook---usestate)
    - [¿Qué es un Hook?](#¿qué-es-un-hook)
		- [Declarando el estado](#declarando-el-estado)
		- [Estado Inicial](#estado-inicial)
		- [Estado de Lectura](#estado-de-lectura)
		- [Estado de Actualización](#estado-de-actualización)
		- [Actualización Funcional](#actualización-funcional)
	- [Gestión de Eventos](#gestión-de-eventos)
		- [Events en HTML y DOM](#eventos-en-html-y-dom)
		- [Eventos en React](#eventos-en-react)
		- [Añadir un Evento](#añadir-un-evento)  
    - [Creación de una Handler Function](#creación-de-una-handler-function)
	- [Re-renderizado de Componentes](#re-renderizado-de-componentes)
	  - [Re-renderizado al actualizar el estado](#re-renderizado-al-actualizar-el-estado)
	- [¿Cuándo deberíamos usar state?](#¿cuándo-deberiamos-usar-state)
      - [State vs Props](#state-vs-props)
- [List y Keys](#list-y-keys)
	- [Almacenamiento de Elementos en Arrays](#almacenamiento-de-elementos-en-arrays)
	- [Renderización de una lista](#renderización-de-una-lista)
	- [Keys](#keys)
	- [Eliminar Elementos de una Lista](#eliminar-elementos-de-una-lista)
	- [Extracción de componentes](#extracting-components)
- [Conditional Rendering](#conditional-rendering)
	- [Conditional Rendering](#conditional-rendering)
	- [Renderizado condicional en función del Estado](#renderizado-condicional-en-función-del-estado)
	- [Extracción de condiciones a funciones](#extracción-de-condiciones-a-funciones)

# State Hooks y Events

Después de esta lección, serás capaz de:

- Describir qué es el estado en un componente React
- Añadir estado a un componente usando el hook `useState
- Crear escuchadores de eventos y utilizarlos para modificar el estado del componente
- Describir cuando los componentes React se vuelven a renderizar


## Introduction

En la lección anterior, vimos cómo los props son esenciales si queremos mostrar algunos datos que provienen de fuera del componente. Usando props, podemos **pasar los datos a un componente** y luego usar esos datos en el propio componente. Ahora veamos qué es el **state** y por qué es tan crucial para nosotros.
  

### Getting Started

Vamos a crear una nueva aplicación React que utilizaremos para los siguientes ejemplos:

```
$ npx create-react-app react-state-and-events  
$ cd react-state-and-events  
$ npm start   
```


Limpia un poco el `App.js`, para que tenga la siguiente estructura:

```jsx
// App.js

import './App.css';

function App() {
  return <div className="App"></div>;
}
export default App;

```


Además, deberías añadir los siguientes estilos CSS a tu archivo `index.css`. Esto te permitirá centrarte en React sin tener que preocuparte por los estilos:  

```css
/* index.css */
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
 
.App {
  margin: 0;
  padding: 20px;
  font-family: sans-serif;
  text-align: center;
  min-height: 100vh;
}
 
.dark {
  background: #282c34;
  color: white;
}
 
.Counter {
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 2px solid black;
  background: cornflowerblue;
  border-radius: 5px;
}
 
button,
select {
  padding: 3px 10px;
  min-width: 50px;
  margin: 5px;
}
 
.WeatherWidget {
  width: 200px;
  height: 200px;
  padding: 20px;
  margin: 10px;
  border: 2px solid grey;
  border-radius: 120px;
  background: lightgoldenrodyellow;
  color: black;
  display: inline-flex;
  flex-direction: column;
  justify-content: center;
}
 
.WeatherWidget span {
  font-size: 36px;
}
 
.WeatherWidget.dark {
  background: #2a3c60;
  color: white;
}
```


## State

El state es el almacenamiento interno del componente. Utilizamos el state para almacenar valores que determinan la apariencia y el contenido del componente. Además, el estado/state se utiliza para controlar cómo se comporta el componente. En resumen, esto significa que el estado del componente determina directamente su aspecto y comportamiento.

Tanto los componentes de clase como los de función pueden tener un estado interno, pero utilizan una sintaxis diferente. En esta lección, nos centraremos en los componentes funcionales, y explicaremos cómo podemos definir y utilizar el estado.

- El estado "vive" en el componente y pertenece al componente mismo. Los props vienen de fuera (de algún otro componente).
- El estado se utiliza para almacenar los datos en el componente que definen su apariencia y su contenido.
- El estado representa la información de la que se encarga un componente. Esto significa que el componente gestiona el estado.
- Los cambios en el estado afectarán al re-renderizado del componente y a lo que el componente muestra.

**[⬆ Volver a contenido](#contenido)**

## Usando state hook - `useState()`

En las lecciones anteriores, hemos trabajado con simples _componentes de función_ que no tenían estado. Como tal podemos referirnos a los componentes sin estado como "stateless components". Ahora estamos introduciendo la posibilidad de utilizar el estado de React en los componentes funcionales. Para añadir _estado_ a un componente funcional usamos el hook de React `useState()`.

### ¿Qué es un Hook?

Un hook es una función especial que te permite "engancharte" a las características de React. Por ejemplo, `useState` es un hook que te permite añadir estado React a componentes de funciones. Más adelante en este módulo, veremos algunos hooks más.

>**Note:**
  Existen algunas reglas especiales sobre dónde puedes y dónde no puedes utilizar hooks dentro de un componente. Puedes aprender más sobre ellas en [Rules of hooks](https://reactjs.org/docs/hooks-rules.html)

Nuestro ejemplo comienza creando un nuevo componente `Counter` e importando el hook `useState` de React:

```jsx
// ./src/components/Counter.js

import React, { useState } from 'react';

function Counter() {
  return (
    <div className="Counter">
      <h2>Counter</h2>

      <p>You clicked 0 times</p>

      <button> - </button>
      <button> + </button>
    </div>
  );
}

export default Counter;
```

Una vez creado, importaremos el `Counter` y lo mostraremos en el `App.js`:

```jsx
// App.js
// ... previous import stays unchanged

import Counter from './components/Counter';

function App() {
  return (
    <div className="App ">
      <h1>React - state and events</h1>

      <Counter />
    </div>
  );
}

export default App;
```


### Declarando el estado

A continuación, utilizando el hook `useState()` crearemos una "variable de estado" dentro del componente `Counter` llamada `count`. La usaremos para mantener un registro del conteo.

```jsx
// ./src/components/Counter.js

import React, { useState } from 'react';

function Counter() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div className="Counter">
      <h2>Counter</h2>

      <p> You clicked { count } times! </p> {/* <-- use the "count" variable here */}

      <button> - </button>
      <button> + </button>
    </div>
  );
}

export default Counter;
```

**¿Qué hace `useState`?** Declara una "variable de estado". Nuestra variable se llama `count` pero podríamos llamarla cualquier otra cosa, como `banana`. Esta es una manera de "preservar" algunos valores entre las llamadas a la función. Las variables "desaparecen" (el ámbito se destruye) cuando la función sale pero las variables _state_ son preservadas por React.

**¿Qué le pasamos a `useState` como argumento?** El único argumento que le pasamos al hook `useState()` es el _estado inicial_. Podemos guardar un número o una cadena (o incluso un objeto y un array) si eso es lo que necesitamos. En nuestro ejemplo, sólo queremos un número para saber cuántas veces ha hecho clic el usuario, así que pasamos `0` como estado inicial. (Si quisiéramos almacenar dos valores diferentes en el estado, llamaríamos a `useState()` dos veces).

**¿Qué devuelve `useState`?** Devuelve un par de valores:

- el estado actual y
- una función para actualizarlo.

Por eso escribimos `const [count, setCount] = useState()`:

```jsx
// ./src/components/Counter.js
import React, { useState } from "react";

function Counter() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);
```

Declaramos una variable de estado llamada `count`, y la establecemos en `0`. React recordará su valor entre re-renders, y proporcionará el más reciente a nuestro componente de función. Si queremos actualizar el `count` actual, podemos llamar a `setCount`.

Puede que te preguntes: ¿por qué `useState` no se llama `createState`?

"Crear" no sería del todo exacto porque el estado sólo se crea la primera vez que se renderiza el componente. Durante los siguientes renders (cuando el componente se actualiza), el _state_ persiste y `useState` devuelve el último estado. De lo contrario, ¡no sería "estado" en absoluto! Esta es también la razón por la que los nombres de los hooks _siempre_ empiezan por `use`.

### Estado Inicial

Además de pasar el valor del estado inicial directamente al hook `useState()`, podemos pasar una función:

```jsx
// ./src/components/Counter.js
 
import React, { useState } from 'react';
 
function Counter() {
// Initialize the state using the function - "lazy initializer"
const [count, setCount] = useState(() => 0);
```

La función pasada a `useState()` se llama **inicializador perezoso** (lazy initializer). Si se pasa una función a `useState` React la llama sólo una vez cuando se está estableciendo el estado inicial. El valor devuelto por la función se establece como el estado inicial.


### Estado de Lectura

Para mostrar el recuento actual en nuestro componente de función, utilizamos `count` directamente:

```jsx
// ./src/components/Counter.js
// ...

<p>You clicked {count} times</p>
```

Llamamos a nuestra variable `count` porque contiene el número de pulsaciones de botón. La inicializamos a cero pasando el `0` como único argumento `useState`.

### Estado de Actualización

En nuestro ejemplo actual, la función `setCount` se encarga de actualizar la variable de estado `count`. Para actualizar el `count` actual, llamamos a `setCount` con un nuevo valor. Para ello, añadiremos un receptor de eventos `onClick` a cada botón y especificaremos una función callback que se ejecutará cuando el usuario haga clic:

En nuestro ejemplo actual, tenemos acceso a la función `setCount`. La función `setCount` se utiliza para actualizar la variable de estado `count`. Para actualizar el `count` actual, llamamos a `setCount` con un nuevo valor.

Para ello, añadiremos un listener de eventos onClick a cada botón con una función callback que se ejecutará cuando el usuario haga clic:

```jsx
// ./src/components/Counter.js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div className="Counter">
      <h2>Counter</h2>

      <p>You clicked {count} times</p>

      <button onClick={() => setCount(count - 1)}> - </button>
      <button onClick={() => setCount(count + 1)}> + </button>
    </div>
  );
}

export default Counter;
```

React volverá a renderizar el componente `Counter`, pasándole el nuevo valor `count`.

Resumamos los pasos anteriores y comprobemos nuestra comprensión.

1.  Para empezar a usar el estado importamos el hook `useState`. Lo utilizamos para crear un estado local en el componente.
    
2.  Dentro del componente, declaramos una nueva variable de estado llamando al hook `useState`. Lo llamamos y le pasamos el valor inicial (por ejemplo `useState(0)`).
    
3.  `useState()` devuelve un par de valores envueltos en un array, a los que damos nombres. Podríamos representar la sintaxis de `useState()` utilizando el siguiente pseudocódigo:
    
```jsx
       const [stateValue, updaterFunction] = useState(initialValue);         
```
    
- El primer valor (`stateValue`) es una "variable de estado".
- El segundo valor (`updaterFunction`) es una función utilizada para actualizar esa variable de estado concreta.

4.  Para actualizar el estado llamamos a la función _state updater function_ y le pasamos el _nuevo valor_. En nuestro ejemplo anterior lo hicimos de la siguiente manera:
    
    ```jsx   
    setCount(count + 1); 
	```
    
5.  Cada vez que se llame a la función _state updater_ React volverá a renderizar el componente (actualizará lo que vemos).

### Actualización Funcional

Si el nuevo estado se calcula utilizando el estado anterior, debe pasar una función a la función _state updater function_. La función recibirá el valor del estado anterior como argumento. El valor devuelto se establece como el siguiente estado.

```jsx
// ./src/components/Counter.js
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div className="Counter">
      <h2>Counter</h2>

      <p>You clicked {count} times</p>

      <button onClick={() => setCount((prevCount) => prevCount - 1)}> - </button>
      <button onClick={() => setCount((prevCount) => prevCount + 1)}> + </button>
    </div>
  );
}

export default Counter;
```


La documentación de React denomina a esta forma de actualizar un estado [actualización funcional](https://reactjs.org/docs/hooks-reference.html#functional-updates). Debes utilizar este patrón para actualizar el estado siempre que se calcule un nuevo estado utilizando el estado anterior.   
   
**[⬆ Volver a contenido](#contenido)**

## Gestión de Eventos

Manejar eventos con elementos React es muy similar a manejar eventos en elementos DOM. Hay algunas diferencias sintácticas:

- Los eventos React se nombran usando camelCase, en lugar de minúsculas.
- Con JSX pasas una función como manejador del evento, directamente en el atributo del evento

### Eventos en HTML y DOM

En el HTML, creamos eventos de la siguiente manera:

```jsx
<button id="btn" onclick="handleClick()">Click Here</button> 
```

También podemos crear el mismo evento utilizando JavaScript y la manipulación del DOM:

```jsx   
const btn = document.getElementById('btn');  
btn.addEventListener(() => handleClick() );         
```

### Eventos en React

En React es ligeramente diferente:

```jsx
<button onClick={() => handleClick()}> Click Here </button>       
```

Como puedes ver, la sintaxis para crear escuchadores de eventos y añadir las funciones manejadoras de eventos en React es ligeramente diferente, pero sigue siendo bastante sencilla. En React, los eventos siempre se nombran usando **camelCase**. La documentación de React proporciona una lista de todos los _[nombres de atributos de eventos](https://reactjs.org/docs/events.html#supported-events)_.

Para registrar un receptor de eventos en un elemento o componente en React pasamos la función manejadora del evento directamente al atributo _event_, como `onClick={ handleClick }`.

### Añadir un Evento

Practiquemos añadiendo escuchadores de eventos. Crearemos otra variable de estado en el `App.js` y la usaremos para manejar el tema de color de la app, permitiéndonos cambiar la apariencia de la app entre temas claros y oscuros.

Importa el `useState` en `App.js` y crea una nueva variable de estado `theme` :

```jsx
// App.js
// ... previous import stays unchanged

// import useState
import { useState } from 'react';

function App() {
  // Declare a new state variable named "theme"
  const [theme, setTheme] = useState('light');

  return (
    <div className={'App ' + theme}>
      <h1>React - state and events</h1>
      <Counter />
    </div>
  );
}
```

Creamos la variable de estado `theme` y le damos el valor inicial `"light"`. La usaremos para cambiar el tema entre `"light"` y `"dark"`.

A continuación, vamos a añadir una selección desplegable con un evento `onChange`:

```jsx
// App.js
// ... previous import stays unchanged

import { useState } from 'react';

function App() {
  const [theme, setTheme] = useState('light');

  return (
    <div className={'App ' + theme}>
      <h1>React - state and events</h1>
      <Counter />

      {/* Add the following "select" dropdown */}
      <select onChange={ event => setTheme(event.target.value) }>
        <option value="light"> Light </option>
        <option value="dark"> Dark </option>
      </select>
    </div>
  );
}

```

Al evento `onChange` le asignamos una función callback `(event) => {}` . Esta función callback llama a `setTheme()` para actualizar el `theme` y establecer el valor (`event.target.value`) proveniente de la opción seleccionada (ya sea `"light"` u `"dark"`).

Como último paso, actualizamos el `className` del div a: `className={"App " + theme}`.

Esto hará que la _className_ cambie cada vez que el `theme` se actualice a `"App light"` o `"App dark"`. Para cambiar la apariencia de la aplicación una vez que el _className_ se actualiza, añadimos el siguiente CSS que cambiará los colores a nuestro `index.css`:

```jsx
/* index.css */     
.dark {
	background: #282c34;    
	color: white;  
}         
```

El resultado será el siguiente:

![Example - change theme using state and events](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-state/react-state-and-events-themes.gif)

### Creación de una handler function

Cuando se trabaja con eventos y estados, un patrón común para mantener el código conciso es crear funciones manejadoras de eventos como funciones independientes. Esto significa que no debemos usar callbacks inline como:

```jsx   
	<select onChange={ event => setTheme(event.target.value) } /> 
```

En su lugar, debemos crear una función fuera y luego hacer referencia a ella por el nombre. Vamos a refactorizar el código en `App.js` para hacerlo:

```jsx
// App.js
// ... imports stay unchanged

function App() {
  const [theme, setTheme] = useState('light');

  const toggleTheme = event => {
    setTheme(event.target.value);
  };

  return (
    <div className={'App ' + theme}>
      <h1>React - state and events</h1>
      <Counter />

      <select onChange={ toggleTheme }>
        <option value="light"> Light </option>
        <option value="dark"> Dark </option>
      </select>
    </div>
  );
}

export default App;
```

De esta manera mantenemos nuestro código limpio y conciso y también nos permite reutilizar la función si es necesario.
   
**[⬆ Volver a contenido](#contenido)**

## Re-renderizado de Componentes

Un componente React se vuelve a renderizar (actualiza el contenido que muestra) cada vez que cambia su estado o sus props.

Un Componente se actualizará cuando reciba los nuevos props del exterior o cuando su estado se actualice. Genial, ¿verdad? No hace falta que le digamos explícitamente al componente que se vuelva a renderizar. ¡React se encarga de todo!

¡Recuerda! Las dos acciones que hacen que un componente se re-renderice y actualice el contenido que muestra son:

- cuando el estado del componente se actualiza,
- cuando cualquier props, proveniente del exterior, se actualiza.

### Re-renderizado al actualizar el estado

React realiza un seguimiento de cada componente de la aplicación. Cada vez que el estado de un componente se actualiza, React volverá a renderizar ese componente en particular para actualizar lo que vemos.

Sin embargo, ¡las _state variables_ y _state_ nunca deben ser actualizadas directamente! Sólo debemos actualizar el estado usando la función updater devuelta por el hook `useState`. Actualizar el estado directamente provocaría que el componente no se volviera a renderizar.

Utilizaremos nuestro componente existente `App` como ejemplo. Veamos qué ocurrirá si intentamos actualizar el estado asignando directamente (`=`) el valor al `theme`:

```jsx
// App.js
// ...

const toggleTheme = event => {
  // setTheme(event.target.value);    <-- COMMENT THE PREVIOUS CODE

  theme = event.target.value; //  WRONG!!
};

// ...
```

Si intentas cambiar el tema de color después de actualizar el código, notarás que no funciona.

Cuando actualizas el estado directamente React no sabe que el estado se actualizó. A cambio, ¡el componente no se volverá a renderizar!

Esta es la razón por la que sólo debemos actualizar el estado utilizando la función updater designada. Volvamos atrás y revirtamos el código a la versión anterior:

```jsx
// App.js
// ...

const toggleTheme = event => {
  setTheme(event.target.value); // CORRECT!
};

// ...
```

¡Nunca debemos actualizar el _state_ directamente! Para actualizar el estado debemos utilizar la función de actualización devuelta por el hook `useState`.

  
### Re-rendering on props update

Cada vez que el valor de los props, procedente del exterior, cambie el componente se actualizará. Podemos pensar en ello como un efecto secundario.

Dicho de otra forma, el componente padre debe pasar un nuevo valor de props para provocar que el componente hijo se vuelva a renderizar.
   
**[⬆ Volver a contenido](#contenido)**

## ¿Cuándo deberiamos usar state?

**¿Qué tipo de información debe guardarse en el estado?** Cualquier cosa que afecte a lo que los usuarios ven y experimentan en nuestra aplicación.

- **¿Conectado?** - Si el usuario está conectado o no tiene un gran efecto en lo que el usuario ve en una aplicación.
    
- **Listas de datos** - Listas de datos como vídeos en YouTube, productos en Amazon, o notificaciones en Facebook son recuperados de la base de datos y comúnmente almacenados como un estado en un componente React. Este tipo de datos se suele almacenar como un array, lo que nos permite iterar sobre los datos fácilmente.
    
- ¿Abierto o cerrado?** - El estado abierto/cerrado de un menú y/o popup en la app también podría almacenarse como un estado. A medida que el usuario interactúa con la aplicación, los diferentes estados van a aparecer y la interfaz de usuario cambiará en consecuencia.
    
- **Formularios** - Los usuarios rellenarán cierta información en los formularios y, en una aplicación React, esos datos se almacenarán temporalmente en el estado, antes de ser enviados al servidor o manipulados de alguna manera.
    
    Almacenar datos en el estado también nos permitirá pre-llenar las entradas del formulario en formularios del tipo editar/actualizar. En particular, los formularios en React deben ser manejados usando estado.
    

### State vs. Props

- **Los componentes pueden utilizar ambos**: Tanto los datos almacenados en el estado como los procedentes de los props pueden ser utilizados y mostrados en el componente.
- **El estado pertenece al componente, los props vienen de fuera**: Al contrario que los props, que vienen del exterior del componente, el estado "vive" y pertenece al propio componente.
- **El estado se puede manipular (actualizar/cambiar)** dentro del componente donde se crea. Los props no pueden ser modificados por el componente que los recibe ya que **los props son `read-only`**.
   
**[⬆ Volver a contenido](#contenido)**

================================================================================

# List y Keys

Después de esta lección, serás capaz de:

- Mostrar una lista en una aplicación React
- Establecer correctamente un atributo `key` a la lista de elementos
- Eliminar elementos de una lista
- Extraer nuevos componentes y dividir responsabilidades de componentes

## Prerrequisitos

- Familiaridad con la sintaxis y las estructuras de datos de objetos y matrices.
- Ser capaz de hacer bucles y trabajar con arrays utilizando los métodos `map`, `filter` y `sort`.

Antes de empezar, te sugerimos que _refresques tu memoria_ sobre la _sintaxis_ y el uso de los métodos `map`, `filter` y `sort`.

## Introducción

Las listas son una de las partes más comunes de la interfaz de usuario en las aplicaciones web. Pueden ser listas de publicaciones y comentarios en aplicaciones como Facebook y Twitter, listados de propiedades en Airbnb, resultados de búsquedas en Google, etc. En esta lección aprenderemos a representar listas en React.


### Primeros pasos

Vamos a crear una nueva aplicación React que utilizaremos para los siguientes ejemplos:

```
$ npx create-react-app react-lists  
$ cd react-lists  
$ npm start        
```

Limpia un poco el `App.js`, para que tenga la siguiente estructura:

```jsx
// App.js

import './App.css';

function App() {
  return (
    <div className="App"></div>
  );
}

export default App;
```

Además, deberías añadir los siguientes estilos CSS a tu archivo `index.css`. Esto te permitirá centrarte en React sin tener que preocuparte por los estilos:

```css
/* index.css */
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
 
code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New', monospace;
}
 
.App {
  text-align: center;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}
 
.list {
  width: 400px;
  padding: 10px;
  box-shadow: 0px 2px 3px grey;
  margin-bottom: 20px;
  background: white;
}
 
.list > li,
.list > p,
.list > div {
  margin: 10px;
  border: 1px solid #f98a8a;
}
 
.MovieCard {
  border: 1px solid grey;
  box-shadow: 0px 2px 3px grey;
  width: 400px;
  text-align: center;
  margin-bottom: 20px;
  padding: 10px;
  border-radius: 4px;
}
 
h2 {
  padding: 15px 30px;
  border: 1px solid #6d6d6d;
  background: lightcyan;
  width: 200px;
  margin: 0 auto;
  margin-bottom: 10px;
}
 
h3 {
  padding: 5px 50px;
  display: inline-block;
}
 
button,
select {
  padding: 3px 10px;
  min-width: 50px;
  height: 40px;
  margin: 5px;
  font-size: 1rem;
}
```


## Almacenamiento de elementos en arrays

En React, puedes almacenar elementos JSX (contenido HTML y componentes) en arrays. Los elementos almacenados en arrays se pueden mostrar directamente en tus componentes poniéndolos entre llaves `{}`.

Vamos a crear un nuevo componente `SimpleList` para ilustrar esto:

```jsx
// src/components/SimpleList.js

// An array containing HTML elements
const numbersList = [<li>1</li>, <li>2</li>, <li>3</li>, <li>4</li>];

function SimpleList() {
  return (
    <div className="list">
      <h2>List</h2>

      {numbersList}
    </div>
  );
}

export default SimpleList;
```

Este código muestra una lista de números entre 1 y 4.

Para ver el resultado, importaremos y renderizaremos el componente `SimpleList` en `App.js`:

```jsx
// App.js
// ... previous import stays unchanged

import SimpleList from './components/SimpleList';

function App() {
  return (
    <div className="App">
      <SimpleList />
    </div>
  );
}

export default App;

```

## Renderización de una Lista

En el ejemplo anterior, mostramos una lista de elementos estáticos almacenados en un array. Pero ¿qué pasa si queremos convertir una matriz de datos, por ejemplo - cadenas:

```jsx
const students = ['Marc', 'Lucy', 'Anna'];        
```

en una lista de elementos:

```jsx   
[<p>Marc</p>, <p>Lucy</p>, <p>Anna</p>];         
```

El método `map()` nos permite convertir un array que contiene datos en un array de elementos y mostrarlo inmediatamente.

El método `map()` **devuelve un nuevo array** poblado con los resultados de llamar a la función dada para cada elemento del array original.

Crearemos un nuevo componente `StudentList` para mostrar esto:

```jsx
// src/components/StudentList.js

function StudentList() {
  const students = ['Marc', 'Lucy', 'Anna'];

  return (
    <div className="list">
      <h2>Student List</h2>
      
      { students.map(name => {
        return <p> { name } </p>
      })}
      
    </div>
  );
}

export default StudentList;

```

Al incrustar `students.map((name) => <p>{name}</p>)` entre llaves `{ }` el array de cadenas se convierte en un array de elementos `<p></p>`, y se muestra inmediatamente.

A continuación, importaremos y mostraremos el componente `StudentList` en `App.js`:

```jsx
// App.js
// ... previous imports stay unchanged

import StudentList from './components/StudentList';

function App() {
  return (
    <div className="App">
      {/* <List /> */}

      <StudentList />
    </div>
  );
}

export default App;
```

Te habrás dado cuenta de que a `.map()` le faltan las llaves habituales `{}` y una sentencia `return`. ¿Recuerdas la sintaxis de la _función de flecha_ concisa? Esta es la que estamos utilizando aquí. La función de flecha concisa se utiliza con frecuencia en React, y es posible que te la encuentres en muchos ejemplos de código React.

## Keys

Cuando ejecute el código del ejemplo anterior, verá una advertencia en la consola diciendo que se debe proporcionar una _key_ para los elementos de la lista. Probablemente se pregunte, ¿qué es una _key_?

:::

Si abrimos la consola para comprobar el resultado, veremos un error:

> Advertencia: Cada hijo de una lista debe tener una única "clave" prop.

:::

Una "clave" es una _prop_ especial que debes incluir al crear listas. **React utiliza _keys_ para identificar qué elementos de la lista han cambiado, se han añadido o se han eliminado ([read more](https://reactjs.org/docs/reconciliation.html#keys)).**


### Index como Key

Para solucionar el problema de la falta de _key_, tenemos que actualizar el componente `StudentList` y añadir una propiedad `key` a los elementos de nuestra lista dentro de `students.map()` . Utilizaremos el elemento del array `index` como clave:

```jsx
// src/components/StudentList.js

const students = ['Marc', 'Lucy', 'Anna'];

function StudentList() {
  return (
    <div className="list">
      <h2>Student List</h2>
      {students.map((name, index) => (
        <p key={index}> 
          {name} 
        </p>
      ))}
    </div>
  );
}

export default StudentList;
```

Utilizamos el _índice_ de cada elemento `key={index}` como valor _key_. Usar _índices_ para claves está bien cuando se renderizan listas estáticas. Sin embargo, esta es una _mala práctica_ en la lista donde el orden de los elementos puede cambiar. Esto puede impactar negativamente en el rendimiento y causar errores en el re-renderizado de componentes ([leer más](https://robinpokorny.medium.com/index-as-a-key-is-an-anti-pattern-e0349aece318)).

No debes usar el _índice_ del `mapa` como _clave_. Esto se considera un _anti-patrón_ que puede llevar a resultados impredecibles.

Puede que te preguntes - ¿entonces por qué lo usamos aquí si no es una buena práctica?

Lo hicimos porque es una forma fácil de demostrar la importancia de las "llaves" y lo utilizamos como paso de transición. A continuación, le mostraremos cómo configurar correctamente _key_ props en una lista.
  

### Claves Únicas / Unique keys

Como `key` prop para el elemento de la lista, siempre debe intentar asignar un valor único y permanente.

La mejor forma de elegir una clave es utilizar una cadena que identifique de forma única un elemento de la lista entre sus hermanos. En la mayoría de los casos, utilizará los ID de sus datos como claves.

Como ejemplo, crearemos un nuevo componente llamado `ProjectList.js` que tiene un array de objetos con IDs únicos:

```jsx
// src/components/ProjectList.js

const projects = [
  { _id: '127fae', name: 'EatBCN', techStack: 'React, Express, MongoDB' },
  { _id: '985afw', name: 'TravelLite', techStack: 'React, Express, Redux' },
  { _id: '347eef', name: 'IronClub', techStack: 'Express, HBS, MongoDB' },
  { _id: '90af21', name: 'ChatApp', techStack: 'React, Express, SocketIO' }
];

function ProjectList() {
  return (
    <div className="list">
      <h2>Project List</h2>

      {projects.map(project => {
        return (
          <div key={project._id}>
            <h3>{project.name}</h3>
            <p>Tech Stack: {project.techStack}</p>
          </div>
        );
      })}
    </div>
  );
}

export default ProjectList;
```

En el ejemplo anterior, cada objeto de la matriz `projects` tiene una propiedad `_id` que contiene un valor de cadena único. Usamos este valor único `_id` como `key`.

Algo importante a tener en cuenta: Cuando creamos listas, siempre debemos asignar la propiedad `key` al elemento más externo (que lo encierra) _devuelto_ por `.map()`.


## Eliminar Elementos de una Lista

Sigamos practicando con las matrices que contienen objetos. En esta sección, veremos cómo crear un componente de lista dinámico que nos permita eliminar elementos de la lista.

Para crear un componente dinámico, necesitaremos un _state_. Así, en lugar de almacenar el array con los datos en una variable, los almacenaremos directamente en el estado. Esto nos dará un control completo de la lista, permitiéndonos _eliminar_, _actualizar_ y _añadir_ elementos a la lista. En este ejemplo, nos centraremos en la eliminación de elementos.

En aras de la claridad, vamos a guardar nuestra matriz con los datos en un archivo separado. En la carpeta `/src`, crea un nuevo archivo llamado `movies-data.json` y pega el siguiente contenido en él:

##### `src/movies-data.json`

```js
[
  {
    "_id": "1ae23ef1",
    "title": "The Godfather",
    "director": "Francis Coppola",
    "hasOscars": true,
    "IMDBRating": 9.2
  },
  {
    "_id": "1ae23ef2",
    "title": "Star Wars",
    "director": "George Lucas",
    "hasOscars": true,
    "IMDBRating": 8.7
  },
  {
    "_id": "1ae23ef3",
    "title": "The Shawshank Redemption",
    "director": "Frank Darabont",
    "hasOscars": false,
    "IMDBRating": 9.3
  },
  {
    "_id": "1ae23ef4",
    "title": "Jurassic Park",
    "director": "Steven Spielberg",
    "hasOscars": false,
    "IMDBRating": 8.0
  },
  {
    "_id": "1ae23ef5",
    "title": "Sharknado",
    "director": "Anthony C. Ferrante",
    "hasOscars": false,
    "IMDBRating": 5.2
  },
  {
    "_id": "1ae23ef6",
    "title": "Titanic",
    "director": "James Cameron",
    "hasOscars": true,
    "IMDBRating": 8.9
  }
]

```

  
### Store the List Array in the State

Dentro de nuestra carpeta `src/components`, vamos a crear un archivo `MovieList.js`. Esta vez vamos a crear un componente con estado utilizando el hook `useState()`, que también nos permitirá practicar el trabajo con el estado:

```jsx
// src/components/MovieList.js

import { useState } from 'react';

// import the array of movie objects
import moviesData from '../movies-data.json';

function MovieList() {
  // Declare a state variable "movies"
  // and set the array from movies-data.json as the initial state
  const [movies, setMovies] = useState(moviesData);

  return (
    <div>
      <h2>Movie List</h2>
    </div>
  );
}

export default MovieList;
```

Creamos una nueva variable de estado `movies` y establecemos su estado inicial al array importado de objetos película `moviesData`.

Para crear una lista tendremos que iterar sobre la variable de estado `movies`. Este enfoque nos permitirá actualizar nuestra lista actualizando la variable de estado `movies`.

Para crear un componente de lista dinámica, que vuelve a iterar cada vez que la lista se actualiza (eliminar un elemento, añadir un elemento, modificarlo), debemos utilizar state y almacenar los datos del array en el state.

Recuerda, un componente **React` sólo vuelve a renderizar cuando recibe nuevos props y cuando su _state_ cambia**.

Antes de renderizar la lista, vamos a importar y mostrar el componente `MovieList` en `App.js`. Para hacer las cosas más claras, comentaremos todos los componentes mostrados previamente:

```jsx
// App.js
// ... previous imports stay unchanged

import MovieList from './components/MovieList';

function App() {
  return (
    <div className="App">
      {/* <List /> */}
      {/* <StudentList /> */}
      {/* <ProjectList /> */}

      <MovieList />
    </div>
  );
}

export default App;
```


### Render the List Array from the State

Ahora, actualicemos `MovieList` para mostrar las películas. Recuerda, para que nuestra lista sea dinámica, ¡debemos renderizar el array almacenado en el estado! Esto significa que estaremos mapeando sobre la variable de estado `movies`:

```jsx
// src/components/MovieList.js
// ... previous imports stay unchanged

function MovieList() {
  const [movies, setMovies] = useState(moviesData);

  return (
    <div>
      <h2>Movie List</h2>
      {movies.map(movie => {
        return (
          <div key={movie._id} className="MovieCard">
            <h3>{movie.title}</h3>
            <p>Director: {movie.director}</p>
            <p>Rating: {movie.IMDBRating}</p>
            <button className="btn-delete">Delete </button>
          </div>
        );
      })}
    </div>
  );
}

export default MovieList;
```

### Delete Button

Esto va cada vez mejor. Cada una de nuestras tarjetas de película tiene ahora un botón de borrado. Estos botones no son funcionales por el momento, pero lo implementaremos a continuación. Vamos a añadir un evento `onClick` a nuestro botón de borrar y crear una función para borrar una película:

```jsx
// src/components/MovieList.js
// ... previous imports stay unchanged

function MovieList() {
  const [movies, setMovies] = useState(moviesData);

  const deleteMovie = movieId => {
    const filteredMovies = movies.filter(movie => {
      return movie._id !== movieId;
    });

    setMovies(filteredMovies);
  };

  return (
    <div>
      <h2>Movie List</h2>
      {movies.map(movie => {
        return (
          <div key={movie._id} className="MovieCard">
            <h3>{movie.title}</h3>
            <p>Director: {movie.director}</p>
            <p>Rating: {movie.IMDBRating}</p>
            <button onClick={() => deleteMovie(movie._id)} className="btn-delete">
              Delete 
            </button>
          </div>
        );
      })}
    </div>
  );
}

export default MovieList;
```

Resumamos cómo funciona la función de borrar una película y `deleteMovie` y comprobemos que lo hemos entendido:

1.  Al hacer clic, el botón de borrar llama a la función `deleteMovie` y le pasa el `_id` de esa película en concreto: `onClick={ () => deleteMovie(movie._id) }`.
    
2.  A continuación, la función `deleteMovie` filtra la matriz de películas existente utilizando el método `.filter()`, para eliminar la película sobre la que se ha hecho clic: `return movie._id !== movieId;`.
    
3.  El método `filter()` creará una nueva matriz llamada `filteredMovies` y excluirá la película seleccionada de esa nueva matriz.
    
4.  Por último, la nueva matriz `filteredMovies` se establece como el nuevo estado a través de la función de actualización del estado `setMovies`. La actualización del estado (variable de estado) hará que el componente se vuelva a renderizar:
    

```
setMovies(filteredMovies)  
```

#### The result

  
![Example - deleting movies from the list](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-lists/react-lists-delete-items.gif)

  

## Extracting Components

Uno de los principales puntos fuertes de React es el enfoque basado en componentes para construir aplicaciones. Nos permite **organizar nuestras interfaces de usuario (UI) en componentes y separar claramente las preocupaciones y responsabilidades**.

Una de las mejores prácticas para mejorar el código y la legibilidad de una aplicación React es dividir grandes componentes complejos en otros más pequeños, también conocido como [extracción de componentes](https://reactjs.org/docs/components-and-props.html#extracting-components).

Nuestro componente `MovieList` está poco a poco perdiendo su forma, con demasiadas cosas sucediendo en un mismo lugar. Podemos mejorarlo extrayendo una parte de su código y trasladándola a un nuevo componente más pequeño.

Extraeremos la siguiente porción de código de `MovieList`:

```jsx
// src/components/MovieList.js
// ...

<div key={movie._id} className="MovieCard">
  <h3>{movie.title}</h3>
  <p>Director: {movie.director}</p>
  <p>Rating: {movie.IMDBRating}</p>
  <button onClick={() => deleteMovie(movie._id)} className="btn-delete">
    Delete 
  </button>
</div>

// ...
```

y crear un nuevo componente `MovieCard` a partir de él, de la siguiente manera:

```jsx
// src/components/MovieCard.js

function MovieCard(props) {
  const { movie } = props;

  return (
    <div className="MovieCard">
      <h3>{movie.title}</h3>
      <p>Director: {movie.director}</p>
      <p>Rating: {movie.IMDBRating}</p>
      {/* Keep the button commented out for now */}
      {/* <button onClick={() => deleteMovie(movie._id)} className="btn-delete">
        Delete 
      </button> */}
    </div>
  );
}

export default MovieCard;
```


Fíjate en esta línea:

```jsx
// ...  
const { movie } = props;  
// ...         
```

Esto significa que "movie" proviene ahora de PROPS, que se pasa como prop desde el componente padre (el componente "MovieList").

Si no hubiéramos desestructurado el objeto props, tendríamos que sustituir el anterior:

```jsx
movie.title;  
movie.director;  
movie.IMDBRating;  
movie._id;         
```

para

```jsx
props.movie.title;
props.movie.director;
props.movie.IMDBRating;
props.movie._id;
```

Como se ha explicado anteriormente, esto significa que ahora tenemos que pasar el objeto `movie` a nuestro nuevo componente `MovieCard` a través de props, ya que los datos no están disponibles directamente en el componente `MovieCard`.


![Example - Extracting a component](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-lists/react-lists-extracting-components.png)


El último paso es importar el nuevo componente `MovieCard` a `MovieList` y utilizarlo en el lugar del que extrajimos su código anteriormente:

```jsx
// src/components/MovieList.js
// ... previous imports stay unchanged

import MovieCard from './MovieCard';

function MovieList() {
  const [movies, setMovies] = useState(moviesData);

  const deleteMovie = movieId => {
    const filteredMovies = movies.filter(movie => {
      return movie._id !== movieId;
    });

    setMovies(filteredMovies);
  };

  return (
    <div>
      <h2>Movie List</h2>
      {movies.map(movie => {
        return <MovieCard key={movie._id} movie={movie} />;
      })}
    </div>
  );
}

export default MovieList;

```

Se ve mucho mejor que antes. Hemos _separado_ la _responsabilidad_ de recorrer la lista, de la de mostrar el elemento en sí. Ahora `MovieList` se encarga de mostrar la lista, mientras que `MovieCard` sólo es responsable de mostrar el contenido de la película.

Ahora, vamos a intentar borrar una película de la lista. Desactiva el botón de borrado en el componente `MovieCard`. ¿Qué ocurre cuando intentas borrar una?

Con toda la reestructuración que hicimos, ya no funciona. El borrado dejó de funcionar porque movimos el botón de borrado a un componente separado y la función `deleteMovie` ya no es accesible. El botón de borrar no puede acceder a la función `deleteMovie` ya que se encuentra en otro componente.

**[⬆ Volver a contenido](#contenido)**

================================================================================================================================

# Conditional Rendering

Después de esta lección serás capaz de:

- Renderizar componentes y contenido según condiciones
- Utilizar los operadores `?` y `&&` para renderizar contenido de forma condicional.
- Organizar y abstraer la lógica de renderizado condicional en funciones.


## Introduction

En React, puedes crear distintos componentes que encapsulen el comportamiento que necesitas. Luego, usando los condicionales puedes renderizar sólo algunos de ellos, dependiendo del estado de tu aplicación.

El renderizado condicional en React funciona de la misma manera que las condiciones en JavaScript. Puedes usar sentencias JavaScript `if-else` o los operadores condicionales `?` y `&&` para renderizar los elementos que representan el estado actual y React actualizará la interfaz de usuario para que coincida con ellos.

**Renderizado condicional** significa renderizar diferentes contenidos de la interfaz de usuario dependiendo de si una condición es `true` o `false`.

### Getting Started

Vamos a crear una nueva aplicación React que utilizaremos para los siguientes ejemplos:

```
$ npx create-react-app react-conditional-rendering  
$ cd react-conditional-rendering  
$ npm start         
```

A continuación encontrarás el código de inicio que necesitamos para esta lección. Siga adelante y cree los siguientes archivos utilizando el código proporcionado:

```jsx
// src/components/MovieList.js
 
import { useState } from 'react';
import moviesData from '../movies-data.json';
 
import MovieCard from './MovieCard';
 
function MovieList() {
  const [movies, setMovies] = useState(moviesData);
 
  const deleteMovie = movieId => {
    const filteredMovies = movies.filter(movie => {
      return movie._id !== movieId;
    });
 
    setMovies(filteredMovies);
  };
 
  return (
    <div>
      <h2>Movie List</h2>
      {movies.map(movie => {
        return <MovieCard key={movie._id} movie={movie} clickToDelete={deleteMovie} />;
      })}
    </div>
  );
}
 
export default MovieList;
```

```jsx
// src/components/MovieCard.js
 
import React from 'react';
 
function MovieCard(props) {
  const { movie, clickToDelete } = props;
 
  return (
    <div className="MovieCard">
      <h3>{movie.title}</h3>
      <p>Director: {movie.director}</p>
      <p>Rating: {movie.IMDBRating}</p>
      <button onClick={() => clickToDelete(movie._id)} className="btn-delete">
        Delete 
      </button>
    </div>
  );
}
 
export default MovieCard;
```

```jsx
// src/App.js
 
import './App.css';
import MovieList from './components/MovieList';
 
function App() {
  return (
    <div className="App">
      <MovieList />
    </div>
  );
}
 
export default App;
```

##### `src/movie-data.json`
```jsx
[
  {
    "_id": "1ae23ef1",
    "title": "The Godfather",
    "director": "Francis Coppola",
    "hasOscars": true,
    "IMDBRating": 9.2
  },
  {
    "_id": "1ae23ef2",
    "title": "Star Wars",
    "director": "George Lucas",
    "hasOscars": true,
    "IMDBRating": 8.7
  },
  {
    "_id": "1ae23ef3",
    "title": "The Shawshank Redemption",
    "director": "Frank Darabont",
    "hasOscars": false,
    "IMDBRating": 9.3
  },
  {
    "_id": "1ae23ef4",
    "title": "Jurassic Park",
    "director": "Steven Spielberg",
    "hasOscars": false,
    "IMDBRating": 8.0
  },
  {
    "_id": "1ae23ef5",
    "title": "Sharknado",
    "director": "Anthony C. Ferrante",
    "hasOscars": false,
    "IMDBRating": 5.2
  },
  {
    "_id": "1ae23ef6",
    "title": "Titanic",
    "director": "James Cameron",
    "hasOscars": true,
    "IMDBRating": 8.9
  }
]
```

```css
/* index.css */
 
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
 
code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New', monospace;
}
 
div,
section,
main {
  box-sizing: border-box;
}
 
nav {
  background: #cec8db;
  color: white;
  padding: 0px 20px;
  box-shadow: 0px 1px 2px gray;
  display: flex;
  align-items: center;
  width: 100%;
  margin-bottom: 10px;
}
 
nav p {
  color: white;
  margin-left: 0px;
  font-size: 24px;
  font-weight: 600;
}
 
h2 {
  padding: 15px 30px;
  border: 1px solid #6d6d6d;
  background: lightcyan;
  width: 300px;
  margin: 0 auto;
  margin-bottom: 10px;
}
 
h3 {
  padding: 5px 50px;
  display: inline-block;
}
 
button,
select {
  padding: 3px 10px;
  min-width: 50px;
  height: 40px;
  margin: 5px;
  font-size: 1rem;
}
 
.App {
  text-align: center;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-height: 100vh;
}
 
.list {
  width: 400px;
  padding: 10px;
  box-shadow: 0px 2px 3px grey;
  margin-bottom: 20px;
  background: white;
}
 
.list > li,
.list > p,
.list > div {
  margin: 10px;
  border: 1px solid #f98a8a;
}
 
.MovieCard {
  border: 1px solid grey;
  box-shadow: 0px 2px 3px grey;
  width: 400px;
  text-align: center;
  margin-bottom: 20px;
  padding: 10px;
  border-radius: 4px;
}
 
.Spinner {
  width: 100%;
  min-height: 100vh;
  position: fixed;
  top: 0;
  display: flex;
  justify-content: center;
  align-items: center;
}
 
.Spinner img {
  width: 100px;
  height: 100px;
}
 
span.green,
span.red,
span.black {
  display: inline-block;
  padding: 3px 10px;
  width: 25px;
  border-radius: 3px;
  color: white;
  font-weight: 600;
}
 
.green {
  background: green;
}
 
.red {
  background: red;
}
 
.black {
  background: black;
}
```

## Conditional Rendering

### Condicional básica `if-else`

Podemos usar sentencias `if` `else` para mostrar condicionalmente contenido en un componente declarando qué contenido debe ser devuelto para una condición específica.

He aquí un ejemplo simplificado de cómo funciona esto:

```jsx
if (true) {
	return <SomeComponentGoesHere />;  
} else {
	return <OtherComponentGoesHere />;  
}         
```

Crearemos un nuevo componente `Spinner.js` que utilizaremos en el siguiente ejemplo:

```jsx
// src/components/Spinner.js

const spinner = 'https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-lists/spinner.gif';

function Spinner() {
  return (
    <div className="Spinner">
      <img src={spinner} alt="loading spinner" />
    </div>
  );
}

export default Spinner;
```

`Spinner` es un componente sencillo que muestra un _gif_ giratorio que podemos mostrar al usuario mientras se carga algún contenido.

Actualizaremos el `App.js` de la siguiente manera:

```jsx
// App.js
// ... previous imports stay unchanged

import Spinner from './components/Spinner'; // <-- add
import { useState } from 'react'; // <-- add

function App() {
  // Declare a new state variable, which we'll call "isLoading"
  const [isLoading, setIsLoading] = useState(true); // <-- add

  if (isLoading) {
    return <Spinner />;
  } 
  else {
    return (
      <div className="App">
        <MovieList />
      </div>
    );
  } 
}

export default App;
```

En el ejemplo anterior, hemos importado el componente `Spinner` y el hook `useState`. Creamos una nueva variable de estado `isLoading` que contiene un booleano. La variable de estado `isLoading` se utiliza como condición para mostrar un spinner _o_ mostrar todo el contenido de la aplicación y el componente `MovieList`.

Para mostrar condicionalmente el contenido utilizamos la sentencia `if-else`.

En aras de la brevedad, hemos omitido añadir un botón y un controlador de eventos. Para alternar entre mostrar el spinner y ver el contenido cambia el valor inicial de la variable de estado `isLoading` a `false`:

```jsx
// const [isLoading, setIsLoading] = useState(true);
const [isLoading, setIsLoading] = useState(false);
```


### Inline `if` con el operador lógico `&&`.

Mientras que el uso de sentencias `if-else` es una buena manera de condicionar el contenido, a veces es necesario utilizar una sintaxis diferente. Hay varias formas de insertar condiciones en JSX.

JSX permite [incrustar expresiones](https://reactjs.org/docs/introducing-jsx.html#embedding-expressions-in-jsx) encerrándolas entre llaves `{}`. Esto incluye el operador lógico de JavaScript `&&`. El operador lógico `&&` puede ser útil para incluir condicionalmente un elemento.

Utilizaremos el componente existente `MovieCard` para dar un ejemplo. Actualizaremos el componente para que muestre un texto diferente dependiendo de si la película ha ganado un Oscar o no:

```jsx
// src/components/MovieCard.js
// ... previous imports stay unchanged

function MovieCard(props) {
  const { movie, clickToDelete } = props;

  return (
    <div className="MovieCard">
      <h3>{movie.title}</h3>
      <p>Director: {movie.director}</p>
      <p>Rating: {movie.IMDBRating}</p>

      {movie.hasOscars && <p>Got the Oscar Award! </p>}
      {!movie.hasOscars && <p>Great movie but no Oscars! </p>}

      <button onClick={() => clickToDelete(movie._id)} className="btn-delete">
        Delete 
      </button>
    </div>
  );
}

export default MovieCard;

```

Resumamos cómo funciona el renderizado condicional anterior y comprobemos que lo hemos entendido:

1.  Cada objeto de película renderizado en la `MovieCard` viene a través de los props, y tiene una propiedad booleana `hasOscars`:
    
```jsx
{
  "_id": "1ae23ef1",
  "title": "The Godfather",
  "director": "Francis Coppola",
  "hasOscars": true,
  "IMDBRating": 9.2
}
```

    
2.  Hemos añadido dos nuevas expresiones incrustadas que utilizan el operador lógico `&&`:
    
```jsx
{
  movie.hasOscars && <p>Got the Oscar Award! </p>;
}
{
  !movie.hasOscars && <p>Great movie but no Oscars! </p>;
}
```

    
3.  La expresión lógica `&&` se evalúa de izquierda a derecha y se comprueba si puede haber un "cortocircuito" en la evaluación.
    
    Esto funciona porque en JavaScript, `true && expression` siempre se evalúa como `expression`, y `false && expression` siempre se evalúa como `false`.
    
    - Si la condición en el lado izquierdo es `true`, el contenido justo después de `&&` aparecerá en la salida.
        
    - Si la condición del lado izquierdo es `false`, el contenido no se mostrará.
        

**Operador lógico `&&` - Evaluación en "cortocircuito "**.

- Si la condición del lado izquierdo es _true_, se ejecuta el código del lado derecho.
- Si la condición del lado izquierdo es _false_, el operador `&&` se "cortocircuitará" para detener la ejecución, y el código del lado derecho no se ejecutará.

  
### Inline if-else con operador ternario `?`.

En JSX, las sentencias **`if-else` no pueden usarse directamente en el marcado.** 
El siguiente código de ejemplo arrojará un error:

```jsx function Example () {
  const showTitle = true;

  return(
    <div>
      {
        if (showTitle) {
          <h1> Example </h1>
        }
      }
    </div>
  )
}

export default Example;
```

Sin embargo, existe otra técnica para complementar esto. Otra forma de mostrar condicionalmente elementos en línea es utilizar el operador condicional (ternario) de JavaScript [`condition ? true : false`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/Conditional_Operator).

Haremos otro ejemplo de cómo mostrar contenido condicionalmente. Esta vez utilizaremos el operador ternario `?`. Actualicemos el código en nuestro `MovieCard.js`:

```jsx
// src/components/MovieCard.js
// ... previous imports stay unchanged

function MovieCard(props) {
  const { movie, clickToDelete } = props;

  return (
    <div className="MovieCard">
      <h3>{movie.title}</h3>
      <p>Director: {movie.director}</p>
      <p>Rating: {movie.IMDBRating}</p>

      {/*   {movie.hasOscars && <p>Got the Oscar Award! </p>}   */}
      {/*   {!movie.hasOscars && <p>Great movie but no Oscars! </p>}   */}
      

      {movie.hasOscars ? <p>Got the Oscar Award! </p> : <p>Great movie but no Oscars!</p>}

      <button onClick={() => clickToDelete(movie._id)} className="btn-delete">
        Delete 
      </button>
    </div>
  );
}

export default MovieCard;
```

El operador ternario `?` actúa como una sentencia en línea `if...else`.

Como puede ver, el ejemplo anterior da el mismo resultado que el anterior, que utiliza `&&`. Depende de usted elegir un estilo apropiado basado en lo que usted y su equipo consideren más legible.


## Renderizado condicional en función del Estado

Las variables de estado se utilizan habitualmente junto con condicionales para especificar el aspecto que debe tener la interfaz de usuario. Podemos utilizar variables de estado para mostrar u ocultar contenido en el componente.

Para mostrar esto, crearemos un nuevo archivo `ImprovedMovieList.js`, y reutilizaremos el código del componente existente `MovieList`. Además del código que copiamos de `MovieList` añadiremos una nueva variable de estado `showMovies` y un _button_ con un escuchador de eventos:

```jsx
// src/components/ImprovedMovieList.js

import { useState } from 'react';
import moviesData from '../movies-data.json';
import MovieCard from './MovieCard';

function ImprovedMovieList() {
  const [movies, setMovies] = useState(moviesData);
  // Declare a new state variable, which we'll call "showMovies"
  const [showMovies, setShowMovies] = useState(true);

  const deleteMovie = movieId => {
    const filteredMovies = movies.filter(movie => {
      return movie._id !== movieId;
    });

    setMovies(filteredMovies);
  };

  const toggleShowMovies = () => {
    setShowMovies(!showMovies);
  };

  return (
    <div>
      <h2>Improved Movie List</h2>

      <button onClick={toggleShowMovies}>{showMovies ? 'Hide' : 'Show'}</button>

      {showMovies &&
        movies.map(movie => {
          return <MovieCard key={movie._id} movie={movie} clickToDelete={deleteMovie} />;
        })}
    </div>
  );
}

export default ImprovedMovieList;
```

Actualizaremos el archivo `App.js` para importar y mostrar el componente `ImprovedMovieList`:

```jsx
// App.js
// ... previous imports stay unchanged

import ImprovedMovieList from './components/ImprovedMovieList';

function App() {
  const [isLoading, setIsLoading] = useState(false);

  if (isLoading) {
    return <Spinner />;
  } else {
    return (
      <div className="App">
        {/* <MovieList /> */}
        <ImprovedMovieList />;
      </div>
    );
  }
}

export default App;
```

Vamos a explicar el ejemplo anterior dividiéndolo en partes:

1.  Copiamos el código del componente existente `MovieList` y lo utilizamos para crear un nuevo componente `ImprovedMovieList`.
    
2.  Al nuevo componente `ImprovedMovieList`, le añadimos una variable de estado `showMovies` que estamos usando para _ocultar_ y _mostrar_ la lista de películas:
    
```jsx
const [showMovies, setShowMovies] = useState(true);         
```

3.  También añadimos un botón con un receptor de eventos `onClick`:

```jsx
<button onClick={ toggleShowMovies }> { showMovies ? 'Hide' : 'Show' } </button>       
```

4.  La función `toggleShowMovies` se invoca cada vez que el usuario pulsa sobre el botón.
    
5.  La función `toggleShowMovies` se utiliza para actualizar el valor de `showMovies`.
    
    Utilizamos el operador (NOT) [`!`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_NOT) para cambiar el valor de `showMovies` al booleano opuesto: `!showMovies`:
    
    - Si `showMovies` es `true` se convierte en `false`.
    - Si `showMovies` es `false` se convierte en `true`.
    
    Este valor se establece como el nuevo estado `setShowMovies(!showMovies)`, que hará que el componente se vuelva a renderizar.
    
6.  Por último, utilizamos el operador `&&` para _mostrar_ u _ocultar_ la lista de películas dependiendo de si `showMovies` es _true_ o _false_:

```jsx
{
	showMovies &&
	      movies.map(movie => {
	            /* rest of the code */
	    });
}         
```

  
![Example - Hide and show Improved Movie List](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-lists/react-conditional-rendering-result.gif)


## Extracción de condiciones a funciones

Siempre debemos vigilar y esforzarnos por mantener nuestro código limpio y legible. La lógica condicional de nuestros componentes puede volverse a veces demasiado compleja y difícil de razonar.

Cuando nuestros condicionales se vuelven demasiado grandes y difíciles de razonar, debemos simplificar el código. Podemos hacerlo extrayendo partes de la lógica en funciones.

Vamos a crear un nuevo componente `ImprovedMovieCard` para mostrar un ejemplo de cómo hacer esto:

```jsx
// src/components/ImprovedMovieCard.js

import React from 'react';

function ImprovedMovieCard(props) {
  const { movie, clickToDelete } = props;

  function generateScoreLabel(score) {
    if (score > 9) {
      return <span className="green">9+</span>;
    } else if (score < 7) {
      return <span className="red">{score}</span>;
    } else {
      return <span className="black">{score}</span>;
    }
  }

  return (
    <div className="MovieCard">
      <h3>{movie.title}</h3>
      <p>Director: {movie.director}</p>
      <p>IMDB Rating: {generateScoreLabel(movie.IMDBRating)}</p>

      {movie.hasOscars ? <p>Got the Oscar Award! </p> : <p>Great movie but no Oscars!</p>}

      <button onClick={() => clickToDelete(movie._id)} className="btn-delete">
        Delete 
      </button>
    </div>
  );
}

export default ImprovedMovieCard;
```

Colocamos parte de la lógica condicional, responsable de mostrar la puntuación IMDB de la película, en una función.

Para evitar escribir los condicionales inline creamos una función llamada `generateScoreLabel`. La función `generateScoreLabel` toma un argumento `score`, y devuelve un elemento span con un formato diferente, dependiendo de la puntuación de la película.

Para ver el resultado, importaremos el nuevo componente `ImprovedMovieCard` a `ImprovedMovieList.js` y lo utilizaremos en lugar del componente `MovieCard`:

```jsx
// src/components/ImprovedMovieList.js
// ... previous imports stay unchanged

import ImprovedMovieCard from './ImprovedMovieCard';

function ImprovedMovieList() {
  const [movies, setMovies] = useState(moviesData);
  const [showMovies, setShowMovies] = useState(true);

  const deleteMovie = movieId => {
    const filteredMovies = movies.filter(movie => {
      return movie._id !== movieId;
    });
    setMovies(filteredMovies);
  };

  const toggleShowMovies = () => {
    setShowMovies(!showMovies);
  };

  return (
    <div>
      <h2>Improved Movie List</h2>

      <button onClick={toggleShowMovies}>{showMovies ? 'Hide' : 'Show'}</button>

      {showMovies &&
        movies.map(movie => {
          return (
            <ImprovedMovieCard 
              key={movie._id} 
              movie={movie} 
              clickToDelete={deleteMovie} 
            />);
        })}
    </div>
  );
}

export default ImprovedMovieList;
```
  
**[⬆ Volver a contenido](#contenido)**