### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `document.querySelector()`

---

### 📖 Descripción Técnica

`querySelector()` es un método del objeto `document` que permite seleccionar el **primer elemento** del DOM que coincida con un **selector CSS válido**.
A diferencia de otros métodos como `getElementById` o `getElementsByClassName`, `querySelector` permite usar selectores más específicos y combinados, igual que en una hoja de estilos.

---

### 🧾 Sintaxis

```javascript
document.querySelector(selectorCSS)
```

---

### 🔠 Parámetros

| Parámetro     | Tipo   | Descripción                                                              |
| ------------- | ------ | ------------------------------------------------------------------------ |
| `selectorCSS` | String | Cualquier selector CSS válido (clase, ID, etiqueta, combinaciones, etc.) |

---

### 🔁 Valor de Retorno

Devuelve el **primer elemento** del DOM que coincida con el selector.
Si no encuentra coincidencias, devuelve `null`.

---

### 💻 Ejemplo de Código

```javascript
const card = document.querySelector('.card');
console.log(card); // Primer elemento con clase "card"

const info = document.querySelector('.premium .info');
console.log(info); // Elemento con clase "info" dentro de un elemento con clase "premium"

const segundoCard = document.querySelector('section.hospedaje .card:nth-child(2)');
console.log(segundoCard); // Segundo ".card" dentro de una sección con clase "hospedaje"

const formulario = document.querySelector('.contenido-hero #formulario');
console.log(formulario); // ID "formulario" dentro de ".contenido-hero"

const navegacion = document.querySelector('nav');
console.log(navegacion); // Primer <nav> del documento
```

> ⚠️ Nota: En tu código original, el selector `nth-child(2` estaba incompleto. Debe cerrarse con `)`. Ya está corregido arriba.

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usa `querySelector()` cuando necesites más precisión con selectores compuestos (como jerarquías de clases o pseudoselectores).
* Para obtener **todos** los elementos que coincidan, usa `document.querySelectorAll()` (devuelve un `NodeList`).
* Puedes seleccionar por:

  * Clase: `'.clase'`
  * ID: `'#id'`
  * Etiqueta: `'div'`, `'section'`, etc.
  * Combinaciones: `'.contenedor .item'`, `'#formulario input'`, etc.