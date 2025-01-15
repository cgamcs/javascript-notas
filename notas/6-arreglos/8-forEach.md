# forEach para iterar un arreglo

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
