### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `document.querySelectorAll()`

---

### 📖 Descripción Técnica

`querySelectorAll()` es un método del objeto `document` que permite seleccionar **todos los elementos** del DOM que coincidan con un selector CSS válido.
A diferencia de `querySelector()`, que solo devuelve el **primer** elemento, `querySelectorAll()` devuelve una **lista estática (NodeList)** con **todas** las coincidencias.

---

### 🧾 Sintaxis

```javascript
document.querySelectorAll(selectorCSS)
```

---

### 🔠 Parámetros

| Parámetro     | Tipo   | Descripción                                                                |
| ------------- | ------ | -------------------------------------------------------------------------- |
| `selectorCSS` | String | Selector CSS válido (clase, ID, etiqueta, combinaciones, pseudoselectores) |

---

### 🔁 Valor de Retorno

Devuelve una **NodeList** (lista estática) de los elementos que coincidan con el selector.
Si no hay coincidencias, la NodeList estará vacía (`length === 0`).

---

### 💻 Ejemplo de Código

```javascript
const card = document.querySelectorAll('.card');
console.log(card); // NodeList con todos los elementos que tienen la clase "card"

const formulario = document.querySelectorAll('#formulario');
console.log(formulario); // NodeList con el elemento con id="formulario" (normalmente solo uno)

const noExiste = document.querySelectorAll('.no-existe');
console.log(noExiste); // NodeList vacío si la clase no existe (length = 0)
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* La **NodeList** devuelta por `querySelectorAll()` **no es un array**, pero se puede recorrer con `forEach`, o convertir con `Array.from()` si se necesita usar métodos como `map` o `filter`.

  ```javascript
  const cardsArray = Array.from(document.querySelectorAll('.card'));
  ```

* A diferencia de `getElementsByClassName`, la NodeList **no se actualiza en vivo**: si el DOM cambia después de la selección, la lista no se actualiza automáticamente.

* Útil para aplicar cambios en lote:

  ```javascript
  document.querySelectorAll('.card').forEach(card => {
    card.classList.add('resaltado');
  });
  ```