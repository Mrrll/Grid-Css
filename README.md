# Grid-Css

Aprendiendo Grid Css
<a name="top"></a>

## Índice de contenidos

- [Grid Explícita](#item1)
- [Grid Explícita Posicionamiento](#item2)

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
.grid-explicit .item:nth-child(10){
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
.grid-explicit .item:nth-child(12){
    color: cyan;
    grid-row: span 2; /* expande y tantas filas */
    grid-column: span 3; /* expande y tantas columnas */
}
.grid-explicit .item:nth-child(13){
    color: teal;
    grid-row: 1 / span 2; /* expande y tantas filas */
    grid-column: 1 / span 2; /* expande y tantas columnas */
}
```

[Subir](#top)
