### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: Recorrido del DOM (`childNodes`, `children`, `parentElement`, `nextElementSibling`, etc.)

---

### 📖 Descripción Técnica

**Traversing the DOM** se refiere a navegar a través de la estructura del documento HTML desde un elemento hacia sus hijos, padres o hermanos.

JavaScript proporciona propiedades específicas del DOM para este propósito, permitiendo recorrer el árbol del documento de manera jerárquica.

---

### 🧾 Propiedades Comunes

| Propiedad                        | Descripción                                                  |
| -------------------------------- | ------------------------------------------------------------ |
| `element.childNodes`             | Lista de **todos** los nodos hijos, incluidos espacios/texto |
| `element.children`               | Lista de **elementos HTML** hijos (sin texto ni espacios)    |
| `element.firstElementChild`      | Primer hijo tipo elemento                                    |
| `element.lastElementChild`       | Último hijo tipo elemento                                    |
| `element.parentNode`             | Nodo padre                                                   |
| `element.parentElement`          | Elemento padre (específicamente un HTMLElement)              |
| `element.nextElementSibling`     | Siguiente hermano tipo elemento                              |
| `element.previousElementSibling` | Hermano anterior tipo elemento                               |

---

### 💻 Ejemplo de Código

```javascript
const navegacion = document.querySelector('nav');

console.log(navegacion);
console.log(navegacion.childNodes); // Incluye nodos de texto (espacios, saltos de línea)
console.log(navegacion.children);   // Solo elementos HTML

console.log(navegacion.children[0]);            // Primer hijo elemento
console.log(navegacion.children[0].nodeName);   // Nombre de etiqueta (ej. A, DIV, etc.)
console.log(navegacion.children[0].nodeType);   // Tipo de nodo (1 = elemento, 3 = texto)

// 🔽 Padre ➜ Hijo
const card = document.querySelector('.card');
console.log(card.children[1].children[1].textContent); // Accede a contenido interno

// Modifica contenido e imagen
card.children[1].children[1].textContent = 'Nuevo heading desde traversing th dom';
card.children[0].src = 'img/hacer2.jpg';

// 🔼 Hijo ➜ Padre
console.log(card.parentNode);                    // Nodo padre (puede incluir texto)
console.log(card.parentElement.parentElement);   // Elemento abuelo (HTMLElement)

// ➡️ Elementos hermanos
console.log(card.nextElementSibling.nextElementSibling); // Segundo hermano siguiente

const ultimoCard = document.querySelector('.card:nth-child(4)');
console.log(ultimoCard);
console.log(ultimoCard.previousElementSibling);  // Hermano anterior

// ⬅️ Primer y último hijo de navegación
console.log(navegacion.firstElementChild);
console.log(navegacion.lastElementChild);
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usa `.children` en lugar de `.childNodes` si solo necesitas elementos HTML.
* `.nodeType` devuelve:

  * `1`: Nodo tipo **elemento**
  * `3`: Nodo tipo **texto** (espacios, saltos de línea)
* Si necesitas recorrer múltiples niveles, asegúrate de validar que los nodos existen (`if (elemento)`).
* Traversing es útil para seleccionar elementos relacionados sin usar selectores complejos.