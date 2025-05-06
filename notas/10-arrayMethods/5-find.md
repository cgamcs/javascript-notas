Método .find()

El método `.find()` se usa para buscar y devolver el primer elemento de un arreglo que cumple con una condición. Si no encuentra ninguno, retorna `undefined`.

Este método no modifica el arreglo original.

## Sintaxis básica

```Javascript
array.find(callback(elementoActual))
```

## Ejemplo con un carrito de compras

Queremos encontrar un producto específico dentro del carrito.

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

## Con .forEach()

```Javascript
let resultado = ''
carrito.forEach( (producto, i) => {
    if(producto.nombre === 'Tablet') {
        resultado = carrito[i]
    }
})

console.log(resultado)
// { nombre: 'Tablet', precio: 200 }
```

## Con .find()

```Javascript
const resultado2 = carrito.find( producto => producto.nombre === 'Tablet')
console.log(resultado2)
// { nombre: 'Tablet', precio: 200 }
```

`.find()` detiene la búsqueda cuando encuentra el primer elemento que cumple la condición.

## ¿En qué casos es útil?

- Cuando necesitas solo un elemento, no varios (si necesitas varios, usa .filter()).
- Para buscar un producto por nombre, ID o código.
- Para encontrar un usuario específico en una lista.
- Cuando quieres evitar hacer un .forEach() manual con condiciones.

## Nota extra

Si quieres encontrar la posición (índice) en lugar del elemento, puedes usar .findIndex().