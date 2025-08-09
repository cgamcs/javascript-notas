# Propiedades privadas en clases (JavaScript POO)

## 1) Concepto

En JavaScript moderno (ES2022 en adelante), podemos definir **propiedades privadas reales** en clases usando el prefijo `#`.
Estas propiedades **solo** son accesibles desde **dentro de la clase** que las define.

---

## 2) Definición de propiedad privada

```js
class Cliente {
  #nombre; // Declaración de propiedad privada

  setNombre(nombre) {
    this.#nombre = nombre; // Acceso permitido dentro de la clase
  }

  getNombre() {
    return this.#nombre;   // Lectura permitida dentro de la clase
  }
}
```

**Claves**

* El `#` antes del nombre indica **privacidad a nivel de lenguaje**.
* No es accesible desde fuera de la clase, ni con `this["#nombre"]`, ni con `obj.#nombre`.
* Diferente a la “convención” `_propiedad` (que es solo un acuerdo, no privacidad real).

---

## 3) Uso básico

```js
const juan = new Cliente();
juan.setNombre('Juan');
console.log(juan.getNombre()); // "Juan"
```

Si intentas:

```js
juan.#nombre = 'Pedro'; // ❌ SyntaxError
```

El motor de JS lanzará un error porque no se puede acceder a propiedades privadas fuera de la clase.

---

## 4) Ejemplo con constructor y métodos

```js
class Cliente {
  #nombre;
  #saldo;

  constructor(nombre, saldo) {
    this.#nombre = nombre;
    this.#saldo = saldo;
  }

  mostrarInformacion() {
    return `Cliente: ${this.#nombre}, tienes un saldo de $${this.#saldo}`;
  }

  static bienvenida() {
    return `Bienvenido al cajero`;
  }
}

const juan = new Cliente('Juan', 500);
console.log(juan.mostrarInformacion()); // ✅ Acceso interno
```

---

## 5) Diferencias con propiedades públicas

| Característica              | Pública (`this.prop`)  | Privada (`#prop`)                |
| --------------------------- | ---------------------- | -------------------------------- |
| Accesible fuera de la clase | ✅ Sí                   | ❌ No                             |
| Visible al iterar keys      | ✅ Sí                   | ❌ No                             |
| Encapsulación real          | ❌ No (solo convención) | ✅ Sí (protegida por el lenguaje) |

---

## 6) Encapsulación con getters/setters

Como las propiedades privadas no son accesibles directamente, puedes exponerlas de forma controlada:

```js
class Cliente {
  #nombre;
  
  constructor(nombre) {
    this.#nombre = nombre;
  }

  get nombre() {
    return this.#nombre;
  }

  set nombre(nuevoNombre) {
    if (nuevoNombre.length > 0) {
      this.#nombre = nuevoNombre;
    } else {
      throw new Error("El nombre no puede estar vacío");
    }
  }
}
```

---

## 7) Ventajas de usar propiedades privadas

* **Encapsulación real**: protegen el estado interno.
* Evitan que el código externo modifique datos críticos.
* Útiles para **invariantes** (reglas que no deben romperse).

---

## 8) Resumen express

* `#propiedad` → propiedad privada de clase.
* Solo se accede desde dentro de la clase.
* Usar **getters** y **setters** para exponer datos de forma controlada.
* Son una mejora de ES2022, antes la privacidad era solo una convención (`_nombre`).
