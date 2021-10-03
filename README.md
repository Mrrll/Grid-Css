# Grid-Css

Aprendiendo Grid Css
<a name="top"></a>

## Índice de contenidos

- [Grid Explícita](#item1)
- [Grid Explícita Posicionamiento](#item2)
- [Grid con Nombres de Línea](#item3)
- [Grid con Áreas](#item4)
- [Grid Implícita](#item5)

<a name="item1"></a>

### Grid Explícita

```html
<section class="container grid-explicit">
  <article class="item">
    <p>item 1</p>
  </article>
  <article class="item">
    <p>item 2</p>
  </article>
  <article class="item">
    <p>item 3</p>
  </article>
  <article class="item">
    <p>item 4</p>
  </article>
  <article class="item">
    <p>item 5</p>
  </article>
  <article class="item">
    <p>item 6</p>
  </article>
  <article class="item">
    <p>item 7</p>
  </article>
  <article class="item">
    <p>item 8</p>
  </article>
  <article class="item">
    <p>item 9</p>
  </article>
  <article class="item">
    <p>item 10</p>
  </article>
  <article class="item">
    <p>item 11</p>
  </article>
  <article class="item">
    <p>item 12</p>
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Recusandae
      commodi ad necessitatibus pariatur? .
    </p>
  </article>
  <article class="item">
    <p>item 13</p>
  </article>
  <article class="item">
    <p>item 14</p>
  </article>
  <article class="item">
    <p>item 15</p>
  </article>
  <article class="item">
    <p>item 16</p>
  </article>
  <article class="item">
    <p>item 17</p>
  </article>
  <article class="item">
    <p>item 18</p>
  </article>
  <article class="item">
    <p>item 19</p>
  </article>
</section>
```

> Css Grid Explícita

```css
.grid-explicit {
  display: grid;
  /* Grid de 3columnasX3rows */
  grid-template-columns: 50% 100px 1fr;
  grid-template-rows: 2rem 20vh 30%;
  /* Grid de 5cX4r */
  grid-template-columns: repeat(5, 20%); /* Iterador y Medida */
  grid-template-rows: repeat(4, auto);
  grid-template-columns: repeat(5, 1fr); /* 1fr espacio disponible */
  grid-template-rows: repeat(4, 1fr);
  /* Grid de 4cX5r */
  grid-template-columns: 20% repeat(2, 30%) 20%;
  grid-template-rows: repeat(5, auto);
  /* gap: 1em; */ /* espaciado entre filas y columnas */
}
```

[Subir](#top)
<a name="item2"></a>

### Grid Explícita Posicionamiento

```css
.grid-explicit .item:nth-child(10) {
  color: red;
  /* Posicionar celda */
  grid-row-start: 2;
  grid-row-end: 3;
  grid-column-start: 2;
  grid-column-end: 3;
  grid-row: 2 / 2; /* grid-row-start / grid-row-end */
  grid-column: 3 / 5; /* grid-column-start / grid-column-end */
  grid-area: 2 / 3 / 3 / 5; /* grid-row-start / grid-row-end / grid-column-start / grid-column-end */
}
.grid-explicit .item:nth-child(12) {
  color: cyan;
  grid-row: span 2; /* expande y tantas filas */
  grid-column: span 3; /* expande y tantas columnas */
}
.grid-explicit .item:nth-child(13) {
  color: teal;
  grid-row: 1 / span 2; /* expande y tantas filas */
  grid-column: 1 / span 2; /* expande y tantas columnas */
}
```

[Subir](#top)
<a name="item3"></a>

### Grid con Nombres de Línea

```html
<section class="container grid-line-names">
  <article class="item">
    <p>Item 1</p>
  </article>
  <article class="item">
    <p>Item 2</p>
  </article>
  <article class="item">
    <p>Item 3</p>
  </article>
  <article class="item">
    <p>Item 4</p>
  </article>
  <article class="item">
    <p>Item 5</p>
  </article>
  <article class="item">
    <p>Item 6</p>
  </article>
  <article class="item">
    <p>Item 7</p>
  </article>
  <article class="item">
    <p>Item 8</p>
  </article>
  <article class="item">
    <p>Item 9</p>
  </article>
</section>
```

> Css Grid con Nombres de Línea

```css
.grid-line-names {
  display: grid;
  /* Grid 3cX3r */
  grid-template-rows: repeat(3, 1fr);
  grid-template-columns: repeat(3, 1fr);
  grid-template-columns: [linea-c1] 1fr [linea-c2] 1fr [linea-c3] 1fr [linea-c4];
  grid-template-rows: [linea-r1] 1fr [linea-r2] 1fr [linea-r3] 1fr [linea-r4];
  grid-template-rows: [linea-r1] auto [linea-r2] auto [linea-r3] auto [linea-r4];
}
.grid-line-names .item:nth-child(3) {
  color: teal;
  grid-row: linea-r3 / linea-r4;
  grid-column: linea-c1 / linea-c4;
  /* grid-area: ; No funciona con grid line name*/
}
```

[Subir](#top)
<a name="item4"></a>

### Grid con Áreas

```html
<section class="container grid-areas">
  <header class="item header">
    <h1>Header</h1>
  </header>
  <article class="item content">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Obcaecati, non
      quaerat debitis impedit nesciunt voluptatem, odit maxime sed maiores
      cupiditate cumque in consequatur quod dicta optio vel alias voluptatum
      atque.
    </p>
  </article>
  <aside class="item sidebar">
    <p>Sidebar</p>
  </aside>
  <footer class="item footer">
    <p>Footer</p>
  </footer>
</section>
```

> Css Grid con Áreas

```css
.grid-areas {
  display: grid;
  /* Grid 2cX3r */
  grid-template-columns: 1fr 200px;
  grid-template-rows: 100px repeat(2, 1fr) 60px;
  grid-template-areas:
    'header header'
    'content sidebar'
    'content .'
    'footer footer';
}
.header {
  grid-area: header;
}
.content {
  grid-area: content;
}
.sidebar {
  grid-area: sidebar;
}
.footer {
  grid-area: footer;
}
```

[Subir](#top)

<a name="item5"></a>

### Grid Implícita

```html
<section class="container grid-implicit">
  <article class="item">
    <p>item 1</p>
  </article>
  <article class="item">
    <p>item 2</p>
  </article>
  <article class="item">
    <p>item 3</p>
  </article>
  <article class="item">
    <p>item 4</p>
  </article>
  <article class="item">
    <p>item 5</p>
  </article>
  <article class="item">
    <p>item 6</p>
  </article>
  <article class="item">
    <p>item 7</p>
  </article>
  <article class="item">
    <p>item 8</p>
  </article>
  <article class="item">
    <p>item 9</p>
  </article>
  <article class="item">
    <p>item 10</p>
  </article>
  <article class="item">
    <p>item 11</p>
  </article>
  <article class="item">
    <p>item 12</p>
  </article>
  <article class="item">
    <p>item 13</p>
  </article>
  <article class="item">
    <p>item 14</p>
  </article>
  <article class="item">
    <p>item 15</p>
  </article>
  <article class="item">
    <p>item 16</p>
  </article>
  <article class="item">
    <p>item 17</p>
  </article>
  <article class="item">
    <p>item 18</p>
  </article>
  <article class="item">
    <p>item 19</p>
  </article>
</section>
```

> Css Grid Implícita
```css
.grid-implicit{
    display: grid;
    /* display: inline-grid; */ /* Compartir el espacio */
    /* Grid 4cX3r */
    grid-template-columns: repeat(4,1fr);
    grid-template-rows: repeat(3, 200px);
}
```
[Subir](#top)
