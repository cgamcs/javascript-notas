# Creando un If()

Los if nos ayudan a hacer comparaciones, por ejemplo si queremos retirar dinero de un cajero, el cajero debe revisar que si tengamos la suficiente cantidad de dinero que deseamos retirar, eso se haria con if.

```Javascript
const puntaje = 1000

if (puntaje == 1000) {
    console.log('Si es igual')
} else {
    console.log('No es igual');
}
```

Este es un ejemplo muy claro, tenemos el puntaje que es igual a 1000, agregamos un if y dentro de los parentesis ponemos las codiciones que se tienen que cumplir para que pase la accion que requerimos en este caso seria el `console.log('Si es igual')`, despues tenemos un else, en este caso sirve si ninugna de las condiciones se cumplen, aqui es para retornar el mensaje de "No es igual" pero podemos dejar solo el if, con eso se sigue corriendo el programa pero no retornara ningun mensaje.

### Operador estricto

Si queremos hacer una comparacion que sea estricta, es decir, si queremos comparar tipos de dato iguales com un entero con solo enteros o strings con strings, y cosas por el estilo debemos usar el operador estricto (===).

```Javascript
const puntaje = 1000

if (puntaje == '1000') { // Operador no estricto
    console.log('Si es igual')
} else {
    console.log('No es igual');
}
// Resultado: 'Si es igual'

if (puntaje === '1000') { // Operador estricto
    console.log('Si es igual')
} else {
    console.log('No es igual');
}
// Resultado: 'No es igual'
```

**NOTA**
Si queremos hacer una comparacion en la que el dato debe de ser diferente de, es decir puntaje debe ser diferente de mil en vez de escribir algo como `puntaje mayor igual que 1000` y `puntaje menor igual que 1000` podemos escribir el comprardor `!=` que vendria siendo **diferente de**.

### Operador mayor que o menor que

Supongamos que vamos a pagar un producto en la tienda, y debemos saber si tenemos suficiente dinero para eso debemos usar los operadores de mayor que o menor que.

```Javascript
const dinero = 500
const totalPagar = 300

if (dinero > totalPagar) {
    console.log('Si podemos pagar')
} else {
    console.log('No podemos pagar');
}
// Resultado: 'Si podemos pagar'
```

La logica de este codigo es: si dinero es mayor que el total a pagar entonces si podemos pagar, en caso contrario no podemos pagar. Si lo escribieramos con el simbolo de menor que (<) tendriamos que cambiar un poco el codigo y seria un poco confuso. Por eso es mejor a comodar tus variables para que resulte de la forma mas entendible tu codigo.

Ahora, si en nuestra cuenta tuviéramos exactamente 300 con los operadores de mayor que o menor que el resultado sería 'No podemos pagar' para resolverlo debemos agregar un igual después de los operadores, ya sea, mayor que o menor que.

```Javascript
const dinero = 300
const totalPagar = 300

if (dinero >= totalPagar) {
    console.log('Si podemos pagar')
} else {
    console.log('No podemos pagar');
}
// Resultado: 'Si podemos pagar'
```

### Creando else if

En el caso de que no tengamos suficiente dinero pero tengamos nuestra tarjeta al momento de pagar en la tineda, cumplir otra condicion para poder pagar.

```Javascript
const dinero = 100
const totalPagar = 300
const tarjeya= true

if (dinero >= totalPagar) {
    console.log('Si podemos pagar')
} else if(tarjeta) {
    console.log('Si podemos pagar con la tarjeta')
} else {
    console.log('No podemos pagar');
}
// Resultado: 'Si podemos pagar con la tarjeta'
```

En los if la primera condicion que se va a ejecutar es la que se cumpla en el ejemplo anterior si hubiesemos tenido suficiente dinero solo hubiese mostrado el mensaje de 'Si podemos pagar' osea que si teniamos suficiente dinero, por eso es importante tener una buena estrucutra de codigo si vamos a trabajar con if's.