# Symbols - Identificadores Únicos e Inmutables

## ¿Qué son los Symbols?

Los **Symbols** son un tipo de dato primitivo introducido en ES6 que representa identificadores únicos e inmutables. Cada Symbol es único, incluso si se crean con la misma descripción.

## Características Fundamentales

### Unicidad Absoluta
```javascript
const sym = Symbol('1')
const sym2 = Symbol('1')

if(sym === sym2) {
    console.log('Son iguales')
} else {
    console.log('Son diferentes') // ← Se ejecuta esto
}

// Cada Symbol es único, sin importar la descripción
```

### Inmutabilidad
Una vez creado, un Symbol no puede ser modificado ni reconstruido.

## Creando Symbols

### Symbol Básico
```javascript
const nombre = Symbol()
const apellido = Symbol()

console.log(nombre)   // Symbol()
console.log(apellido) // Symbol()
```

### Symbol con Descripción
```javascript
const nombreCliente = Symbol('Nombre del cliente')

console.log(nombreCliente) // Symbol(Nombre del cliente)
```

## Symbols como Propiedades de Objetos

### Uso Básico
```javascript
const nombre = Symbol()
const apellido = Symbol()

const persona = {}

// Agregar propiedades Symbol al objeto
persona[nombre] = 'Cesar'
persona[apellido] = 'Garcia'

// Propiedades normales conviven con Symbols
persona.tipoCliente = 'Premium'
persona.saldo = 300

console.log(persona)
console.log(persona[nombre]) // 'Cesar'
```

### Symbol con Descripción en Objeto
```javascript
const nombreCliente = Symbol('Nombre del cliente')

const cliente = {}

cliente[nombreCliente] = 'Pedro'

console.log(cliente)
console.log(cliente[nombreCliente]) // 'Pedro'
console.log(nombreCliente)           // Symbol(Nombre del cliente)
```

## Ventajas de los Symbols

### 1. Propiedades Privadas (Semi-privadas)
```javascript
const _email = Symbol('email privado')
const _id = Symbol('id interno')

class Usuario {
    constructor(nombre, email) {
        this.nombre = nombre
        this[_email] = email
        this[_id] = Math.random()
    }
    
    getEmail() {
        return this[_email]
    }
    
    getId() {
        return this[_id]
    }
}

const usuario = new Usuario('Ana', 'ana@email.com')
console.log(usuario.nombre)     // 'Ana'
console.log(usuario.getEmail()) // 'ana@email.com'

// Estas propiedades no aparecen en enumeraciones normales
console.log(Object.keys(usuario)) // ['nombre']
```

### 2. Evitar Colisiones de Nombres
```javascript
// Librería A
const configA = Symbol('config')

// Librería B
const configB = Symbol('config')

const objeto = {
    [configA]: { tema: 'oscuro' },
    [configB]: { idioma: 'es' },
    config: 'configuración normal'
}

// No hay conflictos entre las diferentes 'config'
console.log(objeto[configA])  // { tema: 'oscuro' }
console.log(objeto[configB])  // { idioma: 'es' }
console.log(objeto.config)    // 'configuración normal'
```

## Symbols y Enumeración

### No Aparecen en Bucles Normales
```javascript
const sym = Symbol('oculto')
const obj = {
    visible: 'se ve',
    [sym]: 'no se ve en for...in'
}

// for...in no incluye Symbols
for (let key in obj) {
    console.log(key) // Solo 'visible'
}

// Object.keys() no incluye Symbols
console.log(Object.keys(obj)) // ['visible']

// JSON.stringify() ignora Symbols
console.log(JSON.stringify(obj)) // {"visible":"se ve"}
```

### Cómo Acceder a Symbols
```javascript
// Object.getOwnPropertySymbols() para obtener Symbols
const symbols = Object.getOwnPropertySymbols(obj)
console.log(symbols) // [Symbol(oculto)]

// Reflect.ownKeys() incluye todo
console.log(Reflect.ownKeys(obj)) // ['visible', Symbol(oculto)]
```

## Casos de Uso Prácticos

