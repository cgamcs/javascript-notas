# Map - Colección de Clave-Valor Avanzada

## ¿Qué es un Map?

Un **Map** es una estructura de datos que almacena pares clave-valor. A diferencia de los objetos, un Map permite cualquier tipo de dato como clave (objetos, funciones, primitivos) y mantiene el orden de inserción.

## Creando y Configurando un Map

### Creación Básica
```javascript
const cliente = new Map()

// Agregar valores con .set()
cliente.set('nombre', 'Karen')
cliente.set('tipo', 'Premium')
cliente.set('saldo', 3000)

console.log(cliente)
```

### Creación con Datos Iniciales
```javascript
const paciente = new Map([
    ['nombre', 'paciente'], 
    ['cuarto', 'No definido']
])

// Agregar más datos
paciente.set('dr', 'Dr asignado')

// Modificar datos existentes
paciente.set('nombre', 'Cesar')

console.log(paciente)
```

## Métodos Principales

### .set() - Agregar/Modificar
```javascript
cliente.set('nombre', 'Karen')    // Crear nueva entrada
cliente.set('nombre', 'Carlos')   // Modificar entrada existente
```

### .get() - Obtener Valor
```javascript
console.log(cliente.get('nombre')) // 'Karen'
console.log(cliente.get('edad'))   // undefined (no existe)
```

### .has() - Verificar Existencia
```javascript
console.log(cliente.has('nombre')) // true
console.log(cliente.has('edad'))   // false
```

### .delete() - Eliminar Entrada
```javascript
cliente.delete('saldo')
console.log(cliente.has('saldo')) // false
```

### .size - Tamaño del Map
```javascript
console.log(cliente.size) // Número de entradas
```

### .clear() - Limpiar Todo
```javascript
cliente.clear() // Elimina todas las entradas
```

## Iterando un Map

### Con forEach
```javascript
paciente.forEach((datos, clave) => {
    console.log(`${clave}:`, datos)
})

// Salida:
// nombre: Cesar
// cuarto: No definido
// dr: Dr asignado
```

### Con for...of
```javascript
// Iterar entradas [clave, valor]
for (let [clave, valor] of paciente) {
    console.log(`${clave}: ${valor}`)
}

// Solo claves
for (let clave of paciente.keys()) {
    console.log(clave)
}

// Solo valores
for (let valor of paciente.values()) {
    console.log(valor)
}
```

## Map vs Objetos

| Característica | Objeto | Map |
|----------------|--------|-----|
| **Claves** | Solo strings/symbols | Cualquier tipo |
| **Tamaño** | Manual (Object.keys().length) | `.size` automático |
| **Iteración** | for...in, Object.keys() | for...of, .forEach() |
| **Orden** | No garantizado* | Orden de inserción |
| **Prototipo** | Tiene claves por defecto | Vacío por defecto |
| **Performance** | Optimizado para records | Optimizado para add/remove |

*En ES2015+ sí se mantiene orden en objetos

## Casos de Uso Prácticos

### 1. Cache/Memoización
```javascript
const cache = new Map()

function calcularCostoso(n) {
    if (cache.has(n)) {
        return cache.get(n)
    }
    
    const resultado = n * n * n // Cálculo costoso
    cache.set(n, resultado)
    return resultado
}
```

### 2. Contadores
```javascript
const contadorPalabras = new Map()
const texto = "hola mundo hola javascript mundo"

texto.split(' ').forEach(palabra => {
    const count = contadorPalabras.get(palabra) || 0
    contadorPalabras.set(palabra, count + 1)
})

console.log(contadorPalabras)
// Map { "hola" => 2, "mundo" => 2, "javascript" => 1 }
```

### 3. Configuraciones por Usuario
```javascript
const configuracionesUsuario = new Map()

configuracionesUsuario.set('user123', {
    tema: 'oscuro',
    idioma: 'es',
    notificaciones: true
})

configuracionesUsuario.set('user456', {
    tema: 'claro',
    idioma: 'en',
    notificaciones: false
})
```

## WeakMap - Versión "Débil" del Map

```javascript
const producto = {
    idProducto: 10,
}

const weakmap = new WeakMap()

// Solo acepta objetos como claves
weakmap.set(producto, 'Monitor')

console.log(weakmap.has(producto)) // true
console.log(weakmap.get(producto)) // 'Monitor'
```

### Características de WeakMap
- **Solo objetos como claves**: No acepta primitivos
- **Garbage Collection**: Las claves pueden ser recolectadas automáticamente
- **No enumerable**: No se puede iterar
- **Métodos limitados**: Solo `.set()`, `.get()`, `.has()`, `.delete()`
- **Privacidad**: Ideal para datos privados asociados a objetos

### Uso de WeakMap para Datos Privados
```javascript
const datosPrivados = new WeakMap()

class Usuario {
    constructor(nombre, email) {
        this.nombre = nombre
        // Email se mantiene privado
        datosPrivados.set(this, { email })
    }
    
    getEmail() {
        return datosPrivados.get(this).email
    }
}

const usuario = new Usuario('Juan', 'juan@email.com')
console.log(usuario.getEmail()) // 'juan@email.com'
// No hay forma de acceder al email directamente
```

## Ventajas del Map

✅ **Claves flexibles** - cualquier tipo de dato
✅ **Tamaño directo** - propiedad `.size`
✅ **Orden garantizado** - mantiene orden de inserción
✅ **Iteración natural** - con for...of y .forEach()
✅ **Performance** - optimizado para add/delete frecuentes

## Desventajas del Map

❌ **Menos soporte** - no funciona con JSON.stringify() directamente
❌ **Sintaxis** - más verbosa que notación de objeto
❌ **Menos métodos** - no tiene métodos de array como .map(), .filter()

## Cuándo Usar Map vs Objeto

### Usa Map cuando:
- ✅ Las claves **no son strings**
- ✅ Necesitas **agregar/eliminar** claves frecuentemente
- ✅ El **tamaño cambia** regularmente
- ✅ Necesitas **iterar** en orden de inserción

### Usa Objeto cuando:
- ✅ Las claves son **strings conocidas**
- ✅ Necesitas **JSON.stringify()**
- ✅ Trabajas con **records/dictionaries** simples
- ✅ Necesitas **métodos** y **prototipo**

## Conversiones Útiles

### Map a Objeto
```javascript
const map = new Map([['a', 1], ['b', 2]])
const obj = Object.fromEntries(map)
console.log(obj) // { a: 1, b: 2 }
```

### Objeto a Map
```javascript
const obj = { a: 1, b: 2 }
const map = new Map(Object.entries(obj))
console.log(map) // Map { "a" => 1, "b" => 2 }
```

### Map a Array
```javascript
const map = new Map([['a', 1], ['b', 2]])
const array = [...map] // [['a', 1], ['b', 2]]
```

## Resumen

- **Map** es ideal para colecciones clave-valor dinámicas
- **Permite cualquier tipo** de clave (objetos, funciones, primitivos)
- **Mantiene orden** de inserción garantizado
- **Mejor performance** para add/delete frecuentes que objetos
- **WeakMap** es perfecto para datos privados y gestión automática de memoria
- **Usa Map** cuando necesites claves flexibles y operaciones dinámicas
