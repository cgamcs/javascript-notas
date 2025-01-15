# Como Acceder a los valores de un objeto

Teniendo el siguiente ejemplo de un objeto, vamos a querer acceder al nombre. Para acceder a los valores de un producto debemos usar algo llamado la **sintaxis de punto**.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

console.log(producto.nombre);
```

![objetos](../../img/objetos(1).png)

Existe una segunda forma que no es tan común pero en algunos casos llega a ser muy util, que es utilizando corchetes.

```jsx
console.log(producto['nombre']);
```