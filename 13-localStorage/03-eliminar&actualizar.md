### 🧠 Tema Principal: Almacenamiento Web

### 📌 Módulo/Función Específica: `localStorage.removeItem()`, `localStorage.setItem()`, `localStorage.clear()`

---

### 📖 Descripción Técnica

Local Storage **no permite modificar datos directamente**; para actualizar un objeto o arreglo debes:

1. Recuperarlo con `getItem()`.
2. Convertirlo con `JSON.parse()`.
3. Modificarlo como cualquier dato de JavaScript.
4. Volverlo a guardar con `JSON.stringify()` y `setItem()`.

Para eliminar claves o limpiar todo el almacenamiento, se usan `removeItem()` y `clear()` respectivamente.

---

### 🧾 Sintaxis

```javascript
localStorage.removeItem('clave');      // Elimina una entrada específica
localStorage.clear();                  // Elimina todo el localStorage
localStorage.setItem('clave', valor);  // Sobrescribe un valor existente
```

---

### 💻 Ejemplo de Código

```javascript
// Eliminar una clave
localStorage.removeItem('nombre');

// Obtener arreglo existente
const mesesArray = JSON.parse(localStorage.getItem('meses'));
console.log(mesesArray);

// Modificar el arreglo
mesesArray.push('Junio');
console.log(mesesArray);

// Guardar el arreglo actualizado
localStorage.setItem('meses', JSON.stringify(mesesArray));

// Limpiar todo el localStorage
localStorage.clear();
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* **`removeItem('clave')`** elimina únicamente la entrada especificada.

* **`clear()`** borra **todas las claves y valores**, sin importar quién las creó.

* Si el valor a actualizar no existe (es `null`), asegúrate de inicializarlo antes de modificarlo:

  ```javascript
  let datos = JSON.parse(localStorage.getItem('misDatos')) || [];
  datos.push('nuevo valor');
  localStorage.setItem('misDatos', JSON.stringify(datos));
  ```

* Para evitar sobrescribir accidentalmente datos importantes, valida siempre lo que vas a actualizar.