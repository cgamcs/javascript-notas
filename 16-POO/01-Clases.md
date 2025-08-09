# Definiendo e instanciando clases en JavaScript (POO)

## 1) ¿Qué es una clase?

Una **clase** es una plantilla para crear objetos con **estado** (propiedades) y **comportamiento** (métodos). En JS es azúcar sintáctica sobre **prototipos**.

```js
class Cliente {
  constructor(nombre, saldo) {
    this.nombre = nombre;      // estado
    this.saldo = saldo;
  }
  mostrarInformacion() {       // comportamiento (método de instancia)
    return `Cliente: ${this.nombre} tiene un saldo de $${this.saldo}`;
  }
  static bienvenida() {        // método estático (de la clase, no de la instancia)
    return `Bienvenido al cajero`;
  }
}
```

**Claves**

* `constructor` se ejecuta en `new`.
* `this` apunta a la **instancia** creada por `new`.
* Los métodos definidos en la clase viven en `Cliente.prototype`.
* `static` define funciones asociadas a la **clase** (utilidades) y **no** a cada objeto.

---

## 2) Instanciación: crear objetos desde la clase

```js
const juan = new Cliente('Juan', 400);
console.log(juan.mostrarInformacion()); // "Cliente: Juan tiene un saldo de $400"
console.log(Cliente.bienvenida());      // "Bienvenido al cajero"
```

**Claves**

* `new` hace 4 cosas: crea un objeto vacío, lo enlaza a `Cliente.prototype`, ejecuta `constructor`, y devuelve la instancia.
* Métodos **de instancia** se invocan con la **instancia** (`juan.método()`).
* Métodos **estáticos** se invocan con la **clase** (`Cliente.método()`).

---

## 3) Class Declaration vs Class Expression

Tu código muestra ambos estilos:

**Declaración (clásica):**

```js
class Cliente { /* ... */ }
```

* Tiene nombre obligatorio.
* No se “hoistea” como las funciones; la referencia existe solo después de su declaración (aunque el nombre sí se reserva en el bloque).

**Expresión de clase:**

```js
const Cliente2 = class {
  constructor(nombre, saldo) {
    this.nombre = nombre;
    this.saldo = saldo;
  }
};
const pablo = new Cliente2('Pablo', 500);
```

* Útil para **asignar a variables**, **pasar como argumento**, o **clases anónimas/nombradas** en contextos más avanzados.

**Cuándo usar cada una**

* **Declaración**: clases “top-level” que exportas o usas en varios lugares.
* **Expresión**: clases internas, factory functions, o cuando quieres controlar el **scope**/nombre.

---

## 4) Métodos de instancia vs estáticos

| Tipo                | Se llama con  | Accede a `this`   | Casos de uso típicos                     |
| ------------------- | ------------- | ----------------- | ---------------------------------------- |
| Instancia           | `obj.met()`   | Sí (la instancia) | Lógica que depende del estado del objeto |
| Estático (`static`) | `Clase.met()` | No (la clase)     | Utilidades, validaciones, creadores      |

**Ejemplo práctico**

```js
class Cliente {
  static esSaldoValido(saldo) { return Number.isFinite(saldo) && saldo >= 0; }
}
Cliente.esSaldoValido(100); // true
```

---

## 5) `this`, `prototype` y `instanceof` (bajo el capó)

* `this` dentro de métodos de clase apunta a la **instancia** (si llamas `instancia.met()`).
* Todos los métodos están en `Clase.prototype`, compartidos por las instancias (ahorra memoria).
* `instancia instanceof Clase` → `true` si la cadena de prototipos incluye `Clase.prototype`.

```js
juan instanceof Cliente; // true
Object.getPrototypeOf(juan) === Cliente.prototype; // true
```

---

## 6) Buenas prácticas

* **Inmutabilidad ligera**: asigna propiedades necesarias en el constructor; evita mutar la forma del objeto después.
* **Valida entradas** (puedes usar métodos estáticos para validar antes de instanciar).
* **Nombres claros**: clases en **PascalCase** (`Cliente`), instancias en **camelCase** (`juan`).
* **Evita lógica pesada en el constructor**; usa métodos o factories.
* **No abuses de `static`**: úsalo solo para utilidades relacionadas al dominio de la clase.

---

## 7) Errores comunes y cómo evitarlos

* Llamar un método estático desde la instancia: `juan.bienvenida()` ❌ (debe ser `Cliente.bienvenida()`).
* Olvidar `new`: `Cliente('Juan', 400)` ❌ (pierdes el `this` correcto).
* Usar arrow functions como métodos de clase sin necesidad: fija léxicamente `this` y dificulta pruebas/override.
* Confiar en hoisting: las clases **no** se pueden usar antes de su definición.

---

## 8) Variantes y extensiones útiles

* **Campos públicos/privados** (Stage 4 en JS moderno):

```js
class Cuenta {
  #saldo = 0;             // privado
  constructor(saldo) { this.#saldo = saldo; }
  get saldo() { return this.#saldo; }
}
```

* **Herencia** con `extends` y `super` (tema para la siguiente clase):

```js
class VIP extends Cliente {
  constructor(nombre, saldo, nivel) {
    super(nombre, saldo);
    this.nivel = nivel;
  }
}
```

---

## 9) Mini-checklist para “definir e instanciar” rápido

1. **Define** la clase con `class Nombre { constructor(...) { ... } }`.
2. **Declara** métodos de instancia según el comportamiento.
3. **Agrega** estáticos solo si son utilidades de la clase.
4. **Crea** objetos con `new Nombre(args)`.
5. **Verifica** con `instanceof` si lo necesitas.

---

## 10) Ejercicios rápidos

1. Agrega a `Cliente` un método `depositar(monto)` que aumente `saldo` y retorne el nuevo saldo. Valida monto > 0.
2. Crea `Cliente.esNombreValido(nombre)` como `static` (no vacío, tipo string).
3. Implementa un `getter` `info` que devuelva el mismo texto de `mostrarInformacion`.

```js
class Cliente {
  constructor(nombre, saldo){ this.nombre = nombre; this.saldo = saldo; }
  get info(){ return `Cliente: ${this.nombre} tiene un saldo de $${this.saldo}`; }
  depositar(monto){
    if(!Number.isFinite(monto) || monto <= 0) throw new Error('Monto inválido');
    this.saldo += monto;
    return this.saldo;
  }
  static esNombreValido(n){ return typeof n === 'string' && n.trim().length > 0; }
}
```

---

## 11) Resumen express (para estudiar)

* **Clase** = plantilla; **instancia** = objeto creado con `new`.
* **constructor** define estado inicial; métodos van al **prototype**.
* **static** = funciones de clase, no de instancia.
* **Declaración** vs **Expresión** de clase: estilo/ámbito, misma semántica base.
* `instanceof` y `prototype` confirman relación clase–instancia.
