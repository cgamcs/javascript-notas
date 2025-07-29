# Uso avanzado del Spread Operator (`...`) en JavaScript
El Spread Operator (`...`) es una característica de ES6 que permite expandir elementos de un arreglo u objeto iterable dentro de otro. Es especialmente útil para copiar, combinar o agregar nuevos elementos sin modificar el original.

## Spread Operator con Arreglos de Índices
```javascript
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio'];

const meses2 = [...meses, 'Agosto'];

console.log(meses2);
```

Explicación
- `...meses` copia todos los elementos del arreglo original `meses`.
- `'Agosto'` se añade como un nuevo elemento al final.
- El arreglo original `meses` no se modifica.

Resultado:

```js
[
  'Enero', 'Febrero', 'Marzo', 'Abril',
  'Mayo', 'Junio', 'Julio', 'Agosto'
]
```

Esta técnica es ideal para mantener la inmutabilidad (no modificar el arreglo original).

## Spread Operator con Arreglos de Objetos
```javascript
const carrito = [
    { nombre: 'Monitor 27 Pulgadas', precio: 500 },
    { nombre: 'Televisión', precio: 100 },
    { nombre: 'Tablet', precio: 200 },
    { nombre: 'Audifonos', precio: 300 },
    { nombre: 'Teclado', precio: 400 },
    { nombre: 'Celular', precio: 700 },
];

const producto = { nombre: 'Disco Duro', precio: 300 };

const carrito2 = [...carrito, producto];

console.log(carrito2);
```

## Explicación
- `...carrito` copia todos los objetos del arreglo original `carrito`.
- `producto` se agrega como un nuevo objeto al final del nuevo arreglo `carrito2`.
- El arreglo `carrito` no se ve afectado.

Resultado en consola:

```js
[
  { nombre: 'Monitor 27 Pulgadas', precio: 500 },
  { nombre: 'Televisión', precio: 100 },
  { nombre: 'Tablet', precio: 200 },
  { nombre: 'Audifonos', precio: 300 },
  { nombre: 'Teclado', precio: 400 },
  { nombre: 'Celular', precio: 700 },
  { nombre: 'Disco Duro', precio: 300 }
]
```

## Ventajas del Spread Operator
- Sintaxis corta y legible.
- No modifica los arreglos originales (inmutabilidad).
- Permite combinar o clonar arreglos fácilmente.
- Funciona tanto con arreglos de valores primitivos como con objetos.
