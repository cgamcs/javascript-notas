# String Methods - Convertir a Mayúsculas o Minúsculas

Supongamos que estamos encargados de una tienda virtual y nos dicen que todos los textos estén en mayúsculas, se puede hacer en css con uppercase, pero también lo podemos hacer desde JavaScript.

```jsx
const producto = 'Monitor 20 Pulgadas';

// Lo transforma todo a mayúsculas
console.log(producto.toUpperCase());

// Lo transforma todo a minúsculas
console.log(producto.toLowerCase());
```

Esto que sentido tiene si se puede hacer desde CSS o la base de datos, bueno suponiendo que tengas un millón de registros ya no es viable cambiarlo desde la base de datos y si los textos que quieres cambiar están en distintas clases o elementos tampoco lo es, además que podrían decirte que “siempre no”.

Un ejemplo muy **practico** para usar el **toLowerCase** es cuando un usuario se registra y pone su correo todo en mayúsculas o algunas letras, por ejemplo: [CESAR@CORREO.COM](mailto:CESAR@CORREO.COM) o [Cesar@correo.com](mailto:Cesar@correo.com) con estos correos una base de datos las va a interpretar como diferentes. Entonces lo que podemos hacer es convertirlas a minúsculas **antes** de pasar el correo a la **base de datos** de la misma forma al iniciar sesión.

Otro método que podemos utilizar es para convertir **números** en **strings**.

```jsx
const precio = 300;
console.log(precio.toString());
```