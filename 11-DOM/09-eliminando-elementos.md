### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `.remove()`, `.removeChild()`

---

### 📖 Descripción Técnica

JavaScript permite **eliminar elementos del DOM** de forma directa con el método `.remove()`, o bien eliminarlos desde su elemento padre con `.removeChild()`.

* `.remove()` elimina el elemento directamente desde sí mismo.
* `.removeChild()` requiere acceder al **elemento padre**, y pasarle el hijo que se quiere eliminar.

---

### 🧾 Sintaxis

```javascript
elemento.remove();
padre.removeChild(hijo);
```

---

### 🔠 Parámetros

| Método           | Parámetro     | Descripción                               |
| ---------------- | ------------- | ----------------------------------------- |
| `.remove()`      | Ninguno       | Elimina el propio elemento                |
| `.removeChild()` | `hijo` (Nodo) | Nodo hijo que se desea eliminar del padre |

---

### 🔁 Valor de Retorno

* `.remove()` → No devuelve nada.
* `.removeChild()` → Devuelve el nodo eliminado.

---

### 💻 Ejemplo de Código

```javascript
const primerEnlace = document.querySelector('a');
primerEnlace.remove(); // Elimina el primer <a> del DOM

// Eliminar desde el padre
const navegacion = document.querySelector('.navegacion');

console.log(navegacion.children); // Lista de hijos antes de eliminar

navegacion.removeChild(navegacion.children[2]); // Elimina el tercer hijo de ".navegacion"
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Usar `.remove()` es más directo, pero **no funciona en navegadores antiguos** como IE11.

* Usar `.removeChild()` garantiza mayor compatibilidad, aunque requiere acceder al padre.

* Puedes almacenar el hijo en una variable antes de eliminarlo si necesitas reutilizarlo o referenciarlo:

  ```javascript
  const enlace = navegacion.children[2];
  navegacion.removeChild(enlace);
  ```

* Antes de eliminar, puedes verificar que el nodo exista:

  ```javascript
  if (navegacion.children.length > 2) {
    navegacion.removeChild(navegacion.children[2]);
  }
  ```