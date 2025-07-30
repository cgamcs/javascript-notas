### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: `window.addEventListener('scroll')`, `getBoundingClientRect()`

---

### 📖 Descripción Técnica

El evento `scroll` se dispara **cada vez que el usuario hace scroll** en la ventana del navegador.
Es útil para detectar cuándo un elemento se vuelve visible, cargar contenido perezosamente (lazy loading), o aplicar animaciones al entrar en pantalla.

En este ejemplo, se usa `getBoundingClientRect()` para conocer la posición de un elemento (`.premium`) respecto a la ventana actual del navegador.

---

### 🧾 Sintaxis

```javascript
window.addEventListener('scroll', () => {
  // lógica personalizada
});

element.getBoundingClientRect();
```

---

### 🔠 Parámetros

| Método                            | Descripción                                                       |
| --------------------------------- | ----------------------------------------------------------------- |
| `window.addEventListener()`       | Escucha el evento de scroll en toda la ventana                    |
| `element.getBoundingClientRect()` | Devuelve un objeto con las posiciones del elemento en el viewport |

---

### 🔁 Valor de Retorno

* `getBoundingClientRect()` devuelve un objeto con propiedades como `.top`, `.left`, `.right`, `.bottom`, que indican la posición del elemento relativo a la ventana visible.

---

### 💻 Ejemplo de Código

```javascript
window.addEventListener('scroll', () => {
    const premium = document.querySelector('.premium');
    const ubicacion = premium.getBoundingClientRect();

    if (ubicacion.top < 978) {
        console.log('Ya está visible');
    } else {
        console.log('Aún no, da más scroll');
    }
});
```

---

### 📋 ¿Qué hace este código?

* Cada vez que haces scroll, calcula qué tan cerca está el elemento `.premium` del **borde superior de la pantalla**.
* Si su propiedad `.top` es menor que `978px`, se considera **visible o cercano a la vista**.

---

### 📝 Notas Adicionales / Mejores Prácticas

* Puedes ajustar el valor `978` según la altura de tu ventana o la posición donde quieras que se active el efecto.
* Para una mejor experiencia, considera **desacoplar lógica de scroll con técnicas como debounce/throttle** para evitar sobrecargar el navegador.
* También puedes usar `IntersectionObserver` como alternativa moderna para detectar visibilidad de elementos.
* Ideal para:

  * Animaciones al hacer scroll
  * Cargar imágenes bajo demanda (lazy loading)
  * Mostrar barras de progreso de lectura
  * Activar secciones fijas o menús flotantes