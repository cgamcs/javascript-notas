# Métodos y métodos estáticos en las clases (JavaScript POO)

## 1) Conceptos clave

En una clase de JavaScript podemos definir **dos tipos de métodos**:

| Tipo                    | Dónde se usa                               | Accede a `this` de instancia                            | Ejemplo de uso              |
| ----------------------- | ------------------------------------------ | ------------------------------------------------------- | --------------------------- |
| **Método de instancia** | Se invoca desde un objeto creado con `new` | ✅ Sí                                                    | `juan.mostrarInformacion()` |
| **Método estático**     | Se invoca directamente desde la clase      | ❌ No (a menos que se pase una instancia como argumento) | `Cliente.bienvenida()`      |

---

## 2) Métodos de instancia

Definidos **sin** la palabra clave `static`.

```js
class Cliente {
  constructor(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
  }

  mostrarInformacion() { // Método de instancia
    return `Cliente: ${this.nombre} tiene un saldo de $${this.saldo}`;
  }
}

const juan = new Cliente('Juan', 400);
console.log(juan.mostrarInformacion()); // ✅ desde la instancia
```

**Características**

* Acceden a las propiedades del objeto (`this.propiedad`).
* Se almacenan en `Clase.prototype` y son compartidos por todas las instancias.
* No requieren más memoria por objeto (ahorro eficiente).

---

## 3) Métodos estáticos (`static`)

Definidos con la palabra clave `static` **antes** del nombre del método.

```js
class Cliente {
  static bienvenida() { // Método estático
    return 'Bienvenido al cajero';
  }
}

console.log(Cliente.bienvenida()); // ✅ desde la clase
```

**Características**

* No acceden a `this` de la instancia (no tienen información individual del objeto).
* Se usan para **utilidades**, **validaciones**, o **constructores alternativos**.
* Se guardan en el propio constructor de la clase (`Cliente.bienvenida`), no en el `prototype`.

---

## 4) Diferencias prácticas

| Característica  | Instancia                        | Estático                       |
| --------------- | -------------------------------- | ------------------------------ |
| Se llama con    | `obj.metodo()`                   | `Clase.metodo()`               |
| Accede a `this` | Sí (instancia)                   | No (clase)                     |
| Vive en         | `Clase.prototype`                | `Clase`                        |
| Contexto de uso | Operaciones con datos del objeto | Funciones generales/auxiliares |

---

## 5) Ejemplo combinado

```js
class Cliente {
  constructor(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
  }

  mostrarInformacion() {
    return `Cliente: ${this.nombre} tiene un saldo de $${this.saldo}`;
  }

  static esSaldoValido(saldo) {
    return typeof saldo === 'number' && saldo >= 0;
  }
}

// Uso
const juan = new Cliente('Juan', 400);

if (Cliente.esSaldoValido(juan.saldo)) {
  console.log(juan.mostrarInformacion());  // Instancia
}
console.log(Cliente.esSaldoValido(-10));   // Estático: false
```

---

## 6) Cuándo usar cada uno

* **Método de instancia** → cuando la lógica depende de **datos específicos** de un objeto.
* **Método estático** → cuando la lógica es **global** a la clase y no necesita datos de una instancia.

---

## 7) Buenas prácticas

* Evita acceder a propiedades de instancia desde un método estático.
* Usa `static` para centralizar funciones comunes (por ejemplo, validaciones, formateo de datos, parseo).
* Mantén la coherencia: métodos que suenan “de utilidad” suelen ser estáticos (`parse`, `fromJSON`, `isValido`).

---

## 8) Resumen express

* **Instancia**: `obj.metodo()` → manipula o lee propiedades del objeto.
* **Estático**: `Clase.metodo()` → función auxiliar, no depende de datos de instancia.
* Ambos son parte de la definición de la clase, pero viven en lugares distintos en memoria.
