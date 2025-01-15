# Mas Sobre Comparar Booleanos

Solo veremos otra manera de comparar los booleanos que seria compararlo directamente con el valor.

```jsx
const boolean1 = true;
const boolean2 = false;

console.log(boolean1 === boolean2); // false

console.log(boolean1 === true); // true

console.log(boolean1 === "true"); // false

console.log(boolean1 !== boolean2); // true
```