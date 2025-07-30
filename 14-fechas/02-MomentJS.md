### 🧠 Tema Principal: Manipulación y Formato de Fechas

### 📌 Módulo/Función Específica: `moment()`, `format()`, `add()`, `calendar()`, `locale()`

---

### 📖 Descripción Técnica

**Moment.js** es una librería de JavaScript que facilita el trabajo con fechas y horas:
✔ Formateo
✔ Comparación
✔ Manipulación (sumar/restar días, horas, etc.)
✔ Localización (idioma y formato regional)

Aunque Moment.js ya no se considera la mejor opción para nuevos proyectos (porque es pesada y existen alternativas como `date-fns` o `dayjs`), **sigue siendo muy útil y fácil de usar**.

---

### 🧾 Sintaxis

```javascript
moment();                      // Fecha actual
moment().format('formato');    // Devuelve una fecha con formato personalizado
moment().add(cantidad, unidad); // Agrega tiempo (días, meses, etc.)
moment().calendar();           // Fecha en formato relativo legible
moment.locale('es');           // Establece el idioma
```

---

### 🔠 Principales Métodos y Formatos

| Método                      | Descripción                                       |
| --------------------------- | ------------------------------------------------- |
| `moment().format()`         | Formatea la fecha según patrones                  |
| `moment().add(n, 'unidad')` | Suma días, meses, años, etc.                      |
| `moment().calendar()`       | Muestra la fecha en estilo natural (Ej. "mañana") |
| `moment.locale('es')`       | Cambia el idioma (en este caso, español)          |

| Formato                    | Resultado (ejemplo)                 |
| -------------------------- | ----------------------------------- |
| `'MMMM Do YYYY h:mm:ss a'` | "julio 29º 2025 6:21:08 pm"         |
| `'LLLL'`                   | "martes, 29 de julio de 2025 18:21" |

---

### 💻 Ejemplo de Código

```javascript
const diaHoy = new Date();

// Establecer idioma
moment.locale('es');

// Formato personalizado
console.log(moment().format('MMMM Do YYYY h:mm:ss a'));

// Formato completo con día de la semana
console.log(moment().format('LLLL', diaHoy));

// Sumar 3 días a la fecha actual y mostrar en formato natural
console.log(moment().add(3, 'days').calendar());
```

---

### 📎 Documentación Oficial

👉 [https://momentjs.com/](https://momentjs.com/)

---

### 📝 Notas Adicionales / Mejores Prácticas

* Puedes usar unidades como `'days'`, `'months'`, `'years'`, `'hours'`, `'minutes'`, `'seconds'`.

* Moment.js **modifica el objeto original**, por lo que si necesitas conservar la fecha original, usa `.clone()`.

  ```javascript
  const nuevaFecha = moment().clone().add(5, 'days');
  ```

* Aunque Moment.js ya no se recomienda para nuevos proyectos grandes, sigue siendo excelente para scripts rápidos, demostraciones o proyectos personales.