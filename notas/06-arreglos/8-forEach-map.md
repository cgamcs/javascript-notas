# forEach y map para iterar un arreglo

El forEach es muy parecido al for pero el forEach es un array method lo que nos facilita un poco el codigo al momento de iterar en los arreglos. Para mostrar como se hace pondre el ejmplo de como se haria la iteracion de un arreglo con for y como se haria con forEach

```Javascript
const carrito = [
    { nombre: 'Monitor 24"', precio: 170},
    { nombre: 'Teclado 60%', precio: 90},
    { nombre: 'Mouse Logitech', precio: 80},
    { nombre: 'Lampara LED', precio: 50},
    { nombre: 'Cargado', precio: 20}
]
```

Nuestro arreglo sera un carrito en el cual se encuentran varios productos con nombre y precio, para iterar sobre el arreglo y mostrar el nombre y precio con un **for** seria asi:

```Javascript
for(let i = 0; i < carrito.length; i++) {
    console.log(`${carrito[i].nombre} - Precio: ${carrito[i].precio}`)
}
```

Pero al ser un arreglo podemos utilizar un array method conocido como forEach no son tantas las lineas de diferencia las que tiene pero es un poco mas facil de usar.

```Javascript
// 'carrito' es todo el arreglo
carrito.forEach( (producto) => { // 'producto' seria cada objeto por separado
    console.log(`${producto.nombre} - Precio: ${producto.precio}`) // Usar producto.nombre seria como tener carrito[i].nombre
})
```

### .map()

La diferencia entre un forEach y un map (esta es pregunta para conseguir empleo) es que map te crea un arreglo nuevo, .map() va a llenar una variable con un arreglo nuevo. Una forma de utilizar map o una manera en la que necesitariamos crear un nuevo arreglo es si queremos traer todos los productos con un precio arriba de $50, ese seria un ejemplo para utilizar .map()

```Javascript
carrito.map( (producto) => {
    console.log(`${producto.nombre} - Precio: ${producto.precio}`)
})
```

**NOTA**

Si quieres ver la diferencia entre forEach y map para entender a que me refiero con nuevo arreglo, debes escribir la siguiente sintaxis:

```Javascript
const arreglo1 = carrito.forEach( (producto) => {
    return `${producto.nombre} - Precio: ${producto.precio}`)
})

const arreglo2 = carrito.map( (producto) => {
    return `${producto.nombre} - Precio: ${producto.precio}`)
})

console.log(arreglo1)
console.log(arreglo2)
```
