# Set - Estructura de Datos con Valores Únicos

## ¿Qué es un Set?

Un **Set** es una estructura de datos que almacena valores únicos. A diferencia de los arrays, un Set no permite valores duplicados y mantiene automáticamente la unicidad de sus elementos.

## Creando un Set

```javascript
const carrito = new Set()

// Agregando elementos
carrito.add('Camisa 1')
carrito.add('Camisa 2')
carrito.add('Camisa 3')
carrito.add('Camisa 4')

console.log(carrito)
```

## Métodos Principales

### .add() - Agregar Elementos
```javascript
carrito.add('Camisa 1')
carrito.add('Camisa 2')
// Si intentas agregar el mismo valor, no se duplica
carrito.add('Camisa 1') // No se agrega porque ya existe
```

### .size - Tamaño del Set
```javascript
console.log(carrito.size) // 4 (número de elementos únicos)
```

### .has() - Verificar si Existe
```javascript
console.log(carrito.has('Camisa 1')) // true
console.log(carrito.has('Camisa 5')) // false
```

### .delete() - Eliminar Elementos
```javascript
carrito.delete('Camisa 4')
console.log(carrito.delete('Camisa 4')) // false (ya no existe)
```

### .clear() - Limpiar Todo
```javascript
// carrito.clear() // Elimina todos los elementos
```

## Iterando un Set

### Con forEach
```javascript
carrito.forEach((producto, index, pertenece) => {
    console.log(producto)    // El valor
    console.log(index)       // El mismo valor (en Set, key = value)
    console.log(pertenece)   // El Set completo
})
```

### Con for...of
```javascript
for (let producto of carrito) {
    console.log(producto)
}
```

## Caso de Uso Práctico: Eliminar Duplicados

### Problema Común
```javascript
const numeros = [10, 20, 30, 40, 50, 10, 20]
// Array con duplicados
```

### Solución con Set
```javascript
const numeros = [10, 20, 30, 40, 50, 10, 20]
const noDuplicados = new Set(numeros)

console.log(noDuplicados) // Set {10, 20, 30, 40, 50}

// Convertir de vuelta a array si es necesario
const arrayLimpio = [...noDuplicados]
console.log(arrayLimpio) // [10, 20, 30, 40, 50]
```

## Set vs Array

| Característica | Array | Set |
|----------------|-------|-----|
| **Duplicados** | ✅ Permite | ❌ No permite |
| **Índices** | ✅ Tiene índices | ❌ No tiene índices |
| **Longitud** | `.length` | `.size` |
| **Buscar** | `.indexOf()` | `.has()` |
| **Agregar** | `.push()` | `.add()` |
| **Eliminar** | `.splice()` | `.delete()` |

## WeakSet - Versión "Débil" del Set

```javascript
const weakset = new WeakSet()

const cliente = {
    nombre: 'Cesar',
    apellido: 'Garcia'
}

// Solo acepta objetos, no primitivos
weakset.add(cliente)

console.log(weakset)

// Esto NO funcionaría:
// const nombre = 'Cesar'
// weakset.add(nombre) // Error: Valor no válido
```

### Características de WeakSet
- **Solo objetos**: No acepta valores primitivos
- **Garbage Collection**: Los objetos pueden ser recolectados por el garbage collector
- **No enumerable**: No se puede iterar
- **Métodos limitados**: Solo `.add()`, `.has()`, `.delete()`

## Casos de Uso del Set

### 1. Lista de Elementos Únicos
```javascript
const hobbies = new Set()
hobbies.add('programar')
hobbies.add('leer')
hobbies.add('programar') // No se duplica
```

### 2. Tracking de Visitantes Únicos
```javascript
const visitantesUnicos = new Set()
visitantesUnicos.add('usuario123')
visitantesUnicos.add('usuario456')
visitantesUnicos.add('usuario123') // No cuenta doble visita
```

### 3. Filtros de Búsqueda
```javascript
const categorias = new Set(['ropa', 'tecnología', 'hogar'])
const filtrosActivos = new Set()

// Agregar/quitar filtros sin duplicados
filtrosActivos.add('ropa')
filtrosActivos.add('tecnología')
```

## Métodos de Conversión

### Set a Array
```javascript
const set = new Set([1, 2, 3, 4])
const array = [...set]          // [1, 2, 3, 4]
const array2 = Array.from(set)  // [1, 2, 3, 4]
```

### Array a Set
```javascript
const array = [1, 2, 2, 3, 3, 4]
const set = new Set(array)      // Set {1, 2, 3, 4}
```

## Ventajas del Set

✅ **Unicidad automática** - no necesitas verificar duplicados
✅ **Rendimiento** - `.has()` es más rápido que `.indexOf()`
✅ **API limpia** - métodos específicos para su propósito
✅ **Memoria eficiente** - no almacena duplicados

## Desventajas del Set

❌ **No tiene índices** - no puedes acceder por posición
❌ **Menos métodos** - no tiene map, filter, reduce
❌ **No mutable por índice** - no puedes cambiar valores específicos

## Cuándo Usar Set

- ✅ Cuando necesites **valores únicos**
- ✅ Para **verificar existencia** frecuentemente
- ✅ **Eliminar duplicados** de arrays
- ✅ **Tracking de elementos** únicos
- ❌ Cuando necesites **índices** o **orden específico**
- ❌ Para **transformaciones** complejas de datos

## Resumen

- **Set** almacena valores únicos automáticamente
- **No permite duplicados** - mantiene unicidad
- **Excelente rendimiento** para verificar existencia
- **Ideal para filtrar duplicados** de arrays
- **WeakSet** es para objetos con gestión automática de memoria
- **Perfecto cuando la unicidad** es más importante que el orden
