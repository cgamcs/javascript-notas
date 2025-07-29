# La diferencia entre Metodo y Funcion

Los metodos son como las funciones, son reutilizables pero existe una diferencia y podemos verlo con la funcion nativa de **parseInt()**. Cuando utilizamos una "funcion" con un punto y despues del nombre de la variable a eso se le conce como metodo.

```Javascript
const numero1 = 20
const numero2 = '20'

console.log( parseInt(numero2) ) // Esto es una funcion

console.log( numero1.toString() ) // Esto es un metodo
```

En el caso de `console.log( parseInt(numero2) )` estamos mandando llamar la funcion **parseInt()** pero tambien le estamos pasando un valor dentro de los parentesis en ese caso se le llama **argumento**, mientras que en la funcion deberia de ser un **parametro**.
