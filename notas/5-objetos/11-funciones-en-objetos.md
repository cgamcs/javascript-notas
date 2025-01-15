# Funciones en Objetos y acceder a sus valores

Habíamos visto anterior mente a utilizar las comillas de apertura (``) para poder utilizar variables dentro de un string.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true,
    mostrarInfo: function() {
        console.log(`El producto: ${nombre} tiene un predio de ${precio}`)
    }
}
```

![objetos](../../img/objetos(6).png)

Podemos ver que nos marca un error diciéndonos que nombre no esta definido, pero si agregamos las variables fuera del objeto nos muestra lo siguiente.

```jsx
const nombre = 'hola';

const precio = 20;

const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true,
    mostrarInfo: function() {
        console.log(`El producto: ${nombre} tiene un predio de ${precio}`)
    }
}

```

![objetos](../../img/objetos(7).png)

Para que no suceda esto debemos usar **this** para poder buscar la propiedad que queremos dentro del mismo objeto. **This** es una forma de referirse al objeto en si mismo porque un objeto puede tener multiple información.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true,
    mostrarInfo: function() {
        console.log(`El producto: ${this.nombre} tiene un predio de ${this.precio}`)
    }
}

```

![objetos](../../img/objetos(8).png)