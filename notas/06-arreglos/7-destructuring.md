# Destructuring en Arreglos

La forma de haces destructuring a los arreglos es un poco parecida pero a la vez no de los objetos las sintaxis seria esta: `const [] = numeros`. En los objetos tu puedes traer solo los elementos que tu quieres llamandolos por su nombre `const { nombre } = producto`, en los arreglos le puedes dar el nombre que tu quieras a los elementos porque hace destructuring en base a las posiciones en las que estan `const [primero] = numeros`.

La posicion en la que pones el nombre dentro de los corchetes afecta el elementos al que le vas a hacer desctructuring, veamos mas ejemplos:

``` Javascript
const numeros = [10 , 20, 30, 40, 50]

const [ primero ] = numeros

const [ primero, segundo ] = numeros // Resultado: 10, 20

/*
  Si queremos mostrar un elemento en especifico sin llamar a los demas
  debemos agregar comas segun los indices saltados
*/
const [ , , tercero] = numeros // Resultado: 30

const [primero, , , cuarto] = numeros // Resultado: 10, 40

/*
  Para llamar un elemento y manterner a todos los demas dentro de un
  arreglo, debemos utilizar un spread operator
*/
const [primero, segundo, ...tercero] = numero // Resultado: 10, 20, [30, 40, 50]
```

**NOTA**

La sintaxis de destructuring utilizando spread operator es muy utilizada en React
