# For Loop

Hablando de las estructuras vimos que estas se ejecutan si una condicion se cumple o no, en el caso de los iteradores se va a ejecutar hasta que una condicion se cumpla o se deje de cumplir.

Para crear un for loop debemos seguir la siguiente sintaxis, que consta de 3 partes:

- El primero es el inicializador, es decir, en que lugar va a empezar a contar nuestro codigo.
- La condicion que vamos a revisar, es decir, hasta donde queremos que se ejecute nuestro codigo.
- El incremento, es la forma en que el contador va a ir incrementar o restanado.

```Javascript
for(let i = 0; i < 10; i++) {
    console.log(`Este es el contador numero: ${i}`)
}

/*
    // Resultado
    Este es el contador numero: 0
    Este es el contador numero: 1
    Este es el contador numero: 2
    Este es el contador numero: 3
    Este es el contador numero: 4
    Este es el contador numero: 5
    Este es el contador numero: 6
    Este es el contador numero: 7
    Este es el contador numero: 8
    Este es el contador numero: 9
*/
```

### Ejemplos de codigo
</br>

**Ejemplo 1:**
```Javascript
for(let i = 1; i <=20; i++) {
    if(i % 2 === 0) {
        console.log(`El numero ${i} es par`)
    } else {
        console.log(`El numero ${i} es impar`)
    }
}

/*
    // Resultado
    El numero 1 es impar
    El numero 2 es par
    El numero 3 es impar
    El numero 4 es par
    El numero 5 es impar
    El numero 6 es par
    El numero 7 es impar
    El numero 8 es par
    El numero 9 es impar
    ...
*/
```
<br>

**Ejemplo 2:**
```Javascript
const carrito = [
    {nombre: 'Monitor 24"', precio: 800},
    {nombre: 'Teclado', precio: 200},
    {nombre: 'Audifonos', precio: 150},
    {nombre: 'Microfono', precio: 500},
    {nombre: 'Mouse', precio: 60},
    {nombre: 'Stand', precio: 70}
]

for(let i = 0; i <= carrito.length; i++) {
    console.log(`${carrito[i].nombre} tiene un precio de: ${carrito[i].precio}`)
}

/*
    // Resultado
    Monitor 24" tiene un precio de: 800
    Teclado tiene un precio de: 200
    Audifonos tiene un precio de: 8150
    Microfonos tiene un precio de: 500
    Mouse tiene un precio de: 60
    Stand tiene un precio de: 70
*/
```