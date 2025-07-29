# Operadores AND y OR

El operador AND (&&) revisa que se cumplan 2 o mas condiciones, es decir, el usuario debe estar autenticado y debe tener dinero suficiente para comprar.

```Javascript
const usuario = true
const puedePagar = true

if (usuario && puedePagar) {
    console.log('Si puede comprar');
}
```

**NOTA**

Si queremos hacer un diferente que hacia una variable solo debemos escribir el signo de admiracion antes de la variable:

```Javascript
const usuario = true
const puedePagar = true

if (!usuario) {
    console.log('Inicia sesion o registrate');
}
```

En este ejemplo podemos escribir varias condiciones, como si no tiene cuenta y no tiene dinero, si no tiene usuario, si no tiene suficiente dinero, para revisar ese tipo de condiciones podemos escribir el siguiente codigo.

```Javascript
const usuario = true
const puedePagar = true

if(usuario && puedePagar) {
    console.log('Si puede comprar');
} else if(!usuario && !puedePagar) {
    console.log('No puedes comprar')
} else if(!usuario) {
    console.log('Inicia sesion o registrate');
} else if(!puedePagar) {
    console.log('Saldo insuficiente');
}
```

Para retomar lo dicho en "Creando un if" es importante la estructura por que en el caso que hubiesemos escrito hasta el ultimo la parte de `!usuario && !puedePagar` y ambos fuesen false primero se hubiera ejecutado la parte de iniciar sesion.

```Javascript
// Mala estructura de codigo
if(usuario && puedePagar) {
    console.log('Si puede comprar');
} else if(!usuario) {
    console.log('Inicia sesion o registrate');
} else if(!puedePagar) {
    console.log('Saldo insuficiente');
} else if(!usuario && !puedePagar) {
    console.log('No puedes comprar')
}
```

### OR

El OR (||) revisa que se cumpla al menos una condicion, es decir, el si se va a pagar un producto pero no tiene suficiente efectivo pero si credito, entonces se cumple la condicion o si no tiene suficiente en ambos pero la suma del efectivo y del credito es mayo o igual al total a pagar entonces se cumple la condicion.

```Javascript
const efectivo = 300
const credito = 400
const disponible = efectivo + credito
const totalPagar = 600

if(efectivo > totalPagar || credito > totalPagar  || disponible > totalPagar ) {
    console.log('Si podemos pagar');
} else {
    console.log('Fondos insuficientes');
}
```