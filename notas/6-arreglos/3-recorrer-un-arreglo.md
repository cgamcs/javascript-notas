# Recorrer un Arreglo

Para explicarlo vamos a empezar con un ejemplo:

```jsx
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', , 'Mayo', , 'Junio'];
```

Cuando entras a Amazon y comienzas a agregar elementos al carrito y después visitas el carrito te comienza a listar todos los elementos que tienes, si usamos la sintaxis del código pasado tendríamos que escribir esto:

```jsx
console.log(meses[0]);
console.log(meses[2]);
console.log(meses[3]);
// Asi sucesivamente
```

Entonces las personas en el carrito de Amazon puede que tengan 0 elementos, 1 o hasta 100  elementos, entonces como haces para recorrer un arreglo, que su distancia que su tamaño pueda ser variable.

Lo primero es saber cuanto mide el arreglo. Para ello tenemos que usar la siguiente sintaxis:

```jsx
console.log(meses.length);
```

![arreglos](../../img/arreglos(6).png)

Como dato importante, este length no inicia en 0 es por que llega hasta el 8.

De esa forma podemos escribir un código que se ejecute solamente la cantidad de meses que hay en un arreglo. Para poder conseguirlo tenemos que usar un iterador en este caso sera un **for loop** que es una función que tiene 3 partes: 1 - es el valor que va a iniciar, 2 - es cuantas veces quieres que se ejecute el código (la cantidad de meses que hay en el arreglo), 3 - la forma en que se recorre si incrementa o decrementa.

```jsx
for(let i = 0; i < meses.length; i++) {

}
```

Por que se utiliza un let en vez de un const? Es porque la variable de i va a ir incrementado es decir va a cambiar constantemente y si recuerdas el valor de const no te permite cambiar el valor, entonces usualmente sera un let.

```jsx
for(let i = 0; i < meses.length; i++) {
	console.log(i);
}
```

![arreglos](../../img/arreglos(7).png)

Ahora ya tenemos nuestra iteración pero cómo mostramos los datos? Necesitamos la siguiente sintaxis:

```jsx
for(let i = 0; i < meses.length; i++) {
    console.log( meses[i]) ;
}
```

!![arreglos](../../img/arreglos(8).png)

Y listo con eso podemos mostrar los elementos que tenemos en nuestro carrito, también si añadiéramos otro mes a nuestro carrito este se mostrar.

```jsx
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio'];
// Julio es el nuevo dato

console.table(meses);

for(let i = 0; i < meses.length; i++) {
    console.log( meses[i]) ;
} 
```

![arreglos](../../img/arreglos(9).png)