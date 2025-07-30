### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `document` (Objeto del DOM)

---

### 📖 Descripción Técnica

El **DOM (Document Object Model)** es una representación estructurada del documento HTML que permite a JavaScript acceder y manipular su contenido, estructura y estilo.
El objeto `document` es la puerta de entrada principal para interactuar con el DOM desde JavaScript.

Este código explora varias propiedades del objeto `document` para familiarizarse con la estructura básica del DOM.

---

### 🧾 Sintaxis Básica

```javascript
document.propiedad
```

---

### 🔠 Parámetros

No se requieren parámetros al acceder a propiedades del objeto `document`.

---

### 🔁 Valor de Retorno

Cada propiedad devuelve un tipo de dato diferente dependiendo del contenido solicitado:

| Propiedad                     | Tipo de dato devuelto                  |
| ----------------------------- | -------------------------------------- |
| `document`                    | `Document`                             |
| `document.head` / `.body`     | `HTMLElement`                          |
| `document.domain`             | `string`                               |
| `document.forms`              | `HTMLFormElement[]` (HTMLCollection)   |
| `document.forms[0]`           | `HTMLFormElement`                      |
| `document.forms[0].id`        | `string`                               |
| `document.forms[0].method`    | `string` (e.g., `"get"` o `"post"`)    |
| `document.forms[0].classList` | `DOMTokenList`                         |
| `document.forms[0].action`    | `string` (URL del action)              |
| `document.links`              | `HTMLAnchorElement[]` (HTMLCollection) |
| `document.links[4].classList` | `DOMTokenList`                         |
| `document.links[4].className` | `string`                               |
| `document.images`             | `HTMLImageElement[]` (HTMLCollection)  |
| `document.scripts`            | `HTMLScriptElement[]` (HTMLCollection) |

---

### 💻 Ejemplo de Código

```javascript
let elemento;

elemento = document;                      // Documento completo
elemento = document.head;                 // <head>
elemento = document.body;                 // <body>
elemento = document.domain;               // Dominio actual (ej. localhost)
elemento = document.forms;                // Todos los formularios
elemento = document.forms[0];             // Primer formulario
elemento = document.forms[0].id;          // ID del formulario
elemento = document.forms[0].method;      // Método (GET o POST)
elemento = document.forms[0].classList;   // Lista de clases CSS
elemento = document.forms[0].action;      // URL de envío

elemento = document.links;                // Todos los enlaces <a>
elemento = document.links[4].classList;   // Lista de clases del 5º enlace
elemento = document.links[4].className;   // Clases como string

elemento = document.images;               // Todas las imágenes
elemento = document.scripts;              // Todos los scripts

console.log(elemento);                    // Visualizar en consola
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usar `console.log()` ayuda a inspeccionar la estructura del DOM durante el desarrollo.
* La mayoría de estas colecciones (como `forms`, `links`, `images`) devuelven un **HTMLCollection**, que es una lista en vivo (se actualiza automáticamente si cambia el DOM).
* Para mayor compatibilidad, se recomienda acceder a elementos usando `document.querySelector` o `getElementById` en lugar de índices directos como `document.forms[0]`.