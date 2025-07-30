### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: `addEventListener()` con eventos de formularios (`input`, `keydown`, `keyup`, `blur`)

---

### 📖 Descripción Técnica

Los **eventos de entrada** permiten reaccionar a la interacción del usuario con campos de texto (`<input>`, `<textarea>`, etc.).
Estos eventos son esenciales para validaciones, formularios reactivos y experiencia de usuario en tiempo real.

---

### 🧾 Sintaxis

```javascript
input.addEventListener('evento', (e) => {
  // lógica
});
```

---

### 🔠 Eventos Comunes

| Evento    | Se activa cuando...                                                  |
| --------- | -------------------------------------------------------------------- |
| `input`   | El contenido del input cambia (por escritura, pegado, borrado, etc.) |
| `keydown` | Se presiona una tecla (antes de que aparezca el carácter)            |
| `keyup`   | Se suelta una tecla                                                  |
| `blur`    | El input pierde el foco (se hace clic fuera, por ejemplo)            |

---

### 🔁 Valor de Retorno

Los `addEventListener()` no devuelven nada. Ejecutan el callback al dispararse el evento.

---

### 💻 Ejemplo de Código

```javascript
const busqueda = document.querySelector('.busqueda');

busqueda.addEventListener('input', (e) => {
    if (e.target.value === '') {
        console.log('Fallo la validación');
    }
});
```

#### Otros eventos útiles que puedes aplicar:

```javascript
busqueda.addEventListener('keydown', () => {
    console.log('Tecla presionada');
});

busqueda.addEventListener('keyup', () => {
    console.log('Tecla liberada');
});

busqueda.addEventListener('blur', () => {
    console.log('Input perdió el foco');
});
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* El evento `input` es el más usado para **validación en tiempo real**.
* Puedes acceder al valor con `e.target.value`.
* Usa `blur` para validaciones finales antes de enviar un formulario.
* Es útil evitar validaciones agresivas con `keydown`, ya que aún no hay texto visible.
* Para limitar caracteres, prevenir acciones, o limpiar entradas, puedes complementar con `preventDefault()` o expresiones regulares.