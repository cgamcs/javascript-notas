# Buenas practicas a la hora de evaluar un Booleano

Este simple código puede hacer que no te contraten porque representa la forma en que escribes código. No es necesario agregar el true en el if ya que tienes como valor true la variable autenticado asi que si solo escribes autenticado ya estas dejando como explicito que es true.

```jsx
// Incorrecto
const autenticado = true;

if(autenticado === true) {
    console.log('Si puedes ver Netflix');
} else {
    console.log('No no puedes ver Netflix');
}

//  Correcto
const autenticado = true;

if(autenticado) {
    console.log('Si puedes ver Netflix');
} else {
    console.log('No no puedes ver Netflix');
}
```

E incluso para este ejemplo tenemos código mas simple conocido como operador ternario.

```jsx
console.log( autenticado ? 'Si esta autenticado' : 'No esta autenticado');
```