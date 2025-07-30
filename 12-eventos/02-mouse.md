### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: `addEventListener()` con eventos de mouse (`click`, `mouseenter`, `mouseout`)

---

### 📖 Descripción Técnica

JavaScript permite detectar y responder a la interacción del usuario con el mouse mediante **eventos del DOM**.
Entre los más comunes se encuentran:

* `click`: cuando se hace clic sobre un elemento.
* `mouseenter`: cuando el cursor entra en el área del elemento (sin propagarse desde hijos).
* `mouseout`: cuando el cursor sale del área del elemento.

---

### 🧾 Sintaxis

```javascript
element.addEventListener('tipoDeEvento', funcion)
```

---

### 🔠 Parámetros

| Parámetro      | Tipo     | Descripción                                                         |
| -------------- | -------- | ------------------------------------------------------------------- |
| `tipoDeEvento` | String   | Tipo de evento a escuchar (`'click'`, `'mouseenter'`, `'mouseout'`) |
| `funcion`      | Function | Función callback que se ejecuta al activarse el evento              |

---

### 🔁 Valor de Retorno

No retorna valor; simplemente **ejecuta la función** asociada al evento cuando este ocurre.

---

### 💻 Ejemplo de Código

```javascript
const nav = document.querySelector('.navegacion');

nav.addEventListener('click', () => {
    console.log('haciendo click en nav');
});

nav.addEventListener('mouseenter', () => {
    console.log('entrando a la nav');
    nav.style.backgroundColor = 'white';
});

nav.addEventListener('mouseout', () => {
    console.log('saliendo de la nav');
    nav.style.backgroundColor = 'transparent';
});
```

---

### 📋 Resultado Esperado

* Al hacer clic sobre `.navegacion` se imprime:

  ```
  haciendo click en nav
  ```
* Al pasar el mouse por encima:

  ```
  entrando a la nav
  ```

  y cambia el fondo a blanco.
* Al sacar el mouse de la navegación:

  ```
  saliendo de la nav
  ```

  y el fondo vuelve a ser transparente.

---

### 📝 Notas Adicionales / Mejores Prácticas

* `mouseenter` y `mouseout` **no se propagan** desde elementos hijos, a diferencia de `mouseover` y `mouseleave`.
* Puedes usar `e.target` y `e.currentTarget` dentro del callback para saber qué elemento fue afectado.
* Para una mejor experiencia visual, considera usar transiciones CSS al cambiar colores.
* También puedes usar eventos similares como: `dblclick`, `mousedown`, `mouseup`, `mousemove`.