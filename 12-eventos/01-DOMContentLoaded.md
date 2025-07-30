### 🧠 Tema Principal: Eventos del DOM

### 📌 Módulo/Función Específica: `document.addEventListener('DOMContentLoaded', ...)`

---

### 📖 Descripción Técnica

El evento `DOMContentLoaded` se dispara cuando el **documento HTML ha sido completamente cargado y analizado**, sin esperar a que se carguen hojas de estilo, imágenes u otros recursos externos.

Es ideal para ejecutar scripts **tan pronto como el DOM esté disponible**, lo cual evita errores por tratar de acceder a elementos que aún no existen.

---

### 🧾 Sintaxis

```javascript
document.addEventListener('DOMContentLoaded', () => {
  // Código que se ejecuta cuando el DOM está listo
});
```

---

### 🔁 Valor de Retorno

Este método **no retorna nada**. Ejecuta la función proporcionada cuando se dispara el evento.

---

### 💻 Ejemplo de Código

```javascript
console.log(1);

document.addEventListener('DOMContentLoaded', () => {
    console.log(2); // Se ejecuta cuando el DOM está cargado
});

console.log(3);
```

#### 🖨️ Resultado en consola:

```
1
3
2
```

Esto demuestra que el navegador **no detiene la ejecución del script**, pero pospone la función del evento hasta que el DOM esté completamente construido.

---

### 📝 Notas Adicionales / Mejores Prácticas

* `DOMContentLoaded` es más rápido que `window.onload`, ya que este último espera a que **todos los recursos (imágenes, CSS, etc.) estén cargados**.
* Este evento es útil para iniciar scripts que interactúan con el DOM sin necesidad de colocar el `<script>` al final del `<body>`.
* Si ya usas módulos ES6 con `type="module"` o frameworks modernos (React, Vue, etc.), es común que el DOM esté listo automáticamente antes de ejecutar tus scripts.