### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulos/Funciones Específicas: `.style`, `.classList.add()`, `.classList.remove()`

---

### 📖 Descripción Técnica

JavaScript permite modificar los estilos CSS de los elementos del DOM de dos formas principales:

1. **Estilo en línea** con la propiedad `.style` (afecta directamente al atributo `style` del elemento).
2. **Clases CSS** mediante el objeto `.classList`, que permite agregar, quitar o alternar clases definidas en tu hoja de estilos.

---

### 🧾 Sintaxis

```javascript
elemento.style.propiedadCSS = valor;
elemento.classList.add('nombre-clase');
elemento.classList.remove('nombre-clase');
```

> **Nota:** Las propiedades CSS se escriben en **camelCase** (por ejemplo, `backgroundColor`, no `background-color`).

---

### 🔠 Parámetros

| Método/Propiedad      | Tipo de parámetro | Descripción                               |
| --------------------- | ----------------- | ----------------------------------------- |
| `.style.propiedad`    | String            | Nombre de la propiedad CSS (en camelCase) |
| `.classList.add()`    | String(s)         | Clase(s) que se van a agregar             |
| `.classList.remove()` | String(s)         | Clase(s) que se van a eliminar            |

---

### 🔁 Valor de Retorno

Estas operaciones **no retornan valores**, pero modifican el DOM directamente.
`console.log(card.classList)` puede usarse para ver el resultado.

---

### 💻 Ejemplo de Código

```javascript
const encabezado = document.querySelector('h1');
console.log(encabezado);

// Modificar estilos en línea
encabezado.style.backgroundColor = 'red';
encabezado.style.fontFamily = 'Arial';
encabezado.style.textTransform = 'uppercase';

const card = document.querySelector('.card');

// Agregar y quitar clases CSS
card.classList.add('nueva-clase');    // Agrega una clase
card.classList.remove('card');        // Elimina una clase existente

console.log(card.classList); // Muestra las clases actuales del elemento
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usa `.style` para cambios dinámicos puntuales o específicos.
* Prefiere `.classList` si necesitas aplicar estilos definidos en tu archivo CSS (mantiene mejor separación entre estructura y estilo).
* Puedes verificar si un elemento tiene una clase con `.classList.contains('clase')`.
* También puedes alternar una clase con `.classList.toggle('clase')`.