# Iteradores y Generadores en JavaScript

## ¿Qué son los Iteradores?

Los **iteradores** son objetos que implementan el protocolo de iteración, proporcionando una forma estándar de recorrer elementos uno por uno. Siguen un patrón específico con un método `next()` que retorna objetos con propiedades `value` y `done`.

## Creando un Iterador Manual

```javascript
function crearIterador(carrito) {
    let i = 0

    return {
        siguiente: () => {
            const fin = (i >= carrito.length)
            const valor = !fin ? carrito[i++] : undefined

            return {
                fin,
                valor
            }
        }
    }
}

const carrito = ['Producto 1', 'Producto 2', 'Producto 3']

// Utilizar el iterador
const recorrerCarrito = crearIterador(carrito)

console.log(recorrerCarrito.siguiente()) // {fin: false, valor: "Producto 1"}
console.log(recorrerCarrito.siguiente()) // {fin: false, valor: "Producto 2"}  
console.log(recorrerCarrito.siguiente()) // {fin: false, valor: "Producto 3"}
console.log(recorrerCarrito.siguiente()) // {fin: true, valor: undefined}
```

## ¿Qué son los Generadores?

Los **generadores** son funciones especiales que pueden pausar y reanudar su ejecución. Se definen con `function*` y utilizan la palabra clave `yield` para producir valores bajo demanda.

## Creando un Generador

```javascript
function* generadorCarrito(carrito) {
    for(let i = 0; i < carrito.length; i++) {
        yield carrito[i];
    }
}

const carrito = ['Producto 1', 'Producto 2', 'Producto 3']

const iterador = generadorCarrito(carrito)

console.log(iterador.next()) // {value: "Producto 1", done: false}
console.log(iterador.next()) // {value: "Producto 2", done: false}
console.log(iterador.next()) // {value: "Producto 3", done: false}
console.log(iterador.next()) // {value: undefined, done: true}
```

## Comparación: Iterador Manual vs Generador

### 👎 Iterador Manual (Más Código)
```javascript
function crearIterador(carrito) {
    let i = 0
    return {
        siguiente: () => {
            const fin = (i >= carrito.length)
            const valor = !fin ? carrito[i++] : undefined
            return { fin, valor }
        }
    }
}
```

### 👍 Generador (Más Simple)
```javascript
function* generadorCarrito(carrito) {
    for(let i = 0; i < carrito.length; i++) {
        yield carrito[i];
    }
}
```

## Protocolo de Iteración en JavaScript

### Protocolo Iterator
Un objeto es un iterador si implementa:
```javascript
{
    next() {
        return {
            value: any,    // El valor actual
            done: boolean  // true si terminó
        }
    }
}
```

### Protocolo Iterable
Un objeto es iterable si implementa:
```javascript
{
    [Symbol.iterator]() {
        return iterator; // Retorna un iterador
    }
}
```

## Iteradores en Estructuras de Datos

```javascript
const ciudades = ['Londres', 'New York', 'Madrid', 'Paris']
const ordenes = new Set([123, 231, 131, 102])
const datos = new Map()

datos.set('nombre', 'Cesar')
datos.set('profesion', 'Desarrollador Web')

// Default - itera valores
for (let ciudad of ciudades) {
    console.log(ciudad)
}
```

### Métodos de Iteración

#### Keys Iterator - Solo Claves
```javascript
for (let keys of ciudades.keys()) {
    console.log(keys) // 0, 1, 2, 3 (índices)
}

for (let keys of ordenes.keys()) {
    console.log(keys) // 123, 231, 131, 102 (valores = claves en Set)
}

for (let keys of datos.keys()) {
    console.log(keys) // 'nombre', 'profesion'
}
```

#### Values Iterator - Solo Valores
```javascript
for (let value of ciudades.values()) {
    console.log(value) // 'Londres', 'New York', etc.
}

for (let value of ordenes.values()) {
    console.log(value) // 123, 231, 131, 102
}

for (let value of datos.values()) {
    console.log(value) // 'Cesar', 'Desarrollador Web'
}
```

#### Entries Iterator - Pares [clave, valor]
```javascript
for (let entry of ciudades.entries()) {
    console.log(entry) // [0, 'Londres'], [1, 'New York'], etc.
}

for (let entry of ordenes.entries()) {
    console.log(entry) // [123, 123], [231, 231], etc.
}

for (let entry of datos.entries()) {
    console.log(entry) // ['nombre', 'Cesar'], ['profesion', 'Desarrollador Web']
}
```

