# Promises en JavaScript

## ¿Qué son las Promises?

Las **Promises** (promesas) son objetos que representan la eventual finalización (o falla) de una operación asíncrona. Son una forma más elegante de manejar código asíncrono comparado con los callbacks tradicionales, evitando el famoso "callback hell".

## Estados de una Promise

Una Promise puede estar en uno de estos tres estados:

- **Pending** 🟡: Estado inicial, ni cumplida ni rechazada
- **Fulfilled** ✅: La operación se completó exitosamente
- **Rejected** ❌: La operación falló

## Creando una Promise Básica

```javascript
const aplicandoDescuento = new Promise((resolve, reject) => {
    const descuento = true

    if(descuento) {
        resolve('Descuento aplicado')
    } else {
        reject('Descuento rechazado')
    }
})

aplicandoDescuento
    .then(resultado => descuento(resultado))
    .catch(error => descuento(error))

function descuento(mensaje) {
    console.log(mensaje)
}
```

## El Problema: Callback Hell

Antes de las Promises, el código asíncrono se veía así:

```javascript
function iniciarCallbackHell() {
    setTimeout(() => {
        nuevoPais('Alemania', mostrarPaises)
        setTimeout(() => {
            nuevoPais('Francia', mostrarPaises)
            setTimeout(() => {
                nuevoPais('Inglaterra', mostrarPaises)
            }, 3000);
        }, 3000);
    }, 3000);
}
```

## La Solución: Promise Chaining

Con Promises, el mismo código se ve mucho más limpio:

```javascript
const paises = []

const nuevoPais = pais => new Promise(resolve => {
    setTimeout(() => {
        paises.push(pais)
        resolve(`Agregado: ${pais}`)
    }, 3000);
})

nuevoPais('Alemania')
    .then(resultado => {
        console.log(resultado)
        console.log(paises)
        return nuevoPais('Francia')
    })
    .then(resultado => {
        console.log(resultado)
        console.log(paises)
        return nuevoPais('Inglaterra')
    })
    .then(resultado => {
        console.log(resultado)
        console.log(paises)
    })
```

## Comparación: Callbacks vs Promises

### 👎 Con Callbacks
```javascript
const paises = ['Mexico', 'Francia', 'España', 'Inglaterra']

function nuevoPais(pais, callback) {
    setTimeout(() => {
        paises.push(pais)
        callback()
    }, 2000);
}

function mostrarPaises() {
    setTimeout(() => {
        paises.forEach(pais => {
            console.log(pais)
        })
    }, 1000);
}

mostrarPaises()
nuevoPais('Alemania', mostrarPaises)
```

### 👍 Con Promises
```javascript
const nuevoPais = pais => new Promise(resolve => {
    setTimeout(() => {
        paises.push(pais)
        resolve(`Agregado: ${pais}`)
    }, 3000);
})
```

## Métodos Principales

### .then()
Se ejecuta cuando la Promise se resuelve exitosamente:

```javascript
promise.then(resultado => {
    console.log(resultado)
    return nuevaPromise() // Permite encadenar
})
```

### .catch()
Se ejecuta cuando la Promise es rechazada:

```javascript
promise.catch(error => {
    console.log('Error:', error)
})
```

### .finally()
Se ejecuta siempre, sin importar el resultado:

```javascript
promise.finally(() => {
    console.log('Operación completada')
})
```

## Encadenamiento (Chaining)

Una de las ventajas principales de las Promises es que se pueden encadenar:

```javascript
nuevoPais('Alemania')
    .then(resultado => {
        console.log(resultado)
        return nuevoPais('Francia') // Retorna otra Promise
    })
    .then(resultado => {
        console.log(resultado)
        return nuevoPais('Inglaterra')
    })
    .then(resultado => {
        console.log(resultado)
    })
    .catch(error => {
        console.log('Error en cualquier punto:', error)
    })
```

## Patrones Comunes

### 1. Transformación de Datos
```javascript
fetch('/api/users')
    .then(response => response.json())
    .then(users => users.map(user => user.name))
    .then(names => console.log(names))
```

### 2. Manejo de Errores Específicos
```javascript
promise
    .then(data => processData(data))
    .catch(error => {
        if (error.type === 'NetworkError') {
            console.log('Error de red')
        } else {
            console.log('Otro error:', error)
        }
    })
```

## Ventajas de las Promises

✅ **Código más legible**: Evita el callback hell
✅ **Mejor manejo de errores**: Un solo .catch() puede manejar múltiples errores
✅ **Encadenamiento**: Fácil composición de operaciones asíncronas
✅ **Estandarización**: Parte del estándar ES6

## Errores Comunes

1. **No retornar en .then()**: Si no retornas, el siguiente .then() recibe undefined
2. **No manejar errores**: Siempre incluir .catch()
3. **Crear Promises innecesarias**: No envolver funciones que ya retornan Promises
4. **Olvidar que son asíncronas**: No asumir que el código se ejecuta inmediatamente

## Cuándo Usar Promises

- **Operaciones de red** (fetch, axios)
- **Operaciones de archivos** (lectura/escritura)
- **Temporizadores** complejos
- **Cualquier operación asíncrona** que puede fallar

## Resumen

- Las **Promises** resuelven el problema del callback hell
- Tienen **tres estados**: pending, fulfilled, rejected
- Permiten **encadenar operaciones** con .then()
- Facilitan el **manejo de errores** con .catch()
- Son la **base para async/await** (que veremos más adelante)
- Hacen el código asíncrono **más legible y mantenible**
