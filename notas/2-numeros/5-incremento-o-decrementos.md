# Incrementos o Decrementos

Veremos como incrementar de uno en uno o en determinada cantidad, también por ejemplo como ir bajando el puntaje de uno en uno o determinada cantidad, es ideal para un videojuego o si estas haciendo un juego de trivia y obtienen una respuesta correcta se le suma el puntaje y si tiene una incorrecta va cayendo el puntaje.

Existen dos formas de ir incrementando de uno en uno, en realidad son 3 pero 2 son las mas utilizadas.

![numeros](../../img/numeros(4).png)

Podemos usar puntaje++ o ++puntaje la diferencia entre una y la otra es que una va a mostrar el nuevo resultado hasta que la vuelvas a llamar y la otra lo hara inmediatamente. Seria lo mismo para restar los valores de uno en uno.

```jsx
let puntaje = 5;

puntaje++; // Primero muestra el valor orignal y lo suma hasta que vuleve a ser llamado (5)
++puntaje; // Incrementa el valor y lo muestra inmediatamente (6)

puntaje--; // Primero muestra el valor orignal y lo reduce hasta que vuleve a ser llamado (5)
--puntaje; // Decrementa el valor y lo muestra inmediatamente (4)
```

Ahora si por ejemplo estamos haciendo un juego de futbol pues si los valores van de uno en uno pero si hacemos uno de básquet los valores irían de 2 o de 3.

```jsx
let puntaje = 5;

puntaje += 3;
puntaje -= 3;
```