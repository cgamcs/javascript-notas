# Método .reduce()

El método `.reduce()` es muy poderoso y se usa para acumular un valor a partir de los elementos de un arreglo. Sirve para hacer sumas, multiplicaciones, contar, agrupar datos y mucho más.

Este método devuelve un solo resultado después de procesar todo el arreglo.

## Sintaxis básica

```Javascript
array.reduce((acumulador, elementoActual) => {
    // lógica
    return nuevoAcumulador
}, valorInicial)
```

## Ejemplo con un carrito de compras

Queremos obtener el total a pagar sumando los precios de todos los productos.

## Con .forEach()

```Javascript
const carrito = [
    { nombre: 'Monitor 27 Pulgadas', precio: 500 },
    { nombre: 'Televisión', precio: 100 },
    { nombre: 'Tablet', precio: 200 },
    { nombre: 'Audifonos', precio: 300 },
    { nombre: 'Teclado', precio: 400 },
    { nombre: 'Celular', precio: 700 },
]

let total = 0
carrito.forEach( producto => total += producto.precio)
console.log(total) // 2200
```

## Con .reduce()
```Javascript
let resultado = carrito.reduce( (total, producto) => total + producto.precio, 0)
console.log(resultado) // 2200
```

En este caso:

- `total` es el acumulador que va sumando los precios.
- `producto` es el elemento actual que estamos procesando.
- `0` es el valor inicial del acumulador (empezamos desde 0).

`.reduce()` recorre todo el arreglo y retorna el total acumulado.

## ¿En qué casos es útil?

- Sumar valores (ejemplo: precios, cantidades, puntuaciones).
- Contar cuántas veces aparece algo en un arreglo.
- Agrupar datos (ejemplo: agrupar productos por categoría).
- Convertir un arreglo en un objeto o en otro arreglo diferente.
- Calcular promedios, máximos, mínimos.

## Nota extra

`.reduce()` es tan poderoso que muchos otros métodos como `.map()`, `.filter()` y `.find()` se pueden implementar usando solo `.reduce()`.