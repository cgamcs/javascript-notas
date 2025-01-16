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
