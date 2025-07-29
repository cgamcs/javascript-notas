# El Object Constructor

Estaremos como crear objetos de la forma que se le conoce como **object constructor**, podemos ver como nuestros objetos utilizan lo que se conoce como **object literal**, es decir, yo tengo que definir el objeto  con mi código pero podemos automatizar la creación de los objetos cuando van a ser multiples objetos.

```jsx
const producto = {
    nombre : 'Monitor 24 Pulgadas',
    precio : 300,
    disponible : true,
    mostrarInfo: function() {
        console.log(`El producto: ${this.nombre} tiene un predio de ${this.precio}`)
    }
}

const producto2 = {
    nombre : 'Monitor 27 Pulgadas',
    precio : 400,
    disponible : true,
    mostrarInfo: function() {
        console.log(`El producto: ${this.nombre} tiene un predio de ${this.precio}`)
    }
}
```

Para escribir un object constructor vamos a escribir una función, la vamos a llamar producto, como vimos anteriormente vamos a utilizar **this** ya que es una forma de referirse al objeto en si mismo, pasándole los valores de nombre y precio, la disponibilidad la dejamos igual a verdadero ya que si se esta creando un nuevo objeto es porque si hay en stock.

```jsx
function Producto(nombre, precio) {
    this.nombre = nombre;
    this.precio = precio;
    this.disponible = true; 
}
```

Para crear un nuevo objecto debemos de escribir la siguiente sintaxis.

```jsx
const producto2 = new Prodcuto(/*nombre*/, /*precio*/);

const producto2 = new Prodcuto('Samsung 24 pulgadas', 2800);
```

![objetos](../../img/objetos(9).png)

Podemos observar que tenemos disponible, nombre y precio, es por eso que es importante la palabra **this**, por que con **this** no se va a perder la referencia de los valores.