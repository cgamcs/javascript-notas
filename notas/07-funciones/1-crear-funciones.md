# Crear funciones

Las funciones en cualquier lenguaje de programacion son una serie de procedimientos o instrucciones, es decir, van a realizar una accion.

Ventajas:
- Mantiene el codigo mas ordenado
- Es mas facil de mantener
- Son reutilizables

Se conocen de dos maneras una es la **expresion** de funcion y la otra es **declaracion** de funcion.

Para crear una funcion se deben de agregar la palabra reservada **function** despues el nombre de la funcion, el nombre tiene las mismas reglas que las variables, es decir, no puede llevar numeros al principio o signos como guion bajo, seguido del nombre debe llevar parentesis donde se llevan los parametros de la funcion, luego se habren llaves y ahi es donde ira el cuerpo de la funcion.

![funciones](../../img/funciones(1).png)

Para mandar a llamar una funcion solo es necesario el nombre de la funcion y sus parentesis:

```Javascript
// Function declaration
function sumar() {
  console.log( 2+ 2 )
}

sumar() // Resultado: 4
```

Hasta aqui la forma de escribir la funcion es la manera conocida como **declaracion** de la funcion, pero tambien tenemos la **expresion** de funcion que se inicia como variable y para llamarla es igual que de la forma declarativa

```Javascript
// Function expression
const sumar2 = function() {
  console.log(3 + 3)
}

sumar2()
```

### Diferencias entre function expression y declaration

Con function declaration podemos acceder a la funcion antes de inicializarla, mientras que con function expression si llamamos la funcion antes de inicializarla nos marcara un error.

¿Por que pasa esto? Por que JavaScript se ejecuta en dos vueltas conocido como **hoisting**, esto quiere decir que en la primera vuelta escanea el documento y registra todas las funciones y determina que variables va a crear, esta etapa se conoce como estapa de creacion, en la segunda vuelta esa funcion ya esta registrada y se le conoce como etapa de ejecucion. En el caso de la function expression podemos ver que no esta declarada como una funcion sino como una variable asi que basicamente para javascript en vez de ver esto:

```Javascript
const sumar2 = function() {
  console.log(3 + 3)
}

sumar2()
```

Javascript en la etapa de creacion ve esto:

```Javascript
const sumar2

sumar2()
```

**NOTA**

En javascript tambien existen funciones nativas como: `alert()`, `prompt()`, `parseInt()`, etc.



