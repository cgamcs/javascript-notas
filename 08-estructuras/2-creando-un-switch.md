# Creando un Switch

Los switch nos sirven para revisar multiples casos un poco parecido a los if pero mas simples de leer, en este ejemplo vamos a revisar con que metodo de pago se va a comprar un producto.

```Javascript
const meotodPago = 'efectivo'

switch(meotodPago) {
     case 'efectivo':
        console.log(`Pagaste con ${meotodPago}`);
        break;
    default:
        console.log('Aun no has seleccionado un metodo de pago o metodo de pago no soportado');
        break;
}
```

Esta es la sintaxis de un switch, primero toma una condicion en este caso metodo de pago, luego el caso que debe cumplir segun la condicion, por ultimo y que es obligatorio en los switches es el **default** vendria siendo com un else, se ejecuta si ninguna de las condiciones anteriores se cumple.

Podemos agregar mas casos pero es importante que lleven la misma sintaxis: cas -> nombre -> ejecucion -> break

```Javascript
const meotodPago = 'cheque'

switch(meotodPago) {
     case 'efectivo':
        console.log(`Pagaste con ${meotodPago}`);
        break;
    case 'cheque':
        console.log(`Pagaste con ${meotodPago}`);
        break;
    case 'tarjeta':
        console.log(`Pagaste con ${meotodPago}`);
        break;
    default:
        console.log('Aun no has seleccionado un metodo de pago o metodo de pago no soportado');
        break;
}
```