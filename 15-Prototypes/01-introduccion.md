### 🧠 Tema Principal: Programación Orientada a Objetos (OOP) en JavaScript

### 📌 Módulo/Función Específica: **Prototype** en funciones constructoras

---

### 📖 Descripción Técnica

En JavaScript, los **prototipos** son la forma en que los objetos heredan propiedades y métodos.
Cada función constructora (como `Cliente`) tiene una propiedad llamada `.prototype`, donde se pueden definir métodos o propiedades **compartidas** entre todas las instancias creadas con `new`.

Esto permite **ahorrar memoria**, ya que los métodos no se duplican por cada objeto.

---

### 🧾 Sintaxis

```javascript
function Constructor(param1, param2) {
    this.propiedad1 = param1;
    this.propiedad2 = param2;
}

Constructor.prototype.metodoCompartido = function() {
    // lógica
};
```

---

### 💻 Ejemplo de Código

```javascript
// Objeto literal (sin prototype)
const cliente = {
    nombre: 'César',
    saldo: 500
};

console.log(cliente); // { nombre: "César", saldo: 500 }

// Función constructora
function Cliente(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
}

// Instancias usando new
const cesar = new Cliente('César', 500);
const juan = new Cliente('Juan', 300);
const diego = new Cliente('Diego', 600);

console.log(cesar, juan, diego);
```

---

### 📎 ¿Qué pasa internamente?

* `Cliente` es una función constructora.
* Cuando usas `new Cliente(...)`, se crea un nuevo objeto y `this` apunta a ese nuevo objeto.
* Todos los objetos creados con `new Cliente()` heredan de `Cliente.prototype`.

---

### 📝 Notas Adicionales / Mejores Prácticas

* Puedes extender las funcionalidades comunes sin duplicarlas:

  ```javascript
  Cliente.prototype.mostrarInfo = function() {
      return `${this.nombre} tiene $${this.saldo}`;
  };

  console.log(cesar.mostrarInfo()); // "César tiene $500"
  ```

* Así, todas las instancias (`cesar`, `juan`, `diego`) comparten una sola copia del método `mostrarInfo`.

* Es el mecanismo base de herencia en JavaScript antes de la introducción de `class`.