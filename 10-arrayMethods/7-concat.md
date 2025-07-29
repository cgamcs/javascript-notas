# Métodos para unir arreglos en JavaScript: `.concat()` y Spread Operator
En JavaScript, existen diferentes formas de combinar arreglos. Dos de las más utilizadas son el método .concat() y el operador de propagación (spread operator ...). Ambas permiten unir múltiples arreglos y elementos en uno solo.

## Método `.concat()`
```javascript
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio'];
const meses2 = ['Agosto', 'Septiembre'];
const meses3 = ['Octubre', 'Noviembre', 'Diciembre'];

// Concatenar arreglos (.concat)
const resultado = meses.concat(meses2, meses3, 'Otro mes');

console.log(resultado);
```

## Explicación
El método `.concat()` se utiliza para unir dos o más arreglos. No modifica los arreglos originales, sino que devuelve uno nuevo.
En este ejemplo:

- `meses.concat(meses2, meses3, 'Otro mes')` une los tres arreglos más el string 'Otro mes'.
- El resultado es un nuevo arreglo con todos los elementos en el orden que fueron pasados:

```js
[
  'Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio',
  'Agosto', 'Septiembre',
  'Octubre', 'Noviembre', 'Diciembre',
  'Otro mes'
]
```

## Spread Operator (`...`)
```javascript
const resultado2 = [...meses, ...meses2, ...meses3, 'Otro mes'];

console.log(resultado2);
```

## Explicación
El spread operator (`...`) permite expandir los elementos de un arreglo dentro de otro. Es una forma moderna y flexible de combinar arreglos o agregar nuevos elementos.

- `...meses` toma cada elemento del arreglo `meses` y lo "esparce" dentro del nuevo arreglo.
- Se puede usar con cuantos arreglos y elementos individuales se necesiten.

El resultado es exactamente igual al del método `.concat()`, pero con una sintaxis más moderna y clara:

```js
[
  'Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo', 'Junio', 'Julio',
  'Agosto', 'Septiembre',
  'Octubre', 'Noviembre', 'Diciembre',
  'Otro mes'
]
```

¿Cuál debería usar?
- Usa `.concat()` si prefieres un enfoque clásico o trabajas en entornos donde no se permite el uso de ES6.
- Usa el spread operator si quieres una sintaxis más limpia, moderna y compatible con otros patrones como la copia de arreglos.
