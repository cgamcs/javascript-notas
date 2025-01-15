# Crear Arrays

Para lo que sirven los arreglos, es para agrupar elementos del mismo tipo, cuando vas empezando es muy común  confundir los arreglos con los objetos, podemos ver que un arreglo agrupa elementos (en plural) mientras que un objeto va a hacer una variable que va agrupar la información de un elemento de un objeto, un arreglo va a atener multiples elementos que sean iguales.

**Ejemplos de uso:** Carrito de compras, likes o comentarios de Facebook.

Vamos a empezar con el código para ver los detalles de un arreglo.

```jsx
const numeros = [ 10, 20, 30, 40, 50 ];
```

![arreglos](../../img/arreglos(1).png)

Los arreglos utilizan algo que se conoce como indices y los arreglos inician en 0, en algunos lenguajes inician en 0 y en realidad no es lo común pero JavaScript no es uno de esos lenguajes.

Con este ejemplo podemos ver como se estructura un arreglo y en realidad no es necesario que sean datos relacionados, se pueden crear arreglos con todo tipo de dato, por ejemplo:

```jsx
const deTodo = [ "Hola", 10, true, "si", null, { nombre: 'Juan', trabajo: 'Programador' } ];
```

![arreglos](../../img/arreglos(2).png)

Como duda no solo podemos tener objetos dentro de nuestro arreglo, también podemos tener otros arreglos dentro de nuestro arreglo