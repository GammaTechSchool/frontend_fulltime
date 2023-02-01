### Contenido   
- [Intro](#react--intro-to-react) 
	- [Frameworks](#frameworks-y-code-libraries)
	- [Introducción a React](#introducción-a-react)
    - [¿Qué es React?](#¿qué-es-react)
	- [Añadir React a una Website](#añadir-react-a-un-sitio-web)
	- [React App Básica](#aplicación-react-básica)
	- [Creando un Componente React](#creando-un-componente-react)
- [Crear React App, JSX and React elements](#create-react-app-jsx-y-react-elements)
	- [React Setup de Proyecto](#react-setup-de-proyecto)
	- [Crear una nueva app](#crear-una-nueva-app)
	- [Estructura de carpetas](#escructura-de-carpetas)
	- [Renderizando la React App en el DOM](#renderizando-la-react-app-en-el-dom)
	- [JSX and elements](#jsx-y-elements)
- [Components & Props](#components-y-props)
	- [Function and Class Components](#function-y-class-components)
	- [Know how the Component tree works](#introducción---saber-cómo-funciona-el-árbol-de-componentes)
	- [Composing components `props.children`](#componiendo-components---propschildren)


# React | Intro to React

## Introducción

En el desarrollo web actual, existen muchas formas de crear interfaces de usuario. Estas pueden ser simples sitios web estáticos, [Aplicaciones Multipágina](https://lvivity.com/single-page-app-vs-multi-page-app#:~:text=A%20Multi%2Dpage%20Application%20is,page%20displayed%20in%20the%20browser.) (renderizado del lado del servidor), [Aplicaciones Web Progresivas (PWA)](https://www.freecodecamp.org/news/what-are-progressive-web-apps/#whatisaprogressivewebapp), [Aplicaciones de una sola página](https://developer.mozilla.org/en-US/docs/Glossary/SPA), etc.

La forma más sencilla de crear una aplicación front-end es utilizando HTML, CSS y JavaScript. Esta es la forma más pura de hacer desarrollo web. No requiere el uso de herramientas, librerías o frameworks.

Sin embargo, este enfoque no se adapta muy bien a la hora de crear grandes aplicaciones web.

A medida que las aplicaciones crecen, tienden a ser difíciles de mantener y escalar. Piensa en una plataforma web como Facebook, Airbnb o Instagram. ¿Cuántos archivos HTML, CSS y JS necesitamos para crear una aplicación de este tipo? La respuesta es miles de archivos.

Dato curioso: El frontend de **Facebook** funciona con más de 60 millones de líneas de **código**. Ya te haces una idea.

A medida que una aplicación crece, puede empezar a encontrar problemas de arquitectura tales como:

- el código y los archivos son muy difíciles de organizar (demasiado código),
- resulta difícil interconectar o reutilizar la lógica y el código entre archivos y funciones,
- Es difícil hacer cumplir patrones de diseño y estructura específicos.

Cuando suceden estas cosas, un framework puede venir a ayudar.

## Frameworks y Code Libraries

**Un Framework es:**

> Un entorno de software universal y reutilizable utilizado para facilitar el desarrollo de aplicaciones, productos y soluciones de software.

Un framework sirve como un entorno de desarrollo y un conjunto de herramientas y comúnmente incluye:

- Programas de apoyo,
- Compiladores/transpiladores,
- Bibliotecas de código (también llamadas paquetes),
- Conjuntos de herramientas,
- Estructura predefinida de la aplicación (estructura de carpetas/archivos y configuración).
- Conjunto impuesto de reglas y principios de diseño bien probados que deben seguirse.

**Un framework JavaScript es** una colección de bibliotecas de código JavaScript y herramientas utilizadas para desarrollar aplicaciones JavaScript.

Un _Framework_ te ayuda a construir aplicaciones más rápido resolviendo problemas comunes de desarrollo. Puede que conozcas otros frameworks, como [Express](https://expressjs.com/). En este módulo, utilizaremos React frontend framework para crear aplicaciones del lado del cliente.

### Front-end Frameworks

Un _front-end framework_ se compone de herramientas, bibliotecas JavaScript y paquetes. Los frameworks front-end ayudan a los desarrolladores a crear y escalar aplicaciones front-end de forma más fácil y rápida.

**Una biblioteca de código es:**

> Una colección de objetos, funciones y métodos que pueden ser reutilizados y compartidos entre múltiples aplicaciones. Una biblioteca realiza operaciones específicas y bien definidas.
> 
> - [Kolev (2017, 31 de julio). _Los pros y los contras de usar un framework](https://jaxenter.com/pros-cons-using-framework-135901.html)

En otras palabras, las **bibliotecas de código** son colecciones de código listo para usar que se utilizan para acelerar la creación de programas.

En lo que respecta a React, todavía hay muchas opiniones divididas sobre la pregunta: "¿React es una _biblioteca_ o es un _marco_?". React toma lo mejor de ambos, y no es fácil trazar la línea y decidirse a favor de uno u otro.

**[⬆](#contenido)**

## Introducción a React

### **¿Qué es React?**

React es una **biblioteca JavaScript front-end** utilizada para crear aplicaciones front-end que se ejecutan en el navegador. Fue creada por [Jordan Walke](https://www.reactiflux.com/transcripts/jordan-walke/), un ingeniero de software que trabaja para Facebook. React se desplegó por primera vez en el newsfeed de [Facebook](https://facebook.com/) en 2011 y en [Instagram.com](https://instagram.com/) en 2012.

React permite a los desarrolladores crear aplicaciones web robustas que manejan cambios dinámicos en los datos sin recargar la página. Además de aplicaciones web, también podemos utilizar React para desarrollar aplicaciones móviles Android e iOS. Esto se hace a través del framework multiplataforma llamado React Native.

### Ventajas de React

- **Desarrollo basado en componentes** - Creamos aplicaciones React usando componentes. Los componentes son pequeñas piezas reutilizables de interfaz de usuario. Esto nos permite construir aplicaciones complejas.
    
- **Separación de intereses** - React permite un diseño limpio y modular de las aplicaciones. Los desarrolladores pueden trabajar en diferentes partes de la aplicación, en un componente específico. De esta forma, no interfieren con el trabajo de otros ni rompen el código existente.
    
- **Velocidad** - React nos permite mantener una estructura clara del proyecto. Una estructura clara acelera el desarrollo.
    
- **Refuerza la estructura** - React refuerza ciertos patrones de diseño y estructura del proyecto. Si todos los desarrolladores del equipo siguen las mismas prácticas, la colaboración mejora.
    
**[⬆](#contenido)**

### Características de React

Echemos un vistazo más de cerca a algunas características esenciales de React:

- **Basado en componentes** - Los componentes son los bloques de construcción de las aplicaciones React. Podemos componer componentes React para hacer UIs complejas. Además, cada componente puede tener estado encapsulado.
    
- **JSX** - [JSX](https://reactjs.org/docs/introducing-jsx.html) es una extensión de sintaxis JavaScript utilizada para escribir HTML y JavaScript juntos. En lugar de separar JavaScript y HTML en archivos diferentes, React utiliza JSX para combinar HTML y JS juntos. JSX acelera y simplifica la creación de aplicaciones y componentes React. No te preocupes, en los próximos pasos profundizaremos en este tema. 
    
- Aprende una vez, escribe donde quieras** - React puede ser usado para pre-renderizar páginas web en el servidor con Node. Además de aplicaciones web, podemos usar React para crear aplicaciones móviles con [React Native](https://reactnative.dev/).
    

Aunque JSX es la forma recomendada para crear aplicaciones React, no es la única. También podemos crear aplicaciones React usando JavaScript.

## Añadir React a un sitio web

Mientras que React es comúnmente utilizado para la creación de aplicaciones de una sola página (más sobre esto más adelante) y con una cadena de herramientas de desarrollo, esta no es la única forma en que se puede utilizar. React se puede añadir a una página web existente con sólo unas pocas líneas de código, sin necesidad de utilizar una cadena de herramientas. He aquí un ejemplo:

```jsx
<!-- index.html -->

<!DOCTYPE html>
<html>
  <head>
    <title>Add React to a Website</title>
    <meta charset="UTF-8" />

    <link rel="stylesheet" href="./src/styles.css" />
    
    <!-- Load Babel - used to parse JSX -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <!-- React's core library-->
    <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <!-- ReactDOM library renders the content created with React to the DOM. -->
    <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    
  </head>

  <body>
    <div id="root"></div>

    <script type="text/babel">
      ReactDOM.render(
        <div>
          <h1>Hello React!</h1>
          <p> React is a front-end JavaScript library </p>
        </div>,
        document.getElementById('root')
      )
    </script>
    
  </body>
</html>

```

Para añadir React a la página HTML como en el ejemplo anterior, tenemos que hacer lo siguiente:

- Crear un DOM container en la página HTML `<div id="root"></div>`.
    
- Añadir Scripts de React.
    
- Añadir Babel (para poder escribir en JSX, ya viene incluido).
    

La configuración anterior es todo lo que se necesita. El contenido JSX que se pasa al método `ReactDOM.render()` se renderizará en el DOM en el div _root_ especificado: `document.getElementById('root')`.

En el ejemplo anterior, hemos renderizado una cantidad bastante pequeña de contenido utilizando React. Sin embargo, podríamos renderizar tanto contenido como fuera necesario. Actualicemos la página `index.html` y añadamos más contenido:

```jsx
<!-- index.html -->
 
<!DOCTYPE html>
<html>
  <head>
    <title>Add React to a Website</title>
    <meta charset="UTF-8" />
    <link rel="stylesheet" href="./src/styles.css" />
    <!-- React's core library-->
    <script crossorigin src="https://unpkg.com/react@17/umd/react.development.js"></script>
    <!-- ReactDOM library renders the content created with React to the DOM. -->
    <script crossorigin src="https://unpkg.com/react-dom@17/umd/react-dom.development.js"></script>
    <!-- Load Babel - used to parse JSX -->
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
  </head>
 
  <body>
    <div id="root"></div>
 
    <script type="text/babel">
      ReactDOM.render(
      
        <div>
          
          <nav>
            <img id="nav-img" src="https://bit.ly/3AwQRV1" />
            <p>Hello React</p>
          </nav>
 
          <div>
            <h2>REACT INTRODUCTION</h2>
          </div>
 
          <a href="https://reactjs.org">
            <button className="btn">BUTTON</button>
          </a>
 
          <div id="gallery">
            <h2>GALLERY</h2>
            <img src="https://bit.ly/3iMeumb" />
            <img src="https://bit.ly/3iLPn32" />
            <img src="https://bit.ly/3BrDAhE" />
            <img src="https://bit.ly/3lsRQkz" />
          </div>
        </div>,
      
        document.getElementById('root')
      )
    </script>
  </body>
</html>
```
**[⬆](#contenido)**

## Aplicación React Básica

Como has visto, añadir React a una página web es bastante sencillo. Ahora bien, el planteamiento de configurarlo todo por tu cuenta no es muy común. Cuando creamos aplicaciones con React, normalmente usamos una cadena de herramientas React que proporciona una estructura de proyecto y una configuración predefinidas.

Empecemos. Para mantenerlo simple por el momento, abriremos una aplicación React existente usando la plataforma [CodeSandbox](https://codesandbox.io/).

Utilizaremos el siguiente ejemplo de _CodeSandbox_ - [React introduction](https://codesandbox.io/s/m3-d1-react-introduction-ielbx?file=/src/App.js):

#### Estructura de la aplicación

La aplicación React anterior es una simple página de destino que contiene varios componentes.

La app utiliza una estructura y configuración diferente a la que utilizamos en el ejemplo anterior. Fue creada usando una herramienta llamada _Create React App_ (más sobre esto más adelante). Esta estructura de app nos permite dividir nuestro código React en componentes.

#### Basado en componentes

Ahora echemos un vistazo al archivo `App.js` .`App.js` es un componente React. Un componente React contiene UI, lógica y datos, todo en un mismo lugar. Notarás en el ejemplo que `App.js` contiene un código que es una mezcla de JavaScript y HTML, ¡todo en el mismo archivo!

**Te estarás preguntando ¿cómo es eso posible?** Bueno, es posible gracias a JSX. JSX nos permite poner _HTML_, _lógica JavaScript_, y _datos_ juntos en el mismo archivo. Cubriremos JSX en detalle en una lección posterior.

El desarrollo basado en componentes aporta los siguientes beneficios:

- El código es reutilizable.
- Podemos duplicar rápidamente los Componentes y moverlos.
- Para actualizar una parte de la aplicación, actualizamos un solo componente sin tocar el resto de la aplicación.

Function App es el componente inicial, siempre creado en primer lugar en una aplicación React, y sirve como padre para todos los demás contenidos y componentes React.

:::

Llamamos `App` a un **componente raíz**, ya que representa la raíz de la aplicación React renderizada en el DOM.
:::

Para entender mejor la estructura de la aplicación anterior y sus componentes, echa un vistazo a la siguiente imagen:

![img](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-intro/react-intro-example.png)

Como puedes ver, `App.js` está mostrando otros componentes `Navbar`, `Headline`, `Button`, `Gallery`, etc.

Con sólo mirar el código en `App.js`, es fácil entender la estructura de la página. Cada parte de la página está representada por un componente. Bonito y ordenado, ¿verdad?

Te estarás preguntando, ¿cómo creamos un componente? Bueno, ¡eso es lo que haremos a continuación!

**[⬆](#contenido)**

## Creando un componente React

Ya has visto cómo los componentes facilitan la organización del código en una aplicación. Ahora probablemente estés ansioso por crear tu primer componente. Así que vamos a crear un componente React.

Continuaremos trabajando en el ejemplo anterior de _CodeSandbox_ - [Introducción a React](https://codesandbox.io/s/m3-d1-react-introduction-ielbx?file=/src/App.js). Trabajaremos sobre el archivo `src/components/MyButton.js`. Si abrimos el archivo, encontraremos el siguiente código:

```jsx
// src/components/MyButton.js

function MyButton() {
  return ( /* HTML & JSX CONTENT */ );
}

export default MyButton;
```
Ahora la función anterior `MyButton` es un componente. En pocas palabras, un componente es una función que devuelve contenido JSX. Lo único que tenemos que hacer aquí es añadir el contenido que queremos mostrar.

Tómate un momento y revisa los otros componentes dentro de la carpeta `/src/components`. Echa un vistazo a los componentes `Headline.js` y `Button.js`. Como puedes ver, son muy similares. Cada componente es una función que devuelve algún contenido JSX.

Un componente React es sólo una función que devuelve contenido JSX u otros componentes.

Así que, para hacer que el componente `MyButton` renderice algún contenido, necesitamos _devolver_ el contenido HTML o JSX de la función.

Actualiza el archivo `MyButton.js` y añade el siguiente contenido en el paréntesis `return`:

```jsx
// src/components/MyButton.js

<a href="https://www.gammatech.school/">
  <button className="btn yellow">MY BUTTON</button>
</a>
```
Después de actualizar el archivo, su código debería tener este aspecto:
```jsx
// src/components/MyButton.js

function MyButton() {
  return (
    <a href="https://www.gammatech.school/">
      <button className="btn yellow">REACT DOCS</button>
    </a>
  );
}

// To make the component available, we have to export it
export default MyButton;

```

**La práctica hace al maestro.** Para aplicar lo que acabas de aprender, deberías intentar crear un componente desde cero. Borra el código existente de `MyButton.js` y vuelve a crear el componente, esta vez desde cero.

### Exportar un componente

Como habrá notado, hay una sentencia **`export default`** al final del fichero. Necesitamos esta sentencia para que el componente esté disponible para ser `importado` desde otros ficheros. Esto significa que debe incluir la sentencia `export default` en cada componente. De lo contrario, el componente no será accesible para la importación, y React lanzará un error.

React soporta la última sintaxis de JavaScript y utiliza las sentencias `import` y `export` para importar y exportar código desde archivos. Esta sintaxis también se conoce como [ES modules](https://exploringjs.com/es6/ch_modules.html).

La modules statement de ES:


```js  
export default ComponentName;         
```

Es equivalente a la de Node:

```js
module.exports = ComponentName;         
```

En React, utilizamos la declaración import y export de los módulos ES para importar y exportar componentes.

### Importar y utilizar un componente

Para empezar a usar el componente `MyButton`, necesitamos `importarlo` al componente donde queremos mostrarlo.

Para ello, abre el archivo `App.js` y añade la siguiente sentencia `import` al principio del archivo:

```jsx 
// App.js  
import MyButton from './components/MyButton';        
```
Una vez importado el componente, el siguiente paso es renderizarlo dentro de la `App`. Para renderizar el componente añádelo dentro de la `return` como una etiqueta, poniendo los corchetes angulares `< >` alrededor del nombre del componente como: `<MiBotón />`. Actualiza el componente `App` de la siguiente manera:

```jsx
// App.js

function App() {
  return (
    <div className="App">
      <Navbar />
      <Headline />

      <Button />
      <Button />      

      <MyButton />

      <Gallery />
    </div>
  );
}

```
**[⬆ Volver a contenido](#contenido)**

================================================================================

# Create React App, JSX y React elements

## Introducción

React es una librería front-end utilizada para la construcción de [interfaces de usuario](https://en.wikipedia.org/wiki/User_interfaces) o componentes UI. React nos proporciona la interfaz de programación para organizar nuestro código en componentes. Gracias a JSX podemos poner el marcado, la lógica y los datos juntos en el mismo archivo, llamado componente. En esta lección exploraremos la sintaxis de JSX y te daremos la oportunidad de practicarla creando componentes React.

Antes de sumergirnos en JSX primero necesitaremos crear una aplicación React. Hay varias formas de crear un nuevo proyecto React y cada una requiere una cierta configuración básica. Primero, tienes que configurar la estructura de archivos e instalar los paquetes de soporte. En segundo lugar, debes configurar el proyecto para que todas estas herramientas funcionen juntas. En esta lección, veremos cómo usar el generador _Create React App_ para crear un nuevo proyecto React.

**[⬆](#contenido)**

## React setup de proyecto

Como React es sólo una librería depende de otras herramientas que proporcionan un entorno de desarrollo.

Para configurar un proyecto React y el entorno de desarrollo _desde cero_ debes instalar y configurar lo siguiente:

-   **Supporting tools:**
    
    -   Un **package manager**, como [Yarn](https://yarnpkg.com/) o [npm](https://www.npmjs.com/).
    -   Un **compiler**, como [Babel](https://babeljs.io/) - usado para convertir JSX a JavaScript.
    -   Un **bundler**, como [webpack](https://webpack.js.org/) o [Parcel](https://parceljs.org/). Los agrupadores proporcionan un servidor de desarrollo y recarga en vivo durante el desarrollo. También agrupan y minifican el código.
-   **React Core paquetes:**
    
    -   [React](https://www.npmjs.com/package/react) - la biblioteca principal de React que nos permite trabajar con JSX,
    -   [ReactDOM](https://www.npmjs.com/package/react-dom) - para renderizar/visualizar la aplicación React en el DOM.

Pero no tenemos que preocuparnos de configurar todo esto desde cero. Los desarrolladores de Facebook han creado una excelente herramienta para ayudarnos a configurar nuestro proyecto react. Esto significa que no tenemos que pasar por la tediosa instalación y configuración.

**[Create React App](https://github.com/facebook/create-react-app) es una herramienta que te ayuda a crear aplicaciones React**. Te ahorra tiempo de instalación y configuración. Proporciona una configuración de aplicaciones lista para usar: paquetes, configuración y estructura de carpetas y archivos. Create React App, o CRA para abreviar, te permite empezar rápidamente y configurar fácilmente un proyecto React que siga las mejores prácticas.

Gracias a `create-react-app`, no tenemos que hacer ninguna configuración manual de herramientas como webpack y babel. Ya están preconfiguradas.

Simplemente ejecuta un comando, y `create-react-app` configura el proyecto React y las herramientas necesarias:

```
$ npx create-react-app name-of-your-app         
```

Gracias a `npx`, no es necesario `npm install` el paquete `create-react-app`, la última versión será descargada y ejecutada.

:::

Sin embargo, si has instalado `create-react-app` (localmente en tu `devDependencies` o incluso globalmente), `npx` utilizará esta versión.

Por lo tanto, si has instalado `create-react-app` globalmente, es posible que desees

```
$ npm uninstall -g create-react-app   
```

para garantizar que npx utilice siempre la última versión.

**Create React App se divide en 2 paquetes**:

-   **`create-react-app`** que es una utilidad global de línea de comandos que se utiliza para crear nuevos proyectos,
-   **`react-scripts`** que es una dependencia de desarrollo en los proyectos generados.

## Crear una nueva app

Vamos a crear una nueva aplicación React:

```
$ npx create-react-app my-first-app         
```

El comando anterior creará un directorio llamado `my-first-app`. Una vez que el script se haya ejecutado, puedes abrir la carpeta del proyecto:

```
$ cd my-first-app  
$ code .         
```

**Nota**: Otras formas de ejecutar create-react-app son las siguientes:

-   [npm](https://github.com/facebook/create-react-app#npm): `npm init react-app my-first-app`
-   [yarn](https://github.com/facebook/create-react-app#yarn): `yarn create react-app my-first-app`

### Scripts integrados

Dentro del proyecto recién creado, puede ejecutar algunos comandos incorporados:

#### `npm start` o `yarn start`

Esto ejecutará la aplicación en modo de desarrollo. Después de ejecutarlo, tu aplicación se iniciará en [http://localhost:3000](http://localhost:3000/).

**La mejor parte**La página se recargará automáticamente si realizas cambios en el código. Verás los errores de compilación y las advertencias de lint en la consola. No es necesaria la configuración manual de `Webpack`.

#### `npm test` o `yarn test`

Inicia el ejecutor de pruebas. `create-react-app` tiene ahora herramientas integradas para empezar a probar tu aplicación mientras la estás desarrollando, y para ello, por defecto, puedes usar [Jest](https://jestjs.io/docs/en/tutorial-react). Esta funcionalidad está fuera del alcance de nuestro curso, pero siéntete libre de [leer más sobre testing aquí](https://create-react-app.dev/docs/running-tests/).

#### `npm run build` o `yarn build`

Compila la aplicación para producción en la carpeta de compilación. Agrupa correctamente React en modo de producción, lo que significa que crea un montón de archivos estáticos y optimiza la compilación para obtener el mejor rendimiento. Después de ejecutar correctamente este comando, tu aplicación estará lista para ser desplegada.

**[`create-react-app`](https://github.com/facebook/create-react-app)** es un proyecto de código abierto en el que colaboran miles de personas con el equipo central. Quizá tú puedas ser uno de ellos.

En este momento, has creado tu primera aplicación React usando `create-react-app`. Actualmente, esta plantilla sólo tiene un componente, el componente `App`. Hemos mencionado brevemente `JSX` antes, pero vamos a volver a él una vez más, y luego, vamos a aprender a trabajar con más de un componente en nuestra aplicación.

### Ejecutar la React App

To run your app use the previously mentioned command:

```
   $ npm start        
```

Como primer paso, vamos a sustituir el contenido generado por el _Create React App_ por el nuestro. Abra el componente `App.js` y elimine el contenido HTML anidado, dejando sólo el elemento `<div className="App"> </div>`.

Después de eliminar el contenido anidado tu `App.js` debería tener este aspecto:

```jsx
// App.js

import logo from './logo.svg';
import './App.css';

function App() {
  return (
    <div className="App">
      {/*  We removed all of the content generated by Create React App */}
    </div>
  );
}

export default App;

```

Podemos empezar ahora a añadir nuestro contenido y componentes:

```jsx
// App.js

import './App.css';
import Header from './components/Header';

function App() {
  return (
    <div className="App">
      
      <h1>Hi YOUR_NAME!</h1>
      
    </div>
  );
}

export default App;

```

**[⬆](#contenido)**

### Escructura de Carpetas

Dentro del directorio, el CRA (_Create React App_) generará la estructura inicial del proyecto e instalará todas las dependencias necesarias:

```
 my-first-app
├── node_modules
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
├── src
│   ├── App.css
│   ├── App.js
│   ├── App.test.js
│   ├── index.css
│   ├── index.js
│   ├── logo.svg
│   ├── serviceWorker.js
│   └── setupTests.js
├── README.md
├── package.json
└── yarn.lock

```

Como puedes ver, no hay configuración ni complicada estructura de carpetas, sólo los archivos que necesitas para construir tu aplicación.

#### Carpeta `public

La carpeta **`public`** contiene archivos que serán leídos por tu navegador mientras desarrollas la aplicación; el más importante de estos archivos es `index.html`.

- **`public/index.html`** es **el único archivo .html para toda la aplicación React**. Por esta razón, decimos que React es una aplicación de una sola página.
    
    En lugar de tener muchas páginas HTML, todo el contenido de la aplicación es gestionado y actualizado dinámicamente por JavaScript. La aplicación y todo su contenido se muestran en esta única página HTML.
    
#### Carpeta`src`

La mayor parte del trabajo de desarrollo de nuestro lado como desarrolladores estará ocurriendo en la carpeta **`src`**.

- El archivo ``src/index.js`` es donde se realiza la principal llamada a _render_ gracias al método _`ReactDOM.render()`_. El método `ReactDOM.render()` inyecta la aplicación React en el `<div id="root">` para que la app pueda ser renderizada en el navegador.
    
- `src/App.js` es un componente React llamado "App". Este componente será el **componente raíz** de todos los demás componentes.
    
- `src/index.css` contiene algunos estilos básicos para nuestra aplicación.
    
- El archivo `src/App.css` almacena los estilos específicos del componente _App_.
    
- El archivo `src/App.test.js` es el primer conjunto de pruebas que podemos ejecutar con el componente App de ejemplo con el que empezamos.
    
- El archivo `package.json` lista todas las dependencias y scripts necesarios para ejecutar correctamente la aplicación React.
    
- La carpeta `node_modules` se genera automáticamente y contiene todas las dependencias instaladas.
    
- El archivo `yarn.lock` o `package-lock.json` (dependiendo del gestor de paquetes) tendrá la lista bloqueada de todas las dependencias instaladas de nuestra app.

Aunque ya lo hemos mencionado antes, merece la pena repetirlo:

-   **`public/index.html`** es **el único archivo `.html` para toda la React app**.
    
    La app React se muestra en esta página HTML, más concretamente en el `<div id="root"></div>`. Todo el contenido de la aplicación se gestiona dinámicamente mediante JavaScript y se muestra en esta página HTML.
    
-   **El archivo ``src/index.js`** se considera **el punto de entrada por defecto a cualquier aplicación React**. Este archivo contiene el método `ReactDOM.render()` que _inyecta_ la aplicación React en el `<div id="root">` para que la app pueda ser renderizada en el navegador.

=======

## Renderizando la React App en el DOM

As mentioned earlier, React is used to create Single-Page Applications. This means that React apps always have only one HTML file, `index.html`. This file serves as a container for loading the JavaScript code that the React app is made of and displaying it in the browser.

#### Renderizado

El archivo `index.html` contiene sólo un elemento en el cuerpo, el `<div id="root">`.

El `<div id="root">` es un elemento contenedor en el que se renderiza toda la aplicación React. La aplicación React es inyectada (añadida) al DOM gracias al método `ReactDOM.render()`.

Te preguntarás, si sólo hay un elemento `<div id="root">` ¿cómo acabamos viendo todo el resto del contenido del DOM?

La aplicación React crea dinámicamente elementos DOM a partir de nuestro código JSX.

Vamos a mostrar esto a través de un ejemplo. En el `index.js` encontrarás el método `ReactDOM.render()`. Aquí puedes ver que el componente `App` está siendo renderizado al DOM con el método `ReactDOM.render()`.

###### index.js


```jsx
// index.js
// ... imports stay unchanged

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

```

El método `ReactDOM.render()` tiene la siguiente sintaxis:

```
ReactDOM.render(whatToAppend, whereToAppend);         
```

-   `whatToAppend` representa el contenido JSX React que queremos inyectar (añadir) al DOM.
    
-   `whereToAppend` representa el elemento DOM al que queremos añadir el contenido JSX React.
    
Si eliminas la parte `whatToAppend` y la sustituyes por `null` notarás que la página en el navegador se queda en blanco. Esto se debe a que nada se muestra en el `<div id="root">` en el DOM:


```js
// index.js
// ... imports stay unchanged

ReactDOM.render(null, document.getElementById('root'));


```

Así, para mostrar cualquier contenido JSX React en la página, tenemos que renderizarlo al DOM usando el método `ReactDOM.render()`. Si añades el siguiente contenido JSX lo verás aparecer en la página:

```jsx
// index.js
// ... imports stay unchanged

ReactDOM.render(
  <div>
    <h1> Hello sir! </h1>
    <p> You are rocking it! </p>
  </div>,
  document.getElementById('root')
);

```


#### Rendering the Root Component

Llamamos `App` a un **componente raíz** ya que es el primer componente React añadido al DOM. Cualquier componente, o cualquier código JSX, que añadamos al `App.js` se añadirá automáticamente al DOM a través del `App.js`.

Vuelve atrás y actualiza el `index.js` al estado anterior:

```jsx
// index.js
// ... imports stay unchanged

ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);

```


## JSX y elements

![image](https://user-images.githubusercontent.com/23629340/42755262-bc6eac9a-88f7-11e8-9a6c-e592ce73e6ab.png)

**JSX** **is a syntax extension to JavaScript**. JSX may remind you of a template language, but it comes with the full power of JavaScript.

**Los navegadores no entienden JSX**. El código JSX se compila en código comprensible para el navegador gracias a Babel. Este proceso se realiza automáticamente. Todos los componentes React y cualquier código JSX se convierten a JavaScript ES5.

El código JSX se compila en JavaScript comprensible para el navegador gracias a Babel. No es necesario instalarlo o configurarlo manualmente, viene junto con _Create React App_. Está preconfigurado y oculto para que puedas centrarte en el código.

Vamos a abrir la aplicación. Eliminaremos el código actualmente presente dentro de la `función App(){}` y dejaremos sólo la siguiente estructura:

```jsx
// App.js

import React from 'react';
import logo from './logo.svg';
import './App.css';

function App() {
  return <div className="App"></div>;
}

export default App;

```

#### JSX Under the Hood

Echemos un vistazo a esta declaración de variable:

```jsx
const element = <h1>Hello world!</h1>;         
```

El código anterior representa un código JSX muy simple. Utilice este fragmento de código y péguelo en [https://babeljs.io/repl](https://babeljs.io/repl) para ver cómo Babel lo convierte en JavaScript. Obtendrá el siguiente código JavaScript:

```js
var element = React.createElement('h1', null, 'Hello, world!');        
```

En pocas palabras, los elementos que creas usando JSX son convertidos por Babel en JavaScript plano. React es una librería JavaScript y en realidad utiliza el método `React.createElement()` para crear los elementos DOM.

![image](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-intro/jsx-to-js-conversion.png)

Add the following code to the _App.js_:

```jsx
// App.js
// ... imports stay unchanged

const heading = <h1> React is cool! </h1>;

function App() {
  return <div className="App">{heading}</div>;
}

export default App;

```

Hemos añadido nuestro elemento JSX super simple (`heading`) en el `App.js` y, dado que el componente _App_ ya está renderizado en el DOM, el `heading` se muestra dentro del componente.

Si aún no has ejecutado tu aplicación, puedes hacerlo ahora y en el `localhost:3000`, este debería ser el resultado esperado.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_afccfa2f8ee61e6f78ed97ddd3441a6a.png)

### Embedding expressions in JSX

**Dos cosas súper importantes a tener en cuenta cuando se trabaja con JSX**:

1.  Puede incrustar cualquier código JavaScript válido en el JSX utilizando las llaves simples: **`{}`**.
2.  Puedes utilizar tantos elementos DOM como desees dentro del código JSX en los componentes React. Sin embargo, todos los elementos de un componente deben envolverse con un único elemento HTML envolvente, el que te parezca más adecuado. Esto significa que **los componentes React siempre deben devolver contenido encerrado en un único elemento HTML**.

Ejemplo: **Wrong** - el componente devuelve dos elementos HTML adyacentes `h1` y `h3`.

```jsx
// Wrong!
function MyComponent() {
  return (
    <h1>Hello sir!</h1>
    <h3>Welcome To the World of React</h3>
  )
}

```

Ejemplo: **Correcto** - ¡el componente devuelve el contenido envuelto en una única etiqueta `div`!

```jsx
// Correct!
function MyComponent() {
  return (
    <div>
      <h1>Hello sir!</h1>
      <h3>Welcome To the World of React</h3>
    </div>
  );
}

```


Toda la potencia de JSX viene con la capacidad de incrustar cualquier expresión válida de JavaScript en el elemento JSX.

#### Ejemplo 1 - embed variables:

```jsx
// App.js
// ... imports stay unchanged

const heading = <h1> React is cool! </h1>;

const student = {
  firstName: 'ana',
  lastName: 'martinez'
};

function App() {
  return (
    <div className="App">
      {heading}

      <h3>
        Hi, {student.firstName} {student.lastName}!
      </h3>
    </div>
  );
}

```


#### Ejemplo 2 - embed functions (o methods):

```jsx
// App.js
// ... everything that we already added stays unchanged, except function App()

const { firstName, lastName } = student;

function App() {
  return (
    <div className="App">
      {heading}

      <h3>
        {/* You can turn this to {firstName} {lastName} */}
        Hi, {student.firstName} {student.lastName}!
      </h3>

      <h4>
        In uppercase: {firstName.toUpperCase()} {lastName.toUpperCase()}.
      </h4>
    </div>
  );
}

```

#### Example 3 - embed function execution:

```jsx
// App.js
// ... everything that we already added stays unchanged, except function App()

function capitalizeFirstLetter(str) {
  return str[0].toUpperCase() + str.slice(1);
}

function App() {
  return (
    <div className="App">
      {heading}

      <h3>
        {/* You can turn this to {firstName} {lastName} */}
        Hi, {student.firstName} {student.lastName}!
      </h3>

      <h4>
        In uppercase: {firstName.toUpperCase()} {lastName.toUpperCase()}.
      </h4>

      <h4>
        Capitalized:
        { capitalizeFirstLetter(firstName) } { capitalizeFirstLetter(lastName) }
      </h4>
    </div>
  );
}

```

#### Example 4: embed the attribute value

En JSX, también podemos incrustar los valores de los atributos:

```jsx
const theId = 'home';

const divElement = <div id={theId}>div with an id</div>;

```

En este punto, probablemente no veas el caso de uso, pero cuando se trata de estilizar en React, tendrás un montón de oportunidades para utilizar la sintaxis anterior.

#### Example 5 - embed static files: images

Para cargar una imagen local con HTML plano, tenemos que establecer el atributo `src` del `<img>` a la ruta local del archivo. Para cargar una imagen externa en HTML plano, establecemos la URL del archivo.

```jsx
<!-- dummy example -->
<img src="./assets/some-image.jpg" alt="some image" />
<img src="https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_129040de20781c45366fd2193fcbb5fd.png" alt="react is cool" />

```

En React, para cargar una imagen almacenada localmente en el proyecto, primero debemos **importar** el archivo:

```jsx
import logo from './assets/logo.png';

// ...

<img src={logo} alt="logo" />

```


Cuando se trata de utilizar imágenes alojadas en línea, el proceso sigue siendo el mismo que si utilizáramos HTML.

```jsx
<img src="https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_129040de20781c45366fd2193fcbb5fd.png" alt="react is cool" />  
```

### Self-closing tags

Cualquier elemento JSX puede escribirse como una etiqueta de cierre automático:

```jsx
<MyComponent />  
// or  
<MyComponent> </MyComponent>         
```

```jsx
<label />  
// or  
<label> </label>         
```

Además, las etiquetas HTML de cierre automático como `<br />`, `<hr />`, y `<img />` deben tener siempre un cierre `/` para ser JSX válido que se pueda transpilar.

```html
<br />         // Correct
<hr />         // Correct
<img src="" /> // Correct


<br>          // Wrong!
<hr>          // Wrong!
<img src="">  // Wrong!

```


### Attributes Names are camelCased

En React, en comparación con el HTML, **todos los atributos con el `-` en su nombre se convierten a su versión _camelCase_**. Ejemplo: `background-color` se convierte en `backgroundColor`.

Algunos de los atributos sin mayúsculas son renombrados a su equivalente en camelCase:

-   onchange —> onChange
-   onclick —> onClick
-   onsubmit —> onSubmit

En general **excepciones**: Porque son palabras reservadas en JavaScript, `class`y`for`se convierten:

-   `class` —> `className`
    
-   `for` —> `htmlFor`
    

Ejemplo

```jsx
<label htmlFor="username" className="control-label">
  Username
</label>

```


### Añadiendo comentarios en JSX

Hay dos reglas cuando se trata de comentar el código en JSX:

- cuando dentro de la parte HTML, los comentarios deben estar en `{/* algún comentario aquí */}`.
- cuando dentro de la parte JavaScript, es decir, entre las llaves donde podemos utilizar todo el poder de JavaScript, los comentarios son los mismos que en los archivos JS `// algún comentario aquí`.

```jsx
<div>
  {/* some comment here */}

  {friends.map(elem => {
    // some comment here
    return elem.name;
  })}
</div>

```
**[⬆ Volver a contenido](#contenido)**

================================================================================

# Components y Props

## Function y Class Components

> Los componentes permiten dividir la interfaz de usuario en piezas independientes y reutilizables, y pensar en cada pieza de forma aislada.
> 
> - [Components and Props -. (n.d.-a). ReactJS Documentation](https://reactjs.org/docs/components-and-props.html)

React te permite definir componentes como _funciones_ o _clases_. Aunque estos dos tipos de componentes difieren en sintaxis y usan diferentes mecanismos para manejar _state_ y _updates_ (más sobre esto más adelante) pueden combinarse y usarse juntos en aplicaciones React.

### Function vs. Class Components

Los componentes funcionales son el futuro de React. Sin embargo, una gran cantidad de aplicaciones React que se ejecutan hoy en día todavía tienen una gran parte de su código base React y componentes escritos como clases. Mientras que la industria se está moviendo constantemente hacia el uso exclusivo de componentes funcionales y _hooks_, los componentes de clase seguirán siendo compatibles con React en un futuro previsible.

> En Facebook, tenemos decenas de miles de componentes escritos como clases, y no tenemos absolutamente ningún plan para reescribirlos. En su lugar, estamos empezando a utilizar ganchos en el nuevo código junto con las clases.
> 
> – [Introducing Hooks, n.d., “Gradual Adoption Strategy” section. ReactJS Documentation](https://reactjs.org/docs/hooks-intro.html#gradual-adoption-strategy)

Así que el punto clave es que deberías usar componentes funcionales cuando crees tus aplicaciones React. Aún así, también deberías estar familiarizado con los fundamentos de los componentes de clase, ya que navegar y trabajar con las bases de código de React más antiguas puede ser parte de tu trabajo en el futuro.

### Componentes Funcionales

**Los componentes funcionales** son simplemente funciones JavaScript y te permiten _devolver/render_ contenido JSX al DOM. Creamos un componente funcional escribiendo una función JavaScript:

```jsx
function ExampleFuncA() {
  return (
    <div>
      <h2> ExampleFuncA - functional component </h2>
    </div>
  );
}

export default ExampleFuncA;

```

También podemos crear componentes funcionales utilizando la sintaxis de la función flecha:

```jsx
const ExampleFuncB = () => {
  return (
    <div>
      <h2> ExampleFuncB - functional (arrow) component </h2>
    </div>
  );
};

export default ExampleFuncB;
```

### Class Components

Creamos un componente de clase definiendo una `class` que extiende `React.Component`.

Al crear un componente `class` debemos importar React en el fichero.

Además, el componente `class` debe contener un método `render(){}`:

```jsx
import React from 'react';

class ExampleClassA extends React.Component {
  render() {
    return (
      <div>
        <h2> ExampleClassA - class component </h2>
      </div>
    );
  }
}

export default ExampleClassA;
```

También puedes ver la clase `React.Component` referenciada como clase `Component`. Si utilizamos esta sintaxis, debemos importar y desestructurar el componente desde el módulo `react`:

```jsx
import React, { Component } from 'react'; // <--

class ExampleClassB extends Component {
  render() {
    return (
      <div>
        <h2> ExampleClassB - class component </h2>
      </div>
    );
  }
}

export default ExampleClassB;

```

En el ejemplo anterior, creamos nuestros componentes de clase extendiendo React `Component`. Hacemos esto para que nuestra clase herede todas las propiedades y métodos útiles incorporados de un componente React. Los dos ejemplos anteriores son iguales, solo que en el segundo ejemplo, estamos usando un [named import](https://developer.mozilla.org/pt-PT/docs/Web/JavaScript/Reference/Statements/import).

¡Recuerda! Importar `React` de la librería `react` es **siempre** necesario en cada componente `class`. Los componentes de clase deben extender `React.Component` lo que requiere que importemos `React`.

### Crear componentes de clase and funcionales 

Vamos ahora a crear una nueva aplicación React para que podamos demostrar cómo escribir componentes y, más tarde, cómo utilizar props.

```   
$ npx create-react-app react-components-props-demo
$ cd react-components-props-demo 
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

Por ahora, seguiremos trabajando dentro del archivo `App.js`. Hemos mencionado brevemente que hay dos tipos principales de componentes en React, _class_ y _functional_. Empezaremos creando primero un componente _class_.

Los componentes de clase deben extender `React.Component` lo que requiere que importemos `React` de la librería `react`. El componente de clase también debe contener el método `render(){}`.

En la carpeta `./src/components` crea un nuevo archivo `Navbar.js`. Este será nuestro nuevo componente de clase `Navbar`:

```jsx
// ./src/components/Navbar.js

import React from 'react';

class Navbar extends React.Component {
  render() {
    return (
      <nav>
        <p>React - Components & props</p>
      </nav>
    );
  }
}

export default Navbar;
```


A continuación, importaremos el componente `Navbar` y lo mostraremos en `App.js`:


```jsx
// App.js
// ... previous imports stay unchanged

import Navbar from './src/components/Navbar';

function App() {
  return (
    <div className="App">
      <Navbar />
    </div>
  );
}
export default App;
```

Seguiremos practicando creando un componente _funcional_.

El componente funcional es, como su nombre indica, una función JavaScript.

En la carpeta `./src/components` crea otro archivo `Greeting.js`. Este será nuestro nuevo componente funcional `Greeting`:

```jsx
// ./src/components/Greeting.js

function Greeting() {
  const message = 'Hello Ana!';

  return (
    <div>
      <u>{message}</u>
    </div>
  );
}

export default Greeting;
```

Importa el nuevo componente y muéstralo actualizando tu `App.js` con el siguiente código:

```jsx
// App.js
// ... previous imports stay unchanged

import Greeting from './src/components/Greeting';

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting />
    </div>
  );
}
export default App;
```

Como puedes ver, `Greeting` es sólo una función, con una característica principal - devuelve `JSX` para poder renderizar el `message` en el DOM. Usamos `Greeting` en la función `App`, envolviéndolo como una etiqueta `<Greeting />`, que es como instanciamos componentes en React. Podemos reutilizar el componente `Greeting` varias veces. Actualicemos `App.js` para hacerlo:

```jsx
// App.js
// ... imports stay unchanged

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting />
      <hr />
      <Greeting />
      <hr />
      <Greeting />
    </div>
  );
}

export default App;
```


Como se ha visto, es bastante fácil reutilizar un componente. Sin embargo, como habrás notado, cada instancia del componente `Greeting` muestra exactamente el mismo contenido. En el siguiente paso, veremos cómo podemos reutilizar el componente y hacer que muestre contenido personalizado pasándole datos a través de `props`.

## Introducción - Saber cómo funciona el Árbol de Componentes

**Los componentes son el núcleo de las aplicaciones React.** Una aplicación React típica se compone de muchos componentes. La estructura de una aplicación React puede representarse como un **árbol de componentes.** El árbol comienza con un **componente raíz** (normalmente llamado App) y tiene una cantidad infinita de componentes hijos anidados.

Para ilustrar esto, vamos a crear y mostrar un nuevo componente en nuestra aplicación existente. En la carpeta `src/components` crea un archivo `Button.js` y añádele el siguiente contenido:

```jsx
// ./src/components/Button.js

function Button() {
  return (
    <a href="https://reactjs.org">
      <button> Click here </button>
    </a>
  );
}

export default Button;
```

A continuación, importaremos y utilizaremos el nuevo componente `Button` para mostrar dos botones en la `Navbar` :

```jsx
// ./src/components/Navbar.js
// ... previous import stays unchanged

import Button from './Button';

class Navbar extends React.Component {
  render() {
    return (
      <nav>
        <p>React - Components & props</p>
        <Button />
        <Button />
      </nav>
    );
  }
}

export default Navbar;
```

Después de renderizar el componente, podemos representar nuestra aplicación en forma de un _árbol de componentes_ con el siguiente aspecto:

![](https://education-team-2020.s3.eu-west-1.amazonaws.com/web-dev/m3/react-intro/react-component-tree-1.png)

El modelo _árbol de componentes_ nos permite representar jerárquicamente la relación entre componentes. Como puede ver, es similar al árbol DOM. Por ejemplo, usando el modelo de árbol de componentes podemos ver que los componentes Navbar y Greeting están todos anidados directamente dentro del App.js.

Pensar en la estructura de una aplicación React de esta manera nos da una vista de pájaro de la aplicación. Esto es necesario para permitirnos visualizar el flujo de datos al pasar datos entre los componentes. Veremos cómo pasar datos entre los componentes mediante el uso de `props` en el siguiente paso.

## Props

Uno de los conceptos fundamentales a la hora de tratar con componentes React son los **props**. Las **props_ representan _los datos que el componente recibe del exterior_.

Conceptualmente, los componentes son como funciones de JavaScript. Aceptan entradas arbitrarias (llamadas `props`) y devuelven elementos React que describen lo que debería aparecer en la pantalla.

### Pasando y accediendo props

El término **props** significa _propiedades_. En JSX, cuando una prop se envía a un componente, se parece a un atributo HTML. Echemos un vistazo. En la función `App`, añade el siguiente trozo de código:

```jsx
// App.js
// ... imports stay unchanged

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting firstName="Harper" />
      <hr />
      <Greeting />
      <hr />
      <Greeting />
      <hr />
    </div>
  );
}
```


El atributo personalizado `firstName="Harper"` que hemos añadido al componente es una prop. El atributo `firstName` y su valor `"Harper"` estarán disponibles dentro del componente a través del objeto `props`.

Para acceder al objeto `props` primero tenemos que especificarlo como parámetro de la función componente:

```jsx
function Example(props) {
  return /* JSX content */;
}
```

Actualicemos el componente `Greeting` para ver esto en la práctica. Añade el parámetro `props` y _console.log_ en la consola:

```jsx
// ./src/components/Greeting.js
function Greeting(props) {
  const message = 'Hello Ana!';

  console.log(props);

  return (
    <div>
      <u>{message}</u>
    </div>
  );
}

export default Greeting;
```

La palabra clave `props` es un objeto. Contiene los valores que pasamos al componente como props, desde el exterior. En este caso, `props` tiene una propiedad `firstName` con el valor `"Harper"`. Abre la consola del navegador y comprueba la salida:

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_e40dc7cb3cbd15a16777b1588aa2b2e3.png)

Podemos acceder a la propiedad `firstName` y mostrarla en el componente. Actualizar el componente `Greeting` :

```jsx
// ./src/components/Greeting.js

function Greeting(props) {
  // const message = 'Hello Ana!';   <== REMOVE
  console.log(props);

  return (
    <div>
      <u>Hello {props.firstName}!</u>
    </div>
  );
}

export default Greeting;
```

Saber que podemos pasar cualquier dato a un componente usando _props_, abre muchas oportunidades para la reutilización de componentes. Vamos a actualizar los componentes `<Greeting>` y pasar un `firstName` props a cada uno:

```jsx
// App.js
// ... imports stay unchanged

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting firstName="Harper" />
      <hr />
      <Greeting firstName="Michelle" />
      <hr />
      <Greeting firstName="Andrea" />
      <hr />
    </div>
  );
}

// ...
```

Los props son _piezas de información que vienen de fuera del componente_. Otra forma de describirlos es que son _los datos que se pasan al componente_.

### Pasando multiples props

Puede pasar tantas _props_ como necesite a un componente. Además, el valor prop pasado puede ser de cualquier tipo de datos (_string_, _number_, _boolean_, _array_, _object_, _function_). Usaremos un nuevo componente `StudentCard` para ver cómo pasar props que tienen diferentes tipos de datos:

1.  Vamos a crear un nuevo fichero `./src/components/StudentCard.js` y el componente `StudentCard`:
```jsx
// ./src/components/StudentCard.js
import React from 'react';

function StudentCard(props) {
  return (
    <div className="StudentCard">
      <p>
        <b>Name:</b> NAME
      </p>
      <p>
        <b>Cohort:</b> CITY - COURSE
      </p>
      <p>
        <b>Current week: WEEK </b>
      </p>
      <br />
    </div>
  );
}

export default StudentCard;

```


2.  A continuación, importaremos el componente `StudentCard` y lo mostraremos dentro de `App.js`. Esta vez pasaremos múltiples props: `name` - _string_, `week` - _number_ e `info` - _object_:

```jsx
// App.js
// ... imports stay unchanged

import StudentCard from './components/StudentCard';

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting firstName="Harper" />
      <Greeting firstName="Michelle" />
      <Greeting firstName="Andrea" />

      <StudentCard name="Eva" week={7} info={{ city: 'BCN', course: 'WEB' }} />
      <StudentCard name="Mat" week={8} info={{ city: 'MIA', course: 'DATA' }} />
    </div>
  );
}

export default App;
```


3.  El componente `StudentCard` recibe los props `name`, `week` e `info` de `App`. Actualizaremos `StudentCard.js` para mostrarlos:

```jsx
// ./src/components/StudentCard.js
import React from 'react';

function StudentCard(props) {
  return (
    <div className="StudentCard">
      <p>
        <b>Name:</b> {props.name}
      </p>
      <p>
        <b>Cohort:</b> {props.info.city} - {props.info.course}
      </p>
      <p>
        <b>Current week: {props.week}</b>
      </p>
      <br />
    </div>
  );
}

export default StudentCard;
```

Fíjate en la sintaxis del objeto que estamos utilizando para acceder a los datos procedentes del objeto `info`: `props.info.city` y `props.info.course`.

#### `props` in the class component

Hemos visto que acceder al objeto `props` es bastante sencillo cuando se trata de componentes funcionales. Vamos a crear un nuevo componente `StudentList` como ejemplo de cómo utilizar `props` en componentes de clase:

```jsx
// ./src/components/Badge.js
import React from 'react';

class Badge extends React.Component {
  render() {
    return <span className="Badge"> {this.props.badgeText} </span>;
  }
}

export default Badge;

```

A continuación, importaremos el componente y lo mostraremos dentro de `App.js` y le pasaremos el prop `badgeText="important"`:

```jsx 
// App.js
// ... imports stay unchanged

import Badge from './components/Badge';

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting firstName="Harper" />
      <Greeting firstName="Michelle" />
      <Greeting firstName="Andrea" />

      <StudentCard name="Eva" week={7} info={{ city: 'BCN', course: 'WEB' }} />
      <StudentCard name="Mat" week={8} info={{ city: 'MIA', course: 'DATA' }} />

      <Badge badgeText="important" />
    </div>
  );
}

export default App;
```

Si estamos dentro de una clase, tenemos que utilizar la palabra clave `this` para acceder a los props. Por eso usamos `{this.props.badgeText}` dentro del componente de clase `Badge`.

## Componiendo components - `props.children`

Hasta ahora hemos visto que los componentes son en su mayoría etiquetas que se cierran solas, como `<Usuario />`.Sin embargo, también puedes escribir componentes como si fueran etiquetas normales:

```jsx
<CoolComponent> </CoolComponent>         
```

Esto nos permite utilizar un componente como **wrapper de otro u otros componentes**. Vamos a crear un nuevo componente `StudentList` para mostrar esto:

```jsx
// ./src/components/StudentList.js

function StudentList(props) {
  return (
    <div>
      <h2>Student List</h2>
      {props.children}
    </div>
  );
}

export default StudentList;
```

Al crear el componente de tal manera decimos: "_este componente será un componente "padre" o "envoltorio" para otros componentes_".

Para mostrar esto, vamos a envolver todos los componentes `StudentCard` con el componente `UserList`:

```jsx
// App.js
// ... previous imports stay unchanged

import StudentList from './components/StudentList';

function App() {
  return (
    <div className="App">
      <Navbar />
      <Greeting firstName="Harper" />
      <Greeting firstName="Michelle" />
      <Greeting firstName="Andrea" />
      <Badge badgeText="important" />

      <StudentList>
        <StudentCard name="Eva" week={7} info={{ city: 'BCN', course: 'WEB' }} />
        <StudentCard name="Mat" week={8} info={{ city: 'MIA', course: 'DATA' }} />
      </StudentList>
    </div>
  );
}
```

Como podemos ver, nada importante ha cambiado en la forma en que se muestra el contenido.

Tener la oportunidad de usar `props.children` nos permite componer componentes. Aprovecharemos mucho esta característica.

Hasta ahora, hemos cubierto **props** y ahora sabemos que las props nos permiten **pasar datos en el componente**. Explicado con términos industriales, podríamos decir que **las props permiten pasar datos por el árbol de componentes**.

Una cosa a tener en cuenta: **las props son inmutables**.

## ¿Cuándo usamos props?

### (1) Las Props son como argumentos de funciones

Puede utilizar props para hacer que sus componentes sean reutilizables. Los props pueden usarse para controlar cómo se muestra el componente. Pasando **diferentes props** a menudo resulta en que el componente **se vea o se comporte de manera diferente**.

En este sentido, los _props_ de un componente son como los argumentos de una función. Los argumentos controlan cómo se comporta una función, al igual que los props controlan cómo se muestra el componente.

Imagina que tuviéramos un **componente para mostrar el tiempo** de una ciudad en particular. En ese caso, la prop que enviaríamos sería probablemente el nombre de la ciudad. Usando ese nombre, probablemente accedería a los datos meteorológicos desde una API.

Renderizando el componente probablemente se vería así:

```jsx
// This code is just hypothetical
// ...
  render() {
    return <WeatherWidget city="Mexico City" />;
  }
// ...
```

El envío de una "ciudad" diferente debería producir información diferente.

![](https://s3-eu-west-1.amazonaws.com/ih-materials/uploads/upload_994ae09ba982413b0341b87a94fe6610.png)

### (2) Comparte información entre componentes

Por definición, los _props_ permiten **compartir datos** entre un componente _parent_ y un componente _child_. Compartir datos de esta manera es muy común. Es bastante común que una acción que ocurre en un componente **afecte a cómo debe comportarse otro** componente.

### (3) Componentes desde `npm`

Hay muchos componentes pre-hechos en el `npm`. A menudo, los componentes que obtienes del `npm` te permitirán configurarlos y personalizarlos mediante el uso de _props_. Veamos un ejemplo.

Primero, instalemos el paquete npm [`react-player`](https://www.npmjs.com/package/react-player).

```
$ npm install react-player         
```

Ahora vamos a importarlo dentro de `App.js` y utilizarlo como cualquier otro componente:

```jsx
// App.js
// ... previous imports stay unchanged

// import ReactPlayer from the npm package
import ReactPlayer from 'react-player';

function App() {
  return (
    <div className="App">
      {/* ... no changes here ... */}
      <hr />
      <ReactPlayer url="https://vimeo.com/channels/top/22439234" playing />
    </div>
  );
}

export default App;
```

Como se indica en la documentación, el uso básico sólo implica la `url` _prop_ - la dirección del vídeo que queremos mostrar. Funciona con muchos de los servicios de vídeo más populares, como YouTube y Vimeo. Aparte de `url`, el componente también tiene otros props sobre los que puedes leer en [la documentación del paquete](https://www.npmjs.com/package/react-player). También usamos la _prop_ `playing` - una prop booleana que controla la reproducción automática.

Además, si no te gusta el vídeo de YouTube más popular del día? ¡Tal vez dos nuevos props puedan ayudarte! El `controls` _prop_ añade controles al reproductor y el `volume` prop te permite controlar el volumen.

```jsx
// App.js
// ... previous imports stay unchanged

  render() {
    return (
      <div className="App">
      {/* ... no changes here ... */}

        <ReactPlayer url="https://vimeo.com/channels/top/22439234" />

        {/* see the new props! */}

        <ReactPlayer
          url="https://www.youtube.com/watch?v=kJQP7kiw5Fk"
          playing
          controls
          volume="0.5"
        />
      </div>
    );
  }
// ...
```

Con un componente como `ReactPlayer`, puedes ver cómo los props te permiten personalizar la forma en que el componente funciona para ti.

**[⬆ Volver a contenido](#contenido)**