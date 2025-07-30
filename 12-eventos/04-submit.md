### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: `addEventListener('submit', callback)`, `preventDefault()`

---

### 📖 Descripción Técnica

El evento `submit` se activa cuando se intenta enviar un formulario.
Este evento permite **interceptar el envío** para validar datos o ejecutar lógica personalizada antes de enviarlo al servidor.

Usando `e.preventDefault()`, se evita que el formulario recargue la página o envíe datos automáticamente, permitiendo una validación manual o un envío asíncrono (por ejemplo, con `fetch` o `AJAX`).

---

### 🧾 Sintaxis

```javascript
form.addEventListener('submit', function(e) {
  e.preventDefault();
  // lógica personalizada
});
```

---

### 🔠 Parámetros

| Parámetro | Tipo  | Descripción                                                                                        |
| --------- | ----- | -------------------------------------------------------------------------------------------------- |
| `e`       | Event | Objeto del evento `submit`, contiene datos del formulario y métodos útiles como `preventDefault()` |

---

### 🔁 Valor de Retorno

No devuelve nada. Ejecuta la función cuando el formulario intenta enviarse.

---

### 💻 Ejemplo de Código

```javascript
const formulario = document.querySelector('#formulario');

formulario.addEventListener('submit', validarFormulario);

function validarFormulario(e) {
    e.preventDefault(); // Detiene el envío automático del formulario

    console.log('Buscando...');

    console.log(e.target.action); // Muestra la URL definida en el atributo action del <form>
}
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Siempre usa `e.preventDefault()` al validar manualmente formularios, para evitar el comportamiento por defecto.
* Puedes acceder a los campos del formulario con `e.target.elements['nombre']` o usando `querySelector` dentro de `formulario`.
* Para validaciones personalizadas, combina este evento con validaciones de campos (`input`, `blur`, etc.).
* Si usas JavaScript para enviar el formulario (por ejemplo, con `fetch`), este evento es el punto de partida ideal.