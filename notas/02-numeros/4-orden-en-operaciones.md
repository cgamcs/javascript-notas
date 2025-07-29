# El Orden de las Operaciones

Estaremos viendo el orden en el que se ejecutan las operaciones, y que de hecho es el mismo al de la escuela, es decir, multiplicaciones y divisiones se ejecutan primero, sumas y restas se ejecutan después. Ejemplo si tenemos `resultado = 20 + 30 * 2` daría como resultado 80 primero se multiplica y después se suma, pero que tendríamos que hacer si queremos que primero se sume, pues al igual que en la escuela llevaría un paréntesis la suma, `resultado = (20 + 30) * 2` y eso nos daría como resultado 100.

```jsx
resultado = 20 + 30 * 2;

resultado = (20 + 30) * 2;

// 20% de descuento
resultado = (20 + 30 + 40 + 50 + 60) * .2;

// Total con impuestos
resultado = (20 + 30) * 1.16;
```

Aquí tenemos el ejemplo de un descuento y de una compra agregando impuestos.