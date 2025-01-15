# Destructuring de Objetos

Veremos como acceder a los valores de un objeto y asignarlos a una variable. Para ello solo necesitaremos crear una variable y asignársela con la sintaxis de punto.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

// Forma vieja
const nombre = producto.nombre;
```

Esa era la forma anterior de hacerla, pero gracias a ECMAScript existe algo llamado **object destructuring**, es decir, extraer del objeto y crear la variable todo en un mismo paso.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

const { nombre } = producto;
```

**Destructuring** te permite eso, te permite extraer `nombre : 'Monitor 24 Pulgadas'`  con todo y el valor  y te crea la variable todo en un solo paso, lo cual te simplifica mucho el código, cuando veas esta sintaxis `const { } = variable` es un buen indicativo que es destructuring. Si queremos extraer mas propiedades podemos hacerlo desde la misma linea **mientras que** sean del mismo objeto.

```jsx
const { nombre, precio } = producto;
```