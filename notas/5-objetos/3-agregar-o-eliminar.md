# Agregar o Eliminar Propiedades de un objeto

Digamos que ya tienes un objeto construido como vimos anteriormente y tiempo después quieres agregar una propiedad ya en la ejecución del proyecto.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

// Agregar nuevas propiedades al objeto
producto.imagen = 'imagen.jpg';
```

En este caso se hace afuera del objeto, se utiliza la **sintaxis de punto** y se utiliza el símbolo de igual. Ahora en dado caso si quisiéramos **eliminar una propiedad**, un ejemplo muy común es cuando desde la base de datos queremos traer un usuario y te trae todos los datos del usuario, asi que, quieres eliminar el password.

```jsx
delete producto.precio;
```