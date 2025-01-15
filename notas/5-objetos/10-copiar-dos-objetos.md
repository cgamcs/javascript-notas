# Copiar 2 Objetos

Una forma de unir dos objetos es usando algo que se conoce com **assign**, tenemos que darle ambos objetos.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true
}

const medidas = {
    peso: '1kg',
    medida: '1m'
}

const resultado = Object.assign(producto, medidas);
```

Existe otra forma llamada **spread operator** o **rest operator** que además es la mas conocida y mas usada.

```jsx
const resultado = { ...producto, ...medidas };
```