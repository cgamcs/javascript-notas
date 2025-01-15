# Object .keys, .values y .entries

Vamos a estar viendo 3 métodos para objetos uno llamado **keys**, otro **values** y otro llamado **entries**, primero veremos keys.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

console.log(Object.keys(producto));
```

Lo que keys nos devuelve es el nombre, precio y disponible. Asi es como podemos entrar a las llaves de un objeto con .keys **muchas veces** se utiliza para ver si un objeto esta **vacío**. Por ejemplo para saber si la consulta en la base de datos de un cliente fue exitosa o no lo puedes hacer con `Object.keys` para saber si el objeto tiene o no información.

![objetos](../../img/objetos(10).png)

Ahora pasaremos a values, si `Object.keys` te retorna la parte izquierda del objeto que son las llaves, `Object.values` te regresara la parte derecha del objeto que son los valores.

![objetos](../../img/objetos(11).png)

Existe otro que se llama `Object.entries`, si .keys te retorna las llaves, .values te retorna los valores, lo que hace entries es que te retorna todo en pares, es decir, primero nombre y su nombre, precio y su precio, disponible y su valor.

![objetos](../../img/objetos(12).png)