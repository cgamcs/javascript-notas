### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: Delegación de eventos + Burbujeo (`event delegation` + `event bubbling`)

---

### 📖 Descripción Técnica

La **delegación de eventos** aprovecha el comportamiento del **Event Bubbling**, donde los eventos se propagan desde el elemento objetivo hacia los elementos padres.

En lugar de agregar un `addEventListener()` a cada elemento hijo, se añade **un solo listener al contenedor padre**, y se utiliza `e.target` para determinar en cuál hijo ocurrió el evento.

Esto es útil cuando:

* Tienes muchos elementos similares (como listas, tarjetas, botones).
* Los elementos se crean dinámicamente.
* Quieres mejor rendimiento o un solo punto de control.

---

### 🧾 Sintaxis

```javascript
padre.addEventListener('click', function(e) {
  if (e.target.matches('selector')) {
    // lógica para el hijo
  }
});
```

---

### 🔠 Parámetros Clave

| Propiedad               | Descripción                                        |
| ----------------------- | -------------------------------------------------- |
| `e.target`              | Elemento específico donde ocurrió el clic          |
| `.classList.contains()` | Verifica si el elemento tiene una clase específica |

---

### 💻 Ejemplo de Código

```javascript
const cardDiv = document.querySelector('.card');

cardDiv.addEventListener('click', e => {
    if (e.target.classList.contains('titulo')) {
        console.log('Hiciste click en titulo');
    }

    if (e.target.classList.contains('precio')) {
        console.log('Hiciste click en precio');
    }

    if (e.target.classList.contains('card')) {
        console.log('Hiciste click en card');
    }
});
```

---

### 📋 ¿Qué hace este código?

* Agrega un **único listener** al contenedor `.card`.
* Cuando se hace clic en un elemento hijo, el evento sube (bubbling).
* Se evalúa qué clase tiene el `e.target` para ejecutar la lógica correspondiente:

  * Si hiciste clic en `.titulo`, imprime: `"Hiciste click en titulo"`.
  * Si hiciste clic en `.precio`, imprime: `"Hiciste click en precio"`.
  * Si hiciste clic en el mismo `.card`, imprime: `"Hiciste click en card"`.

---

### 📝 Notas Adicionales / Mejores Prácticas

* Puedes usar `e.target.matches('selector')` como alternativa más flexible.
* Ideal para **listas dinámicas**, **componentes reutilizables**, y cuando los hijos **se generan con JS**.
* También puedes combinar con atributos `data-*` para lógica más escalable:

  ```html
  <div data-tipo="titulo">Texto</div>
  ```

  ```js
  if (e.target.dataset.tipo === 'titulo') {
    console.log('Click en título');
  }
  ```