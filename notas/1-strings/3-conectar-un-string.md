# Conectar un String y un Template String

Vamos a ver como concatenar dos strings o dos líneas en uno solo, existen varias formas la primera seria utilizando .concat con el cual puedes usar variables o strings para concatenar.

```jsx
const producto = 'Monitor 20" ';
const precio = '30 USD';

console.log(producto.concat(precio));
console.log(producto.concat('En descuento'));
```

Tambien puedes utilizar un + y con ese también puedes agregar strings.

```jsx
console.log(producto + precio);
console.log(producto + 'con un precio de ' + precio);
```

La forma mas común de concatenar variables y strings es de la siguiente manera.

```jsx
console.log('El producto ' + producto + 'tiene un precio de ' + precio);
```

Otra forma es usar comas entre strings y variables.

```jsx
console.log('El producto', producto, 'tiene un precio de', precio);
```

Qué pasa si me hace falta uno? Bueno nos marcara un error, el problema de esta sintaxis y como se soluciono fue un gran paso para JavaScript en la version ECMAScript 6, trajo consigo una mejor forma de concatenar variables que se conoce como **template strings** o **template literals** y en esta version en vez de usar comillas dobles o simples se utilizan estas comillas como inclinadas ( `` ) se llama backtick o acento grave, y para dar con las variables se utiliza el signo de dólar y llaves ( ${} ).

```jsx
console.log(`El producto ${producto} tiene un precio de ${precio}`);
```

La característica principal que tienen estos template strings es que las variables se agregan con estas sintaxis y que lo demás sigue siendo un string.