# Async/Await - JavaScript Asíncrono Simplificado

## ¿Qué es Async/Await?

**Async/Await** es una sintaxis que simplifica el trabajo con código asíncrono en JavaScript. Está construido sobre Promises pero permite escribir código asíncrono que se lee como código síncrono, eliminando la necesidad de encadenar `.then()`.

## Comparación: Try/Catch vs Async/Await

### Código Síncrono con Try/Catch

```javascript
console.log(1 + 1)

try {
    hola() // Función que no existe
} catch (error) {
    console.log(error)
}

console.log(1 + 1)
```

### El Mismo Patrón pero Asíncrono

```javascript
function descargarClientes() {
    return new Promise((resolve, reject) => {
        const error = false

        setTimeout(() => {
            !error ? resolve('El listado de clientes se descargó correctamente') 
                   : reject('Error de conexión') 
        }, 3000);
    })
}
```

## Implementación con Async/Await

### Usando async function

```javascript
async function ejecutar() {
    try {
        console.log(1 + 1)

        const respuesta = await descargarClientes()

        console.log(respuesta)
        console.log(2 + 2)
    } catch (error) {
        console.log(error)
    }
}

ejecutar()
```

### Usando Arrow Functions

```javascript
const ejecutar = async () => {
    try {
        console.log(1 + 1)

        const respuesta = await descargarClientes()

        console.log(respuesta)
        console.log(2 + 2)
    } catch (error) {
        console.log(error)
    }
}

ejecutar()
```

## Múltiples Operaciones Asíncronas

### Secuencial (una después de otra)
```javascript
const app = async () => {
    try {
        console.log('Iniciando...')
        
        const clientes = await descargarNuevosClientes()
        console.log(clientes)
        
        const pedidos = await descargarNuevosPedidos()
        console.log(pedidos)
        
        console.log('Terminado')
    } catch (error) {
        console.log(error)
    }
}
```

### Paralelo (al mismo tiempo)
```javascript
function descargarNuevosClientes() {
    return new Promise(resolve => {
        console.log('Descargando clientes')

        setTimeout(() => {
            resolve('Clientes descargados')
        }, 5000)
    })
}

function descargarNuevosPedidos() {
    return new Promise(resolve => {
        console.log('Descargando pedidos')

        setTimeout(() => {
            resolve('Pedidos descargados')
        }, 3000)
    })
}

const app = async () => {
    try {
        const respuesta = await Promise.all([
            descargarNuevosClientes(), 
            descargarNuevosPedidos()
        ])
        console.log(respuesta)
    } catch (error) {
        console.log(error)
    }
}

app()
```

## Fetch API con Async/Await

```javascript
const url = 'https://picsum.photos/list'

document.addEventListener('DOMContentLoaded', obtenerDatos)

async function obtenerDatos() {
    try {
        const respuesta = await fetch(url)
        const resultado = await respuesta.json()
        console.log(resultado)
    } catch (error) {
        console.log(error)
    }
}
```

## Comparación: Promises vs Async/Await

### 👎 Con Promises (más verboso)
```javascript
function obtenerDatos() {
    fetch(url)
        .then(respuesta => respuesta.json())
        .then(datos => {
            console.log(datos)
            return procesarDatos(datos)
        })
        .then(procesados => {
            console.log(procesados)
            return guardarDatos(procesados)
        })
        .then(resultado => {
            console.log('Guardado:', resultado)
        })
        .catch(error => {
            console.log('Error:', error)
        })
}
```

### 👍 Con Async/Await (más legible)
```javascript
async function obtenerDatos() {
    try {
        const respuesta = await fetch(url)
        const datos = await respuesta.json()
        console.log(datos)
        
        const procesados = await procesarDatos(datos)
        console.log(procesados)
        
        const resultado = await guardarDatos(procesados)
        console.log('Guardado:', resultado)
    } catch (error) {
        console.log('Error:', error)
    }
}
```

## Palabras Clave

### `async`
- Se coloca **antes de la función**
- Hace que la función **siempre retorne una Promise**
- Permite usar `await` dentro de la función

### `await`
- Solo se puede usar **dentro de funciones async**
- **Pausa la ejecución** hasta que la Promise se resuelva
- **Retorna el valor** de la Promise resuelta

## Patrones Comunes

