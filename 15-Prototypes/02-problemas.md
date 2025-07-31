### 🧠 Tema Principal: Programación Orientada a Objetos (OOP)

### 📌 Módulo/Función Específica: Reutilización de métodos sin `prototype`

---

### 📖 Descripción Técnica

Cuando no se utiliza `prototype` para definir métodos compartidos entre objetos, cada tipo de objeto (como `Cliente` o `Empresa`) necesita su **propia función externa** para manejar acciones similares (por ejemplo, formatear información). Esto provoca:

* **Duplicación de lógica**
* **Mayor mantenimiento**
* **Menor cohesión entre datos y comportamiento**

---

### 💻 Ejemplo del Problema

```javascript
function Cliente(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
}

function Empresa(nombre, saldo, categoria) {
    this.nombre = nombre;
    this.saldo = saldo;
    this.categoria = categoria;
}

// Dos funciones similares pero separadas
function formatearCliente(cliente) {
    const { nombre, saldo } = cliente;
    return `El cliente ${nombre} tiene un saldo de $${saldo}`;
}

function formatearEmpresa(empresa) {
    const { nombre, saldo, categoria } = empresa;
    return `La empresa ${nombre} tiene un saldo de $${saldo}, en la categorias de ${categoria}`;
}
```

---

### 📎 Problemas Detectados

1. **Duplicación de funciones** que hacen lo mismo (formatear) con ligeras diferencias.
2. **Falta de encapsulamiento**: el comportamiento está fuera del objeto.
3. No se puede llamar a un método directamente sobre el objeto (`cliente.formatear()` no existe).
4. Si agregas más tipos de objetos, tendrás que seguir creando más funciones externas.

---

### ✅ Solución con `prototype`

Asignando un método directamente al prototipo de cada constructor:

```javascript
Cliente.prototype.formatear = function() {
    return `El cliente ${this.nombre} tiene un saldo de $${this.saldo}`;
};

Empresa.prototype.formatear = function() {
    return `La empresa ${this.nombre} tiene un saldo de $${this.saldo}, en la categoría de ${this.categoria}`;
};

console.log(cesar.formatear());
console.log(samsung.formatear());
```

---

### 📝 Notas Adicionales / Mejores Prácticas

* Definir métodos en el `prototype` permite que todas las instancias compartan el mismo comportamiento sin duplicación.
* Favorece la **cohesión**: los datos y su comportamiento están agrupados en un mismo objeto.
* Facilita el mantenimiento y extensión del código, especialmente en aplicaciones más grandes.