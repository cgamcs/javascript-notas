# Break & continue en un forLoop

Se utilizan tanto en entrevistas de trabajo como en la vida diaria. Break funciona para detener un forLoop. Por ejemplo si nos piden crear un for loop que se deje de ejecutarse en x numero.

```Javascript
for(let i = 1; i < 10; i++) {
    if(i === 5) {
        console.log(`Es el numero: ${i}`)
        break
    }

    console.log(`Numero: ${i}`)
}

/*
    // Resultado:
    // Numero: 1
    // Numero: 2
    // Numero: 3
    // Numero: 4
    // Es el numero: 5
*/
```

Continue funciona para cumplir con una condicion pero seguir ejecutando el codigo, es decir la condicion o codigo que este antes de ese continue se va a ejecutar pero cuando se cumpla la condicion todo el codigo despues de ese continue no se ejecutara.

```Javascript
for(let i = 1; i < 10; i++) {
    if(i === 5) {
        console.log('CINCO')
        continue
    }

    console.log(`Numero: ${i}`)
}

/*
    // Resultado:
    // Numero: 1
    // Numero: 2
    // Numero: 3
    // Numero: 4
    // CINCO
    // Numero: 6
    // Numero: 7
    // Numero: 8
    // Numero: 9
    // Numero: 10
*/
```

**EJEMPLO:**

Caso donde se le quiere informar al comprador que un producto de su carrito de compras tiene un descuento.

```Javascript
const carrito = [
    {nombre: 'Monitor 24"', precio: 800},
    {nombre: 'Teclado', precio: 200},
    {nombre: 'Audifonos', precio: 150, descuento: true},
    {nombre: 'Microfono', precio: 500},
    {nombre: 'Mouse', precio: 60},
    {nombre: 'Stand', precio: 70}
]

for(let i = 0; i < carrito.length; i++){
    if(carrito[i].descuento) {
        console.log(`El producto ${carrito[i].nombre} tiene descuento`)
    }

    console.log(carrito[i].nombre)
}
```