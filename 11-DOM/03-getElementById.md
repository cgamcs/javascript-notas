### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `document.getElementById()`

---

### 📖 Descripción Técnica

`getElementById()` es un método del objeto `document` que permite seleccionar **un único elemento** del DOM que tenga el atributo `id` especificado.
Es uno de los métodos más rápidos y directos para acceder a un elemento del DOM.

---

### 🧾 Sintaxis

```javascript
document.getElementById(id)
```

---

### 🔠 Parámetros

| Parámetro | Tipo   | Descripción                                  |
| --------- | ------ | -------------------------------------------- |
| `id`      | String | El valor del atributo `id` del elemento HTML |

> *Importante:* El valor debe coincidir exactamente con el `id` (sin `#` como en CSS).

---

### 🔁 Valor de Retorno

Devuelve un único objeto `HTMLElement` si se encuentra el elemento.
Si **no existe** ningún elemento con ese `id`, devuelve `null`.

---

### 💻 Ejemplo de Código

```javascript
const formulario = document.getElementById('formulario');
console.log(formulario); // Muestra el elemento con id="formulario"

const NoExiste = document.getElementById('NoExiste');
console.log(NoExiste); // Devuelve null si no existe ese ID
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* El atributo `id` debe ser **único** dentro del documento HTML.
* Es más rápido que otros selectores como `querySelector('#id')`, pero menos flexible si necesitas lógica más compleja.
* Antes de manipular un elemento, siempre es buena práctica verificar si existe:

  ```javascript
  const el = document.getElementById('formulario');
  if (el) {
    // El elemento existe, se puede manipular
    el.style.backgroundColor = 'lightblue';
  }
  ```