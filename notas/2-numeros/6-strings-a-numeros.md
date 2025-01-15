# Convertir Strings a Números

Veremos como convertir los siguientes strings en números. Como puedes ver “20” como tal si es un numero pero dentro de un strings.

```jsx
const numero1 = "20";
const numero2 = "20.2";
const numero3 = "Uno";
const numero4 = 20;
```

Para cambiar a numero el primer string tendremos que usar un objeto llamado Number y un método que sirve para cambiar de un numero en string a un numero es parseInt.

```jsx
console.log(Number.parseInt(numero1));
```

Este método parseInt funciona para cambiar números en string a numero pero en enteros, si queremos cambiar el numero2 que contiene decimales debemos usar parseFloat.

```jsx
console.log(Number.parseFloat(numero2));
```

Ahora para el numero 3 no es un numero como tal es una palabra para eso podemos comprobar que sea un numero entero con el método isInteger.

```jsx
console.log(Number.isInteger(numero3));
```