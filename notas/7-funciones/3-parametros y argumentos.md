# Parametros y argumentos en funciones

Para que una funcion pase de ser "estatica" a ser mas dinamica debemos pasarle parametros, veamos un ejemplo con la funcion sumar():

```Javascript
function sumar() {
  console.log(2 + 2)
}

sumar() // Resultado: 4
```

Cada que volvamos a llamar la funcion el resultado va a ser el mismo 4, 4, 4, para que en verdad sea una suma con los valors que nosotros queramos debemos darle parametros dentro de la funcion.

```Javascript
function sumar(x, y) { // x, y son parametros
  console.log( x + y )
}

sumar(2, 3) // Resultado: 5
sumar(4, 4) // Resultado: 8
sumar(1, 2) // Resultado: 3
```

Los valores que estan dentro de los parentesis al momento de llamar la funcion `sumar(2, 3)` son los llamados argumentos. Estos son valores **reales** mientras que los x, y de console.log son los valores **representativos**.

![funciones](../../img/funciones(2).png)

**NOTA**

Si no le pasamos ningun argumento al llamar la funcion nos maracara como undefined ambos valores, para eso podemos utilizar los parametros por default. Los parametros por default nos ayudan a marcar un resultado en caso de que no se agreguen los argumentos y mostrar un mejor resultado.

Por ejemplo, si queremos saludar al usuario:

```Javascript
function saludar(nombre = 'Desconocido', apellido = '') {
    console.log(`Hola ${nombre} ${apellido}`)
}

saludar('Cesar', 'Garcia') // Resultado: 'Hola Cesar Garcia'
saludar('Cesar',) // Resultado: 'Hola Cesar
saludar() // Resultado: 'Hola Desconocido' 
```
