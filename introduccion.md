## Variables con var

Var era la forma de escribir las variables en versiones anteriores de ECMAScript hoy en día las opciones se reducen a dos let y const.

JavaScript **NO** es un lenguaje tipado como Java, tiene sus extension como TypeScript pero JavaScript como tal no lo es, sus variables **pueden cambiarse** no son fijas.

```jsx
// Inicializar una variable con un valor
var producto = 'Monitor de 27"';

console.log(producto);

// Las variables se pueden reasignar
producto = 'Monitor de 24"';

console.log(producto);

// JavaScript es un lenguaje de tipo dinámico, no se especifica tipo de dato
producto = 20;

console.log(producto);

// Se pueden inicializar sin valor y asignarlo después
var disponible;

disponible = true;

disponible = false;

// Inicializar multiples variables
var categoría = 'Computadoras',
    marca = 'Marca Famosa',
    calificación = 5;
```

Una variable puede contener letras, guiones bajos o numero pero **NO** pueden iniciar con un **numero**.

```jsx
// No funciona
var 99dias;
var 01_;

// Si funciona
var dias99;
var _01;
```

No es recomendable inicializar tus variables con guion bajo pero si es posible usarlo.

Existen diferentes estilo para crear variables con mas de una palabra, por ejemplo.

```jsx
var nombreproducto; // Tiene dos palabras no se diferencia muy bien
```

La forma mas común de hacerlo en JavaScript es el método **Camel Case** o camelCase, existen diferentes formas también existe una llamada **underscore**, **snake** esta forma no es tan común, **pascal case** que esta **se utiliza mas** con clases, es decir, una **clase** siempre inicia con una letra mayúscula de la siguiente manera.

```javascript
// camelCase
var nombreProducto;
// underscore
var nombre_producto;
// snake
var nombre_producto_categoria;
// PascalCase
var NombreProducto;
```

## Variables con let

Var era la forma de escribir las variables en versiones anteriores de ECMAScript hot en día las opciones se reducen a dos **let y const**, las reglas siguen siendo las mismas sin embargo de hoy en adelante se recomienda usar let y const, aunque si buscas ejemplos de JavaScript lo mas seguro es que utilicen var.

Entonces let te permite inicializar una variables y asignarle un valor, también te permite **reasignar** el valor.

```jsx
let producto = 'Tablet';

// Reasignar el valor
producto = 'Monitor';

producto = 20;

producto = true;

producto = null;
```

Puedes reasignar el valor ya sea un string, un entero o un booleano, eso es lo bueno de las variables con let es que si te permiten reasignar los valores.

Tambien puedes asignar una variable sin algún valor.

```jsx
let precio;
```

Mas que nada la diferencia entre var y let es lo que se le conoce el **scope** (alcance que tendrá tu código) de la variables.

## Variables con const

La tercer forma de construir variables se le conoce como const y existen muy pocas diferencias entre let y const, las reglas para crear variables también aplican para let y const.

La principal diferencia y fundamental es que const no puede ser reasignado.

La segunda diferencia es que const las variables deben inicializar con un valor, es decir, si yo pongo esto:

```jsx
const prodcuto;

const producto;
producto = 'Tablet';
```

Me va a marcar un error, debo de agregarle un valor a la variable. Y tiene que inicializar no puedes crear la variable sin valor y después asignarle uno.

```jsx
const producto = 'Tablet';
```

Esas son las diferencias mas importantes entre let y const, no se pueden reasignar y también deben inicializar con un valor.