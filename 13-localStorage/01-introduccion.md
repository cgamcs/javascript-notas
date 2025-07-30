### 🧠 Tema Principal: Almacenamiento Web

### 📌 Módulo/Función Específica: `localStorage.setItem()`, `JSON.stringify()`

---

### 📖 Descripción Técnica

**Local Storage** es una API del navegador que permite **almacenar datos en el navegador del usuario** de forma **persistente**, es decir, incluso después de recargar la página o cerrar el navegador.

El almacenamiento se realiza como **pares clave-valor**, y ambos deben ser de tipo `string`.
Para guardar objetos o arreglos, se utiliza `JSON.stringify()` para convertirlos en texto.

---

### 🧾 Sintaxis

```javascript
localStorage.setItem(clave, valorString);
```

---

### 🔠 Parámetros

| Parámetro | Tipo     | Descripción                              |
| --------- | -------- | ---------------------------------------- |
| `clave`   | `string` | Nombre con el que se guarda el valor     |
| `valor`   | `string` | El contenido a guardar (debe ser string) |

---

### 🔁 Valor de Retorno

No retorna ningún valor. Almacena la información en el navegador.

---

### 💻 Ejemplo de Código

```javascript
// Almacenar una cadena simple
localStorage.setItem('nombre', 'Cesar');

// Almacenar un objeto
const producto = {
    nombre: "Monitor de 24 pulgadas",
    precio: 300
};
const productoString = JSON.stringify(producto);
localStorage.setItem('producto', productoString);

// Almacenar un arreglo
const meses = ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo'];
const mesesString = JSON.stringify(meses);
localStorage.setItem('meses', mesesString);
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Para **recuperar datos** del localStorage, se usa `localStorage.getItem('clave')`.

* Si guardaste un objeto o array, debes usar `JSON.parse()` al leerlo:

  ```javascript
  const producto = JSON.parse(localStorage.getItem('producto'));
  ```

* Todos los datos en localStorage son **persistentes** hasta que se eliminen manualmente o con `localStorage.removeItem()` o `localStorage.clear()`.

* El tamaño máximo permitido varía entre navegadores (\~5 MB por dominio).

* No debe usarse para datos sensibles (no está encriptado).