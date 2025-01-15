# Destructuring de Objetos Animados

Si queremos hacer destructuring a objetos mas complejos como en el capitulo anterior debemos hacer lo siguiente.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true,
    informacion : {
        medidas : {
            altura : '12 cm',
            largo : '10 cm',
            ancho : '15 cm'
        },
        peso : '1 kg',
        fabricacion : {
            pais : 'China'
        }
    }
}

const { nombre } = producto;
```

Con este ejemplo no hay problema, pero si queremos llegar a la parte de fabricación lo que debemos hacer es lo siguiente.

```jsx
const { nombre, informacion: {fabricacion} } = producto;
```

Y su método de entrada seria este.

```jsx
console.log(nombre);
console.log(fabricacion);
```

![objetos](../../img/objetos(4).png)

### Por qué solo se entra a fabricación y no a toda la parte de información?

Esto pasa porque lo que esta dentro de las llaves es lo que crea la variable si, asi como nombre crea la variable de nombre, si tenemos `información: { fabricación }` y fabricación esta al final de la sintaxis, entonces esa es la variable que se va a crear.

```jsx
const { nombre, informacion: { fabricacion: { pais } } } = producto;

console.log(nombre);
console.log(pais);
```

Si además de país también queremos extraer la información debemos agregar una coma, y lo mismo con fabricación si es el caso.

```jsx
const { nombre, informacion, informacion: { fabricacion, fabricacion: { pais } } } = producto;

console.log(nombre);
console.log(informacion);
console.log(fabricacion);
console.log(pais);
```