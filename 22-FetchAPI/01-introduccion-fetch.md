# Fetch API - Peticiones HTTP Modernas

## ¿Qué es Fetch API?

**Fetch API** es la forma moderna de realizar peticiones HTTP en JavaScript. Reemplaza a XMLHttpRequest con una interfaz más limpia y basada en Promises, permitiendo obtener datos de servidores de manera asíncrona.

## Ventajas de Fetch sobre XMLHttpRequest

✅ **Sintaxis más simple** y legible
✅ **Basado en Promises** - mejor manejo asíncrono
✅ **Interfaz moderna** y estándar
✅ **Mayor flexibilidad** en configuración
✅ **Mejor manejo de errores**

## Ejemplo Básico - Cargar Archivo de Texto

```javascript
const cargarTxtBtn = document.querySelector('#cargarTxt')
cargarTxtBtn.addEventListener('click', obtenerDatos)

function obtenerDatos() {
    const url = 'data/datos.txt'
    
    fetch(url)
        .then(respuesta => {
            console.log(respuesta)
            console.log(respuesta.status)      // 200
            console.log(respuesta.statusText)  // "OK"
            console.log(respuesta.type)        // "basic"
            console.log(respuesta.url)         // URL completa

            return respuesta.text()
        })
        .then(datos => {
            console.log(datos)
        })
        .catch(error => {
            console.log(error)
        })
}
```

## Cargando Datos JSON

### JSON Simple

```javascript
const cargarJsonBtn = document.querySelector('#cargarJSON')
cargarJsonBtn.addEventListener('click', obtenerDatos)

function obtenerDatos() {
    const url = 'data/empleado.json'

    fetch(url)
        .then(respuesta => {
            console.log(respuesta.status)
            console.log(respuesta.statusText)
            console.log(respuesta.type)
            console.log(respuesta.url)

            return respuesta.json()
        })
        .then(datos => {
            mostrarHTML(datos)
        })
        .catch(error => {
            console.log(error)
        })
}

function mostrarHTML({empresa, id, nombre, trabajo}) {
    const contenido = document.querySelector('.contenido')
    contenido.innerHTML = `
        <p>Empleado: ${nombre}</p>
        <p>Empresa: ${empresa}</p>
        <p>Trabajo: ${trabajo}</p>
        <p>ID: ${id}</p>
    `
}
```

### Array de JSON

```javascript
const cargarJSONBtn = document.querySelector('#cargarJSONArray')
cargarJSONBtn.addEventListener('click', obtenerDatos)

function obtenerDatos() {
    const url = 'data/empleados.json'

    fetch(url)
        .then(respuesta => respuesta.json())
        .then(datos => mostrarHTML(datos))
}

function mostrarHTML(empleados) {
    const contenido = document.querySelector('.contenido')

    let html = ''

    empleados.forEach(empleado => {
        const { nombre, id, empresa, trabajo } = empleado

        html += `
            <p>Empleado: ${nombre}</p>
            <p>Empresa: ${empresa}</p>
            <p>Trabajo: ${trabajo}</p>
            <p>ID: ${id}</p>
        `
    });

    contenido.innerHTML = html
}
```

## Consumiendo APIs Externas

```javascript
const cargarAPI = document.querySelector('#cargarAPI')
cargarAPI.addEventListener('click', obtenerDatos)

function obtenerDatos() {
    const url = 'https://picsum.photos/list'

    fetch(url)
        .then(respuesta => respuesta.json())
        .then(datos => mostrarHTML(datos))
}

function mostrarHTML(datos) {
    const contenido = document.querySelector('.contenido')

    let html = ''

    datos.forEach(perfil => {
        const { author, post_url } = perfil

        html += `
            <p>Autor: ${author}</p>
            <a href="${post_url}" target="_blank">Ver Imagen</a>
        `
    });

    contenido.innerHTML = html
}
```

## Métodos de Respuesta

| Método | Descripción | Uso |
|--------|-------------|-----|
| `.text()` | Convierte a texto plano | Archivos .txt, HTML |
| `.json()` | Parsea como JSON | APIs, datos estructurados |
| `.blob()` | Para archivos binarios | Imágenes, archivos |
| `.arrayBuffer()` | Buffer de datos | Datos binarios avanzados |

