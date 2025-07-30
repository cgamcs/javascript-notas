### 🧠 Tema Principal: Manipulación del DOM

### 📌 Módulo/Función Específica: `document.getElementsByClassName()`

---

### 📖 Descripción Técnica

`getElementsByClassName()` es un método del objeto `document` que permite obtener todos los elementos del DOM que tienen una clase CSS específica.
Devuelve una colección en vivo (HTMLCollection), lo que significa que se actualiza automáticamente si el DOM cambia.

---

### 🧾 Sintaxis

```javascript
document.getElementsByClassName(nombreDeClase)
```

---

### 🔠 Parámetros

| Parámetro       | Tipo   | Descripción                                    |
| --------------- | ------ | ---------------------------------------------- |
| `nombreDeClase` | String | El nombre de la clase CSS que se desea buscar. |

> *Nota:* No se incluye el punto `.` como en los selectores CSS. Solo se escribe el nombre de la clase.

---

### 🔁 Valor de Retorno

Devuelve un **HTMLCollection** de todos los elementos que coinciden con el nombre de clase.
Esta colección **no es un array**, pero puede recorrerse con un bucle `for`, `for...of`, o convertirse en array con `Array.from()`.

---

### 💻 Ejemplo de Código

```javascript
const header = document.getElementsByClassName('header');
console.log(header); // HTMLCollection con los elementos con clase "header"

const hero = document.getElementsByClassName('hero');
console.log(hero); // HTMLCollection con los elementos con clase "hero"

// Si la clase existe varias veces en el DOM
const contenedores = document.getElementsByClassName('contenedor');
console.log(contenedores); // HTMLCollection con todos los elementos "contenedor"

// Si la clase no existe
const NoExiste = document.getElementsByClassName('NoExiste');
console.log(NoExiste); // HTMLCollection vacío (length = 0)
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Aunque `getElementsByClassName` retorna múltiples elementos, si solo esperas uno, puedes acceder directamente con el índice: `elementos[0]`.
* Para seleccionar un solo elemento con clase, también puedes usar `document.querySelector('.clase')`.
* Al ser una **colección en vivo**, cualquier cambio en el DOM afectará inmediatamente el contenido del HTMLCollection.
* Para convertir la colección en un array (para usar `map`, `filter`, etc.), puedes hacer:

  ```javascript
  const elementosArray = Array.from(document.getElementsByClassName('contenedor'));
  ```