### 1. Metadatos de Objetos
```javascript
const metadata = Symbol('metadata')

function crearUsuario(nombre, email) {
    const usuario = {
        nombre,
        email,
        [metadata]: {
            createdAt: new Date(),
            version: '1.0',
            internal: true
        }
    }
    return usuario
}

const user = crearUsuario('Luis', 'luis@email.com')
console.log(user[metadata]) // Metadatos internos
```

### 2. Estados Internos de Clases
```javascript
const _estado = Symbol('estado interno')
const _validar = Symbol('método privado')

class Maquina {
    constructor() {
        this[_estado] = 'detenida'
    }
    
    [_validar]() {
        return this[_estado] !== 'error'
    }
    
    iniciar() {
        if (this[_validar]()) {
            this[_estado] = 'funcionando'
            console.log('Máquina iniciada')
        }
    }
    
    getEstado() {
        return this[_estado]
    }
}

const maquina = new Maquina()
maquina.iniciar()
console.log(maquina.getEstado()) // 'funcionando'

// El estado y el método de validación están "ocultos"
console.log(Object.keys(maquina)) // []
```

### 3. Extensión de APIs sin Conflictos
```javascript
// Extender Array sin afectar el prototipo original
const customMethod = Symbol('métodoPersonalizado')

Array.prototype[customMethod] = function() {
    return this.filter(x => x > 0).map(x => x * 2)
}

const numeros = [1, -2, 3, -4, 5]
console.log(numeros[customMethod]()) // [2, 6, 10]

// No interfiere con métodos normales de Array
console.log(numeros.map(x => x + 1)) // [2, -1, 4, -3, 6]
```

## Symbols Globales

### Symbol.for() - Registry Global
```javascript
// Crear o recuperar Symbol global
const globalSym1 = Symbol.for('app.config')
const globalSym2 = Symbol.for('app.config')

console.log(globalSym1 === globalSym2) // true (mismo Symbol)

// Symbol.keyFor() obtiene la clave
console.log(Symbol.keyFor(globalSym1)) // 'app.config'
```

### Diferencia con Symbol() Normal
```javascript
const local1 = Symbol('test')
const local2 = Symbol('test')
const global1 = Symbol.for('test')
const global2 = Symbol.for('test')

console.log(local1 === local2)   // false (diferentes)
console.log(global1 === global2) // true (mismo)
```

## Well-Known Symbols

JavaScript incluye Symbols predefinidos para personalizar comportamientos:

```javascript
// Symbol.iterator - Define cómo iterar un objeto
const miIterable = {
    *[Symbol.iterator]() {
        yield 1
        yield 2
        yield 3
    }
}

for (let valor of miIterable) {
    console.log(valor) // 1, 2, 3
}

// Symbol.toStringTag - Personaliza Object.prototype.toString()
class MiClase {
    get [Symbol.toStringTag]() {
        return 'MiClasePersonalizada'
    }
}

const instancia = new MiClase()
console.log(instancia.toString()) // [object MiClasePersonalizada]
```

## Cuándo Usar Symbols

### ✅ Usa Symbols para:
- **Propiedades semi-privadas** en objetos/clases
- **Evitar colisiones** de nombres en APIs
- **Metadatos internos** que no deben ser visibles
- **Extensiones** de objetos sin conflictos
- **Configuración de comportamientos** especiales

### ❌ No uses Symbols para:
- **Datos que necesitas serializar** (JSON)
- **Propiedades que otros desarrolladores** necesitan acceder fácilmente
- **Casos simples** donde strings funcionan bien
- **Performance crítica** (tienen un pequeño overhead)

## Limitaciones

1. **No son serializables**: JSON.stringify() los ignora
2. **No son enumerables**: No aparecen en for...in o Object.keys()
3. **Requieren referencia**: Necesitas la variable Symbol para acceder
4. **Debugging**: Más difíciles de inspeccionar

## Resumen

- **Symbols** son identificadores únicos e inmutables
- **Cada Symbol es único**, incluso con la misma descripción
- **Ideales para propiedades semi-privadas** y evitar colisiones
- **No aparecen en enumeraciones** normales (for...in, Object.keys)
- **Symbol.for()** crea Symbols globales reutilizables
- **Perfectos para metadatos** y extensiones sin conflictos
- **No son serializables** - no funcionan con JSON
