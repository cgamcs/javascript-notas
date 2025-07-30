### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: Propagación de eventos (`Event Bubbling`) y `e.stopPropagation()`

---

### 📖 Descripción Técnica

El **Event Bubbling** (burbujeo de eventos) es un comportamiento por defecto en JavaScript donde, al hacer clic en un elemento, el evento se **propaga desde el elemento más interno hacia los padres**.

Por ejemplo, si haces clic en `.titulo`, también se dispara el evento `click` en su contenedor `.info` y luego en `.card`, **a menos que se detenga la propagación**.

Para evitar que el evento suba en la jerarquía, se utiliza `e.stopPropagation()`.

---

### 🧾 Sintaxis

```javascript
element.addEventListener('click', function(e) {
  e.stopPropagation(); // Detiene el burbujeo
  // lógica del evento
});
```

---

### 🔁 Valor de Retorno

No retorna valor. Controla el flujo del evento a través de la jerarquía del DOM.

---

### 💻 Ejemplo de Código

```javascript
const cardDiv = document.querySelector('.card');
const infoDiv = document.querySelector('.info');
const tituloDiv = document.querySelector('.titulo');

cardDiv.addEventListener('click', e => {
    e.stopPropagation();
    console.log('Diste click en card');
});

infoDiv.addEventListener('click', e => {
    e.stopPropagation();
    console.log('Diste click en info');
});

tituloDiv.addEventListener('click', e => {
    e.stopPropagation();
    console.log('Diste click en titulo');
});
```

---

### 🧪 ¿Qué pasa si haces clic en `.titulo`?

1. Sin `stopPropagation()`: se ejecutan los 3 eventos en orden: `titulo`, luego `info`, luego `card`.
2. Con `stopPropagation()` (como en el código): **solo se ejecuta el evento en `.titulo`** y no se propaga a sus padres.

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usa `e.stopPropagation()` cuando **quieras evitar efectos secundarios** en elementos padres.
* Ideal para prevenir conflictos cuando diferentes niveles tienen comportamientos distintos.
* También puedes usar `e.stopImmediatePropagation()` si hay **múltiples listeners en el mismo elemento** y quieres detener todos.
* Si usas **delegación de eventos**, evita usar `stopPropagation()` innecesariamente, ya que puede interferir con el manejo global.