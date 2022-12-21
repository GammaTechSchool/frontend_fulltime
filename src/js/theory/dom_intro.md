![](../../assets/Logo_Yellow.png)

# Accessing and modifying the DOM

## Qué es el DOM
El DOM (Documet Object Model) es la representación, en forma de **_nodos_** y **_objetos_** de un documento de HTML.
Cuando el navegador nos presenta una web (un documento HTML), además de la visualización de la misma, nos genera de manera automática un **_objeto_** con cada elemento de HTML que contenga la web. Este objeto está disponible en todo momento y podemos acceder a él usando JavaScript.
Dentro del DOM, cada elemento de HTML tiene su representación en forma de objeto, con propiedades que podemos leer y modificar, y métodos que podemos usar para interactuar con él.

## Cómo acceder al DOM
En JavaScript, siempre que tengamos nuestro archivo `.js` ligado a un archivo `.html`, podemos acceder al DOM a través del objeto `documet`. Este objeto cuenta con múltiples métodos para interactuar con él. 

### Acceso a los nodos del DOM
En el DOM, cada elemento o etiqueta HTML se llama **_nodo_**. Podemos acceder a ellos usando los métodos que incluye el objeto **_document_**. Estos métodos son:

- `getElementById(<<id>>)`: selecciona los elementos que tengan el `id` indicado. Devuelve un único elemento, pues las `id` son únicas.
- `getElementsByClassName(<<class>>)`: selecciona los elementos que tengan la clase indicada. Devuelve una **_colección_**  iterable, pues las clases son comunes a varios elementos.
- `getElementsByTagName(<<tag>>)`: selecciona los elementos que tengan la `tag` o etiqueta indicada. Devuelve una **_colección_** iterable, pues puede haber varios elementos con la misma etiqueta.
- `querySelector(<<selector>>)`: selecciona elementos usando selectores de CSS. Devuelve un único elemento, el primero que cumpla el selector.
- `querySelectorAll(<<selector>>)`: selecciona elementos usando selectores de CSS. Devuelve una **_colección_** iterable con todos los elementos que cumplan el selector.
```html
<body>
	<h1 id="title">Título</h1>
	<h2 id="subtitle">Subtítulo</h2>
	<p class="paragraph">Párrafo 1</p>
	<p class="paragraph">Párrafo 2</p>
	<p class="paragraph">Párrafo 3</p>
	<div>
		<img src="./assets/photo.jpg">
		<span class="inner-span">Span 1</span>
		<span class="inner-span">Span 2</span>
	</div>
</body>
```
```javascript
const title = document.getElementById("title");
console.log(title);     // <h1 id="title">Título</h1>

const subtitle = document.getElementByTagName("h2");
console.log(subtitle);  // [h2#subtitle]

const paragraphs = document.getElementsByClassName("paragraph");
console.log(paragraphs);  // [p.paragraph, p.paragraph, p.paragraph]

const img = document.querySelector("div > img");
console.log(img);  // <img src="./assets/photo.jpg">

const spans = document.querySelectorAll("div > .inner-span");
console.log(spans);  // [span.inner-span, span.inner-span]
```

Estos métodos nos permiten guardar los nodos o elementos de nuestro documento HTML en variables, para que más adelante podamos interactuar con ellos.

Como puede verse, `querySelector()` y `querySelectorAll()` permiten usar selectores de CSS, con ellos podemos seleccionar de manera más flexible, mientras que el resto de métodos nos obligan a seleccionar sólo `id`,  `class` o `tags`. Podemos seleccionar cualquier elemento con `querySelector()`, pero no así con el resto de métodos. Por ese motivo, aquí se recomienda usar siempre `querySelector()` y `querySelectorAll()`, y así se hará en los ejemplos a partir de ahora.

Es importante saber que las colecciones que devuelve `querySelectorAll()` son iterables (su contenido está ordenado con índices de base `0`), pero **_no_** son arrays. Podemos usar `forEach` para iterar por ellas, pero no podemos usar otros métodos de array como `map`, `filter` o `reduce`.

### Modificación de los nodos del DOM
Una vez hemos guardado los nodos de HTML que hemos traído con `querySelector()`, podemos interactuar con ellos como con cualquier objeto de JavaScript. Los nodos tienen muchas propiedades (muchísimas), por lo que no vamos a verlas todas.

#### Texto
Podemos acceder al texto de un nodo usando la propiedad `innerText` o `textContent`. La primera nos muestra el texto visible del nodo, la segunda también el que esté oculto (caracteres escapados, elementos con `visibility: hidden`, etc.). 
```javascript
const title = document.querySelector("#title");
console.log(title.innerText);  // Título

title.innerText = "Nuevo Título";
console.log(title); // <h1 id="title">Nuevo Tïtulo</h1>
```

#### Estilos
También podemos darle estilos *inline* a un nodo. Para ello, usamos la propiedad `style` y una propiedad de CSS. Cuando las propiedades de CSS lleven `-`, ahora estarán escritas en `camelCase`:
```javascript
const title = document.querySelector("#title");

title.style.color = "red";
title.style.backgroundColor = "blue";
console.log(title);  // <h1 id="title" style="color: red; background-color: blue;">Nuevo Tïtulo</h1>
```

