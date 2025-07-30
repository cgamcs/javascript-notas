### 🧠 Tema Principal: Objetos Integrados de JavaScript

### 📌 Módulo/Función Específica: `Date`, `getFullYear()`, `getTime()`, `getDate()`, `Date.now()`

---

### 📖 Descripción Técnica

El objeto `Date` en JavaScript permite **trabajar con fechas y horas**.
Para usar sus métodos, es necesario crear una instancia con `new Date()`.

Existen métodos `get` para obtener partes específicas de la fecha, como el año, día, hora, etc.
Una excepción es `Date.now()`, que se puede llamar directamente sin crear una instancia.

---

### 🧾 Sintaxis

```javascript
const fecha = new Date();       // Fecha y hora actuales

fecha.getFullYear();            // Año (ej. 2025)
fecha.getTime();                // Tiempo en milisegundos desde 1970
fecha.getDate();                // Día del mes (1-31)

Date.now();                     // Milisegundos desde el 1 de enero de 1970
```

---

### 🔠 Métodos usados

| Método          | Retorna                        |
| --------------- | ------------------------------ |
| `getFullYear()` | El año completo (ej. `2025`)   |
| `getTime()`     | Tiempo en ms desde 01/01/1970  |
| `getDate()`     | Día del mes (1–31)             |
| `Date.now()`    | Igual a `new Date().getTime()` |

---

### 💻 Ejemplo de Código

```javascript
const diaHoy = new Date();

let valor;

valor = diaHoy;                // Fecha completa
valor = diaHoy.getFullYear(); // Año actual
valor = diaHoy.getTime();     // Tiempo en milisegundos desde 1970
valor = diaHoy.getDate();     // Día del mes

console.log(valor);
```

---

### 📋 Comentario Importante

```javascript
// Date.now() muestra la cantidad de milisegundos desde el 01/01/1970
console.log(Date.now());
```

---

### ⚠️ Nota de Seguridad

> Si estás desarrollando un sistema crítico como **exámenes en línea**, **NO confíes en la hora del cliente**, ya que los usuarios pueden modificarla en su computadora.

✅ **Mejor práctica:** Validar la hora en el **servidor**, no con JavaScript en el navegador.

---

### 📝 Notas Adicionales

* Puedes usar otras funciones útiles como `getMonth()`, `getHours()`, `toLocaleDateString()`, etc.
* Las fechas en JavaScript **empiezan en 0**, por ejemplo, `getMonth()` retorna 0 para enero, 11 para diciembre.
* Para convertir a una fecha legible:

  ```javascript
  console.log(diaHoy.toLocaleDateString());
  console.log(diaHoy.toLocaleTimeString());
  ```