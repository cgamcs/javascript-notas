# Objetos dentro de Objetos

Veamos como crear objetos dentro de otro objeto. Es tan sencillo como abrir un nuevo objeto dentro del objeto que ya tenias escrito.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true,
    informacion : {
        peso : '1kg',
        medida : '1m'
    }
}
```

Y para llegar a él mediante la sintaxis de punto es igual.

```jsx
console.log(producto.informacion);
```

![objetos](../../img/objetos(2).png)

Y al final un objeto puede ser tan complejo como uno lo necesite.

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
```

```jsx
console.log(producto);
console.log(producto.informacion.medidas.altura);
console.log(producto.informacion.peso);
console.log(producto.informacion.fabricacion);
```

![objetos](../../img/objetos(3).png)