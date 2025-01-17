# Como agregar funciones dentro de objetos

Para agregar una funcion dentro de un objeto debemos iniciarla dentro del despues del valor al que le queremos dar la funcion.

```Javascript
const reproductor {
    reproduciendo: function() {
        console.log(`Reproduciendo...`)
    }
}
```

Si queremos llamar la funcion debemos escribir el nombre de la variable y respues el nombre del valor dentro del objeto seguido de parentesis porque es una funcion.

```Javascript
const reproductor {
    reproduciendo: function() {
        console.log('Reproduciendo...')
    }
}

reproductor.reproduciendo() // Resultado: 'Reproduciendo'
```

Tambien podemos pasarle parametros y argumentos a las funciones aunque esten dentro del objeto.

```Javascript
const reproductor {
    reproduciendo: function() {
        console.log('Reproduciendo...')
    },
    agregarPalylist: function(nombre) {
        console.log(`Agregando nueva playlist: ${nombre}`)
    }
}

reproductor.reproduciendo()
reproductor.agregarPalylist('Pop') // Resultado: 'Agregando nueva playlist: Pop'
```