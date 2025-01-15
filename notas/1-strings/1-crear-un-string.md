# Crear un String

Los strings o cadenas de texto representan un **texto** que se puede **asignar a una variable** cosas como el nombre de un cliente, de un producto, de una categoría, todo eso es un texto y se representa por medio de un string, existen dos formas de crear lo que se le conoce como una **cadena de texto primitiva** y existe otra que es un poco menos común, en total serian 3.

Primero tenemos el string por comillas pueden ser simples o dobles es lo mismo eso lo convierte en u string.

```jsx
const producto = 'Monitor 20 pulgadas';

console.log(producto);
```

Existe otra manera de indicar que es un string.

```jsx
const producto2 = String('Monitor 24 pulgadas');

console.log(producto2);
```

Y la tercera forma que no es tan común es creando un **nuevo objeto** de tipo **string**.

```jsx
const producto3 = new String('Monitor de 27 pulgadas');

console.log(producto3);
```

Podemos ver que viene en string pero con cada letra tomando una posición.

![strings](../../img/strings(1).png)

Para los strings se podría decir que también existen reglas como que necesitan comillas dobles o simples al inicio y al final, es decir, no puede poner comillas dobles al inicio y al final comillas simples y viceversa, ejemplo: “Hola Mundo’. Otra es que en el ejemplo que tenemos de **Monitor de 24 pulgadas** usualmente para referirse a las pulgadas usamos comillas dobles entonces podemos escribir dentro de un string comillas dobles pero la estructura del mismo debe de ser con comillas simples, ejemplo: ‘Monitor de 24”’. Para poder usar un las comillas dobles en un string ya con comillas dobles debes de hacer algo que se le conoce como escapar las comillas y se hace con una diagonal invertida (\).

```jsx
const producto = 'Monitor 20"';
const producto = "Monitor 20\"";

console.log(producto);

// Error
const producto = "Monitor 20"";
```

![strings](../../img/strings(2).png)