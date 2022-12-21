![](../../assets/Logo_Yellow.png)

# Ejercicios DOM - Fix Wikipedia

### Introducción
En este ejercicio tendrás que aplicar todos tus conocimientos de manejo del DOM. Al final de este texto encontrarás un HTML que puedes copiar y pegar en tu propio documento para trabajar con él.
El HTML contiene un fragmento de un artículo de Wikipedia, sin embargo se han perdido trozos, y no hay ningún estilo. Deberás solucionar esto siguiendo las indicaciones de abajo.
NOTA: en este ejercicio **_NO_** puedes usar CSS, ni modificar el HTML directamente; sólo puedes usar JavaScript.

### Instrucciones
1. En el documento sobra el `h2` con la clase `subtitle`. Debes eliminarlo.
2. Los `span` con la clase `bold` deben aparecer en negrita. Hazlo sin tocar el documento de CSS: dale los estilos **_inline_**.
3. Los `span` con la clase `italics` deben ir en cursiva. Hazlo sin tocar el documento de CSS: dale los estilos **_inline_**.
4. En el `article` con la `id="index"` hay dentro una lista que ha perdido sus elementos. Te proporcionamos aquí el array con el texto de dichos elementos en orden; itera sobre la lista y ve creando los `li` necesarios con el texto apropiado: `["Introducción", "Biografía", "Obras"]`.
5. Todos los elementos de las listas dentro de la `section` con las obras deben tener la clase `"work-item"`.
6. A todos los link del documento les faltan sus `url`. Aquí tienes un array con las mismas, en orden; itera sobre la lista y da a cada elemento su atributo `href` con la `url` correspondiente:
```javascript
[
"https://es.wikipedia.org/wiki/Generaci%C3%B3n_del_27",
"https://es.wikipedia.org/wiki/Albert_Einstein",
"https://es.wikipedia.org/wiki/John_Maynard_Keynes",
"https://es.wikipedia.org/wiki/Marie_Curie",
"https://es.wikipedia.org/wiki/Luis_Bu%C3%B1uel",
"https://es.wikipedia.org/wiki/Rafael_Alberti",
"https://es.wikipedia.org/wiki/Salvador_Dal%C3%AD"
]
```

#### HTML inicial
```html
<body>
	<main>
		<article id="index">
			<h2 class="section-header">Índice</h2>
			<ul></ul>
		</article>

		<div id="title-container">
			<h1 id="title">Federico García Lorca</h1>
			<h2 id="subtitle">No sé qué hace este h2, pero no debería estar aquí</h2>
		</div>

		<section id="intro-section">
			<p><span class="bold">Federico García Lorca</span> (Fuente Vaqueros, Granada, 5 de junio de 1898 - camino de Víznar a Alfacar, Granada, 18 de agosto de 1936) fue un poeta, dramaturgo y prosista español. Adscrito a la <a>generación del 27</a>, fue el poeta de mayor influencia y popularidad de la literatura española del siglo xx y como dramaturgo se le considera una de las cimas del teatro español del siglo xx. Fue asesinado por el bando sublevado un mes después del golpe de Estado que provocó el inicio de la guerra civil española.</p>
		</section>

		<section id="biography-section">

			<h2 class="section-header">Biografía</h2>

			<p>Nació el 5 de junio de 1898 en el municipio granadino de Fuente Vaqueros, en el seno de una familia de posición económica desahogada, y fue bautizado como <span class="bold">Federico del Sagrado Corazón de Jesús García Lorca</span>.</p>

			<p>En su adolescencia, se interesó más por la música que por la literatura; estudió piano con Antonio Segura Mesa y entre sus amigos de la universidad lo conocían más como músico que por escritor novel.</p>

			<p>En 1914 se matriculó en la <span class="bold">Universidad de Granada</span> para estudiar las carreras de <span class="italics">Filosofía y Letras</span> y de <span class="italics">Derecho</span>. Durante esta época, el joven Lorca se reunía con otros jóvenes intelectuales en la tertulia <span class="italics">El Rinconcillo</span> del café Alameda. Más tarde se trasladaría a la <span class="bold">Residencia de Estudiantes de Madrid</span>.</p>

			<p>La <span class="bold">Residencia de Estudiantes</span> era en aquella época un hervidero intelectual, que acogió a figuras de la talla de <a>Albert Einstein</a>, <a>John Maynard Keynes</a> y <a>Marie Curie</a>, lo que influyó enormemente en la formación intelectual de Lorca. De esta forma, entre 1919 y 1926, se relacionó con muchos de los escritores e intelectuales más importantes de España, como <a>Luis Buñuel</a>, <a>Rafael Alberti</a> o <a>Salvador Dalí</a>.</p>
		</section>

		<section id="works-section">
			<h2>Obras</h2>
			<article class="works-article">
				<h3>Poesía</h3>
				<ul>
					<li>Canciones (1921)</li>
					<li>Poema del cante jondo (1921)</li>
					<li>Oda a Salvador Dalí (1926)</li>
					<li>Romancero gitano (1928)</li>
					<li>Poeta en Nueva York (1930)</li>
					<li>Llanto por Ignacio Sánchez Mejías (1935)</li>
					<li>Seis poemas galegos (1935)</li>
					<li>Sonetos del amor oscuro (1936)</li>
					<li>Diván del Tamarit (1940)</li>
				</ul>
			</article>

			<article class="works-article">
				<h3>Teatro</h3>
				<ul>
					<li>El maleficio de la mariposa (1920)</li>
					<li>Mariana Pineda (1927)</li>
					<li>La zapatera prodigiosa (1930)</li>
					<li>Retablillo de Don Cristóbal (1930)</li>
					<li>El público (1930)</li>
					<li>Así que pasen cinco años (1931)</li>
					<li>Amor de don Perlimplín con Belisa en su jardín (1933)</li>
					<li>Bodas de sangre (1933)</li>
					<li>Yerma (1934)</li>
					<li>Doña Rosita la soltera o el lenguaje de las flores (1935)</li>
					<li>La casa de Bernarda Alba (1936)</li>
				</ul>
			</article>

		</section>

	</main>
</body>
```