### 🧠 Tema Principal: Manipulación del DOM + Eventos

### 📌 Módulo/Función Específica: `addEventListener()`, `classList.contains()`, `classList.add()`, `classList.remove()`, `textContent`

---

### 📖 Descripción Técnica

Este ejemplo muestra cómo crear un comportamiento **interactivo y dinámico** en la página usando JavaScript.
Un botón flotante (`.btn-flotante`) controla la visibilidad de un pie de página (`.footer`) al alternar clases y contenido de texto mediante un **evento `click`**.

Se utilizan:

* `addEventListener()` para escuchar eventos.
* `classList.contains()`, `.add()` y `.remove()` para verificar y modificar clases.
* `textContent` para cambiar dinámicamente el texto del botón.

---

### 🧾 Sintaxis Clave

```javascript
elemento.addEventListener('evento', funcion)
elemento.classList.contains('clase')
elemento.classList.add('clase')
elemento.classList.remove('clase')
elemento.textContent = 'nuevo texto'
```

---

### 💻 Ejemplo de Código

```javascript
const btnFlotante = document.querySelector('.btn-flotante');
const footer = document.querySelector('.footer');

btnFlotante.addEventListener('click', () => {
    if (footer.classList.contains('activo')) {
        // Si el footer está activo, lo ocultamos
        footer.classList.remove('activo');
        btnFlotante.classList.remove('activo');
        btnFlotante.textContent = 'Idioma y Moneda';
    } else {
        // Si el footer está oculto, lo mostramos
        footer.classList.add('activo');
        btnFlotante.classList.add('activo');
        btnFlotante.textContent = 'Cerrar';
    }
});
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Este patrón es útil para **mostrar/ocultar elementos** como menús, modales o tooltips.
* Cambiar la clase `"activo"` permite aplicar o quitar estilos CSS como `display: none`, `opacity`, `transform`, etc.
* Cambiar el `textContent` del botón mejora la experiencia del usuario al reflejar el estado actual.
* Puedes encapsular este comportamiento en una función reutilizable para otros elementos interactivos.

---

### 🧪 Posible Extensión

Este ejemplo puede evolucionar para:

* Agregar animaciones al `footer` usando CSS (`transition`, `transform`).
* Guardar el estado (abierto o cerrado) en `localStorage`.
* Accesibilidad: cambiar `aria-expanded`, usar `role="button"`, etc.