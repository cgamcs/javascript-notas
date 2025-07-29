# ¿Qué son los Arrow Functions?

Los arrow functions se agregaron hace relativamente poco y nos ayudan a tener una sintaxis un poco mas corta.

Estas son las primeras diferencias, el function se cambia por un `=>`.

```Javascript
const arrow1 = function() {
    console.log('Aprendiendo arrow function')
}

const arrow2 = () => {
    console.log('Aprendiendo arrow function')
}

arrow2() // Llamando la funcion
```

En este caso se puede hacer aun mas pequeña la sintaxis:

```Javascript
const arrow2 = () => 'Aprendiendo arrow function'

console.log(arrow2())
```

- Al ser una linea de codigo se pueden elimnar las llaves.
- Al ser una sola linea de codigo las arrow se da por implicito como return asi que la variable de arrow2 tiene el valor de 'Aprendiendo arrow function'.

### Utilizar parametros con arrow functions

Si utilizamos un parametro en nuestra funcion incluso podemos eliminar los parentesis y se volveria mas corta nuestra linea de codigo.

```Javascript
const arrow = lenguaje => {
    console.log(`Aprendiendo ${lenguaje}`)
}

console.log(arrow('JavaScript'))
```

Pero si utilizamos mas de un argumento si debemos escribir los parentesis:

```Javascript
const arrow = (lenguaje, lenguaje2) => {
    console.log(`Aprendiendo ${lenguaje} y ${lenguaje2}`)
}

console.log(arrow('JavaScript', 'Node.js'))
```

### Arrow functions en map y forEach

No hay mucha ciencia solo es utilizar la forma de arrow function.

```Javascript
const carrito = [
    { nombre: 'Monitor 24"', precio: 170},
    { nombre: 'Teclado 60%', precio: 90},
    { nombre: 'Mouse Logitech', precio: 80},
    { nombre: 'Lampara LED', precio: 50},
    { nombre: 'Cargado', precio: 20}
]

// Map
carrito.map( producto => `${producto.nombre} - Precio: ${producto.precio}` ) // Con return

// forEach
carrito.forEach( producto => console.log(`${producto.nombre} - Precio: ${producto.precio}`) )
```

**NOTA**

Si quieren agregar las arrow function al ejemplo del reproductor debe verse algo asi:

```Javascript
const reproductor = {
    reproduciendo: (id) => `Reproduciendo cancion con el id ${id}`,
    pausar: () => 'Pausando...',
    borrar: () => 'Borrando cancion...',
    agregarPlaylist: (nombre) => `Agregando nueva playlist ${nombre}`    
}

console.log(reproductor.reproduciendo(30))
console.log(reproductor.reproduciendo(10))
console.log(reproductor.pausar())
console.log(reproductor.reproduciendo(20))
console.log(reproductor.borrar())
console.log(reproductor.agregarPlaylist('Heaven'))
```