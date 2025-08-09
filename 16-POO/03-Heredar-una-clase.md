# Heredar una clase en JavaScript (POO)

## 1) Concepto

En JavaScript, **heredar** una clase significa crear una nueva clase que reutiliza y amplía las propiedades y métodos de otra clase.
Esto se hace con la palabra clave `extends` y el llamado a `super()` en el constructor.

---

## 2) Clase base

```js
class Cliente {
  constructor(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
  }

  mostrarInformacion() {
    return `Cliente: ${this.nombre} tiene un saldo de $${this.saldo}`;
  }

  static bienvenida() {
    return `Bienvenido al cajero`;
  }
}
```

**Claves**

* Es la **superclase** o clase padre.
* Tiene propiedades (`nombre`, `saldo`) y métodos (instancia y estáticos).
* Otras clases podrán **heredar** su funcionalidad.

---

## 3) Clase hija con `extends`

```js
class Empresa extends Cliente {
  constructor(nombre, saldo, telefono, categoria) {
    super(nombre, saldo); // Llama al constructor de Cliente
    this.telefono = telefono;
    this.categoria = categoria;
  }

  mostrarInformacion() {
    return `Empresa: '${this.nombre}' tiene un saldo de $${this.saldo}, información de contacto: ${this.telefono}, categoría: ${this.categoria}`;
  }

  static bienvenida() {
    return `Bienvenido al cajero empresarial`;
  }
}
```

**Claves**

* `extends` → enlaza `Empresa` a `Cliente` para heredar sus métodos y propiedades.
* `super()` → **obligatorio** en el constructor de la subclase antes de usar `this`.
  Llama al constructor de la clase padre.
* Puedes **sobrescribir** (override) métodos de instancia y estáticos.
* Si no sobrescribes un método, se usará el heredado.

---

## 4) Sobrescritura de métodos

En el ejemplo:

* `mostrarInformacion()` en `Empresa` reemplaza el de `Cliente` con más detalles.
* `bienvenida()` estática también se redefine para personalizar el mensaje.

```js
const empresa = new Empresa('Cesar Dev', 500, 8230129192, 'Aprendizaje en Línea');
console.log(empresa.mostrarInformacion());
// Usa el método sobrescrito en Empresa
```

---

## 5) Uso de métodos heredados

Si `Empresa` no definiera `mostrarInformacion()`, usaría automáticamente el de `Cliente`:

```js
class Empresa extends Cliente {}
```

En este caso:

```js
const e = new Empresa('Test SA', 1000, '555-1234', 'Servicios');
console.log(e.mostrarInformacion()); // Llama al método de Cliente
```

---

## 6) Ejemplo de ejecución del código

```js
const pablo = new Cliente('Pablo', 400);
const empresa = new Empresa('Cesar Dev', 500, 8230129192, 'Aprendizaje en Línea');

console.log(empresa);
// Empresa { nombre: 'Cesar Dev', saldo: 500, telefono: 8230129192, categoria: 'Aprendizaje en Línea' }

console.log(empresa.mostrarInformacion());
// "Empresa: 'Cesar Dev' tiene un saldo de $500, información de contacto: 8230129192, categoría: Aprendizaje en Línea"

console.log(Cliente.bienvenida());
// "Bienvenido al cajero"

console.log(Empresa.bienvenida());
// "Bienvenido al cajero empresarial"
```

---

## 7) Relación entre clases

```js
empresa instanceof Empresa; // true
empresa instanceof Cliente; // true
```

Esto ocurre porque `Empresa` hereda de `Cliente`, así que toda instancia de `Empresa` también es instancia de `Cliente`.

---

## 8) Buenas prácticas

* Usa `super()` siempre antes de `this` en el constructor de la clase hija.
* Sobrescribe solo los métodos que realmente necesitas cambiar.
* Para agregar funcionalidad sin perder lo heredado, puedes usar:

```js
mostrarInformacion() {
  return super.mostrarInformacion() + `, categoría: ${this.categoria}`;
}
```

* Métodos estáticos también pueden heredarse y sobrescribirse.

---

## 9) Resumen express

* `extends` → crea herencia.
* `super()` → llama al constructor o métodos del padre.
* Métodos heredados → si no los redefinimos, se usan tal cual.
* Se pueden sobrescribir tanto métodos de instancia como estáticos.
* La herencia permite **reutilizar código** y **especializar** clases.
