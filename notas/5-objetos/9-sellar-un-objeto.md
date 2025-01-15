# Sellar un Objeto

A diferencia de Freeze lo que hace seal es que no se pueden agregar ni eliminar propiedades pero si se puede modificar las existentes.

Si quieres saber si un objeto esta sellado debes de escribir lo siguiente:

```jsx
console.log(Object.isSeald('objeto'));
```

**ESTO SI SE PUEDE HACER**

```jsx
"use strict";

const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

Object.seal(producto);

producto.disponible = false;

console.log(producto);
```

**ESTO NO SE PUEDE HACER**

```jsx
"use strict";

const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

Object.seal(producto);

producto.imagen = 'imagen.jpg';

console.log(producto);
```

```jsx
"use strict";

const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

Object.seal(producto);

delete producto.precio;

console.log(producto);
```