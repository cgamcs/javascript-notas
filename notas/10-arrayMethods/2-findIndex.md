# Método .findIndex()

El método `.findIndex()` es muy utilizado tanto en entrevistas como en proyectos reales. Sirve para encontrar el índice del primer elemento que cumple con una condición. Si no encuentra ninguno, retorna `-1`.

Es útil cuando necesitas saber en qué posición está un elemento dentro de un arreglo.

## Sintaxis básica

```Javascript
array.findIndex(callback(elementoActual))
```

## Ejemplo con un arreglo tradicional

Queremos encontrar en qué índice se encuentra `'Abril'` en el arreglo `meses`.

```Javascript
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio'];

const indice = meses.findIndex( mes => mes === 'Abril' )

if(indice > 0) {
    console.log(`Abril fue encontrado en el indice ${indice}`)
}

// Resultado:
// Abril fue encontrado en el indice 3
```

`.findIndex()` retorna `3`, ya que `'Abril'` está en la posición 3 del arreglo.

## Ejemplo con un arreglo de objetos

Ahora queremos encontrar la posición de un producto específico dentro de un carrito de compras.

```Javascript
const carrito = [
    { nombre: 'Monitor 27 Pulgadas', precio: 500 },
    { nombre: 'Televisión', precio: 100 },
    { nombre: 'Tablet', precio: 200 },
    { nombre: 'Audifonos', precio: 300 },
    { nombre: 'Teclado', precio: 400 },
    { nombre: 'Celular', precio: 700 },
]

const indice2 = carrito.findIndex( producto => producto.nombre === 'Tablet')
console.log(indice2) // 2
```

El producto `'Tablet'` está en la posición 2 del arreglo.

También podemos buscar por otros campos, por ejemplo por precio:

```Javascript
const indice3 = carrito.findIndex( producto => producto.precio === 400)
console.log(indice3) // 4
```

## ¿En qué casos es útil?

- Cuando quieres modificar un elemento específico y necesitas su índice.
- Para eliminar un elemento de un arreglo usando splice().
- Para reemplazar un objeto dentro de un arreglo de objetos.
- Cuando necesitas la posición y no solo saber si existe (en ese caso usarías `.some()`).

## Nota extra

Si solo quieres obtener el elemento que cumple la condición (en lugar del índice), puedes usar el método `.find()`.