# String Methods - Includes y Length

Estaremos viendo lo que son los métodos para cadenas de texto, por ejemplo si quieres enviar un tweet tienes que restringir tu comentarios a 100 caracteres por decir un numero, cómo saben ellos cuantas letras tiene mi tweet? Eso se logra por un método de los strings, con JavaScript podemos utilizar .length

```jsx
const producto = 'Monitor 20"';

console.log(producto.length);
```

De esa forma sabemos cuantos caracteres tiene un string.

Cuando buscas en Amazon y quieres buscar un monitor, un teléfono pues le pones en la barra de búsqueda teléfono o case o celular, etc. Eso lo puedes hacer con algo llamado index of.

```jsx
console.log(producto.indexOf('Monitor'));
```

![Untitled](../../img/strings(3).png.png)

Nos arroja un cero esto quiere decir que la palabra Monitor se encuentra en la posición 0, si pusiéramos 20 nos arrojaría 8. Si escribiera Tablet me lanzaría un -1 ósea que no existe.

Existe otra manera más util que IndexOf se llama includes, el cual nos arroja un true si se encuentra o un false si no, algo importante es que ambos son estrictos si Monitor lo buscas con minúsculas te mostrara false.

```jsx
console.log(producto.includes('Monitor'));
```

A todo esto se le conoce como métodos, te preguntaras porque length no lleva paréntesis mientras que IndexOf e includes si, es porque length es de los poco métodos que no tienen paréntesis y es mas que nada porque es una propiedad.