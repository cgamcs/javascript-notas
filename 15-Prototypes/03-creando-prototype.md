### 🧠 Tema Principal: Programación Orientada a Objetos (OOP)

### 📌 Módulo/Función Específica: `Constructor.prototype.metodo`

---

### 📖 Descripción Técnica

Los **prototipos** permiten agregar métodos a una función constructora para que todas sus instancias los compartan sin duplicar código.
Esto es parte del modelo de herencia de JavaScript basado en prototipos.

En este ejemplo, se crea un constructor `Cliente` y se definen tres métodos directamente en su `prototype`.

---

### 🧾 Sintaxis

```javascript
function Constructor() {
    this.propiedad = valor;
}

Constructor.prototype.metodo = function() {
    // lógica del método
};
```

---

### 🔠 Métodos definidos en el ejemplo

| Método                  | Función                                                 |
| ----------------------- | ------------------------------------------------------- |
| `tipoCliente()`         | Retorna un tipo según el saldo: Normal, Platinum o Gold |
| `nombreClienteSalto()`  | Devuelve nombre, saldo y tipo en un string formateado   |
| `retiraSaldo(cantidad)` | Resta una cantidad al saldo del cliente                 |

---

### 💻 Ejemplo de Código

```javascript
function Cliente(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
}

// Método 1
Cliente.prototype.tipoCliente = function() {
    let tipo;
    if (this.saldo > 10000) tipo = 'Gold';
    else if (this.saldo > 5000) tipo = 'Platinum';
    else tipo = 'Normal';
    return tipo;
};

// Método 2
Cliente.prototype.nombreClienteSalto = function() {
    return `Nombre: ${this.nombre}, Saldo: $${this.saldo}, Tipo: ${this.tipoCliente()}`;
};

// Método 3
Cliente.prototype.retiraSaldo = function(retira) {
    this.saldo -= retira;
};

// Crear instancia
const pedro = new Cliente('Pedro', 12000);

console.log(pedro.tipoCliente());           // Gold
console.log(pedro.nombreClienteSalto());    // Info completa
pedro.retiraSaldo(3000);
console.log(pedro.nombreClienteSalto());    // Nuevo saldo: 9000 → Platinum
console.log(pedro);                         // Objeto con nombre y saldo
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Los métodos definidos en el `prototype` son **compartidos entre todas las instancias**, lo que ahorra memoria.
* Puedes extender fácilmente un constructor sin modificar su definición original.
* Es una forma tradicional de implementar POO antes de `class` en ES6.
* Este patrón es útil cuando quieres lógica común para múltiples objetos creados con la misma función constructora.