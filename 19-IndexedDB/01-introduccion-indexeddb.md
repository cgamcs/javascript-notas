# IndexedDB - Base de Datos del Navegador

## ¿Qué es IndexedDB?

**IndexedDB** es una base de datos NoSQL del lado del cliente que permite almacenar grandes cantidades de datos estructurados en el navegador web. A diferencia de localStorage, IndexedDB puede manejar datos complejos y ofrece capacidades de consulta más avanzadas.

## Características Principales

- **Asíncrono**: No bloquea la interfaz de usuario
- **Transaccional**: Garantiza la integridad de los datos
- **Gran capacidad**: Puede almacenar mucho más datos que localStorage
- **Índices**: Permite crear índices para búsquedas eficientes
- **Tipos de datos**: Soporta objetos JavaScript, arrays, fechas, etc.

## Creando una Base de Datos

### Paso 1: Abrir la Base de Datos

```javascript
let DB

function crmDB() {
    // Crear base de datos versión 1.0
    let crmDB = window.indexedDB.open('crm', 1.0)

    // Si hay un error
    crmDB.onerror = function() {
        console.log('Hubo un error a la hora de crear la BD')
    }

    // Si se creó bien
    crmDB.onsuccess = function() {
        console.log('Base de datos creada')
        DB = crmDB.result
    }

    // Configuración de la base de datos
    crmDB.onupgradeneeded = function(e) {
        // Referencia a la base de datos
        const db = e.target.result

        const objectStore = db.createObjectStore('crm', {
            keyPath: 'crm',
            autoIncrement: true
        });

        // Definir columnas (índices)
        objectStore.createIndex('nombre', 'nombre', { unique: false })
        objectStore.createIndex('email', 'email', { unique: true })
        objectStore.createIndex('telefono', 'telefono', { unique: false })

        console.log('columnas creadas')
    }
}
```

### Paso 2: Configurar el Event Listener

```javascript
document.addEventListener('DOMContentLoaded', () => {
    crmDB()

    setTimeout(() => {
        crearCliente()
    }, 3000);
})
```

## Creando Registros (Transacciones)

```javascript
function crearCliente() {
    // Crear transacción de lectura-escritura
    let transaction = DB.transaction(['crm'], 'readwrite')

    transaction.oncomplete = function() {
        console.log('Transacción Completada')
    }

    transaction.onerror = function() {
        console.log('Hubo un error')
    }

    // Obtener el object store
    const objectStore = transaction.objectStore('crm')

    // Datos del nuevo cliente
    const nuevoCliente = {
        telefono: 128912890,
        nombre: 'Cesar',
        email: 'cesar@gmail.com'
    }

    // Agregar el cliente
    const peticion = objectStore.add(nuevoCliente)

    console.log(peticion)
}
```

## Conceptos Clave

### Object Store
Es como una "tabla" en una base de datos relacional. Almacena los datos principales.

### Índices
Permiten realizar búsquedas eficientes por campos específicos:
- **unique: true**: No permite valores duplicados
- **unique: false**: Permite valores duplicados

### Transacciones
Garantizan que las operaciones se completen correctamente:
- **readonly**: Solo lectura
- **readwrite**: Lectura y escritura

### Key Path
Define cuál campo actuará como clave primaria:
- **autoIncrement: true**: Genera claves automáticamente

## Eventos Importantes

| Evento | Descripción |
|--------|-------------|
| `onerror` | Se ejecuta cuando hay un error |
| `onsuccess` | Se ejecuta cuando la operación es exitosa |
| `onupgradeneeded` | Se ejecuta cuando se crea o actualiza la estructura |
| `oncomplete` | Se ejecuta cuando la transacción se completa |

## Ventajas vs Desventajas

### ✅ Ventajas
- **Mayor capacidad** que localStorage
- **Búsquedas eficientes** con índices
- **Datos estructurados** complejos
- **Transacciones** para integridad
- **Asíncrono** - no bloquea UI

### ❌ Desventajas
- **Más complejo** que localStorage
- **API asíncrona** requiere callbacks
- **No todos los navegadores** antiguos lo soportan
- **Curva de aprendizaje** más pronunciada

## Casos de Uso Ideales

- **Aplicaciones offline** que necesitan sincronizar datos
- **Almacenamiento de archivos** grandes (imágenes, documentos)
- **Caché de datos** de APIs para mejorar rendimiento
- **Aplicaciones de gestión** con muchos registros

## Errores Comunes

1. **No manejar eventos**: Siempre definir onerror y onsuccess
2. **Versiones incorrectas**: Incrementar versión al cambiar estructura
3. **Transacciones mal configuradas**: Usar el tipo correcto (readonly/readwrite)
4. **No esperar a que la DB esté lista**: Usar setTimeout o eventos apropiados

## Resumen

- **IndexedDB** es una base de datos NoSQL potente para el navegador
- Permite almacenar **datos estructurados complejos** con gran capacidad
- Utiliza **transacciones asíncronas** para garantizar integridad
- Los **Object Stores e índices** facilitan la organización y búsqueda
- Ideal para **aplicaciones que requieren almacenamiento offline** robusto
