# Método .filter()

El método `.filter()` se usa para crear un nuevo arreglo que contiene solo los elementos que cumplen una condición. Si ningún elemento cumple la condición, retorna un arreglo vacío.

Este método no modifica el arreglo original.

## Sintaxis básica

```Javascript
array.filter(callback(elementoActual))
```

## Ejemplo con un carrito de compras

Queremos **filtrar** productos según diferentes condiciones.

```Javascript
const carrito = [
    { nombre: 'Monitor 27 Pulgadas', precio: 500 },
    { nombre: 'Televisión', precio: 100 },
    { nombre: 'Tablet', precio: 200 },
    { nombre: 'Audifonos', precio: 300 },
    { nombre: 'Teclado', precio: 400 },
    { nombre: 'Celular', precio: 700 },
]
```

## Productos con precio mayor a 300

```Javascript
let resultado = carrito.filter( producto => producto.precio > 300 )
console.log(resultado)
```

## Productos con precio menor a 300

```Javascript
resultado = carrito.filter( producto => producto.precio < 300 )
console.log(resultado)
```

## Todos menos los 'Audifonos'

```Javascript
resultado = carrito.filter( producto => producto.nombre !== 'Audifonos' )
console.log(resultado)
```

## Solo los 'Audifonos'

```Javascript
resultado = carrito.filter( producto => producto.nombre === 'Audifonos' )
console.log(resultado)
```

## ¿En qué casos es útil?

- Crear un nuevo arreglo excluyendo o incluyendo ciertos elementos.
- Filtrar productos según precio, categoría o stock.
- Obtener usuarios activos y excluir los inactivos.
- Separar datos que cumplen cierta regla de los que no.
- Implementar buscadores o sistemas de filtros (ejemplo: e-commerce).

## Nota extra

Si solo quieres **el primer elemento** que cumple la condición (y no todos), puedes usar el método `.find()`.