### 1. Fetch con Validación
```javascript
async function obtenerUsuario(id) {
    try {
        const respuesta = await fetch(`/api/usuarios/${id}`)
        
        if (!respuesta.ok) {
            throw new Error(`Error HTTP: ${respuesta.status}`)
        }
        
        const usuario = await respuesta.json()
        return usuario
    } catch (error) {
        console.error('Error obteniendo usuario:', error)
        throw error
    }
}
```

### 2. Múltiples APIs en Paralelo
```javascript
async function obtenerDatos() {
    try {
        const [usuarios, productos, pedidos] = await Promise.all([
            fetch('/api/usuarios').then(r => r.json()),
            fetch('/api/productos').then(r => r.json()),
            fetch('/api/pedidos').then(r => r.json())
        ])
        
        return { usuarios, productos, pedidos }
    } catch (error) {
        console.error('Error:', error)
    }
}
```

### 3. Retry Logic
```javascript
async function fetchConReintentos(url, maxReintentos = 3) {
    for (let i = 0; i < maxReintentos; i++) {
        try {
            const respuesta = await fetch(url)
            return await respuesta.json()
        } catch (error) {
            if (i === maxReintentos - 1) throw error
            console.log(`Reintento ${i + 1}...`)
            await new Promise(resolve => setTimeout(resolve, 1000))
        }
    }
}
```

## Ventajas de Async/Await

✅ **Código más legible** - parece código síncrono
✅ **Mejor debugging** - stack traces más claros
✅ **Manejo de errores unificado** con try/catch
✅ **Menos anidamiento** - evita callback hell
✅ **Compatibilidad con Promises** - funciona con código existente

## Errores Comunes

### 1. Olvidar `await`
```javascript
// ❌ Incorrecto - no espera
async function malo() {
    const datos = fetch('/api/datos') // Retorna Promise, no datos
    console.log(datos) // Promise { <pending> }
}

// ✅ Correcto
async function bueno() {
    const datos = await fetch('/api/datos')
    console.log(datos) // Response object
}
```

### 2. No usar `async` con `await`
```javascript
// ❌ Error de sintaxis
function sinAsync() {
    const datos = await fetch('/api/datos') // SyntaxError
}

// ✅ Correcto
async function conAsync() {
    const datos = await fetch('/api/datos')
}
```

### 3. No manejar errores
```javascript
// ❌ Sin manejo de errores
async function malo() {
    const datos = await fetch('/api/datos')
    // Si fetch falla, la función crashea
}

// ✅ Con manejo de errores
async function bueno() {
    try {
        const datos = await fetch('/api/datos')
        return datos
    } catch (error) {
        console.error('Error:', error)
        return null
    }
}
```

## Promise.all vs Secuencial

### ⚡ Paralelo (más rápido)
```javascript
async function paralelo() {
    const inicio = Date.now()
    
    const [datos1, datos2, datos3] = await Promise.all([
        operacionAsync1(), // 2 segundos
        operacionAsync2(), // 3 segundos  
        operacionAsync3()  // 1 segundo
    ])
    
    console.log(`Tiempo total: ${Date.now() - inicio}ms`) // ~3 segundos
}
```

### 🐌 Secuencial (más lento)
```javascript
async function secuencial() {
    const inicio = Date.now()
    
    const datos1 = await operacionAsync1() // 2 segundos
    const datos2 = await operacionAsync2() // 3 segundos
    const datos3 = await operacionAsync3() // 1 segundo
    
    console.log(`Tiempo total: ${Date.now() - inicio}ms`) // ~6 segundos
}
```

## Cuándo Usar Cada Uno

| Situación | Usar |
|-----------|------|
| **Operaciones independientes** | Promise.all (paralelo) |
| **Una operación depende de otra** | await secuencial |
| **Algunas pueden fallar** | Promise.allSettled |
| **Solo necesitas la primera** | Promise.race |

## Resumen

- **Async/Await** simplifica el código asíncrono usando sintaxis síncrona
- **`async`** hace que una función retorne una Promise
- **`await`** pausa la ejecución hasta que la Promise se resuelva
- **Try/catch** maneja errores de forma unificada
- **Promise.all** ejecuta operaciones en paralelo
- **Más legible** que Promises encadenadas
- **Compatible** con todo el ecosistema de Promises existente
