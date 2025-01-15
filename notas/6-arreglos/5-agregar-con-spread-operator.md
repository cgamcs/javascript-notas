# Crear un nuevo arreglo con el spread operator

En las nuevas versiones de javascript se agregaron algunas funciones que digamos hacen los mismo, unas se les conoce como declarativas y otras como formas imperativas, la forma imperativa son con los metodos **push** y **unshift** al agregar los elementos sobre ese mismo arreglo, es decir, modificamos la variable original. Cuando fue la gran actualizacion de javascript se agregaron las funciones declarativa, la forma declarativa es un paradigma que explica la logica sin describir tanto el flujo de control.

![arreglos](../../img/arreglos(13).png)

Para entederlo mejor en la forma declarativa vamos agregando elementos realizando copias de la variable original.

``` Javascript
const carrito = []

const producto = {
    nombre: 'Monitor 24"',
    precio: 170
}

const producto2 = {
    nombre: 'Teclado 60%',
    precio: 100
}

const producto3 = {
    nombre: 'Mouse',
    precio: 30
}
```

Para agregar elementos a un arreglo con spread operator necesitamos crear una nueva variable **let** y entonces podemos utilizar el spread operator.

``` Javascript
let resultado

resultado = [...carrito, producto] // Esto crea una copia de carrito y agrega el objeto de producto
```

Para mostrar el arreglo con el nuevo elemento deberiamos llamar a resultado no al carrito.

``` Javascript
let resultado

resultado = [...carrito, producto] // Esto crea una copia de carrito y agrega el objeto de producto

resultado = [...resultado, producto2] // Asi agregamos mas elementos al carrito

resultado = [producto3, ...resultado] // De esta forma podemos hacer lo mismo que unshift, agregar un elemento al principio del arreglo
```
