### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: Prevención de propagación en contenido dinámico + `onclick`, `stopPropagation()`

---

### 📖 Descripción Técnica

Cuando se crean elementos dinámicamente (como con `createElement`), sus eventos también pueden **propagarse hacia elementos padres** debido al **Event Bubbling**.

Para **evitar que el clic en un hijo dispare eventos en sus contenedores**, se usa `event.stopPropagation()` dentro del manejador del evento.

En este caso, el párrafo con clase `precio` tiene un evento `onclick`, pero si estuvieras usando delegación o un `addEventListener` en el contenedor, el clic también se propagaría.

---

### 🧾 Sintaxis

```javascript
element.onclick = (event) => {
  event.stopPropagation();
  // lógica específica
};
```

> Si no usas `event` y no detienes la propagación, el clic subirá y podrá activar otros listeners en elementos padres.

---

### 💻 Ejemplo de Código

```javascript
const parrafo3 = document.createElement('p');
parrafo3.textContent = '$800 por persona';
parrafo3.classList.add('precio');
parrafo3.onclick = (event) => {
    event.stopPropagation(); // 🚫 Detiene el bubbling
    nuevaFuncion(1);
};

function nuevaFuncion(id){
    console.log('click en el parrafo', id);
}
```

🔁 También se crean elementos como `.info`, la imagen, y el `.contenedorCard`, que se insertan en un contenedor:

```javascript
const contenedor = document.querySelector('.hacer .contenedor-cards');
contenedor.appendChild(contenedorCard);
```

---

### 📋 ¿Qué sucede?

* Al hacer clic en el `<p class="precio">`, se ejecuta `nuevaFuncion(1)` y **no se propaga** el evento.
* Si hay un `click` en `contenedorCard` o `.contenedor-cards`, no se activa a menos que no detengas el bubbling.
* Si quitaras `stopPropagation`, el evento **subiría** a cualquier contenedor que esté escuchando `click`.

---

### 📝 Notas Adicionales / Mejores Prácticas

* Siempre usa `event.stopPropagation()` cuando un elemento hijo **tiene comportamiento exclusivo** y no quieres que el evento dispare lógica en los padres.

* Si estás usando `addEventListener`, recuerda que debes capturar el evento como parámetro:

  ```js
  elemento.addEventListener('click', function(e) {
    e.stopPropagation();
  });
  ```

* Es especialmente útil cuando combinas **delegación de eventos** con **elementos creados dinámicamente**.