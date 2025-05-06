# Método .every()

El método `.every()` verifica si todos los elementos de un arreglo cumplen con una condición. Retorna `true` si todos pasan la prueba, y `false` si al menos uno falla.

Este método **no modifica** el arreglo original.

## Sintaxis básica

```Javascript
array.every(callback(elementoActual))
```
## Ejemplo con un carrito de compras

Queremos verificar si **todos** los productos tienen un precio menor a 1000.

```Javascript
const carrito = [
    { nombre: 'Monitor 27 Pulgadas', precio: 500 },
    { nombre: 'Televisión', precio: 100 },
    { nombre: 'Tablet', precio: 200 },
    { nombre: 'Audifonos', precio: 300 },
    { nombre: 'Teclado', precio: 400 },
    { nombre: 'Celular', precio: 700 },
]

const resultado = carrito.every( producto => producto.precio < 1000 )
console.log(resultado) // true
```

- En este caso, todos los precios son menores a 1000, por eso retorna `true`.
- Si al menos un producto tuviera un precio mayor o igual a 1000, retornaría `false`.

## ¿En qué casos es útil?

- Validar que todos los elementos cumplen cierta condición.
- Verificar si todos los usuarios están activos.
- Comprobar si todos los números son positivos.
- Checar si todos los productos están en stock.
- Confirmar que todas las tareas están marcadas como completadas.

## Nota extra

Si quieres comprobar si al menos uno cumple con la condición (y no todos), puedes usar el método `.some()`.