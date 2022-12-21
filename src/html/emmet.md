![logotipo de GammaTech School](../assets/Logo_Yellow.png)

# Emmet

## Introducción

[Emmet](https://docs.emmet.io) es una herramienta que nos permite crear HTML a partir de una línea de texto.

Con algo tan simple como esto:

```html
nav>ul>li
```

es capaz de hacer algo como esto:

```html
<nav>
    <ul>
        <li></li>
    </ul>
</nav>
```
Como puedes ver, es una herramienta muy útil para escribir bloques complejos de HTML de manera sencilla. Lo único que hay que hacer es aprenderse un par de reglas.

Puedes aprender más en los siguientes enlaces:
- [Emmet](https://docs.emmet.io)
- [Chuleta Emmet](https://docs.emmet.io/cheat-sheet)


#### Etiquetas con contenido
Para introducir contenido en una étiqueta, usamos `{}`:
```html
h1{Soy un header}
```

Resultado:
```html
<h1>Soy un header</h1>
```

#### Nesting de etiquetas
Para "meter" una etiqueta dentro de otra, usa `>`:
```html
div>ul>li
```

Resultado:
```html
<nav>
    <ul>
        <li></li>
    </ul>
</nav>
```

#### Etiquetas hermanas (al mismo nivel)
Cuando queremos crear etiquetas de HTML que no están una dentro de otra, sino que están al mismo nivel, usamos `+`:

```html
h1+p
```

Resultado:
```html
<h1></h1>
<p></p>
```

#### Etiquetas multiplicadas
Podemos crear un número determinado de la misma etiqueta usando `*`:
```html
p*4
````

Resultado:
```html
<p></p>
<p></p>
<p></p>
<p></p>
```

#### Etiquetas agrupadas
Podemos combinar las operaciones anteriores y agruparlas usando `()`:

```html
div>(div>h1+p)+div>h2
````

Resultado:
```html
<div>
    <div>
        <h1></h1>
        <p></p>   
    </div>
    <div>
        <h2></h2>
    </div>
</div>
```

#### Añadir clases e id
Para añadirle clases y etiquetas a los elementos de HTML, usamos `.` para las clases y `#` para id:

```html
div.container
h1#title
```

Resultado:
```html
<div class="container"></div>
<h1 id="title"></h1>
```

## Ejercicios
Escribe en una línea para ejecutar con Emmet el resultado que se muestra en los siguientes apartados (todos deben ser escritos en una única línea de Emmet):

1. Elementos simples

```html
<h1></h1>
<h2></h2>
<p></p>
```

2. Elementos con contenido

```html
<h1>Soy un título</h1>
<p>y yo un párrafo</p>
```

3. Anidamiento simple

```html
<h1><mark></mark></h1>
```

4. Anidamiento con contenido

```html
<h1><mark>El texto subrayado</mark></h1>
```

5. Anidamiento con múltiples elementos

```html
<ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

6. Anidamiento con múltiples elementos y contenido

```html
<ul>
  <li>Elemento</li>
  <li>Elemento</li>
  <li>Elemento</li>
  <li>Elemento</li>
  <li>Elemento</li>
</ul>
```