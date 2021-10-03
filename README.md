# Grid-Css

Aprendiendo Grid Css
<a name="top"></a>

## Índice de contenidos

- [Grid Explícita](#item1)
- [Grid Explícita Posicionamiento](#item2)
- [Grid con Nombres de Línea](#item3)
- [Grid con Áreas](#item4)
- [Grid Implícita](#item5)
- [Flujo de la Grid](#item6)
- [Flujo de la Grid Dense](#item7)
- [Grid Items en Capas (superposición)](#item8)
- [Ordenamiento de Grid Items](#item9)
- [Alineamiento de Grid Items](#item10)
- [Alineamiento de Grid Tracks](#item11)
- [Tamaños Máximos y Mínimos de Grid Tracks](#item12)
- [Grid con Patrones Repetitivos](#item13)
- [Grids Dinámicas](#item14)
- [Responsive sin Media Queries](#item15)
- [Grids Anidados](#item16)

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
.grid-implicit {
  display: grid;
  /* display: inline-grid; */ /* Compartir el espacio */
  /* Grid 4cX3r */
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 200px);
}
```

[Subir](#top)

<a name="item6"></a>

### Flujo de la Grid

```html
<section class="container grid-flow">
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
  <article class="item">
    <p>Item 10</p>
  </article>
  <article class="item">
    <p>Item 11</p>
  </article>
  <article class="item">
    <p>Item 12</p>
  </article>
  <article class="item">
    <p>Item 13</p>
  </article>
  <article class="item">
    <p>Item 14</p>
  </article>
  <article class="item">
    <p>Item 15</p>
  </article>
  <article class="item">
    <p>Item 16</p>
  </article>
  <article class="item">
    <p>Item 17</p>
  </article>
  <article class="item">
    <p>Item 18</p>
  </article>
  <article class="item">
    <p>Item 19</p>
  </article>
</section>
```

> Css Flujo de la Grid

```css
.grid-flow {
  display: grid;
  /* Grid de 5cX3r */
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(3, 100px);
  grid-auto-flow: row; /* Cambia el flujo */
  /* grid-auto-rows: 100px; */
  grid-auto-columns: 50px; /* Tamaños de Items no explicitos */
  grid-auto-flow: column;
}
```

[Subir](#top)
<a name="item7"></a>

### Flujo de la Grid Dense

```html
<section class="container grid-flow-dense">
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
  <article class="item">
    <p>Item 10</p>
  </article>
  <article class="item">
    <p>Item 11</p>
  </article>
  <article class="item">
    <p>Item 12</p>
  </article>
  <article class="item">
    <p>Item 13</p>
  </article>
  <article class="item">
    <p>Item 14</p>
  </article>
  <article class="item">
    <p>Item 15</p>
  </article>
  <article class="item">
    <p>Item 16</p>
  </article>
  <article class="item">
    <p>Item 17</p>
  </article>
  <article class="item">
    <p>Item 18</p>
  </article>
  <article class="item">
    <p>Item 19</p>
  </article>
</section>
```

> Css Flujo de la Grid Dense

```css
.grid-flow-dense {
  display: grid;
  /* Grid de 5cX4r */
  grid-template-columns: repeat(5, 1fr);
  grid-template-rows: repeat(4, 100px);
  /* grid-auto-flow: row dense; */
  grid-auto-flow: column dense;
}
.grid-flow-dense .item:nth-child(11) {
  color: cyan;
  grid-row: span 3;
  grid-column: span 3;
}
```

> [Subir](#top) >
> <a name="item8"></a>

### Grid Items en Capas (superposición)

```html
<section class="container grid-layers">
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
</section>
```

> Css Grid Items en Capas (superposición)

```css
.grid-layers {
  display: grid;
  /* Grid de 4cX4r */
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(4, 1fr);
}
.grid-layers .item:nth-child(1) {
  background-color: yellow;
  grid-column: 1 / 3;
  grid-row: 1 / 3;
}
.grid-layers .item:nth-child(2) {
  background-color: blue;
  grid-column: 3 / 5;
  grid-row: 1 / 3;
}
.grid-layers .item:nth-child(3) {
  background-color: green;
  grid-column: 1 / 3;
  grid-row: 3 / 5;
}
.grid-layers .item:nth-child(4) {
  background-color: orange;
  grid-column: 3 / 5;
  grid-row: 3 / 5;
}
.grid-layers .item:nth-child(5) {
  background-color: teal;
  grid-column: 2 / 4;
  grid-row: 2 / 4;
}
```

> [Subir](#top)

<a name="item9"></a>

### Ordenamiento de Grid Items

```html
<section class="container grid-order">
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
</section>
```

> Css Ordenamiento de Grid Items

```css
.grid-order {
  display: grid;
  /* Grid de 3cX2r */
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);
}
.grid-order .item:nth-child(1) {
  order: 4;
}
.grid-order .item:nth-child(2) {
  order: 5;
}
.grid-order .item:nth-child(3) {
  order: 2;
}
.grid-order .item:nth-child(4) {
  order: 3;
}
.grid-order .item:nth-child(5) {
  order: 1;
}
```

> [Subir](#top) > <a name="item10"></a>

### Alineamiento de Grid Items

```html
<section class="container grid-align">
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
</section>
```

> Css Alineamiento de Grid Items

```css
.grid-align {
  display: grid;
  /* Grid de 3cX2r */
  grid-template-columns: repeat(3, 200px);
  grid-template-rows: repeat(2, 200px);
  justify-items: center;
  align-items: center;
}
.grid-align .item:nth-child(4) {
  justify-self: start;
  align-self: center;
}
```

> [Subir](#top)

<a name="item11"></a>

### Alineamiento de Grid Tracks

```html
<section class="container grid-align-tracks">
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
</section>
```

> Css Alineamiento de Grid Tracks

```css
.grid-align-tracks {
  display: grid;
  /* Grid de 3cX2r */
  grid-template-columns: repeat(3, 200px);
  grid-template-rows: repeat(2, 200px);
  justify-content: space-evenly;
  align-content: space-evenly;
  /* Alineacion de las columnas y filas */
}
```

> [Subir](#top)

<a name="item12"></a>

### Tamaños Máximos y Mínimos de Grid Tracks

```html
<section class="container grid-min-max">
  <article class="item">
    <p>Item 1</p>
    <p>
      Lorem, ipsum dolor sit amet consectetur adipisicing elit. Repellendus rem
      earum autem quas tenetur, vero vel, eveniet dolores explicabo odit cumque
      tempora porro suscipit eius deserunt ab quis, voluptates saepe.
    </p>
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
</section>
```

> Css Tamaños Máximos y Mínimos de Grid Tracks

```css
.grid-min-max {
  display: grid;
  /* Grid de 4cX?r */
  grid-template-columns: repeat(4, minmax(100px, 200px)); /* minimo y maximo */
  grid-template-columns: repeat(
    4,
    minmax(min-content, 200px)
  ); /* min-content Propiedad Constante  */
  grid-template-columns: repeat(
    4,
    minmax(100px, min-content)
  ); /* min-content Propiedad Constante  */
  grid-template-columns: repeat(
    4,
    minmax(min-content, max-content)
  ); /* max-content Propiedad Constante  */
}
```

> [Subir](#top) > <a name="item13"></a>

### Grid con Patrones Repetitivos

```html
<section class="container grid-repeat">
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
  <article class="item">
    <p>Item 10</p>
  </article>
  <article class="item">
    <p>Item 11</p>
  </article>
  <article class="item">
    <p>Item 12</p>
  </article>
  <article class="item">
    <p>Item 13</p>
  </article>
  <article class="item">
    <p>Item 14</p>
  </article>
  <article class="item">
    <p>Item 15</p>
  </article>
  <article class="item">
    <p>Item 16</p>
  </article>
  <article class="item">
    <p>Item 17</p>
  </article>
  <article class="item">
    <p>Item 18</p>
  </article>
  <article class="item">
    <p>Item 19</p>
  </article>
</section>
```

> Css Grid con Patrones Repetitivos

```css
.grid-repeat {
  display: grid;
  /* Grid de 4cX4r */
  /* grid-template-columns: repeat(3, 10% 20% 30% 40%); */
  grid-template-columns: repeat(1, 10% 20% 30% 40%);
  grid-template-rows: repeat(2, 50px 100px);
  grid-auto-rows: 100px;
}
```

> [Subir](#top)

<a name="item14"></a>

### Grids Dinámicas

```html
<section class="container grid-dynamics">
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
</section>
```

> Css Grids Dinámicas

```css
.grid-dynamics {
  display: grid;
  /* Grid de 4cX?r */
  grid-template-columns: repeat(4, 100px);
  grid-template-columns: repeat(auto-fill, 100px); /* rellena el grid */
  grid-template-columns: repeat(
    auto-fit,
    100px
  ); /* Ajusta el grid con los tracks */
  grid-template-columns: repeat(
    auto-fill,
    minmax(100px, 1fr)
  ); /* Ajusta el grid con los tracks */
  grid-template-columns: repeat(
    auto-fit,
    minmax(100px, 1fr)
  ); /* Ajusta el grid con los tracks */
}
```

> [Subir](#top)

<a name="item15"></a>

### Responsive sin Media Queries

```html
<section class="container grid-responsive">
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
  <article class="item">
    <p>Item 10</p>
  </article>
  <article class="item">
    <p>Item 11</p>
  </article>
  <article class="item">
    <p>Item 12</p>
  </article>
  <article class="item">
    <p>Item 13</p>
  </article>
  <article class="item">
    <p>Item 14</p>
  </article>
  <article class="item">
    <p>Item 15</p>
  </article>
  <article class="item">
    <p>Item 16</p>
  </article>
  <article class="item">
    <p>Item 17</p>
  </article>
  <article class="item">
    <p>Item 18</p>
  </article>
  <article class="item">
    <p>Item 19</p>
  </article>
</section>
```

> Css Responsive sin Media Queries

```css
.grid-responsive {
  display: grid;
  /* Grid de ?cX?r */
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 1em;
}
```

> [Subir](#top)

<a name="item16"></a>

### Grids Anidados

```html
<section class="container grid-nested">
  <article class="item grid-nested">
    <div class="sub-item">
      <p>Sub-Item 1</p>
    </div>
    <div class="sub-item">
      <p>Sub-Item 2</p>
    </div>
    <div class="sub-item">
      <p>Sub-Item 3</p>
    </div>
    <div class="sub-item">
      <p>Sub-Item 4</p>
    </div>
    <div class="sub-item">
      <p>Sub-Item 5</p>
    </div>
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
</section>
```

> Css Grids Anidados

```css
.grid-nested {
  display: grid;
  /* Grid de 3cX?r */
  grid-template-columns: repeat(3, 1fr);
}
.sub-item {
  padding: 1rem;
  border: medium solid #ccc;
  background-color: #ddd;
}
```

> [Subir](#top)
