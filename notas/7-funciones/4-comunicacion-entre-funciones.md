# Como se comunican las funciones

Si queremos tener un codigo limpio y que sea facil de mantener podemos dividir una funcion de 300 lineas de codigo en funciones mas pequeñas, el caso aqui es como llamar esas funciones que se dividieron en otras funciones.

La forma natural que hemos visto es llamar la funcion antes o despues de la funcion dependiendo como se inicializo, pero donde vamos a escribirla dentro de otra funcion va a depender del uso que tenga cada una. Vamos a verlo con un ejemplo:

```Javascript
iniciarApp() // Inicia la primera funcion

function iniciarApp() {
     console.log('Iniciando app...')

     segundaFuncion() // Llamamos la segunda funcion despues de que se termine la primera funcion
}

function segundaFuncion() {
    console.log('Desde la segunda funcion')

    usuarioAutenticado('Cesar') // Llamamos una tercera funcion
}

function usuarioAutenticado(usuario) {
    console.log('Autenticando usuario espere...')

    console.log(`Usuario: ${usuario} autenticado`)
}
```

Como puedes ver en el ejemplo se le llama a la funcion despues de que se ejecuta la funcion "padre" podria decirse, pero no solo es al terminar tambien puede ser al comienzo, ejemplo:

```Javascript
iniciarApp() // Inicia la primera funcion

function iniciarApp() {
     console.log('Iniciando app...')

     segundaFuncion() // Llamamos la segunda funcion despues de que se termine la primera funcion
}

function segundaFuncion() {
    limpiandoContenido() // Llamamos una tercera funcion

    console.log('Mostrando nuevo contenido')
}

function limpiandoContenido() {
    console.log('Limpiando contenido anterior')

    console.log('Contenido limpiado')
}
```

### Ejemplos con funciones que se pasan valores

El sumar el contenido de un carrito y ademas calcular el impuesto total es un buen ejemplo para explicar como se pasan valores las funciones

```Javascript
let total = 0 // Iniciaciamos una variable que empiece en 0

// Agregamos dos funciones una para ir sumando el costo de un producto al carrito
// y otro para al terminar de sumar el total, agregar el 15% de impuestos
function agregarCarrito(precio) {
}

function calcularImpuesto(total) {
}
```

En los casos anteriores mostramos la informacion con console log pero si queremos que una funcion retorne un variable tenemos que utilizar **return** y los valores u operaciones que queremos retornar.

```Javascript
let total = 0

function agregarCarrito(precio) {
    return total += precio // Suma el precio al total
}

function calcularImpuesto(total) {
    return total * 1.15 // Agrega el 15%
}

// Agregamos los "productos"
total = agregarCarrito(300)
total = agregarCarrito(100)
total = agregarCarrito(500)
```

Para mostrar el costo total ya con impuestos necesitamos crear una variable mostrando el valor que retorna la funcion de **calcularImpuestos**, se agregar el argumento 'total' por la variable no por el parametro.

```Javascript
let total = 0

function agregarCarrito(precio) {
    return total += precio
}

function calcularImpuesto(total) {
    return total * 1.15
}

total = agregarCarrito(300)
total = agregarCarrito(100)
total = agregarCarrito(500)

const totalPagar = calcularImpuesto(total)

console.log(`El total a pagar es de $${totalPagar}`)
```