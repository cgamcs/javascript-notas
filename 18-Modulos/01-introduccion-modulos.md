# Módulos en JavaScript

## ¿Qué son los Módulos?

Los **módulos** en JavaScript son una forma de organizar y estructurar el código dividiéndolo en archivos separados. Cada módulo puede exportar funciones, variables, clases u objetos para que puedan ser utilizados en otros archivos mediante importaciones.

## ¿Por qué usar Módulos?

- **Organización**: Mantiene el código organizado y fácil de mantener
- **Reutilización**: Permite reutilizar código en diferentes partes de la aplicación
- **Encapsulación**: Cada módulo tiene su propio ámbito, evitando conflictos de nombres
- **Mantenimiento**: Facilita la actualización y depuración del código

## Exportaciones (Export)

### Exportación Named (Nombrada)

```javascript
// cliente.js
export const nombreCliente = 'Cesar'
export const ahorro = 200

export function mostrarInformacion(nombre, ahorro) {
    return `Nombre: ${nombre} - Ahorro: ${ahorro}`
}

export function tieneSaldo(ahorro) {
    if(ahorro > 0){
        console.log('Tiene saldo')
    } else {
        console.log('No tiene saldo')
    }
}

export class Cliente {
    constructor(nombre, ahorro) {
        this.nombre = nombre
        this.ahorro = ahorro
    }

    mostrarInformacion() {
        return `Nombre: ${this.nombre} - Ahorro: ${this.ahorro}`
    }
}
```

### Exportación Default

```javascript
// cliente.js
export default function nuevaFuncion() {
    console.log('Este es el export default')
}
```

## Importaciones (Import)

### Importación Named y Default

```javascript
// app.js
import nuevaFuncion, { nombreCliente, ahorro, mostrarInformacion, tieneSaldo, Cliente } from './cliente.js'
import { Empresa } from './empresa.js'

// Usando las importaciones
nuevaFuncion()
console.log(nombreCliente)
console.log(ahorro)
console.log(mostrarInformacion(nombreCliente, ahorro))

tieneSaldo(ahorro)

const cliente = new Cliente(nombreCliente, ahorro)
console.log(cliente.mostrarInformacion())
```

## Herencia entre Módulos

```javascript
// empresa.js
import { Cliente } from './cliente.js'

export class Empresa extends Cliente {
    constructor(nombre, ahorro, categoria) {
        super(nombre, ahorro)
        this.categoria = categoria
    }

    mostrarInformacion() {
        return `Nombre: ${this.nombre} - Ahorro: ${this.ahorro} - Categoría: ${this.categoria}`
    }
}
```

## Diferencias Clave

| Tipo de Exportación | Sintaxis Export | Sintaxis Import |
|---------------------|-----------------|------------------|
| **Named** | `export const nombre = 'Juan'` | `import { nombre } from './archivo.js'` |
| **Default** | `export default function() {}` | `import miFuncion from './archivo.js'` |
| **Mixto** | Ambas en el mismo archivo | `import default, { named } from './archivo.js'` |

## Errores Comunes

1. **Olvidar la extensión .js** en las importaciones
2. **No usar llaves `{}`** para exportaciones named
3. **Intentar usar `export default`** múltiples veces en el mismo archivo
4. **No configurar correctamente** el `type: "module"` en package.json

## Buenas Prácticas

- **Un módulo por archivo**: Mantén cada módulo en su propio archivo
- **Nombres descriptivos**: Usa nombres claros para tus exportaciones
- **Organización por carpetas**: Agrupa módulos relacionados en carpetas
- **Documentación**: Comenta qué exporta cada módulo

## Resumen

- Los **módulos** permiten dividir el código en archivos separados y reutilizables
- Existen **dos tipos de exportaciones**: named y default
- Se pueden **combinar ambos tipos** de exportación en el mismo módulo
- Los módulos facilitan la **organización, mantenimiento y reutilización** del código
- Es fundamental usar la **sintaxis correcta** para importaciones y exportaciones
