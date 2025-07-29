# Buenas practicas con los fi

Si queremos revisar la condicion de una variable que sea `true` no necesitamos escribir la condicion como `variable === true` podemos solo escribir el nombre de la variable.

```Javascript
const autenticado = true

if(autenticado) {
    console.log('El usuario esta autenticado');
}
```

Si tenemos varios if con disitntas condifiones debemos escribir el condigo con una buena estructura, por asi decirlo de mayor a menor importancia

```Javascript
const puntaje = 300

if(puntaje > 400) {
    console.log('Buen puntaje felicidades')
} else if (puntaje > 300) {
    console.log('Bien hecho, sigue asi')
}
```

Si no te gusta escribir como `else if` puedes escribir puros if y agregar un return al final del codigo, eso hace que no se ejecute el siguiente codigo al terminar de cumplirse la condicion y de hecho es una buena practica hacerlo de esta manera.

```Javascript
const puntaje = 300

if(puntaje > 400) {
    console.log('Buen puntaje felicidades')
    return
}

if (puntaje > 300) {
    console.log('Bien hecho, sigue asi')
    return
}
```

Si lo escribirmos de esta manera seria incluso mejor si lo hacemos dentro de una funcion para revisar el puntaje.

```Javascript
const puntaje = 300

function revisarPuntaje() {
    if(puntaje > 400) {
        console.log('Buen puntaje felicidades')
        return
    }

    if (puntaje > 300) {
        console.log('Bien hecho, sigue asi')
        return
    }
}

revisarPuntaje()
```