### 🧠 Tema Principal: Almacenamiento Web

### 📌 Módulo/Función Específica: `localStorage.getItem()`, `JSON.parse()`

---

### 📖 Descripción Técnica

El método `localStorage.getItem()` permite **recuperar datos previamente almacenados** en el navegador mediante `localStorage.setItem()`.
Los datos se recuperan **en formato string**, por lo que si guardaste un objeto o arreglo, es necesario convertirlo a su forma original con `JSON.parse()`.

---

### 🧾 Sintaxis

```javascript
const valor = localStorage.getItem('clave');
```

---

### 🔠 Parámetros

| Parámetro | Tipo     | Descripción                      |
| --------- | -------- | -------------------------------- |
| `clave`   | `string` | El nombre de la clave almacenada |

---

### 🔁 Valor de Retorno

Devuelve un valor de tipo `string`.
Si la clave no existe, retorna `null`.

---

### 💻 Ejemplo de Código

```javascript
// Recuperar string simple
const nombre = localStorage.getItem('nombre');
console.log(nombre); // 'Cesar'

// Recuperar objeto (como string) y convertirlo a objeto real
const productoJSON = localStorage.getItem('producto');
// console.log(productoJSON); // Muestra como string
console.log(JSON.parse(productoJSON)); // Muestra como objeto

// Recuperar arreglo
const meses = localStorage.getItem('meses');
const mesesArray = JSON.parse(meses);
console.log(mesesArray); // ['Enero', 'Febrero', 'Marzo', 'Abril', 'Mayo']
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Siempre usa `JSON.parse()` al recuperar objetos o arrays almacenados con `JSON.stringify()`.

* Antes de acceder a propiedades, verifica que el valor no sea `null` para evitar errores:

  ```javascript
  const producto = localStorage.getItem('producto');
  if (producto) {
      const datos = JSON.parse(producto);
      console.log(datos.nombre);
  }
  ```

* Puedes recorrer arreglos u objetos recuperados como lo harías normalmente en JavaScript:

  ```javascript
  mesesArray.forEach(mes => console.log(mes));
  ```