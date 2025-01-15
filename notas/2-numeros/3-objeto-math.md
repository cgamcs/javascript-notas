# El Objeto Math

Math como podemos ver es un objeto, tiene varias funciones y podemos ver cuales son en la misma consola. Puedes acceder a ella colocando Math, un punto y después el nombre de la función, ejemplo: `Math.PI`

![numeros](../../img/numeros(3).png)

Veremos lo mas usado en cuestión de funciones.

```jsx
// PI
resultado = Math.PI;
```

Funciona para mostrar el valor de PI.

```jsx
// Redondear
resultado = Math.round(2.8);
resultado = Math.round(2.3);
resultado = Math.round(2.5);

// Redondear hacia arriba
resultado = Math.ceil(2.1);

// Redondear hacia arriba
resultado = Math.floor(2.8);

```

Funciona para redondear, **round** redondea hacia arriba desde .5 pero **ceil** redondea desde 2.1 a 3 y **floor** desde 2.9 a 2.

```jsx
// Raiz Cuadrada
resultado = Math.sqrt(144);
```

Sirve para mostrar la raíz cuadrada de cualquier numero.

```jsx
// Absoluto
resultado = Math.abs(-500);
```

Sirve para mostrar solo el valor absoluto de un numero en este ejemplo -500 mostraría solamente 500.

```jsx
// Potencia
resultado = Math.pow(2, 4);
```

Se refiere a la potencia de un numero con este ejemplo hablamos de 2 a la potencia de 4, es decir, el resultado seria 16.

```jsx
// Minimo
resultado = Math.min(3, 5, 1, 6, 12, -3);

// Maximo
resultado = Math.max(3, 5, 1, 6, 12, -3);
```

No nada mas solo son los valores mínimo o máximo de una lista de números.

```jsx
// Aleatorio
resultado = Math.random();

// Aleatorio dentro de un rango
resultado = Math.floor( Math.random() * 30 );
```

Crea numero aleatorios si se escribe como el primer ejemplo serán números muy bajos (hablamos de decimales) y por el otro lado le podemos asignar rangos y que sean numero enteros con funciones que vimos anteriormente.