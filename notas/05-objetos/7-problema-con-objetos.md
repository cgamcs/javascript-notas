# El Problema con los Objetos

Como los objetos están hechos como una variable constante no podemos editarlos es decir no podemos escribir lo siguiente.

```jsx
const producto2 = 'Monitor';
producto2 = 'Tablet';
```

Esto nos va a marcar error, lo que si podemos hacer es editar sus propiedades, ya que al ser una variable pero que esta hecha un objeto si podemos editar, agregar o eliminar propiedades.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

producto.nombre = 'iPad 11 Pulgadas'

console.log(producto);
```

![objetos](../../img/objetos(5).png)