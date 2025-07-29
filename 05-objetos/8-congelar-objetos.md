# Congelar un Objeto para no poderlo modificar

Veamos una serie de métodos para los objetos, uno que nos va a permitir modificar las llaves de un objeto.

Ya vimos anteriormente que un objeto puede ser modificado, entonces como hacemos para que un objeto se comporte como una constante? Para eso tenemos que usar el modo estricto.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

producto.disponible = false;
producto.imagen = 'imagen.jpg';
```

Al igual que los operadores de comparación (20 == ‘20’ → true) esto solo comparaba el valor pero con tres iguales era un comparador estricto (20 === ‘20’ → false) para habilitar el modo estricto basta con escribir “use strict” al inicio del documento.

```jsx
"use strict";

const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

producto.disponible = false;
producto.imagen = 'imagen.jpg';

console.log(producto);
```

El modo estricto va a exigir que cumplas ciertas reglas a la hora de escribir tu código de JavaScript y ya que lo habilitamos tenemos acceso a una serie de métodos u Object Methods. Para prevenir que un objeto sea modificado se utiliza un método llamado freeze

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

Object.freeze(producto);
```

Esto no permitirá modificar, eliminar o agregar propiedades al objeto si quisiéramos hacerlo tendríamos que crear un duplicado de ese objeto. Para saber si un objeto esta congelado debemos escribir `console.log(Object.isFreeze(producto));` y te mostrara true o false.