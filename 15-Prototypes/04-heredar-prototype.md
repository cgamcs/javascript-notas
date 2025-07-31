### 🧠 Tema Principal: Herencia Prototípica

### 📌 Módulo/Función Específica: `Function.call()`, `Object.create()`, `prototype.constructor`

---

### 📖 Descripción Técnica

En JavaScript, una función constructora puede **heredar propiedades y métodos** de otra usando **prototipos**.
Este patrón se llama **herencia prototípica** y permite reutilizar lógica entre "clases" constructoras.

En este ejemplo:

* `Persona` hereda de `Cliente`.
* `Persona` obtiene los métodos `tipoCliente()`, `nombreClienteSalto()` y `retiraSaldo()` definidos en `Cliente.prototype`.
* Además, `Persona` define su propia propiedad adicional: `telefono`.

---

### 🧾 Sintaxis

```javascript
// Heredar propiedades
ConstructorHijo.call(this, arg1, arg2);

// Heredar métodos
ConstructorHijo.prototype = Object.create(ConstructorPadre.prototype);
ConstructorHijo.prototype.constructor = ConstructorHijo;
```

---

### 💻 Ejemplo de Código

```javascript
// Función constructora base
function Cliente(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
}

// Métodos de Cliente
Cliente.prototype.tipoCliente = function() {
    if (this.saldo > 10000) return 'Gold';
    if (this.saldo > 5000) return 'Platinum';
    return 'Normal';
};

Cliente.prototype.nombreClienteSalto = function() {
    return `Nombre: ${this.nombre}, Saldo: $${this.saldo}, Tipo: ${this.tipoCliente()}`;
};

Cliente.prototype.retiraSaldo = function(retira) {
    this.saldo -= retira;
};

// Función constructora hija
function Persona(nombre, saldo, telefono) {
    Cliente.call(this, nombre, saldo); // Hereda propiedades
    this.telefono = telefono;
}

// Hereda métodos (prototipo)
Persona.prototype = Object.create(Cliente.prototype);
Persona.prototype.constructor = Persona;

// Método propio de Persona
Persona.prototype.mostrarTelefono = function() {
    return `El teléfono de ${this.nombre} es: ${this.telefono}`;
};

// Instanciar objeto
const pedro = new Persona('Pedro', 10000, 8130974226);

console.log(pedro.nombreClienteSalto());    // Método heredado
console.log(pedro.mostrarTelefono());       // Método propio
```

---

### 📎 ¿Qué hace cada línea clave?

* `Cliente.call(this, ...)`: copia las propiedades (nombre, saldo) en `Persona`.
* `Object.create(Cliente.prototype)`: permite que `Persona` herede los métodos de `Cliente`.
* `Persona.prototype.constructor = Persona`: corrige la propiedad `.constructor` (importante para mantener la referencia correcta en herencia).

---

### 📝 Notas Adicionales / Mejores Prácticas

* Siempre establece `constructor` después de usar `Object.create()`, de lo contrario seguirá apuntando al constructor padre.
* Si olvidas `Object.create`, las instancias de `Persona` no podrán acceder a los métodos de `Cliente`.
* Esta técnica se conoce como **herencia parasítica combinada**, típica antes de `class` en ES6.
* Puedes seguir extendiendo más prototipos en `Persona.prototype`.