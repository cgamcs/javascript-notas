# Crear y Comparar Booleans

El tipo de dato boolean solo puede tener dos valores true o false. Colocar un boolean básicamente es un true o false porque si **comparamos** con un strings nos va a retornar **false** incluso si usamos el comparador no estricto.

```jsx
const boolean1 = true;
const boolean2 = false;
const boolean3 = "true";

console.log(boolean1); // true
console.log(boolean2); // false

console.log(boolean1 == boolean3); // false
```

Existe otra forma de construir un boolean con los new como vimos anteriormente pero eso no lo crea en un booleano lo que va a ser sera un objeto porque este tipo de constructores usualmente crean objeto no el valor primitivo.

```jsx
const boolean4 = new Boolean(true);
```