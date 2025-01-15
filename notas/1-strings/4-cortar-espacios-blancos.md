# Cortar espacios en blancos de un String

Esto lo vas a utilizar ya que a lo largo de la vida como programador existirán muchos formularios donde las personas para pasar la validación agregaran mucho espacio en blanco mientras que nosotros solo queremos los datos importantes. Podemos utilizar los siguientes métodos.

```jsx
const producto = '                   Monitor 20"                   ';

console.log(producto.trimStart());
console.log(producto.trimEnd());
```

![strings](../../img/strings(4).png.png)

Esto solo nos quitara los espacios que estén al inicio o al final pero no ambos. En JavaScript se pueden usar los métodos de forma encadenada y a eso se conoce también como chaining, colocar un método y colocar después el otro.

```jsx
console.log( producto.trimStart().trimEnd() );
```

![strings](../../img/strings(5).png.png)

Tambien podemos usar el método trim hace exactamente lo mismo elimina hacia ambas direcciones los espacios en blanco. trim Start y trim End funcionan mas que nada para cuando solo quieres eliminar hacia un lado.

```jsx
console.log( producto.trim() );
```