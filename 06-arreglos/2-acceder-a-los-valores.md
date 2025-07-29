# Acceder a los valores de un Array

Como vimos anteriormente los arreglos tienen indices, esos indices sirven para determinar la posición de un dato. Utilizando el código anterior como ejemplo vamos a acceder a cualquiera de sus datos.

```jsx
const numeros = [10, 20, 30, 40, 50];
```

Para verlo en la consola podemos usar:

```jsx
console.log(numeros);
console.table(numeros);
```

![arreglos](../../img/arreglos(3).png)

Con cualquiera de las dos formas podemos ver el índice, con el vamos a poder acceder al dato con la siguiente sintaxis:

```jsx
console.log(numeros[2]);
```

Con esa sintaxis le estamos diciendo que queremos recuperar el dato con el índice numero 2.

![arreglos](../../img/arreglos(4).png)

Si queremos acceder a un arreglos de arreglos (arreglo dentro de otro arreglo) tienes que pasarle ambos indices en el caso que quieras un dato en especifico de ese arreglo.

```jsx
const numeros = [10, 20, 30, 40, 50 [60, 70, 80]];
```

![arreglos](../../img/arreglos(5).png)

```jsx
console.log(numeros[5]);
console.log(numeros[5][2]);
```

![arreglos](../../img/arreglos(6).png)

Si solo le pasamos un valor nos regresara todo el arreglo, si queremos un dato en especifico hay que indicar los dos indices.