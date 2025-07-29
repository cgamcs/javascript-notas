# Comparar Null y Undefined

Es importante mencionar que en JavaScript hay diferentes tipos de datos primitivos a los que hemos visto además de string y number tenemos lo que se conoce como boolean y también existe un par llamado undefined y null.

```jsx
// Undefined
let numero;

console.log(numero);

// Null
let numero2 = null;

console.log(numero2);
```

Undefined quiere que decir que el valor de variable no esta definida, mientras que null se refiere a que no hay nada. Si comparamos undefined contra null lo lógico seria que fuese falso pero no JavaScript nos dice que es true eso usualmente lleva a ejecutar o ejecución de código no deseado o comportamientos extraños ya que estamos comparando un valor que no existe y de todas formas nos esta retornando true. Para ese tipo de cosas si es mas util el comparador estricto.