Este código hará que el elemento `h1` que hemos seleccionado tenga el fondo azul y la fuente roja, como puede comprobarse ahora viendo su HTML: ahora se le ha aplicado un estilo **_inline_** con el atributo `style`.

#### Clases
Podemos accesder a la lista de clases de un elemento usando la propiedad `classList` que contiene un `array` con las clases que tiene.
```html
<p class="paragraph light-p">Párrafo</p>
```
```javascript
const paragraph = document.querySelector("p");
console.log(paragraph.classList); // ['paragraph', 'light-p']
```

Por lo tanto, podemos añadir o quitar clases del mismo modo que podemos añadir o quitar elementos de un array:
```html
<p class="paragraph">Párrafo</p>
```
```javascript
const paragraph = document.querySelector("p");
console.log(paragraph.classList);  // ['paragraph']

paragraph.classList.push("light");
console.log(paragraph.classList);  // ['paragraph', 'light']
```

Pero el método `classList()` nos provee a su vez de otras formas de añadir y quitar classes, usando dos métodos propios:
```html
<p class="paragraph">Párrafo</p>
```
```javascript
const paragraph = document.querySelector("p");

// quitar la clase "paragraph"
paragraph.classList.remove("paragraph");
// añadir la clase "light-text"
paragraph.classList.add("light-text");
concole.log(paragraph);  // <p class="light-text">Párrafo</p>
```

#### innerHTML
También es posible modificar el HTML **_dentro_** de un elemento, es decir, de sus *children* (no del propio elemento) usando `innerHTML`:
```html
<p class="paragraph">Párrafo</p>
```
```javascript
const paragraph = document.querySelector("p");
console.log(paragraph);  // <p class="paragraph">Párrafo</p>

paragraph.innerHTML = "<span class='myClass'>Span!</span>";
console.log(paragraph);  // <p class="paragraph"><span class='myClass'>Span!</span></p>
```

#### Atributos en general
Cualquier atributo es susceptible de ser creado y modificado mediante estos métodos. Por ejemplo, podemos añadir o alterar el atributo `src` de una imagen, o el `href` de un enlace:
```html
<img>
<a>Link</a>
```
```javascript
const img = document.querySelector("img");
const link = document.querySelector("a");

img.src = "../assets/photo.jpg";
link.href = "https://www.google.com";

console.log(img);   // <img src="../assets/photo.jpg">
console.log(link);  // <a href="https://www.google.com">Link</a>
```

#### Parent / child / sibling
Cada elemento del DOM guarda, a su vez, información acerca de los elementos que le rodean. Una vez has accedido a un nodo, podrás saber también cuál es su `parent`, cuáles son sus `children`, o su siguiente `sibling`.
```html
<section>
	<h1>Título</h1>
	<h2>Subtítulo</h2>
	<div>
		<p>Párrafo 1</p>
		<p>Párrafo 2</p>
		<p>Párrafo 3</p>
	</div>
</section>
```
```javascript
const h1 = document.querySelector("h1");
const h2 = document.querySelector("h2");
const div = document.querySelector("div");
const paragraphs = document.querySelectorAll("p");

console.log(h1.parentElement);  //  <section>...</section>

console.log(h1.nextElementSibling);  //  <h2>Subtítulo</h2>

console.log(h2.previousElementSibling);  //  <h1>Título</h1>

console.log(div.children);  //  [p, p, p]

console.log(paragrpahs[0].parentElement.parentElement);  // <section>...</section>
```

### Crear y eliminar nodos del DOM
Del mismo modo que podemos modificar nodos, también podemos crearlos y eliminar los ya existentes.

#### Crear un nodo
Para crear un nodo usamos `createElement("<elemento de HTML>")`:
```javascript
const h1 = document.createElement("h1");
console.log(h1);  // <h1></h1>

h1.innerText = "Title";
console.log(h1);  // <h1>Title</h1>
```

Ahora bien, que lo hayamos creado y guardado en nuestra variable, no quiere decir que el nodo aparezca en nuestro HTML. Nos falta añadirlo al DOM. Para ello, tenemos que introducirlo como `child` de otro elemento ya existente. Si no hubiera ninguno, lo haremos en el `<body>`.
Para añadir un nodo como hijo de otro, usamos `<parent>.appendChild(<child>)`, o bien, si queremos añadir varios a la vez: `<parent>.append(<child>, <child>, ...)`.
```html
<div class="container"></div>
```
```javascript
const div = document.querySelector(".container");

const paragraph = document.createElement("p");
p.innerText = "Párrafo 1";
console.log(paragraph);  //  <p>Párrafo 1</p>

div.appendChild(paragraph);
console.log(div);  //  <div><p>Párrafo 1</p></div>
```

#### Eliminar un nodo
Para eliminar un nodo, no tenemos más que usar el método `remove()`:
```html
<div>
	<p>Párrafo 1</p>
	<p>Párrafo 2</p>
	<p>Párrafo 3</p>
</div>
```
```javascript
const div = document.querySelector("div");
const paragraphs = document.querySelectorAll("p");
paragraphs.forEach(p => p.remove());

console.log(paragraphs);  // []
console.log(div);         // <div></div>
```