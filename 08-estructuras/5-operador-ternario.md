# Operador Ternario

Este operador es un if pero de una sola linea y es un poco comun de ver, la forma de su sintaxis es un poco extraña pero vendria siendo la siguiente:

```Javascript
const autenticado = true
const puedePagar = true

console.log(autenticado && puedePagar ? 'Si puede pagar' : 'No puede pagar')
```

Por asi decirl el `?` es el comienzo de las llavez o donde se va a ejecutar la condicion y los dos puntos (`:`) son el else.

Tambien existen los ternarios anidados que vendrian siendo un if dentro de otro if. Esta otra forma es muy rara de ver pero si existe la forma de escribirlos.

```Javascript
const autenticado = true
const puedePagar = true

console.log(autenticado ? puedePagar ? 'Si esta autenticado y puede pagar' : 'Si esta autenticado, no puede pagar' : 'No puede pagar')
```