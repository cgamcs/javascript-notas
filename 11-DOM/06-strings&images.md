### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `.innerText`, `.textContent`, `.innerHTML`, `.textContent =`, `.src =`

---

### 📖 Descripción Técnica

Estas propiedades permiten **leer o modificar el contenido textual o visual** de los elementos HTML desde JavaScript:

* `.innerText`: obtiene o asigna el texto visible del elemento (respeta estilos como `visibility: hidden`).
* `.textContent`: obtiene o asigna **todo** el texto, visible o no.
* `.innerHTML`: obtiene o asigna el contenido HTML interno.
* `.textContent =` y `.innerHTML =`: permiten modificar directamente el texto o HTML del elemento.
* `.src`: permite leer o cambiar la URL de una imagen (`<img>`).

---

### 🧾 Sintaxis

```javascript
elemento.innerText
elemento.textContent
elemento.innerHTML

elemento.textContent = 'nuevo texto';
elemento.innerHTML = '<strong>nuevo HTML</strong>';

imagen.src = 'ruta/nueva-imagen.jpg';
```

---

### 🔠 Parámetros

No requieren parámetros, excepto cuando se asigna un nuevo valor.

---

### 🔁 Valor de Retorno

| Propiedad      | Valor devuelto                  |
| -------------- | ------------------------------- |
| `.innerText`   | Texto visible del elemento      |
| `.textContent` | Todo el texto, visible o no     |
| `.innerHTML`   | Texto + etiquetas HTML internas |
| `.src`         | URL actual de la imagen         |

---

### 💻 Ejemplo de Código

```javascript
const encabezado = document.querySelector('.contenido-hero h1');
console.log(encabezado);

// Leer contenido
console.log(encabezado.innerText);     // Solo texto visible
console.log(encabezado.textContent);  // Todo el texto (incluso oculto)
console.log(encabezado.innerHTML);    // Texto + etiquetas internas

// Modificar texto
const nuevoHeading = 'nuevo heading';
document.querySelector('.contenido-hero h1').textContent = nuevoHeading;

// Modificar imagen
const img = document.querySelector('.card img');
img.src = 'img/hacer2.jpg'; // Cambia la imagen mostrada
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usa `.textContent` para asegurar que obtienes todo el texto, sin importar estilos CSS.
* Si necesitas insertar etiquetas HTML dentro del texto, usa `.innerHTML` (con precaución para evitar XSS).
* Cambiar `.src` en una imagen es útil para efectos de galería, sliders, o cambios dinámicos de contenido.
* Siempre verifica que el elemento exista antes de modificarlo:

  ```javascript
  const img = document.querySelector('.card img');
  if (img) img.src = 'img/nueva-imagen.jpg';
  ```