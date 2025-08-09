# APIs del Navegador

## ¿Qué son las APIs del Navegador?

Las **APIs del navegador** son interfaces que nos permiten acceder a funcionalidades específicas del navegador web como notificaciones, geolocalización, cámara, micrófono, pantalla completa, y muchas más. Estas APIs nos dan superpoderes para crear experiencias web más ricas e interactivas.

## 1. Notification API - Notificaciones del Sistema

### Solicitar Permisos

```javascript
const notificarBtn = document.querySelector('#notificar')

notificarBtn.addEventListener('click', () => {
    Notification
        .requestPermission()
        .then(resultado => {
            console.log('El resultado es ', resultado)
        })
})
```

### Mostrar Notificaciones

```javascript
const verNotificacion = document.querySelector('#verNotificacion')
verNotificacion.addEventListener('click', () => {
    if(Notification.permission === 'granted') {
        const notificacion = new Notification('Esta es la notificación', {
            icon: 'img/ccj.png',
            body: 'Aprende a programar con Juan'
        })

        notificacion.onclick = () => {
            window.open('https://www.codigoconjuan.com')
        }
    }
})
```

## 2. Intersection Observer API - Detección de Visibilidad

```javascript
document.addEventListener('DOMContentLoaded', () => {
    const observer = new IntersectionObserver(entries => {
        if(entries[0].isIntersecting) {
            console.log('Ya está visible')
        }
    })

    observer.observe(document.querySelector('.premium'))
})
```

### Casos de Uso
- **Lazy loading** de imágenes
- **Animaciones** al hacer scroll
- **Analíticas** de visualización
- **Infinite scroll**

## 3. Network Information API - Estado de Conexión

```javascript
window.addEventListener('online', actualizarEstado)
window.addEventListener('offline', actualizarEstado)

function actualizarEstado() {
    if(navigator.onLine) {
        console.log('Sí estás conectado')
    } else {
        console.log('No estás conectado')
    }
}
```

### Aplicaciones Prácticas
- **Modo offline** en aplicaciones
- **Sincronización** de datos
- **Mensajes de estado** de conexión
- **Optimización** según conectividad

## 4. Fullscreen API - Pantalla Completa

```javascript
const abrirBtn = document.querySelector('#abrir-pantalla-completa')
const salirBtn = document.querySelector('#salir-pantalla-completa')

abrirBtn.addEventListener('click', pantallaCompleta)
salirBtn.addEventListener('click', cerrarPantallaCompleta)

function pantallaCompleta() {
    document.documentElement.requestFullscreen()
}

function cerrarPantallaCompleta() {
    document.exitFullscreen()
}
```

### Casos de Uso
- **Presentaciones** web
- **Juegos** en línea
- **Reproductores de video**
- **Aplicaciones inmersivas**

## 5. Page Visibility API - Detección de Visibilidad de Página

```javascript
document.addEventListener('visibilitychange', () => {
    if(document.visibilityState === 'visible') {
        console.log('Ejecutar función para ver el video')
    } else {
        console.log('Pausar el video')
    }
})
```

### Aplicaciones
- **Pausar/reanudar videos** automáticamente
- **Suspender animaciones** cuando no están visibles
- **Optimizar recursos** del sistema
- **Analíticas** de tiempo en página

## 6. Speech Recognition API - Reconocimiento de Voz

```javascript
const salida = document.querySelector('#salida')
const microfono = document.querySelector('#microfono')

microfono.addEventListener('click', ejecutarSpeechAPI)

function ejecutarSpeechAPI() {
    const SpeechRecognition = webkitSpeechRecognition
    const recognition = new SpeechRecognition()

    recognition.start()

    recognition.onstart = function() {
        salida.classList.add('mostrar')
        salida.textContent = 'Escuchando...'
    }

    recognition.onspeechend = function() {
        salida.textContent = 'Se dejó de grabar'
        recognition.stop()
    }

    recognition.onresult = function(e) {
        setTimeout(() => {
            const { confidence, transcript } = e.results[0][0]

            const speech = document.createElement('P')
            speech.innerHTML = `Grabado: ${transcript}`

            const seguridad = document.createElement('P')
            seguridad.innerHTML = `Confianza: ${parseInt(confidence * 100)}%`

            salida.appendChild(speech)
            salida.appendChild(seguridad)
        }, 1000);
    }
}
```

### Características
- **Transcripción en tiempo real**
- **Nivel de confianza** en el resultado
- **Múltiples idiomas** soportados
- **Control por voz** en aplicaciones

## Comparación de APIs

| API | Soporte | Casos de Uso | Complejidad |
|-----|---------|--------------|-------------|
| **Notification** | ✅ Excelente | Alertas, recordatorios | 🟢 Fácil |
| **Intersection Observer** | ✅ Muy bueno | Lazy loading, animaciones | 🟡 Media |
| **Network Info** | ⚠️ Limitado | Apps offline, sync | 🟢 Fácil |
| **Fullscreen** | ✅ Excelente | Juegos, presentaciones | 🟢 Fácil |
| **Page Visibility** | ✅ Excelente | Optimización recursos | 🟢 Fácil |
| **Speech Recognition** | ⚠️ Webkit mainly | Control por voz | 🔴 Compleja |

## Mejores Prácticas

### 1. Verificar Soporte
```javascript
if ('Notification' in window) {
    // La API está disponible
} else {
    // Fallback o mensaje de error
}
```

### 2. Manejar Permisos Correctamente
```javascript
if (Notification.permission === 'granted') {
    // Crear notificación
} else if (Notification.permission !== 'denied') {
    // Solicitar permiso
}
```

### 3. Proporcionar Fallbacks
```javascript
try {
    // Usar API moderna
    const observer = new IntersectionObserver(...)
} catch (error) {
    // Fallback para navegadores antiguos
    window.addEventListener('scroll', ...)
}
```

## Errores Comunes

1. **No verificar soporte**: No todas las APIs están en todos los navegadores
2. **Ignorar permisos**: Muchas APIs requieren permisos del usuario
3. **No manejar errores**: Las APIs pueden fallar por varias razones
4. **Sobre-uso**: No todas las apps necesitan todas las APIs

## Consideraciones de UX

- **Pedir permisos en contexto**: No solicites permisos inmediatamente
- **Explicar beneficios**: Di por qué necesitas el permiso
- **Graceful degradation**: La app debe funcionar sin las APIs
- **Respeto al usuario**: No abuses de notificaciones o APIs

## Resumen

- Las **APIs del navegador** extienden las capacidades de las aplicaciones web
- Cada API resuelve **problemas específicos** de UX y funcionalidad
- Es crucial **verificar soporte** y manejar permisos apropiadamente
- Permiten crear **experiencias más ricas** e interactivas
- Siempre proporcionar **fallbacks** para navegadores que no las soporten