## Propiedades de la Respuesta

### Información del Estado

```javascript
fetch(url).then(respuesta => {
    console.log(respuesta.status)     // 200, 404, 500, etc.
    console.log(respuesta.statusText) // "OK", "Not Found", etc.
    console.log(respuesta.ok)         // true si status 200-299
    console.log(respuesta.type)       // "basic", "cors", "opaque"
    console.log(respuesta.url)        // URL final (después de redirects)
})
```

## Patrón de Uso Común

### Versión Completa
```javascript
fetch(url)
    .then(respuesta => {
        // Verificar si la respuesta es exitosa
        if (!respuesta.ok) {
            throw new Error(`Error: ${respuesta.status}`)
        }
        return respuesta.json()
    })
    .then(datos => {
        // Procesar los datos
        console.log(datos)
    })
    .catch(error => {
        // Manejar errores
        console.error('Error:', error)
    })
```

### Versión Simplificada
```javascript
fetch(url)
    .then(respuesta => respuesta.json())
    .then(datos => mostrarHTML(datos))
    .catch(error => console.log(error))
```

## Comparación: Antes vs Ahora

### 👎 XMLHttpRequest (Antiguo)
```javascript
const xhr = new XMLHttpRequest()
xhr.open('GET', 'data/empleados.json')
xhr.onreadystatechange = function() {
    if (xhr.readyState === 4 && xhr.status === 200) {
        const datos = JSON.parse(xhr.responseText)
        mostrarHTML(datos)
    }
}
xhr.send()
```

### 👍 Fetch API (Moderno)
```javascript
fetch('data/empleados.json')
    .then(respuesta => respuesta.json())
    .then(datos => mostrarHTML(datos))
```

## Manejo de Errores

### Tipos de Errores
1. **Errores de red**: Sin conexión, servidor caído
2. **Errores HTTP**: 404, 500, etc.
3. **Errores de parsing**: JSON malformado

### Manejo Robusto
```javascript
fetch(url)
    .then(respuesta => {
        if (!respuesta.ok) {
            if (respuesta.status === 404) {
                throw new Error('Archivo no encontrado')
            } else if (respuesta.status === 500) {
                throw new Error('Error del servidor')
            } else {
                throw new Error(`Error: ${respuesta.status}`)
            }
        }
        return respuesta.json()
    })
    .then(datos => {
        // Procesar datos
    })
    .catch(error => {
        console.error('Error capturado:', error.message)
    })
```

## Mejores Prácticas

### 1. Verificar Estado
```javascript
if (!respuesta.ok) {
    throw new Error(`HTTP error! status: ${respuesta.status}`)
}
```

### 2. Manejar Diferentes Tipos de Contenido
```javascript
const contentType = respuesta.headers.get('content-type')
if (contentType && contentType.includes('application/json')) {
    return respuesta.json()
} else {
    return respuesta.text()
}
```

### 3. Loading States
```javascript
function obtenerDatos() {
    mostrarLoading(true)
    
    fetch(url)
        .then(respuesta => respuesta.json())
        .then(datos => {
            mostrarHTML(datos)
            mostrarLoading(false)
        })
        .catch(error => {
            mostrarError(error)
            mostrarLoading(false)
        })
}
```

## Casos de Uso Comunes

- **Cargar datos de configuración** al iniciar la app
- **Obtener contenido dinámico** desde APIs
- **Cargar archivos de texto** o JSON
- **Consumir servicios web** externos
- **Implementar autocompletado** con búsquedas
- **Cargar contenido bajo demanda** (lazy loading)

## Limitaciones y Consideraciones

- **CORS**: Puede haber restricciones de origen cruzado
- **Soporte**: No disponible en Internet Explorer
- **Timeouts**: No tiene timeout por defecto
- **Abortar peticiones**: Requiere AbortController

## Resumen

- **Fetch API** es la forma moderna de hacer peticiones HTTP
- **Basado en Promises** - más limpio que XMLHttpRequest
- **Múltiples formatos**: .text(), .json(), .blob()
- **Información completa** de la respuesta (status, headers, etc.)
- **Manejo de errores** más claro y estructurado
- **Ideal para APIs modernas** y desarrollo web actual
