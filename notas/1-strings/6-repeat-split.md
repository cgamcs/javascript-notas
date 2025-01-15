# String Methods - Repeat y Split

### Repeat

Con repeat podemos repetir una cadena de texto.

```jsx
const producto = 'Monitor 20 Pulgadas ';

// .repeat te va a permitir repetir una cadena de texto
const texto = ' en promocion'.repeat(3);
```

![strings](../../img/strings(9).png)

Esto lo podemos combinar por ejemplo con los template strings.

```jsx
const producto = 'Monitor 20 Pulgadas ';
const texto = ' en promocion'.repeat(3);

console.log(texto);
console.log(`${producto} ${texto}!!!`);
```

![strings](../../img/strings(10).png)

<aside>
💡 Si te lo preguntabas, cuando escribes .repeat(2.4) no lo repite dos veces y fracción si no que lo redondea a un numero entero, si esta en 2.9 se redondea a 2

</aside>

Existe otro método llamado Split y  te va a permitir dividir un string

```jsx
const actividad = 'Estoy aprendiendo JavaScript Moderno';

console.log(actividad.split(" "));
```

![strings](../../img/strings(11).png)

Esto es muy util por ejemplo cuando tienes listado, por ejemplo en un sitio web de recetas, tienes un listado de los ingredientes, puedes usar esta técnica para mostrar un listado de categorías con recetas relacionadas.

![strings](../../img/strings(12).png)

Otro ejemplo es como twitter resalta sus hashtags.

```jsx
const tweet = 'Aprendiendo JavaScript #JSModernoConJuan';
console.log(tweet.split("#"));
```