## Generadores Avanzados

### Generador Infinito
```javascript
function* contadorInfinito() {
    let count = 0
    while (true) {
        yield count++
    }
}

const contador = contadorInfinito()
console.log(contador.next().value) // 0
console.log(contador.next().value) // 1
console.log(contador.next().value) // 2
```

### Generador con Parámetros
```javascript
function* generadorConParametros() {
    const x = yield 'Dame un número'
    const y = yield 'Dame otro número'
    return x + y
}

const gen = generadorConParametros()
console.log(gen.next())      // {value: "Dame un número", done: false}
console.log(gen.next(5))     // {value: "Dame otro número", done: false}
console.log(gen.next(10))    // {value: 15, done: true}
```

### Generador Fibonacci
```javascript
function* fibonacci() {
    let a = 0, b = 1
    while (true) {
        yield a
        [a, b] = [b, a + b]
    }
}

const fib = fibonacci()
for (let i = 0; i < 10; i++) {
    console.log(fib.next().value) // 0, 1, 1, 2, 3, 5, 8, 13, 21, 34
}
```

## Ventajas de Generadores vs Iteradores

### ✅ Generadores
- **Sintaxis más simple** con `function*` y `yield`
- **Menos código boilerplate**
- **Pausan automáticamente** la ejecución
- **Integración nativa** con for...of
- **Memory efficient** - valores bajo demanda

### ✅ Iteradores Manuales
- **Control total** sobre el comportamiento
- **Flexibilidad** en la implementación
- **Pueden manejar estados complejos**
- **No requieren generadores** (compatible con ES5)

## Casos de Uso Prácticos

### 1. Procesamiento de Datos Grandes
```javascript
function* procesarArchivo(lineas) {
    for (let linea of lineas) {
        // Procesar línea por línea sin cargar todo en memoria
        yield procesarLinea(linea)
    }
}
```

### 2. Implementar Range
```javascript
function* range(start, end, step = 1) {
    for (let i = start; i < end; i += step) {
        yield i
    }
}

for (let num of range(0, 10, 2)) {
    console.log(num) // 0, 2, 4, 6, 8
}
```

### 3. Control de Flujo Asíncrono
```javascript
function* flujoAsync() {
    const datos1 = yield fetch('/api/datos1')
    const datos2 = yield fetch('/api/datos2')
    const resultado = yield procesarDatos(datos1, datos2)
    return resultado
}
```

## Estructuras de Datos Iterables por Defecto

| Estructura | Iterable | Default Iterator |
|------------|----------|------------------|
| **Array** | ✅ | Valores |
| **String** | ✅ | Caracteres |
| **Set** | ✅ | Valores |
| **Map** | ✅ | Entradas [key, value] |
| **NodeList** | ✅ | Elementos DOM |
| **Object** | ❌ | No iterable |

## Hacer un Objeto Iterable

```javascript
const miObjeto = {
    datos: [1, 2, 3, 4, 5],
    
    *[Symbol.iterator]() {
        for (let item of this.datos) {
            yield item * 2
        }
    }
}

for (let valor of miObjeto) {
    console.log(valor) // 2, 4, 6, 8, 10
}
```

## Cuándo Usar Cada Uno

### Usa Generadores cuando:
- ✅ Necesites **procesamiento bajo demanda**
- ✅ Trabajes con **conjuntos de datos grandes**
- ✅ Quieras **sintaxis simple** para iteración
- ✅ Implementes **secuencias infinitas**

### Usa Iteradores Manuales cuando:
- ✅ Necesites **control fino** sobre el comportamiento
- ✅ Tengas **lógica compleja** de iteración
- ✅ Quieras **compatibilidad** con entornos antiguos
- ✅ Implementes **patrones específicos**

## Resumen

- **Iteradores** proporcionan un protocolo estándar para recorrer datos
- **Generadores** simplifican la creación de iteradores con `function*` y `yield`
- **Arrays, Set, Map** tienen iteradores nativos (keys, values, entries)
- **Generadores** son memory-efficient y procesan datos bajo demanda
- **Perfectos para datos grandes** o secuencias infinitas
- **Symbol.iterator** permite hacer cualquier objeto iterable
