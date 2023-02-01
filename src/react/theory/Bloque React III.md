### Contenido
- [Forms (Controlled Componente)](#forms-controlled-components)
	- [Getting Started](#getting-started)
	- [Forms](#formularios)
	- [Controlled Components](#controlled-components)
	- [Data Flow](#flujo-de-datos---datos-abajo-acciones-arriba)
- [Hooks & Lifecycle](#hooks-and-lifecycle)
	- [The Component Lifecycle](#the-component-lifecycle)
	- [Hooks](#hooks)
	- [Fetching data with useEffect](#obtención-de-datos-con-useeffect)
- [Routing Introduction](#introducción-a-routing)
	- [React Router](#react-router)
- [Routing Advanced](#routing-advanced)
	- [URL Parameters](#url-parametros)
	- [Query Strings](#query-strings)
	
# Forms (Controlled Components)

## Introducción

![](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/form-example.png)

En esta unidad de aprendizaje, veremos cómo implementar **formularios** en nuestras aplicaciones React. Como ya sabemos, los elementos `HTML form` funcionan un poco diferente a otros elementos **DOM**. Los elementos de formulario naturalmente mantienen algún _estado interno_.

En React, implementamos formularios utilizando un enfoque ligeramente diferente. Usamos la etiqueta HTML `form` para crear formularios, pero sin depender del estado interno del formulario. En su lugar, los valores del formulario se controlan utilizando el estado del componente. Por ahora, esto puede no tener mucho sentido, pero lo tendrá al final de esta lección. 

### Empezando

Vamos a crear una nueva aplicación React que utilizaremos para los siguientes ejemplos:

```
$ npx create-react-app react-forms  
$ cd react-forms  
$ npm start         
```

Limpia un poco el `App.js`, para que tenga la siguiente estructura:
```jsx
// App.js
import "./App.css";
 
function App() {
  return <div className="App"></div>;
}
 
export default App;
```

Sigue adelante y crea los archivos que se muestran a continuación utilizando los fragmentos proporcionados:

```jsx
// src/components/MovieList.js
 
import { useState } from "react";
import moviesDataJSON from "../movies-data.json";
import MovieCard from "./MovieCard";
 
 
function MovieList() {
  const [movies, setMovies] = useState(moviesDataJSON);
 
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

```jsx
// src/components/MovieCard.js
 
import React from "react";
 
function MovieCard(props) {
  const { movie } = props;
 
  return (
    <div className="MovieCard">
      <h3>{movie.title}</h3>
      <p>Director: {movie.director}</p>
      <p>Rating: {movie.IMDBRating}</p>
    </div>
  );
}
 
export default MovieCard;
```

```jsx
// src/App.js
 
import "./App.css";
import MovieList from "./components/MovieList";
 
function App() {
  return (
    <div className="App">
      <MovieList />
    </div>
  );
}
 
export default App;
```

##### `src/movies-data.json`
```js
[
  {
     "_id":"1ae22ff0",
     "title":"A Beautiful Mind",
     "director":"Ron Howard",
     "hasOscars":true,
     "IMDBRating":8.2
  },
  {
     "_id":"1ae22ff1",
     "title":"American Gangster",
     "director":"Ridley Scott",
     "hasOscars":false,
     "IMDBRating":7.9
  },
  {
     "_id":"1ae22ff2",
     "title":"American Hustle",
     "director":"David O. Russel",
     "hasOscars":false,
     "IMDBRating":7.2
  },
  {
     "_id":"1ae22ff3",
     "title":"Beauty and the Beast",
     "director":"Gary Trousdale",
     "hasOscars":true,
     "IMDBRating":8.1
  },
  {
     "_id":"1ae22ff4",
     "title":"Brave heart",
     "director":"Mel Gibson",
     "hasOscars":true,
     "IMDBRating":8.3
  },
  {
     "_id":"1ae22ff5",
     "title":"Captain Phillips",
     "director":"Paul Greengrass",
     "hasOscars":false,
     "IMDBRating":7.8
  },
  {
     "_id":"1ae22ff6",
     "title":"Dallas Buyers Club",
     "director":"Jean-Marc Vallée",
     "hasOscars":true,
     "IMDBRating":8.1
  },
  {
     "_id":"1ae22ff7",
     "title":"Django Unchained",
     "director":"Quentin Tarantino",
     "hasOscars":true,
     "IMDBRating":8.4
  },
  {
     "_id":"1ae22ff8",
     "title":"Die Hard",
     "director":"John McTiernan",
     "hasOscars":false,
     "IMDBRating":8.2
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
 
h2 {
  padding: 15px 30px;
  border: 1px solid #6d6d6d;
  background: #ad89fb;
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
 
.MovieCard,
.AddMovie {
  border: 1px solid grey;
  box-shadow: 0px 2px 3px grey;
  width: 400px;
  text-align: center;
  margin-bottom: 20px;
  padding: 10px;
  border-radius: 4px;
}
 
.AddMovie {
  background: #fffee7;
}
 
.AddMovie label {
  width: 100px;
  display: block;
  margin: 0 auto;
}
 
.AddMovie input {
  padding: 10px;
  display: inline-block;
  margin: 2px 0 10px;
}
 
.AddMovie input[type='checkbox'] {
  height: 30px;
  display: block;
  margin: 0 auto;
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
**[⬆](#contenido)**

## Formularios

Los elementos HTML `<form>` funcionan de forma un poco diferente a otros elementos DOM. Antes de empezar, repasemos las características más importantes de los elementos `<form>`:

- Los elementos de formulario por defecto mantienen un estado interno. Este estado interno es la forma en que los elementos de formulario almacenan los valores de entrada.
    
- Otro comportamiento importante de los formularios HTML es el envío del formulario.  Cada vez que un usuario envía el formulario, el formulario enviará los datos y refrescará la página. Este es un comportamiento no deseado en aplicaciones de una sola página (aplicaciones React). Cuando se recarga una página, se recarga toda la aplicación y se pierde cualquier estado existente.
    

Para anular este comportamiento por defecto, debemos almacenar los datos del formulario en el estado y tener una función JavaScript que maneje el envío del formulario. Este enfoque se denomina "componente controlado".

**[⬆ Volver a contenido](#contenido)**

## Controlled Components

### ¿Qué es un Componente Controlado?

En HTML, los elementos de formulario como `<input>`, `<textarea>` y `<select>` normalmente mantienen su propio estado y lo actualizan en función del input del usuario. Este es un comportamiento predeterminado del formulario dictado por el navegador.

En un componente controlado, se anula el comportamiento predeterminado del formulario. Los datos del formulario son gestionados por un componente React y se mantienen _en el estado del componente_. El estado del componente actúa como _"única fuente de verdad"_ manteniendo los valores de los elementos del formulario.

Un componente controlado es un componente que renderiza elementos de formulario y los controla manteniendo los datos del formulario en el estado del componente.

**[⬆](#contenido)**

### Creación de un componente controlado

Vamos a crear un componente controlado. Crea un nuevo archivo `AddMovie.js` dentro de la carpeta `./src/components` y agrégale el siguiente contenido:

```jsx
// src/components/AddMovie.js

import { useState } from "react";

function AddMovie(props) {
  const [title, setTitle] = useState("");
  const [director, setDirector] = useState("");
  const [IMDBRating, setIMDBRating] = useState(5);
  const [hasOscars, setHasOscars] = useState(true);

  return (
    <div className="AddMovie">
      <h4>Add a Movie</h4>

      {/* form will be added here */}
    </div>
  );
}

export default AddMovie;
```

Bien, hasta aquí tenemos el estado configurado así que pasemos a crear nuestro primer formulario React:

```jsx
// ./src/components/AddMovie.js

// ...

  return (
    <div className="AddMovie">
      <h4>Add a Movie</h4>
  
      <form>
        <label>Title: </label>
        <input 
            type="text" 
            name="title" 
            value={title} 
        />
        
  
        <label>Director: </label>
        <input 
            type="text" 
            name="director" 
            value={director} 
        />
  
        <label>IMDB Rating: </label>
        <input 
            type="number" 
            name="IMDBRating" 
            value={IMDBRating} 
        />
  
        <label>Won Oscars: </label>
        <input 
            type="checkbox" 
            name="hasOscars" 
            checked={hasOscars} 
        />
        
        <button type="submit">Add a Movie</button>
      </form>
    </div>
  );

// ...
```

Todavía no podemos ver el formulario porque aún no hemos usado este componente. Así que vamos a importarlo y renderizarlo en nuestro componente `MoviesList.js`:

```jsx
// ./src/components/MoviesList.js
// ... previous imports stay unchanged

import AddMovie from "./AddMovie";

function MovieList() {
  const [movies, setMovies] = useState(moviesDataJSON);

  return (
    <div>
      <AddMovie /> {/* <==  ADD HERE ! */}
      { movies.map(movie => {
        return <MovieCard key={movie._id} movie={movie} />;
      }) }
    </div>
  );
}

export default MovieList;
```

Bien, ahora podemos ver el formulario PERO la consola del navegador está ardiendo . Tenemos que hacer algo con este error:

> _You provided a `value` prop to a form field without an `onChange` handler… set either `onChange` or `readOnly`._

Si intentas escribir alguna entrada en el formulario, te darás cuenta de que las entradas no funcionan.

Cada una de nuestras entradas está ahora conectada al estado a través del atributo `value`. Las entradas muestran ahora los valores procedentes de sus correspondientes variables de estado a las que están conectadas (por ejemplo, `value={director}`.

Para mostrar el contenido introducido en la entrada, debemos actualizar su variable de estado en cada pulsación de tecla. Para ello, debemos añadir un evento "onChange" y una función "handler" a cada entrada, que se ejecutará cada vez que se pulse una tecla o se produzca un cambio en la entrada.

Añadiremos un evento `onChange` a cada elemento de entrada y crearemos una _handler function_ para cada entrada:

```jsx
// ./src/components/AddMovie.js

// ... previous imports stay unchanged

function AddMovie(props) {
  // ...

  const handleTitleInput = e => setTitle(e.target.value);

  const handleDirectorInput = e => setDirector(e.target.value);

  const handleRatingInput = e => setIMDBRating(e.target.value);

  const handleOscarsInput = e => setHasOscars(e.target.checked);
  // e.target.checked is a boolean value from the `checkbox` input

  return (
    <div className="AddMovie">
      <h4>Add a Movie</h4>
      <form>
        <label>Title:</label>
        <input 
          type="text" 
          name="title" 
          value={title} 
          onChange={handleTitleInput} 
        />

        <label>Director:</label>
        <input 
          type="text" 
          name="director" 
          value={director} 
          onChange={handleDirectorInput} 
        />

        <label>IMDB Rating:</label>
        <input 
          type="number" 
          name="IMDBRating" 
          value={IMDBRating} 
          onChange={handleRatingInput} 
        />

        <label>Won Oscars:</label>
        <input 
          type="checkbox" 
          name="hasOscars" 
          checked={hasOscars} 
          onChange={handleOscarsInput} 
        />

        <button type="submit">Add a Movie</button>
      </form>
    </div>
  );
}

export default AddMovie;
```
Bien, genial, el error ha desaparecido y nuestras entradas ahora se actualizan en cada pulsación o cambio.

Nuestro componente `AddMovie` es ahora un _componente controlado_. Todas las entradas están controladas por el propio componente (no por el navegador) y están mostrando los valores procedentes del estado del componente.

**[⬆](#contenido)**

### Prevenir la recarga de la página

Todavía hay un comportamiento por defecto de los formularios que no hemos tratado. Estamos hablando del evento _"on submit"_. Nuestro formulario todavía tiene el comportamiento por defecto de los formularios HTML de recargar la página cuando se pulsa el botón de enviar.

Si haces clic en el botón de envío, verás que toda la aplicación se recarga y empieza desde cero. Esto significa que todo el estado guardado en los componentes se pierde, ¡se borra!

Para evitar esto tenemos que añadir un evento `onSubmit` y una función manejadora que gestione el envío del formulario. De esta forma podremos evitar el comportamiento por defecto y también acceder a los datos que el usuario ha introducido.

Actualizaremos el `AddMovie.js` y añadiremos un evento `onSubmit` al `<form>`. También crearemos una función manejadora `handleSubmit`:

```jsx 
// src/components/AddMovie.js
// ... previous imports stay unchanged

function AddMovie(props) {
  // ...

  const handleSubmit = (e) => {        // <==  ADD
    e.preventDefault();
    const newMovie = { title, director, IMDBRating, hasOscars };

    console.log("Submitted: ", newMovie);
  }

  
  return (
    <div className="AddMovie">
      <h4>Add a Movie</h4>
      <form onSubmit={handleSubmit} >        {/*   <== ADD EVENT */}
        <label>Title:</label>
        <input
          type="text"
          name="title"
          value={title}
          onChange={handleTitleInput}
        />

        <label>Director:</label>
        <input
          type="text"
          name="director"
          value={director}
          onChange={handleDirectorInput}
        />

        <label>IMDB Rating:</label>
        <input
          type="number"
          name="IMDBRating"
          value={IMDBRating}
          onChange={handleRatingInput}
        />

        <label>Won Oscars:</label>
        <input
          type="checkbox"
          name="hasOscars"
          checked={hasOscars}
          onChange={handleOscarsInput}
        />

        <button type="submit">Add a Movie</button>
      </form>
    </div>
  );
```

La función `handleSubmit` será llamada cada vez que el formulario sea enviado. Esto ocurre cuando el usuario pulsa sobre el botón de envío `Add a Movie` o pulsando Enter mientras el botón está en foco.

En la primera parte de la función usamos `e.preventDefault()` para cancelar el comportamiento por defecto del formulario, la página se recarga. Después de evitar que la página se recargue, accedemos a los datos de entrada almacenados en el estado (variables de estado `title`, `director`, etc.).

De momento, accedemos a estos datos para crear un nuevo objeto llamado `newMovie` y lo registramos en la consola. En los próximos pasos, veremos cómo añadir el pase de `newMovie` al componente `MovieList`.

**[⬆](#contenido)**


## Flujo de Datos - "Datos abajo, acciones arriba"

La frase _"Data down, Actions up"_ resume el flujo de información en las apps React. En las lecciones y ejercicios anteriores ya hemos podido pasar datos hacia abajo y enviar acciones hacia arriba, pero nos tomaremos un momento para explicar un poco más este concepto e ilustrarlo con un ejemplo.

**Data down**
En React, los datos se envían hacia abajo desde el componente padre al componente hijo a través de las _props_.

La segunda parte "actions up" se refiere a enviar los datos desde el componente hijo de vuelta al padre.

**Actions up**
El componente hijo puede enviar datos de vuelta al componente padre con la ayuda de funciones callback.

### Añadir nueva película

Conectaremos nuestro nuevo componente controlado `AddMovie` con la `MovieList`. Este es un ejemplo perfecto para demostrar como suben las acciones.

En el componente `MovieList`, crearemos una nueva función que luego pasaremos al componente `AddMovie`. El componente `AddMovie` utilizará esta función para enviar datos al componente padre `MovieList` (**actions up**).

Como hay varias cosas nuevas que tenemos que añadir o actualizar en `MovieList.js`, vamos a resumirlas en pasos:

1.  Añadir nueva función `addNewMovie`:
    
    La función `addNewMovie` recibe un argumento, un objeto `newMovie` a añadir. Añadiremos la `newMovie` al array `moviesData`. Para **evitar mutar el estado directamente**, crearemos una copia del array `movies` y le añadiremos la `newMovie`.
    
```jsx
const addNewMovie = (newMovie) => {
  // Create a new array
  const updatedMovies = [...movies, newMovie];

  setMovies(updatedMovies);
};

````
    
2.  Pase la función `addNewMovie` como prop al componente `<AddMovie />`:
    
```jsx
<AddMovie addMovie={addNewMovie} />
```

Después de añadir el código anterior al componente `MovieList`, tu archivo `MovieList.js` debería tener este aspecto:

```jsx
// src/components/MovieList.js
// ... imports stay unchanged

function MovieList() {
  const [movies, setMovies] = useState(moviesDataJSON);

  
  // ADD
  const addNewMovie = (movie) => {
    const updatedMovies = [...movies, movie];

    setMovies(updatedMovies);
  };


  return (
    <div>
      <AddMovie addMovie={addNewMovie} />  {/* <== UPDATE */}
      {movies.map(movie => {
        return <MovieCard key={movie._id} movie={movie} />;
      })}
    </div>
  );
}

export default MovieList;
```
Pasamos la función `addNewMovie` como prop al componente hijo `<AddMovie />`.

Cada vez que el formulario del componente `AddMovie` es enviado podemos llamar a `addNewMovie` y pasarle el objeto `newMovie`.

Actualizaremos la función `handleSubmit` en `AddMovie.js` para hacer esto:

```jsx
// src/components/AddMovie.js
// ... imports stay unchanged

function AddMovie(props) {
  // ...

  const handleSubmit = (e) => {
    e.preventDefault();
    const newMovie = { 
      title, 
      director,
      IMDBRating,
      hasOscars
    };

    console.log("Submitted", newMovie);
    props.addMovie(newMovie);          // <== ADD

    // Reset the state
    setTitle("");
    setDirector("");
    setIMDBRating(5);
    setHasOscars(true);
}

// ...

}
```

**Result:**  

![gif - react-forms-lu-result-2](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-lists/react-forms-lu-result-2.gif)

**[⬆](#contenido)**


### La etiqueta `select` y el filtrado

En HTML, `<select>` crea una lista desplegable. Para demostrar su funcionalidad, crearemos un nuevo componente llamado `FilterMovies`. Lo utilizaremos para filtrar la lista de películas mostradas, basándonos en su primera letra.

```jsx
// src/components/FilterMovies.js

import { useState } from "react";

function FilterMovies(props) {
  const [firstLetter, setFirstLetter] = useState("All");

  const handleSelect = e => {
    setFirstLetter(e.target.value);

    console.log("selected", e.target.value);
  };

  return (
    <div className="FilterMovies">
      <label>Show movies by first letter:</label>
      <select value={firstLetter} onChange={handleSelect}>
        <option value="All">All</option>
        <option value="A">A</option>
        <option value="B">B</option>
        <option value="C">C</option>
        <option value="D">D</option>
      </select>
    </div>
  );
}

export default FilterMovies;
```

El componente `FilterMovies` muestra un menú desplegable `<select>` . El menú desplegable muestra una lista de letras iniciales para todas las películas de nuestra lista. Creamos solo cinco opciones. Esto se debe a que tenemos una pequeña cantidad de películas en nuestra lista y todas comienzan con las letras A - D.

La etiqueta `<select>` funciona según el mismo principio que la etiqueta `<input>` . La convertimos en un _componente controlado_ de la misma manera, añadiendo el atributo `value` y el evento `onChange`.

Desglosemos el ejemplo anterior en pasos para una mejor comprensión:

1. Creamos un componente con estado llamado `FilterMovies`, con una variable de estado `firstLetter`. El valor inicial de la variable de estado `firstLetter` es una cadena `"All"`.
2. Conectamos el elemento `<select>` al estado mediante el atributo `value` : `value={firstLetter}`.
3. Para cambiar el estado y mostrar la _opción_ seleccionada, agregamos el evento `onChange` y una función de controlador `handleSelect`.
4. Cuando un usuario seleccione una opción del menú desplegable, se ejecutará la función `handleSelect` .
5. En la función `handleSelect` tenemos acceso al valor de _opción_ seleccionado `e.target.value`. Establecemos el valor seleccionado como el nuevo estado para la variable de estado `firstLetter` : `setFirstLetter(e.target.value);`

Procesaremos el nuevo componente `FilterMovies` dentro de `MovieList`. Actualice `MovieList.js` con el siguiente código:

```jsx
// src/components/MovieList.js
// ... previous imports stay unchanged

import FilterMovies from "./FilterMovies";  //  <== IMPORT

function MovieList() {
  const [movies, setMovies] = useState(moviesDataJSON);
  
  
  const addNewMovie = (movie) => {
    const updatedMovies = [...movies, movie];

    setMovies(updatedMovies);
  };

  return (
    <div>
      <FilterMovies />   {/*  <== ADD   */}
      
      <AddMovie addMovie={addNewMovie} />
      { movies.map((movie) => {
        return <MovieCard key={movie._id} movie={movie} />;
      }) }
    </div>
  );
}

export default MovieList;
```

A continuación, conectaremos el componente `FilterMovies` con `MovieList` y lo usaremos para filtrar la lista de películas.

Dado que hay varias cosas que debemos agregar en `MovieList.js`, las dividiremos en pasos:

1. Primero, agregue una nueva variable de estado `moviesData`:
    
     Crearemos una nueva variable de estado y la usaremos para almacenar todas las películas. Usaremos `moviesData` como nuestro array principal que contiene todas las películas. Lo necesitaremos en el siguiente paso, ya que tendremos que filtrar todas las películas.
    
```jsx
    const [moviesData, setMoviesData] = useState(moviesDataJSON); 
```
    

2.  Actualizar la función `addNewMovie`:
    
    Cada vez que se añada una nueva película, añadiremos el objeto `newMovie` al array `moviesData` y `movies`.

```jsx
const addNewMovie = (newMovie) => {
  const updatedMovies = [...movies, newMovie];
  const updatedMoviesData = [...moviesData, newMovie]; // <== ADD

  setMovies(updatedMovies);
  setMoviesData(updatedMoviesData);   // <== ADD
};
```

3.  Añadir nueva función `filterMovieList`:
    
    La función `filterMovieList` toma un argumento `str`, que es una cadena. Usaremos `str` para filtrar las películas.
    
    Si `str === "All"` mostraremos todas las películas.
    
    Si `str` tiene otro valor ( `"A"`, `"B"`, `"C"` o `"D"`) filtraremos las películas para mostrar sólo las que empiecen por esa letra.
    
    Al filtrar, usaremos `moviesData` como nuestro array maestro que contiene todas las películas.
    
```jsx
const filterMovieList = (str) => {
  let filteredMovies;
  
  if (str === "All") {
    filteredMovies = moviesData;
  } else {
    filteredMovies = moviesData.filter((movie) => {
      return movie.title[0].toLowerCase() === str.toLowerCase();
    });
  }

  setMovies(filteredMovies);
};
```
4.  Pase la función `filterMovieList` como prop al componente `<FilterMovies />`:
    
```jsx
<FilterMovies filterMovies={filterMovieList} />
```

Después de añadir el código anterior al componente `MovieList` tu archivo `MovieList.js` debería tener este aspecto:

```jsx
// src/components/MovieList.js
// ... imports stay unchanged

function MovieList() {
  const [movies, setMovies] = useState(moviesDataJSON);
  const [moviesData, setMoviesData] = useState(moviesDataJSON); // <== ADD

  
  // UPDATE
  const addNewMovie = (movie) => {
    const updatedMovies = [...movies, movie];
    const updatedMoviesData = [...moviesData, movie]; // <== ADD

    setMovies(updatedMovies);
    setMoviesData(updatedMoviesData);  // <== ADD
  };

  
  // ADD
  const filterMovieList = (str) => {
    let filteredMovies;
    if (str === "All") {
      filteredMovies = moviesData;
    } else {
      filteredMovies = moviesData.filter((movie) => {
        return movie.title[0].toLowerCase() === str.toLowerCase();
      });
    }

    setMovies(filteredMovies);
  };

  return (
    <div>
      <FilterMovies filterMovies={filterMovieList} />  {/* <== UPDATE */}
      
      <AddMovie addMovie={addNewMovie} />
      { movies.map(movie => {
        return <MovieCard key={movie._id} movie={movie} />;
      }) }
    </div>
  );
}

export default MovieList;
```

Hemos pasado la función `filterMovieList` como prop al componente hijo `<FilterMovies />`.

Ahora podemos invocar `filterMovieList` desde el componente `FilterMovies`. De esta forma podemos ejecutar la función `filterMovieList` cada vez que el usuario _seleccione_ una opción.

Actualicemos la función `handleSelect` en el `FilterMovies.js`:

```jsx
// src/components/FilterMovies.js
// ... imports stay unchanged

function FilterMovies(props) {
  // ...

  const handleSelect = (e) => {
    setFirstLetter(e.target.value);

    console.log("selected", e.target.value);
    props.filterMovies(e.target.value);      // <== ADD
  };

// ...
```
**[⬆ Volver a contenido](#contenido)**

================================================================================

# Hooks and Lifecycle

## Introducción

React proporciona una interfaz adicional que nos permite personalizar cómo se comporta un componente durante la fase específica de su existencia. Esta interfaz está disponible tanto en componentes _class_ como en componentes _functional_. En los componentes de clase, podemos personalizar el comportamiento del componente utilizando _[Métodos del ciclo de vida](https://reactjs.org/docs/glossary.html#lifecycle-methods)_ y en los componentes funcionales utilizando _[hooks](https://reactjs.org/docs/hooks-intro.html)_. En esta lección, nos centraremos en los componentes funcionales y en los hooks.

  
### Getting Started

Vamos a crear una nueva aplicación React que utilizaremos para los siguientes ejemplos:

```
$ npx create-react-app react-hooks  
$ cd react-hooks  
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

Como punto de partida, utilizaremos el código proporcionado a continuación. Siga adelante y cree el archivo que se muestra a continuación utilizando el fragmento proporcionado:

```css
/* index.css */
 
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
 
.App {
  font-family: sans-serif;
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  background: #ffffff;
}
 
.dark {
  background: #282c34;
  color: white;
}
 
.Counter,
.Timer {
  width: 300px;
  margin: 0 auto;
  padding: 20px;
  border: 2px solid black;
  background: cornflowerblue;
  border-radius: 5px;
}
 
.Timer {
  background-color: azure;
}
 
button,
select {
  padding: 5px 10px;
  min-width: 50px;
  margin: 5px;
  font-size: 18px;
}
 
.card {
  min-width: 400px;
  width: 90%;
  padding: 10px;
  box-shadow: 0px 2px 3px grey;
  margin-bottom: 20px;
  background: #cfb2d6;
  border-radius: 4px;
}
 
.list > li,
.list > p,
.list > div {
  margin: 10px;
}
 
.logo,
img {
  width: 200px;
}
 
.search-bar {
  padding: 20px;
}
 
.search-bar input {
  padding: 5px 20px;
  border-radius: 5px;
  border: 1px solid gray;
}
```

## The Component Lifecycle

Casi todo en nuestro mundo tiene un ciclo de vida, de principio a fin. Del mismo modo, desde el momento en que se crea, cada componente React pasa por un _ciclo de vida_.

Hay _tres_ fases principales en el _ciclo de vida_ de un componente React:  

### 1. Mounting

La fase de montaje tiene lugar cuando el componente se crea inicialmente y se añade al DOM. Podríamos describirla simplemente como _creación del componente_.

Durante la fase de montaje, el componente React es instanciado y renderizado en el DOM por primera vez. El _estado_ de los componentes con estado se inicializa en este momento.

La fase de _montaje_ a menudo se denomina _renderización inicial_.

### 2. Updating

A continuación viene la fase de _Actualización_, o _Update_ para abreviar. Una _Update_ sólo puede ocurrir después de que el componente haya sido inicialmente creado y renderizado en el DOM.

Un _Update_ se desencadena por el cambio de los disparadores `state` o `props` del componente. En otras palabras, siempre que cambien el estado o las propiedades del componente, éste se actualizará.

Podemos utilizar la fase _Updating_ para ejecutar código cuando el `state` o `props` del componente se actualicen.

### 3. Unmounting

La última fase en el _ciclo de vida_ del componente ocurre cuando el componente es eliminado del DOM y destruido. La documentación de React llama a esta fase _Desmontaje_.

La fase _Unmounting_ nos permite ejecutar el código y realizar la limpieza (cancelar peticiones, cancelar temporizadores activos, etc.) antes de que el componente sea eliminado del DOM.


## Hooks

### ¿Qué es un hook?

Los componentes funcionales de React tienen varios _hooks_ que podemos usar para ejecutar algún código durante la fase particular del ciclo de vida. Estos _hooks_ nos permiten _engancharnos_ a una fase específica e insertar nuestra propia funcionalidad.

Los _Hooks_ son funciones que te permiten "_engancharte_ a" las características de estado y ciclo de vida de _React_. Se utilizan en componentes funcionales. React llamará automáticamente a cada Hook que configures en un componente durante la fase correspondiente del ciclo de vida.

React proporciona varios hooks incorporados. Incluso puedes crear tus propios hooks para reutilizar comportamientos de estado entre diferentes componentes.

Veremos primero el hook `useState` y repasaremos lo que hemos aprendido previamente.

Los hooks no funcionan dentro de los componentes de clase. Los componentes de clase tienen [métodos de ciclo de vida especiales](https://reactjs.org/docs/state-and-lifecycle.html#adding-lifecycle-methods-to-a-class) que cumplen el mismo propósito. No cubriremos los métodos del ciclo de vida de las clases durante este tiempo.


### State hook - `useState`

#### Declarar el estado

El `useState` es un Hook que te permite añadir estado React a componentes de funciones.

En el siguiente ejemplo, utilizaremos el hook `useState` para añadir un estado a dos componentes. Empezaremos creando un nuevo componente `Counter`:

```jsx
// src/components/01-use-state/Counter.js

import React, { useState } from "react";

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

A continuación, importaremos el componente `Counter` y lo renderizaremos en `App.js`. También importaremos `useState` y lo usaremos para crear una variable de estado para mostrar/ocultar el componente `Counter`:

```jsx
// App.js

import "./App.css";
import { useState } from "react";
import Counter from "./components/01-use-state/Counter";

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {show && <Counter />}
    </div>
  );
}

export default App;
```

Vamos a resumir cómo funciona el hook `useState`:

Durante la fase de montaje, React crea las variables de estado declaradas por el hook `useState`.

El hook `useState()` toma un argumento, el _initial state_. Este valor se establece como la primera versión del estado disponible justo después del render inicial. Por ejemplo, en el componente `Counter` inicializamos la variable de estado `count` a `0`.

El hook `useState()` devuelve un par de valores envueltos en un array. El primer valor es la variable de estado, y el segundo es la función utilizada para actualizarla.

Podríamos representar la sintaxis de `useState()` usando el siguiente pseudocódigo:

```jsx
const [stateValue, updaterFunction] = useState(initialValue);
```

Para almacenar datos en el estado, a veces no es necesario crear múltiples variables de estado. **Las variables de estado también pueden contener objetos y arrays**, que puedes utilizar para agrupar datos similares.

#### Renderización de componentes

**Los componentes React se vuelven a renderizar automáticamente cada vez que hay un cambio en su "estado" o "prop".

En el ejemplo anterior, nuestro componente `Counter` se renderizará cada vez que se llame a `setCount()`. Del mismo modo, nuestro componente `App` se volverá a renderizar cada vez que se llame a `setShow()` para actualizar el estado.

Lo importante a tener en cuenta es que **_state_ debe ser actualizado a través de la función _updater_**. Nunca debemos actualizar el estado directamente. Si actualizáramos el estado directamente, el componente no se volvería a renderizar:

```jsx
// WRONG      

count = count + 1         
```

```jsx
// CORRECT      

setCount( count + 1 )         
```

Podemos resumir esta regla diciendo: "cada vez que una variable de estado se actualice a través de la función _updater_, el componente se volverá a renderizar".

El componente React se re-renderiza automáticamente cada vez que su `state` o `props` se actualizan.

#### Bucle infinito de re-renderización

Digamos que queremos crear un componente que actúe como un _timer_. El componente debería comenzar mostrando _0_ como el número de segundos. Cada segundo el número debería incrementarse en 1.

Piensa cómo haríamos esto. ¿Cómo actualizaríamos el estado cada segundo?

Para ello necesitaremos `setInterval`. Si recuerdas, `setInterval` nos permite ejecutar una función en un intervalo de tiempo determinado.

Ahora, aquí es donde llegamos al siguiente punto importante. **Usar `setInterval` directamente** en el componente de la función funcionará, pero **puede causar potencialmente un re-renderizado infinito**. Vamos a demostrarlo creando un nuevo componente, llamado `Timer`:

```jsx
// src/components/02-use-state-loop/Timer.js

import React, { useState } from "react";

function Timer() {
  const [count, setCount] = useState(0);

  setInterval(() => {
    setCount(count + 1);
  }, 1000);

  return (
    <div className="Timer">
      <h2>Timer</h2>

      <h3>{count}</h3>
    </div>
  );
}

export default Timer;
```

Lo importamos y renderizamos en la `App.js`:

```jsx
// App.js
// ... previous imports stay unchanged

import Timer from "./components/02-use-state-loop/Timer";   // <== IMPORT

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {/* {show && <Counter />} */}
      
      {show && <Timer />}                     {/* <== ADD  */}
    </div>
  );
}

export default App;
```

¿Qué ocurre cuando ejecutamos nuestra aplicación con el nuevo componente `Timer`?

Observa cómo el temporizador empieza a comportarse de forma inesperada. La razón de esto es que el código anterior crea un bucle infinito de re-renderización.


![Example - Component in a re-rendering loop](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-hooks/react-rerendering-loop.gif)


Para entender mejor lo que ocurre, vamos a dividirlo en pasos:

1.  El componente `Timer` tiene un `setInterval` colocado directamente en el cuerpo de la función.
2.  2. El componente `setInterval` llama continuamente a `setCount()` (cada 1 segundo) para actualizar el _state_.
3.  El componente `Timer` se vuelve a renderizar, cada vez que el _state_ se actualiza.
4.  Cuando el componente se vuelve a renderizar, el código en el cuerpo de la función se ejecuta de nuevo y crea un nuevo `setInterval` temporizador.
5. De esta manera se crean múltiples temporizadores _setInterval_ causando un número creciente de re-renders hasta que hay demasiados re-renders y actualizaciones que el componente finalmente se bloquea.

La pregunta es, ¿cómo prevenir un bucle de re-renderización como el de arriba?

Hay dos reglas que debes tener en cuenta:

- Primero, **evitar llamar a la función actualizadora de estado _directamente_ en el cuerpo del componente**. Llamar a la función actualizadora de estado provoca que el estado se actualice en cada renderizado y causa un bucle de re-renderizado.
    
- En segundo lugar, cuando necesites **actualizar el estado tan pronto como se cree el componente, utiliza el hook `useEffect`**. Comúnmente se hace esto para la obtención inicial de datos cuando se establece una suscripción, o un temporizador.
    
    En el siguiente paso, veremos cómo hacer esto con el hook `useEffect`.

### Effect Hook - `useEffect`

#### ¿Qué es un Effect?

Hemos dicho que los _hooks_ permiten ejecutar cierto código en momentos concretos del ciclo de vida, como después de crear un componente, o después de actualizarlo. El nombre para estas acciones es "side effects" o para abreviar, "effects".

En React, un **_effect_ es: "_el código que quieres que se ejecute durante una fase específica del ciclo de vida_. "**.

Las suscripciones, temporizadores y otros efectos secundarios no están permitidos directamente dentro del cuerpo principal de un componente de función. Como hemos visto anteriormente, hacerlo provocará bucles de re-renderización, errores e inconsistencias en la interfaz de usuario.

El hook `useEffect` (también llamado _Effect Hook_) te permite ejecutar tus side effects. Obtener datos, configurar una suscripción, iniciar un temporizador y cambiar manualmente el DOM en componentes React son ejemplos de acciones comunes (también conocidas como _side effects_) que puedes querer configurar en tus componentes.

En concreto, el hook `useEffect` te permite ejecutar side effects durante las tres fases del ciclo de vida:

-   **Mounting phase**
-   **Update phase**
-   **Unmounting phase**

#### Sintaxis de `useEffect`

La sintáxis de `useEffect` es la siguiente:

```jsx
// Actual syntax
useEffect(() => {}, [])         
```

Como puedes ver `useEffect` toma dos argumentos:

```jsx
// Pseudo code:
useEffect(didUpdate, dependencyArray)         
```

- `didUpdate` - una función que contiene el código (side effect) que queremos ejecutar.
- `dependencyArray` - el array de valores de los que depende el efecto. React vigila este array para cualquier cambio y cuando un valor en este array cambia, el efecto se ejecutará.

#### `useEffect` - Mounting phase

Podemos configurar el `useEffect` para **ejecutar código en la mounting phase**, **sólo una vez**. Es decir, justo después de crear el componente y renderizarlo en el DOM por primera vez.

Para ello, usamos el hook `useEffect` con la siguiente sintaxis:

```jsx
// Run the effect only once 
// during the mounting phase

useEffect(() => {}, [])
```

El array vacío `[]` significa que "este efecto no depende de nada", y por lo tanto se ejecutará sólo una vez, después del render inicial.

Con el `useEffect` podemos arreglar nuestro componente `Timer` del ejemplo anterior. Podemos crear un efecto que se ejecute sólo una vez y que inicie el temporizador `setInterval` después del render inicial.

Para mostrar como fijar `useEffect`, crearemos un nuevo componente `TimerTwo`:

```jsx
// src/components/03-use-effect-mounting/TimerTwo.js

import React, { useState, useEffect } from "react";       // <== IMPORT

function TimerTwo() {
  const [count, setCount] = useState(0);

  // Add the effect in the function body
  useEffect(() => {
    console.log("useEffect - Mounting (initial render)");
    
    const id = setInterval(() => {
      setCount((prevCount) => prevCount + 1);
    }, 1000);
    
  }, [] );  // <--  [] means: Run the effect only once, after initial render

  return (
    <div className="Timer">
      <h2>Timer Two</h2>

      <h3>{count}</h3>
    </div>
  );
}

export default TimerTwo;
```

A continuación, lo importaremos y lo renderizaremos en `App.js`:

```jsx
// App.js
// ... previous imports stay unchanged

import TimerTwo from "./components/03-use-effect-mounting/TimerTwo";  // <== IMPORT

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {/* {show && <Counter />} */}
      {/* {show && <Timer />} */}

      {show && <TimerTwo />}              {/*  <== ADD  */}
    </div>
  );
}

export default App;
```

¡Et Voilà_! El componente funciona ahora como debería. Gracias a `useEffect`, iniciamos el temporizador **sólo una vez**, durante la mounting phase tras el render inicial.

El array de dependencias vacío `[]` es la parte crucial. Le dice a React que ejecute nuestro side effect (código en `useEffect`) sólo una vez.

Te habrás dado cuenta de que hemos llamado a nuestra función de actualización de estado `setCount` con una sintaxis diferente. Te preguntarás por qué no usamos la sintaxis habitual, como esta:

```jsx
setCount(count + 1);
```

Si lo hiciéramos así, nuestro temporizador se actualizaría a _1_ y luego se quedaría en el mismo valor (puedes probarlo).

**El problema es que `useEffect` captura el `count` del primer render.** Es igual a `0`.

Como nuestro efecto sólo se ejecuta una vez, el _closure_ en `setInterval` siempre hace referencia al `count` del primer render, y `count + 1` es siempre `1`.

La forma de solucionarlo es sustituir la función del actualizador de estado `setCount(count + 1)` por la función [functional update form](https://reactjs.org/docs/hooks-reference.html#functional-updates):

```jsx
setCount((prevCount) => prevCount + 1);
```

Esta es una sintaxis adicional que puede utilizar con las funciones _state updater_. De esta forma siempre podrás leer _estados_ frescos para esa _variable de estado_.

Ahora, haz clic en el botón **Ocultar** para quitar el componente de la pantalla. Si abres la _consola_ verás el siguiente error:

> Warning: Can’t perform a React state update on an unmounted component. This is a no-op, but it indicates a memory leak in your application. To fix, cancel all subscriptions and asynchronous tasks in a useEffect cleanup function.

El problema se produce porque el componente se elimina del DOM (se destruye) mientras el temporizador de intervalos sigue funcionando. Como dice la _advertencia_, esto puede causar una fuga de memoria. ¿Cómo debemos cancelar el intervalo restante?

Tenemos que cancelar el intervalo en la fase de _desmontaje_ antes de que el componente sea eliminado del DOM. Veremos cómo hacerlo a continuación.

#### `useEffect` - Unmounting phase

A menudo, los _efectos_ crean recursos que deben limpiarse antes de que el componente abandone la pantalla, como una suscripción o un temporizador, como en el ejemplo anterior. Antes de que el componente _desmonte_, debemos cancelar todos los procesos restantes para evitar fugas de memoria.

Para ello, la función pasada a **`useEffect` puede devolver una función de limpieza**.

Demostraremos cómo configurarla utilizando un nuevo componente ``TimerThree``:

```jsx
// ./src/components/04-use-effect-unmounting/TimerThree.js

import React, { useState, useEffect } from "react";

function TimerThree() {
  const [count, setCount] = useState(0);

  
  useEffect(() => {
    console.log("useEffect - Mounting (initial render)");
    const id = setInterval(() => {
      setCount((prevCount) => prevCount + 1);
    }, 1000);

    // Return a "cleanup function" which will run automatically
    // before the component is removed from the DOM
    return () => {                                               // <== ADD
      console.log("Cleanup - Component Unmounting");
      clearInterval(id);
    };
  }, []);
  

  return (
    <div className="Timer">
      <h2>Timer Three</h2>

      <h3>{count}</h3>
    </div>
  );
}

export default TimerThree;
```

A continuación, importaremos el componente `TimerThree` en `App.js` y lo renderizaremos:

```jsx
// App.js
// ... previous imports stay unchanged

import TimerThree from "./components/04-use-effect-unmounting/TimerThree"; // <== IMPORT

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {/* {show && <Counter />} */}
      {/* {show && <Timer />} */}
      {/* {show && <TimerTwo />} */}

      { show && <TimerThree /> }                  {/*  <== ADD  */}
    </div>
  );
}

export default App;
```

Actualizamos el código del ejemplo anterior `TimerTwo`, y añadimos la función de limpieza a nuestro `useEffect` :

```jsx
return () => {
  console.log("Cleanup - Component Unmounting");
  clearInterval(id);
};
```

Podemos pensar en la función devuelta como un "efecto de limpieza". React ejecutará la _función_ _devuelta_ automáticamente durante la _fase de desmontaje_, justo antes de que el componente sea eliminado del DOM y destruido. De esta forma podemos limpiar y cancelar cualquier proceso restante.

Esto nos permite cancelar el temporizador `setInterval` antes de que el componente sea eliminado de la UI. De esta forma nos deshacemos del _warning_ anterior.

Para detener el temporizador de intervalo, utilizamos el método `clearInterval()`.

**_Cleanup function_ es una función devuelta por `useEffect`**. Se utiliza para limpiar cualquier recurso restante que el componente haya creado como temporizadores, peticiones pendientes, etc. Cuando se establece, la _función de limpieza_ se ejecutará automáticamente durante la fase de desmontaje. Es decir, antes de que el componente se elimine del DOM.

#### `useEffect` - Conditional updates

Vimos cómo configurar `useEffect` para ejecutar código (efectos) sólo una vez, durante el renderizado inicial.

El hook `useEffect` también puede usarse para ejecutar código durante la fase _Update_, siempre que haya una actualización de estado o de props.

Como habrás notado, `useEffect` toma un segundo argumento `[]` el _array de dependencias_. El array de dependencias se utiliza para especificar los valores de los que depende el efecto. Además, React realiza un seguimiento de este array para saber si debe volver a ejecutar el efecto.

**Cada vez que un valor especificado en el array de dependencia se actualiza, React vuelve a ejecutar el efecto.

Crearemos un nuevo componente `TimerFour` usando el código anterior como base. Mostraremos cómo ejecutar condicionalmente un _effect_:

```jsx
// ./src/components/05-use-effect-conditional-updates/TimerFour.js
import React, { useState, useEffect } from "react";

function TimerFour() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("useEffect - Mounting (initial render)");
    const id = setInterval(() => {
      setCount((prevCount) => prevCount + 1);
    }, 1000);

    return () => {
      clearInterval(id);
      console.log("Component Unmounting");
    };
  }, []);
  

  // Add a new effect that will run only
  // when the `count` value updates
  useEffect(() => {                              // <== ADD
    console.log("useEffect - on update");
    document.title = count;
  }, [count] );     
  
  // [count] means: this effect depends on the value `count`,
  // therefore re-run the effect every time `count` updates.
  

  return (
    <div className="Timer">
      <h2>Timer Four</h2>
      <h3>{count}</h3>
    </div>
  );
}

export default TimerFour;
```

Igual que antes, importaremos y renderizaremos el nuevo componente `TimerFour` en `App.js`:

```jsx
// App.js
// ... previous imports stay unchanged

//  IMPORT 
import TimerFour from "./components/05-use-effect-conditional-updates/TimerFour";

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {/* {show && <Counter />} */}
      {/* {show && <Timer />} */}
      {/* {show && <TimerTwo />} */}
      {/* { show && <TimerThree /> } */}

      { show && <TimerFour /> }                  {/*  <== ADD  */}
    </div>
  );
}

export default App;
```

En el ejemplo anterior, hemos añadido un efecto al `TimerFour` que actualiza el título de la _página_. Como queremos ejecutar este efecto cada vez que la variable de estado `count` se actualiza, añadimos `count` al array de dependencias:

```jsx
// App.js
// ... previous imports stay unchanged

//  IMPORT 
import TimerFour from "./components/05-use-effect-conditional-updates/TimerFour";

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {/* {show && <Counter />} */}
      {/* {show && <Timer />} */}
      {/* {show && <TimerTwo />} */}
      {/* { show && <TimerThree /> } */}

      { show && <TimerFour /> }                  {/*  <== ADD  */}
    </div>
  );
}

export default App;
```

**Importante:** Establecer `useEffect` sin el segundo argumento `[]` (array de dependencias) hará que `useEffect` se ejecute en cada render. Esto podría causar un bucle infinito de re renderizado.

```jsx
useEffect(() => {})         
```

### Reglas de los hooks

Los hooks son funciones JavaScript, pero hay que seguir dos reglas cuando se usan. React proporciona un [plugin linter](https://www.npmjs.com/package/eslint-plugin-react-hooks) para aplicar estas reglas automáticamente. Este _plugin_ se incluye por defecto en _Create React App_. Las dos reglas son:

#### 1. Llamar hooks sólo en el nivel superior

**No llames a hooks dentro de bucles, condiciones o funciones anidadas. En su lugar, utiliza siempre hooks en el nivel superior de tu función React antes de cualquier retorno temprano. Siguiendo esta regla, te aseguras de que los hooks son llamados en el mismo orden cada vez que se renderiza un componente. Esto es lo que permite a React preservar correctamente el estado de los hooks entre múltiples llamadas a `useState` y `useEffect`. (Si tienes curiosidad puedes leer más sobre esto [aquí](https://reactjs.org/docs/hooks-rules.html#explanation).)

#### 2. Llamar hooks sólo desde funciones React

**No llames a los hooks desde funciones JavaScript normales, en su lugar, puedes::

- Llamar hooks desde componentes de funciones React.
- Llamar hooks desde [custom hooks](https://reactjs.org/docs/hooks-custom.html) .


## Obtención de datos con `useEffect`

Para el final, vamos a hacer un ejemplo de obtención de datos de una API y mostrarlo en un componente. Este es uno de los escenarios comunes donde usaremos hooks. Para ello necesitaremos los hooks `useEffect` y `useState`.

Para utilizar esta API aprenderemos a crear una local:
https://dev.to/myogeshchavan97/how-to-easily-create-and-host-your-own-rest-api-without-writing-a-single-line-of-code-2np4

Pregunte al Lead Teacher qué debe incluir en la API.

Crearemos un nuevo componente `GammaList` para demostrarlo:

```jsx
// src/components/GammaList.js

import { useState, useEffect } from "react";
import axios from "axios";

const apiURL = "http://localhost:3000/apartaments";

function GammaList() {
  const [fetching, setFetching] = useState(true);
  const [apartments, setApartments] = useState([]);

  useEffect(() => {
    console.log("useEffect - Initial render (Mounting)");
    axios.get(apiURL).then((response) => {
      setApartments(response.data);
      setFetching(false);
    });
  }, []);

  return (
    <div>
      <h3>List of apartments</h3>
      {fetching && <p>Loading ...</p>}

      {apartments.map((apt) => {
        return (
          <div key={apt._id} className="card">
            <img src={apt.img} alt="apartment" />
            <h3>{apt.title}</h3>
            <p>Price: {apt.pricePerDay}</p>
          </div>
        )
      })}
    </div>
  );
}

export default GammaList;
```

Renderizaremos el nuevo componente en el `App.js`:

```jsx
// App.js
// ... previous imports stay unchanged

import GammaList from './components/GammaList';      // <== IMPORT

function App() {
  const [show, setShow] = useState(true);

  return (
    <div className="App">
      <button onClick={() => setShow(!show)}>
        { show ? "Hide" : "Show"}
      </button>
      {/* {show && <Counter />} */}
      {/* {show && <Timer />} */}
      {/* {show && <TimerTwo />} */}
      {/* { show && <TimerThree /> } */}
      {/* {show && <TimerFour />} */}
      
      {show && <GammaList />}                  {/*   <== ADD   */}
    </div>
  );
}

export default App;
```

Asegúrate de instalar axios:

```
$ npm i axios         
```

Repasemos el código del componente `GammaList` y comprobemos que lo hemos entendido:

1.  Hemos importado el hook `useEffect` y el `useState`.
    
2.  En el cuerpo de la función del componente declaramos las variables de estado `fetching` y `apartments`:
    
    - La variable de estado `fetching` se utiliza para mostrar el mensaje _"Loading"_ cuando la obtención de datos está en curso.
        
    - La variable de estado `apartments` se utiliza para almacenar los datos procedentes de la API. Su estado inicial es un array vacío `[]`. El estado inicial de `apartments` debe ser un array, ya que estamos _mapeando_ sobre él en el `return`: `apartments.map((apt) =>` .
        
3.  A continuación, creamos un efecto utilizando el hook `useEffect`. Configuramos el efecto para que se ejecute _sólo una vez_ en el render inicial estableciendo el _array de dependencias_ vacío `[]` como segundo argumento de `useEffect`.
    
4.  Cuando el componente se renderiza inicialmente, el _effect_ se ejecuta y realiza una petición `axios` a la API.
    
5.  5. Una vez realizada la petición, tomamos los `response` _data_ devueltos por la API. El `response.data` contiene la lista de apartamentos. Llamamos a `setApartments(response.data)` para establecer los datos en el estado.
    
6.  La variable `fetching` se encarga de mostrar el mensaje de carga mientras se obtienen los datos. Por eso, en cuanto recibimos la respuesta de la API, la ponemos a false: `setFetching(false)`.

**[⬆ Volver a contenido](#contenido)**

================================================================

# Introducción a Routing 

## Introducción

React se utiliza para crear aplicaciones de una sola página. Sin embargo, esto no implica necesariamente que no podamos tener múltiples páginas en nuestras aplicaciones.

Aunque las _SPAs_ sólo tienen un archivo HTML, todavía se espera que tengan las características de los sitios web tradicionales, como la navegación entre páginas. Por ejemplo, los usuarios deben poder visitar diferentes páginas o marcar una página como favorita, lo que requiere varias páginas. Cada página debe tener también una URL específica. Además, los botones de avance y retroceso deberían mover al usuario hacia atrás y hacia delante en el historial de navegación.

React tiene su propia manera de tratar con esto, que se logra utilizando la biblioteca _**React Router**_. La librería router de React se compone de tres paquetes:

-   `react-router`,
-   `react-router-dom` 
-   `react-router-native`.

En esta lección, usaremos el paquete npm **react-router-dom** para crear múltiples páginas y navegación.

### Getting Started

Para empezar esta lección, vamos a crear una nueva aplicación React. Vamos a hacer un sitio web de portafolio simple con algunas páginas diferentes que permiten a los usuarios ir a través de ellos por separado.

```   
$ npx create-react-app react-routing-intro  
$ cd react-routing-intro         
```

Dentro de la carpeta de nuestro proyecto, _instala_ el `react-router-dom`:

```   
$ npm install react-router-dom         
```

Y entonces inicializa la app:

```
$ npm start         
```

Limpia la `App.js` un poco para que tenga la siguiente estructura:

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

Como punto de partida, utilizaremos el código proporcionado a continuación. Siga adelante y cree los archivos que se muestran a continuación utilizando los fragmentos proporcionados:

```css
/* index.css */
 
body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", "Roboto", "Oxygen",
    "Ubuntu", "Cantarell", "Fira Sans", "Droid Sans", "Helvetica Neue",
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
 
code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, "Courier New",
    monospace;
}
 
.App {
  text-align: center;
}
 
.page-img {
  width: 70%;
}
 
.Navbar {
  display: flex;
  justify-content: space-between;
  background: #352275;
  padding: 5px 20px;
}
 
.Navbar li,
.Navbar a {
  list-style: none;
  text-decoration: none;
  display: inline-block;
  margin: 0px 20px;
  font-size: 1.2rem;
  color: white;
}
```

```jsx
// src/pages/HomePage.js
 
const imgURL = "https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-routing/home.gif";
 
function HomePage() {
  return (
    <div>
      <h1>Home</h1>
      <img src={imgURL} alt="home gif" className="page-img" />
    </div>
  );
}
 
export default HomePage;
```

```jsx
// src/pages/AboutPage.js
 
const imgURL = "https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-routing/about.gif";
 
function AboutPage() {
  return (
    <div>
      <h1>About</h1>
      <img src={imgURL} alt="the office gif" className="page-img" />
    </div>
  );
}
 
export default AboutPage;
```

```jsx
// src/pages/ErrorPage.js
 
const imgURL = "https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-routing/404.gif";
 
function ErrorPage() {
  return (
    <div>
      <h1>404</h1>
      <img src={imgURL} alt="404 error gif" className="page-img" />
    </div>
  );
}
 
export default ErrorPage;
```

```jsx
// src/pages/ProjectsPage.js
 
import { useState, useEffect } from "react";
import projectsData from "./../projects-data.json";
 
function ProjectsPage() {
  const [projects, setProjects] = useState([]);
 
  // This effect will run only once on initial render.
  // To do it we set the dependency array empty [].
  useEffect(() => {
    setProjects(projectsData);
  }, []);
 
  return (
    <div>
      <h2>Projects</h2>
      {projects.map((project) => {
        return (
          <div key={project.id} className="project">
            <h3>{project.name}</h3>
            <p>{project.technologies}</p>
          </div>
        );
      })}
    </div>
  );
}
 
export default ProjectsPage;
```

```jsx
// src/components/Navbar.js
 
function Navbar() {
  return (
    <nav className="Navbar">
      <ul>
        <li>Home</li>
        <li>About</li>
        <li>Projects</li>
      </ul>
    </nav>
  );
}
 
export default Navbar;
```

**`src/projects-data.json`**
```js
[
  {
    "_id": "1a",
    "name": "The Frogger Clone",
    "year": 2017,
    "technologies": "JavaScript, jQuery",
    "description": "The first project game clone."
  },
  {
    "_id": "2b",
    "name": "iTravel",
    "year": 2017,
    "technologies": "Mongo DB, ExpressJS, NodeJS, JavaScript, HTML, CSS",
    "description": "Web App that allows logged in users to share their experiences about travel destinations."
  },
  {
    "_id": "3c",
    "name": "The Plan",
    "year": 2017,
    "technologies": "Mongo DB, ExpressJS, Angular2, NodeJS, JavaScript, HTML, CSS",
    "description": "Web App that allows logged in users to plan your next activity with your friends or business partners."
  },
  {
    "_id": "4e",
    "name": "UnoApp",
    "year": 2017,
    "technologies": "Mongo DB, ExpressJS, NodeJS, JavaScript, HTML, CSS",
    "description": "App for the lovers of the well-known game Uno"
  }
]
```


## React Router

_React Router_ es una colección de **componentes de navegación** utilizados para manejar la navegación front-end. _React Router_ hace esto vigilando la URL del navegador, modificando el historial del navegador y manteniendo el estado de la UI sincronizado. De esta forma, React Router nos permite navegar entre diferentes componentes como si fueran páginas.

**React Router** proporciona los siguientes componentes:

-   **`<BrowserRouter>`** -Este componente mantiene la _User Interface sincronizada con la URL_. Usa la History API de HTML5 .
-   **`<HashRouter>`** - Utiliza la parte hash de la URL. (Solo para navegadores antiguos que no admiten la API de historial de HTML5).
-   **`<Routes>`**
-   **`<Route>`** - Renderiza un componente UI_ dependiendo de la URL.
-   **`<Link>`** - Renderiza un link de navegación (basicamente un tag `<a>` , pero cambian la URL sin refrescar la página)

The first thing we need to do is to choose a router implementation; for web applications, we have two options:

**Side note:**

La [History APl](https://developer.mozilla.org/en-US/docs/Web/API/History_API) es una interfaz del navegador que proporciona acceso al _historial_ de sesiones del navegador (páginas visitadas en la pestaña actual) a través del objeto [history](https://developer.mozilla.org/en-US/docs/Web/API/Window/history). El objeto _history_ permite navegar hacia adelante y hacia atrás por el historial del usuario, manipular el contenido de la pila del historial y gestionar la ubicación actual (URL en el navegador) a través de `history.location`.

_React Router_ proporciona una abstracción sobre la interfaz de la API de Historia que nos permite crear múltiples páginas e implementar la navegación front-end.

### Componentes que representan páginas

Para construir un React SPA con múltiples páginas, necesitamos componentes separados que representen páginas. Ya habíamos creado la carpeta `/src/pages`. Dentro de ella, tenemos los componentes `HomePage.js`, `AboutPage.js`, `ErrorPage.js`, y `ProjectsPage.js`. En esta carpeta, deberías guardar sólo _componentes grandes_ que representen _páginas_. Si esto aún no tiene sentido, no te preocupes. Lo explicaremos en el siguiente paso.

### Configurar el React Router- `<BrowserRouter>`

En este punto, podemos empezar a implementar nuestra navegación front-end usando React Router.

El primer paso es configurar el `<BrowserRouter>`, que es un componente raíz para React Router. Para ello, primero tendremos que actualizar `index.js`.

```jsx
// index.js
// ... previous imports stay unchanged

import { BrowserRouter as Router } from 'react-router-dom'; // <== IMPORT

// Next, wrap the <App /> with the <Router> and </Router> tags

ReactDOM.render(
  <Router>                            
    <App />
  </Router>,                        
  document.getElementById("root")
);

reportWebVitals();
```

Importamos el `BrowserRouter` y le damos el alias `Router` utilizando la sintaxis `import as` de ES6.

El trabajo principal del componente `<Router>` es crear un objeto histórico y mantener un registro de la localización (URL). A partir de ahora, el componente `<Router>` controlará la navegación y el [browser history](https://developer.mozilla.org/en-US/docs/Web/API/History_API) en nuestra aplicación. Siempre que la localización (URL) cambie debido a alguna acción de navegación, `<Router>` interceptará ese cambio y renderizará el componente de página correspondiente.

### Crear rutas - `<Routes>` & `<Route>`

El siguiente paso es configurar el enrutamiento utilizando los componentes `<Route>`. El componente `<Route>` se utiliza para definir qué página queremos mostrar para una URL específica.

En el archivo `App.js`, importaremos los componentes de página `HomePage`, `AboutPage`, `ErrorPage`, y `ProjectsPage`. A continuación, para configurar el enrutamiento para empezar a mostrar estas páginas, necesitamos importar los componentes `Routes` y `Route` de `react-router-dom`. Los usaremos para definir las rutas y páginas que mostrará nuestra aplicación:

```jsx
// App.js
// ... previous imports stay unchanged 

import Navbar from "./components/Navbar";      // <== IMPORT
import HomePage from "./pages/HomePage";       // <== IMPORT
import AboutPage from "./pages/AboutPage";     // <== IMPORT
import ProjectsPage from "./pages/ProjectsPage";   // <== IMPORT
import ErrorPage from "./pages/ErrorPage";         // <== IMPORT

import { Routes, Route } from "react-router-dom";  // <== IMPORT

function App() {
  return (
    <div className="App">
      <Navbar />
      
      {/*   Add <Route /> components between <Routes> and </Routes>   */} 
      <Routes>
        <Route path="/" element={<HomePage />} /> 
        <Route path="/about" element={<AboutPage />} />
        <Route path="/projects" element={<ProjectsPage />} />
      </Routes>
      
    </div>
  );
}

export default App;
```
  
El componente `<Routes>` es el padre de los componentes `<Route>`. Cuando la URL cambia, `<Routes>` muestra el elemento del componente hijo `<Route>` que coincide con la ubicación de la URL.

Dentro de `<Routes>`, usamos componentes `<Route>` para definir las páginas de nuestra aplicación.

Las principales _props_ del componente `<Route>` son `path` y `element`. Por ejemplo, echemos un vistazo a la siguiente `<Ruta>`:

```jsx
<Route path="/about" element={ <AboutPage /> } />         
```

Esta `<Ruta>` dice lo siguiente: `<AboutPage />` se mostrará como contenido dentro de la `<Ruta>` siempre que la URL del navegador cambie a `/about`.

Puedes probarlo navegando al resto de las rutas a través de la barra de URL del navegador:

-   [http://localhost:3000/](http://localhost:3000/) --> **HomePage**
-   [http://localhost:3000/about](http://localhost:3000/about) --> **AboutPage**
-   [http://localhost:3000/projects](http://localhost:3000/projects) --> **ProjectsPage**

Excelente, ¡eso funciona muy bien! Definimos _tres páginas_ en nuestra app y creamos las _rutas_ correspondientes para que React Router sepa cuándo tiene que renderizarlas.

### 404 Page Route

Ahora bien, ¿qué pasaría si intentamos visitar una ruta (URL) inexistente?

Digamos que tecleamos mal la URL e intentamos abrir [http://localhost:3000/contact](http://localhost:3000/contact), la página que no existe. Haz la prueba tú mismo. No hay contenido, ¿verdad?

Esto es completamente normal ya que intentamos visitar la ruta (URL) que no existe en nuestra aplicación. Para solucionar este caso, es una buena práctica añadir un _fallback_ `<Ruta>` mostrando una página de Error. De esta forma podemos notificar al usuario que la página no existe.

Como nuestra página de Error, usaremos un componente existente `src/pages/ErrorPage.js`. Vamos a configurar una nueva ruta para este caso.

En `App.js`, crearemos una nueva `<Ruta>` esta vez **con el `path="*"`** que renderice el componente `ErrorPage`. Colocaremos esta nueva ruta en la parte inferior, después del resto de componentes `<Route>`:

```jsx
// App.js
// ... previous imports stay unchanged

function App() {
  return (
    <div className="App">
      <Navbar />
      
      <Routes>
        <Route path="/" element={<HomePage />} /> 
        <Route path="/about" element={<AboutPage />} />
        <Route path="/projects" element={<ProjectsPage />} />
        
        <Route path="*" element={ <ErrorPage /> } />   {/*  <== ADD */}        
      </Routes>

    </div>
  );
}

export default App;
```

Configurada de esta forma, la última `<Ruta>` actúa como una ruta alternativa que se activará sólo cuando ninguna de las otras rutas coincida.

Para probarlo, puede intentar visitar una ruta (URL) inexistente, como [http://localhost:3000/foo](http://localhost:3000/foo).

### Navegación - `<Link>`

Genial, hemos construido la base. Sigamos adelante. Necesitamos algunos _links_, y preferiblemente, los necesitamos en la _navbar_.

Nuestro componente `<Navbar />` ya contiene la estructura básica. Tendremos que actualizar y añadir enlaces que podamos utilizar para navegar entre las páginas.

Utilizaremos el componente `react-router-dom` `<Link>` . `<Link>` es un reemplazo de React Router para el elemento de enlace estándar `<a href=""> </a>`. Cada vez que renderice un componente `<Link>` , se renderizará un anchor (`<a>`) en el código HTML de su aplicación.

```jsx 
// src/components/Navbar.js

import { Link } from "react-router-dom";     // <== IMPORT

function Navbar() {
  return (
    <nav className="Navbar">
      <ul>
        <Link to="/"> Home </Link>           {/* <== ADD */}
        <Link to="/about"> About </Link>      {/* <== ADD */}
        <Link to="/projects"> Projects </Link>  {/* <== ADD */}
      </ul>
    </nav>
  );
}

export default Navbar;
```

Para probarlo, haga clic en los enlaces de la barra de navegación. Al hacer clic, un _Enlace_ activará la representación del componente de página correspondiente, uno en el que la prop `to` del _Enlace_ coincida con la `path` de la _Ruta_. Por ejemplo:

Al hacer clic en el _Link_ que tiene `to="/about"`:

```jsx
<Link to="/about"> About </Link>       
```

Activará la renderización del componente especificado en la Ruta con el valor `path="/about"`:

```jsx
<Route path="/about" element={<AboutPage />} />         
```

  
### Enlace de navegación estilizado - `<NavLink>`

El `<NavLink>` es un tipo especial de `<Link>` que puede estilizarse como "activo" cuando coincide con la ubicación actual. Para empezar a usar `<NavLink>`, tenemos que importarlo desde `react-router-dom`.

Como ejemplo de cómo usar `<NavLink>`, vamos a actualizar el componente `Navbar`. Reemplazaremos todos los `Link`s existentes con el `NavLink`:

```jsx
// src/components/Navbar.js

import { Link, NavLink } from "react-router-dom";   // <== IMPORT

function Navbar() {
  return (
    <nav className="Navbar">
      <ul>
        {/* <Link to="/"> Home </Link> */}
        {/* <Link to="/about"> About </Link> */}
        {/* <Link to="/projects"> Projects </Link> */}
        
        {/*    ADD    */}
        <NavLink to="/" className={({ isActive }) => isActive ? "selected" : ""}>
          Home
        </NavLink>
        
        <NavLink 
          to="/about" 
          className={({ isActive }) => isActive ? "selected" : ""}
         >
          About
        </NavLink>
        
        <NavLink 
          to="/projects" 
          className={({ isActive }) => isActive ? "selected" : ""}
        >
          Projects
        </NavLink>
        
      </ul>
      
    </nav>
  );
}

export default Navbar;
```

Añadiremos los siguientes estilos a `index.css`. Contiene estilos para el nombre de la clase que establecimos en el atributo `activeClassName`:

```css
/* index.css */
.selected {
  text-shadow: 1px 0px 3px white;
  color: #fff;
  border-bottom: rgba(255, 255, 255, 0.639) solid 2px;
  padding-bottom: 5px;
}
```

### `<Navigate>`

El componente `<Navigate>` se utiliza para implementar redireccionamientos, por ejemplo cuando queremos proteger una determinada página y mostrarla sólo a usuarios autorizados.

Para demostrar su uso, crearemos una nueva versión del componente `HomePage` que utiliza `<Navigate>`. Vamos a crear un componente llamado `HomePageWithNavigate`:

```jsx
// src/pages/HomePageWithNavigate.js

import { useState } from "react";
import { Navigate } from "react-router-dom";

const imgURL = "https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-routing/home.gif";


function HomePageWithNavigate() {
  const [isLoggedIn, setIsLoggedIn] = useState(true);

  if (!isLoggedIn) return <Navigate to="/error" />;

  return (
    <div>
      <h1>Home - With Navigate</h1>
      <img src={imgURL} alt="home" className="page-img" />
    </div>
  );
}

export default HomePageWithNavigate;
```

Lo importaremos en `App.js` y lo usaremos en la Ruta que renderiza el componente `HomePage`:

```jsx
// App.js
// ... previous imports stay unchanged

import HomePageWithNavigate from "./pages/HomePageWithNavigate";  // <== IMPORT 


function App() {
  return (
    <div className="App">
      <Navbar />

      <Routes>
        {/* <Route  path="/" element={<HomePage />} /> */}
        <Route  path="/" element={<HomePageWithNavigate />} />   {/* <== ADD */}
        <Route path="/about" element={<AboutPage/>} />
        <Route path="/projects" element={<ProjectsPage/>} />

        <Route path="*" element={<ErrorPage />} />
      </Routes>      
    </div>
  );
}

export default App;
```

Al redirigir un `<Navigate>` se navegará a una nueva ubicación (URL). La nueva ubicación sustituirá a la actual en la _pila de la historia_, como hacen las redirecciones del lado del servidor **(HTTP 3xx)**.

Como esto era sólo para propósitos de demostración, y para evitar que nuestra página de inicio nos diera 404, sigue adelante y cambia el valor de `isLoggedIn` a `true` en el archivo `HomePageWithNavigate.js`:

```jsx
// src/pages/HomePageWithNavigate.js

// ... no changes in imports

  
function HomePageWithNavigate() {
  const [isLoggedIn, setIsLoggedIn] = useState(true); // <== UPDATE

  // ... no changes
}

export default HomePageWithNavigate;
```

Ahora tenemos nuestra página de inicio de nuevo la representación de los contenidos, por lo que 404 se ha ido.

### Pasar props a un componente de página

En algunas ocasiones, es posible que desee renderizar un componente de página pasándole también algunos props adicionales.

Digamos que los _datos_ que mostramos en el componente `ProjectsPage`_ tienen que venir del componente padre a través de los props. Así, en lugar de cargar el archivo _`projects-data.json`_ directamente en el componente `ProjectsPage`, lo importaríamos en el componente `App.js` y se lo pasaríamos como una prop.

En el `App.js`, importaremos el array con los proyectos del fichero `src/projects-data.json`. Luego actualizaremos el `<Route>` que está renderizando la `ProjectsPage` para pasar el array como prop:

```jsx 
// App.js
// ... previous props stay unchanged

import projectsData from "./projects-data.json";    // <== IMPORT

function App() {
  return (
    <div className="App">
      <Navbar />
      
      <Routes>
        {/* <Route  path="/" element={<HomePage />} /> */}
        <Route  path="/" element={<HomePageWithNavigate />} />
        <Route path="/about" element={<AboutPage/>} />
        
        <Route 
          path="/projects" 
          element={ <ProjectsPage projects={projectsData} /> } 
        />

        <Route path="*" element={<ErrorPage />} />
      </Routes>
    </div>
  );
}

export default App;
```

El siguiente paso es actualizar el componente `ProjectsPage`. Eliminaremos la importación anterior y actualizaremos el hook existente `useEffect` para utilizar los datos que llegan a través de `props`:

```jsx
// ./src/pages/ProjectsPage.js

import { useState, useEffect } from "react";
// import projectsData from "./../projects-data.json";  // <== REMOVE

function ProjectsPage (props) {                     // <== UPDATE
  const [projects, setProjects] = useState([]);

  // This effect depends on `props.projects`.
  // It will run on initial render, and every time
  // when the `props.projects` updates.
  useEffect(() => {
    setProjects(props.projects);                  // <== UPDATE
  }, [props.projects]);                           // <== UPDATE

  
  return (
    <div>
      <h1>Projects</h1>
      {projects.map((project) => {
        return (
          <div key={project._id} className="project">
            <h3>{project.name}</h3>
            <p>{project.technologies}</p>
          </div>
        );
      })}
    </div>
  );
}

export default ProjectsPage;
```

El siguiente paso es actualizar el componente `ProjectsPage`. Eliminaremos la importación anterior y actualizaremos el hook existente `useEffect` para utilizar los datos que llegan a través de `props`:Utilizamos el array de dependencia para especificar que nuestro _effect_ depende de `props.projects`. De esta forma, el código del _effect_ se ejecutará tanto en el render inicial como cada vez que se actualice el valor de `props.projects`.

**[⬆ Volver a contenido](#contenido)**

================================================================

# Routing Advanced

## Introcción

Después de aprender los conceptos básicos de enrutamiento en React, ahora estás listo para abordar los conceptos avanzados de React Router. En esta lección, aprenderás a establecer y acceder a los parámetros de URL y a trabajar con cadenas de consulta de URL.

## Getting Started

Como punto de partida, utilizaremos el código de la _app_ que creamos en la parte anterior de React Router. 

Tal y como lo dejamos al final de la última lección, tenemos desplegadas las páginas _Home_, _About_ y _Project_. Ahora profundizaremos y aprenderemos a configurar páginas dinámicas con la ayuda del Enrutador React. Veamos cómo hacerlo.

## URL Parametros

Un **_parámetro URL_ es la parte de la URL que cambia dinámicamente.** Por ejemplo, si quisiéramos ver información sobre el proyecto _1a_, visitaríamos la ruta `/projects/1a`. Para ver la información sobre el proyecto _2b_, visitaríamos `/projects/2b`.

Esa última parte de la URL (`1a`, `2b`, etc.) que va cambiando es el parámetro _URL_. En los próximos pasos, explicaremos cómo configurar los parámetros _URL_ con `<Ruta>` y cómo acceder a ellos desde un componente.

### Projects Page

Trabajaremos sobre el componente existente `<ProjectsPage />`. Este es el aspecto del componente:

```jsx 
// src/pages/ProjectsPage.js

import { useState, useEffect } from "react";

function ProjectsPage (props) {
  const [projects, setProjects] = useState([]);

  useEffect(() => {
    setProjects(props.projects);
  }, [props.projects]);


  return (
    <div>
      <h1>Projects</h1>
      {projects.map((project) => {
        return (
          <div key={project._id} className="project">
            <h3>{project.name}</h3>
            <p>{project.technologies}</p>
          </div>
        );
      })}
    </div>
  );
}

export default ProjectsPage;
```

Repasemos el código anterior y expliquemos cómo funciona el componente `ProjectsPage`.

El componente `ProjectsPage` recibe un array de proyectos a través de props (`props.projects`). El array de proyectos se pasa como prop desde `App.js`.

Usamos el hook `useEffect` para ejecutar código después de que el componente se haya renderizado. En nuestro caso, lo usamos para guardar el array `props.projects` en la variable de estado `projects`.

Podemos ver la `ProjectsPage` haciendo click en el enlace disponible en la `Navbar` (ya tenemos un _NavLink_ en la `Navbar` que nos lleva a `/projects`). Sigue adelante y abre la página. Como puede ver, la página muestra una lista de proyectos.

Ahora empieza la diversión. Convertiremos el nombre de cada proyecto en un enlace en el que se puede hacer clic y que nos llevará a una _**Página de detalles**_ independiente para cada proyecto.


### Configuración de parámetros URL

¿Recuerdas cómo en el pasado con Express usábamos _`req.params`_ para obtener los ids de las URLs? Bueno, una característica similar está disponible en el React Router en el frontend.

Con _React Router_ podemos designar una parte dinámica de la URL para que coincida poniendo dos puntos `:` antes de ella. Esto es similar a lo que hicimos en Express. La única diferencia es que estamos haciendo esto **con React Router en el frontend**.

Empezaremos convirtiendo el nombre del proyecto en un _Link_ y veremos cómo cambia la URL.

Importaremos el `Link` de React Router a la `ProjectsPage.js` y actualizaremos la línea de código que está mostrando el nombre del proyecto:

```jsx
// src/pages/ProjectsPage.js
// ... previous imports stay unchanged

import { Link } from "react-router-dom";     // <== IMPORT

function ProjectsPage() {
  const [projects, setProjects] = useState([]);

  // This effect will run only once on initial render.
  // To do it we set the dependency array empty [].
  useEffect(() => {
    setProjects(props.projects);
  }, [props.projects]);

  return (
    <div>
      <h2>Projects</h2>
      {projects.map((project) => {
        return (
          <div key={project._id} className="project">
            <h3>
              
              {/*   ADD   */}
              <Link to={`/projects/${project._id}`}> 
                {project.name} 
              </Link>
              
            </h3>
            <p>{project.technologies}</p>
          </div>
        );
      })}
    </div>
  );
}

export default ProjectsPage;
```

Si ahora hacemos clic en el nombre de un proyecto, veremos que la URL cambia. Si hacemos clic en algunos de ellos, observará que una parte de la URL cambia _dinámicamente_: el id del proyecto.

Cada una de estas URLs debería navegar a la página que mostrará los datos sobre el proyecto específico. Como esta página aún no existe, vemos la página _404_ renderizada. Así que necesitaremos un nuevo componente de página para mostrar esa información.

Dentro de la carpeta `/pages`, crea un nuevo archivo llamado `ProjectDetailsPage.js`.

Dentro del archivo, importaremos el array `project-data.json` (este componente también necesitará acceder a él) y un hook de React Router - `useParams()`:

```jsx
// src/pages/ProjectDetailsPage.js

import projectsData from './../projects-data.json';
import { useParams, Link } from 'react-router-dom'

function ProjectDetailsPage(props) {
  
  const { projectId } = useParams();
  console.log('projectId -->', projectId);
  
  return (
    <div>
      <h1>Project Details</h1>
      
      <Link to="/projects">Back</Link>
    </div>
  )
}

export default ProjectDetailsPage;

```

El hook de React Router `useParams()` devuelve un objeto con parámetros URL. Lo usamos para obtener el valor del parámetro URL `projectId`.

Todavía hay un paso que tenemos que dar - tenemos que renderizar este componente, así que vamos a importarlo a nuestro `App.js`:

```jsx
import "./App.css";
import Navbar from "./components/Navbar";
import HomePage from "./pages/HomePage";
import AboutPage from "./pages/AboutPage";
import ProjectsPage from "./pages/ProjectsPage";
import ErrorPage from "./pages/ErrorPage";
import HomePageWithNavigate from "./pages/HomePageWithNavigate";
import { Routes, Route } from "react-router-dom";

import projectsData from './projects-data.json';

import ProjectDetailsPage from "./pages/ProjectDetailsPage";  // <== IMPORT

function App() {
  return (
    <div className="App">
      <Navbar />
      
      <Routes>
        {/* <Route  path="/" element={ <HomePage /> } /> */}

        <Route path="/" element={ <HomePageWithNavigate /> } />
        <Route path="/about" element={ <AboutPage /> } />
        
        <Route
          path="/projects"
          element={ <ProjectsPage projects={projectsData} /> }
        />
        
        {/*  ADD  */}
        <Route 
          path="/projects/:projectId" 
          element={ <ProjectDetailsPage /> } 
        />        

        <Route path="*" element={ <ErrorPage /> } />
      </Routes>
    </div>
  );
}

export default App;
```

Ahora, abra la **Página de Proyectos** en el navegador y haga clic en cualquiera de los enlaces.

Verá que a medida que cambia la URL se muestra la página `ProjectDetailsPage`. Si comprueba la _consola del navegador_, verá el id del proyecto procedente de los parámetros de la URL.

```
// projectId --> 1a         
```

### Accediendo a Parámetros URL

Nuestro siguiente paso es tomar el parámetro `projectId` que obtuvimos de la URL y mostrar el proyecto que tiene el mismo id. Vamos a hacerlo:

```jsx
// src/pages/ProjectDetailsPage.js

import projectsData from './../projects-data.json';
import { useParams, Link } from 'react-router-dom'

function ProjectDetailsPage(props) {

  const { projectId } = useParams();
  console.log('projectId', projectId);
  
  // Method .find() returns the first found matching element,
  // or `null` if no matching element is found.
  const foundProject = projectsData.find((oneProject) => {   //  <== ADD
    return oneProject._id === projectId;
  });

  return (
    <div>
      <h1>Project Details</h1>
      {!foundProject && <h3>Project not found!</h3>}  {/* <== ADD  */}

      {/*  ADD  */}
      {foundProject && (
        <>
          <h2>{foundProject.name}</h2>
          <h3>Tech Stack: {foundProject.technologies}</h3>
          <p>{foundProject.description}</p>
          <Link to="/projects">Back</Link>
        </>
      )}
    </div>
  );
}

export default ProjectDetailsPage;

```

¡Funciona a las mil maravillas! Podemos ver cómo se muestra la página de detalles de cada proyecto simplemente capturando el `projectId` de la URL. No es difícil, ¿verdad? Extraer un _id_ de la URL es el caso de uso más común y te ayudará mucho. Para ver un ejemplo diferente, visita la página: [React Training - URL Parameters](https://v5.reactrouter.com/web/example/url-params).


### Accediendo a Parámetros URL con `useEffect`

Otra forma de utilizar los valores del parámetro _URL_ sería con el hook `useEffect`. Probablemente necesitarás utilizar el mismo enfoque que el que se muestra en el siguiente ejemplo en tus futuras aplicaciones, así que vamos a mostrar cómo se hace.

Actualizaremos la página `ProjectDetailsPage` para importar los hooks `useState` y `useEffect`. Moveremos nuestra _lógica de búsqueda de proyecto_ al hook `useEffect`.

```jsx
// ./src/pages/ProjectDetailsPage.js

import projectsData from './../projects-data.json';
import { useParams, Link } from 'react-router-dom'
import { useState, useEffect } from 'react';         // <== IMPORT


function ProjectDetailsPage (props) {
  const [foundProject, setFoundProject] = useState(null); // <== ADD
  
  const { projectId } = useParams();
  console.log('projectId', projectId);  

  // This effect depends on the `projectId` value.
  // It will run on initial render, and every time
  // the `projectId` value updates.
  useEffect(() => {                                      // <== ADD
    const project = projectsData.find((projectObj) => {
      return projectObj._id === projectId;
    })

    if (project) {
      setFoundProject(project);
    }
    
  }, [projectId]);


  return (
    <div>
      <h1>Project Details</h1>
      
      {!foundProject && <h3>Project not found!</h3>}
      
      {foundProject && (
        <>
          <h2>{foundProject.name}</h2>
          <h3>Tech Stack: {foundProject.technologies}</h3>
          <p>{foundProject.description}</p>
          <Link to="/projects">Back</Link>
        </>
      )}
    </div>
  )
}

export default ProjectDetailsPage;
```

Tener la lógica de búsqueda del proyecto dentro del `useEffect` te permite sustituir fácilmente la lógica anterior para obtener los datos del servidor en lugar de obtenerlos de un array estático. 
Ejemplo:

```jsx
// ...
  const { projectId } = useParams();
  console.log('projectId', projectId);  

  useEffect(() => {
    // Get the project by id from the server
    axios.get('http://example.com/api/projects/' + projectId)
      .then((response) => {
        setFoundProject(response.data);
      })
    
  }, [projectId]);

// ...
```


## Query Strings

Las query strings se utilizan para incrustar datos en la URL. Cuando quieres pasar información a través de la URL, pero no quieres usar parámetros `URL`, usarías una (query string) **cadena de consulta.** Echemos un vistazo a la siguiente URL:

**[https://www.booking.com/search?place=Barcelona&destType=hotel](https://www.booking.com/search?place=Barcelona&destType=hotel)**

La URL anterior tiene dos cadenas de consulta: `place` y `destType`. De este modo, _[booking.com](http://booking.com/)_ utiliza las cadenas de consulta para filtrar el _lugar_ y el _tipo_ de habitación que busca.

![](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-routing/query-strings-example.png)

Ahora, ¿cómo accedemos a la información de las query strings? Lo hacemos usando el hook de React Router `useSearchParams()`. Vamos a crear un nuevo componente `QueryStringExample` para mostrar esto:

```jsx
// src/pages/QueryStringExample.js

import { useEffect } from 'react';
import { useSearchParams } from 'react-router-dom'

function QueryStringExample(props) {
  const [searchParams, setSearchParams] = useSearchParams();

  // Get the values from the URL query strings 
  // Example: http://localhost:3000/example?place=Miami&destType=Hotel
  const place = searchParams.get("place");
  const destType = searchParams.get("destType");
  
  useEffect(() => {
    console.log('place', place)
    console.log('destType', destType);
  }, []);

  return (
    <div>
      <h2>Query String Example</h2>
      <p>
        Open the console to see the logged query string values
      </p>
    </div>
  )
}

export default QueryStringExample;
```

Y como último paso lo importaremos a `App.js` y añadiremos una nueva `<Ruta>` para renderizarla:

```jsx
// App.js
// ... previous imports stay unchanged

import QueryStringExample from "./pages/QueryStringExample"; // <== IMPORT

function App() {
  return (
    <div className="App">
      <Navbar />
      
      <Routes>
        {/* <Route  path="/" element={ <HomePage /> } /> */}

        <Route path="/" element={ <HomePageWithNavigate /> } />
        <Route path="/about" element={ <AboutPage /> } />
        
        <Route
          path="/projects"
          element={ <ProjectsPage projects={projectsData} /> }
        />

        <Route 
          path="/projects/:projectId" 
          element={ <ProjectDetailsPage /> } 
        />            
        
        {/* ADD  */}
        <Route path="/example" element={ <QueryStringExample /> } />

        <Route path="*" element={ <ErrorPage /> } />
      </Routes>
    </div>
  );
}

export default App;
```

Ahora, para verlo en acción visita la ruta `/example` e incluye una cadena de consulta con las claves `place` y `destType`. Por ejemplo:

-   [http://localhost:3000/example?place=Miami&destType=Apartment](http://localhost:3000/example?place=Miami&destType=Apartment)
    
-   [http://localhost:3000/example?place=Paris&destType=House](http://localhost:3000/example?place=Paris&destType=House)
    
-   [http://localhost:3000/example?place=Amsterdam&destType=Hotel](http://localhost:3000/example?place=Amsterdam&destType=Hotel)
    

Compruebe la consola para ver los valores de la cadena de consulta registrados.

**[⬆ Volver a contenido](#contenido)**