# 🤖 Guía Práctica: Trabajar con el Agente AI

> **Un ejemplo completo de principio a fin**: Desde recibir el step en Jira hasta crear la versión final.

---

## 📖 Índice

### 1. [🎯 Visión General del Proceso](#-visión-general-del-proceso)

### 2. [🔄 Trabajar en Múltiples Sesiones de Chat](#-trabajar-en-múltiples-sesiones-de-chat)
   - [Estrategia: División por Fases](#-estrategia-recomendada-división-por-fases)
   - [Plantilla: Inicio de Chat (Análisis)](#-plantilla-inicio-de-chat-análisis)
   - [Plantilla: Continuación (Desarrollo)](#-plantilla-continuación-de-chat-desarrollo)
   - [Plantilla: Chat de QA](#-plantilla-chat-de-qa)
   - [Plantilla: Chat de Versionado](#-plantilla-chat-de-versionado)
   - [Tips para Máxima Eficiencia](#-tips-para-máxima-eficiencia-entre-chats)
   - [Flujo Óptimo Multi-Chat](#-flujo-óptimo-multi-chat)
   - [Ejemplo Real Multi-Chat](#-ejemplo-real-de-multi-chat)
   - [Reglas de Oro](#-resumen-reglas-de-oro)

### 3. [📝 Fase 1: Inicio - Análisis del Step](#-fase-1-inicio---análisis-del-step)
   - [Plantilla del Prompt Ideal](#-plantilla-del-prompt-ideal)
   - [Ejemplo Real - AMPC-1305](#-ejemplo-real---ampc-1305)
   - [Mi Análisis Completo](#-mi-respuesta)

### 4. [📋 Fase 2: Planificación - Crear Subtareas en Jira](#-fase-2-planificación---crear-subtareas-en-jira)
   - [Plantilla del Prompt](#-plantilla-del-prompt-ideal-1)
   - [Ejemplo Real](#-ejemplo-real---ampc-1305-1)
   - [8 Subtareas Detalladas](#-mi-respuesta-1)

### 5. [💻 Fase 3: Desarrollo - Implementar Subtareas](#-fase-3-desarrollo---implementar-subtareas)
   - [Plantilla del Prompt](#-plantilla-del-prompt-ideal-2)
   - [Día 2: Subtarea 1 - Dependencias](#-día-2-subtarea-1---dependencias)
   - [Día 3: Subtarea 2 - Tipos](#-día-3-subtarea-2---tipos)
   - [Día 4: Subtarea 3 - Servicio](#-día-4-subtarea-3---servicio)
   - [Día 5: Subtarea 4 - Hook](#-día-5-subtarea-4---hook)
   - [Día 6: Subtarea 5 - Botón](#-día-6-subtarea-5---botón-en-componente)
   - [Días siguientes: Subtareas 6, 7, 8](#-día-6-continuación-subtareas-6-7-8)

### 6. [✅ Fase 4: QA - Revisión de Código](#-fase-4-qa---revisión-de-código)
   - [Plantilla del Prompt](#-plantilla-del-prompt-ideal-3)
   - [Ejemplo Real](#-ejemplo-real---ampc-1305-2)
   - [Mi Revisión Completa](#-mi-respuesta-2)

### 7. [📦 Fase 5: Versionado - Crear Release](#-fase-5-versionado---crear-release)
   - [Plantilla del Prompt](#-plantilla-del-prompt-ideal-4)
   - [Ejemplo Real](#-ejemplo-real---ampc-1305-3)
   - [Proceso de Versionado](#-mi-acción)

### 8. [💡 Tips y Buenas Prácticas](#-tips-y-buenas-prácticas)
   - [Mejores formas de comunicarte](#-mejores-formas-de-comunicarte-conmigo)
   - [Puedo leer imágenes](#-puedo-leer-imágenes)
   - [Cuándo hacer cada cosa](#-cuándo-hacer-cada-cosa)
   - [Comandos útiles](#-comandos-que-puedo-ejecutar)
   - [Lo que NO hago](#-lo-que-no-hago-y-está-bien)

### 9. [📜 Trabajar con .cursorrules](#-trabajar-con-cursorrules)
   - [¿Qué son las .cursorrules?](#-qué-son-las-cursorrules)
   - [Cómo las uso automáticamente](#-cómo-las-uso-automáticamente)
   - [Cuándo actualizar las .cursorrules](#-cuándo-actualizar-las-cursorrules)
   - [Tips para mantener las reglas](#-tips-para-mantener-las-reglas)
   - [Ejemplos de uso](#-ejemplos-de-uso)

### 10. [🆘 Solución de Problemas](#-solución-de-problemas)
   - [No encuentras el componente](#problema-no-encuentras-el-componente-que-te-menciono)
   - [El código no funciona](#problema-el-código-que-generaste-no-funciona)
   - [Quiero cambiar la subtarea](#problema-quiero-cambiar-algo-de-la-subtarea)
   - [¿Por qué hiciste esto así?](#problema-por-qué-hiciste-esto-así)
   - [Prefiero otro approach](#problema-prefiero-otro-approach)
   - [Olvidé algo](#problema-olvidé-algo-en-el-step)

### 11. [📋 Template de Inicio Rápido](#-template-de-inicio-rápido)

---

## 🎯 Visión General del Proceso

Vamos a seguir un ejemplo real completo: **AMPC-1305 - Añadir botón de descarga múltiple en OverviewModule**

```
STEP COMPLETO: De Jira → Código → Tests → Versión

Día 1:    📝 Recibes el step → Análisis → Crear subtareas en Jira
Día 2-5:  💻 Implementar subtareas (una por día)
Día 6:    ✅ QA completo del feature
Día 7:    📦 Crear versión y marcar step como Done
```

---

## 🔄 Trabajar en Múltiples Sesiones de Chat

### ⚠️ Realidad: Límite de Contexto

Un step completo NO se puede hacer en un solo chat. Llegarás al límite de contexto (tokens). Por eso necesitas dividir el trabajo en múltiples sesiones.

### 📅 Estrategia Recomendada: División por Fases

```
CHAT 1 (Día 1):  Análisis + Planificación
  ├─ Análisis completo del step
  └─ Crear subtareas de Jira

CHAT 2 (Día 2):  Subtareas 1-2
  ├─ Implementar subtarea 1
  └─ Implementar subtarea 2

CHAT 3 (Día 3):  Subtareas 3-4
  ├─ Implementar subtarea 3
  └─ Implementar subtarea 4

CHAT 4 (Día 4):  Subtareas 5-6
  ├─ Implementar subtarea 5
  └─ Implementar subtarea 6

CHAT 5 (Día 5):  Subtareas 7-8
  ├─ Implementar subtarea 7
  └─ Implementar subtarea 8

CHAT 6 (Día 6):  QA + Versionado
  ├─ Revisión completa
  └─ Crear versión
```

---

## 🎯 Cómo Ponerme en Contexto en Cada Chat

### Regla de Oro

**Siempre empieza cada nuevo chat con un "Estado del Step"**

---

### 📋 Plantilla: Inicio de Chat (Análisis)

```markdown
Step nuevo: AMPC-XXXX

**Descripción:**
[Descripción completa de Jira]

**Criterios de aceptación:**
- [Lista completa]

**Diseño:**
[Imagen o enlace]
```

---

### 📋 Plantilla: Continuación de Chat (Desarrollo)

```markdown
Continúo con AMPC-XXXX: "[Título del step]"

**Estado actual:**
✅ Subtarea 1: [Título] - Commit: abc123
✅ Subtarea 2: [Título] - Commit: def456
⏳ Subtarea 3: [Título] - VOY A HACER ESTA
⬜ Subtarea 4: [Título] - Pendiente
⬜ Subtarea 5: [Título] - Pendiente

**Ahora voy a:**
Implementar subtarea 3: [Descripción de la subtarea]

[Opcional: Pega la descripción completa de la subtarea desde Jira]
```

#### Ejemplo Real:

```markdown
Continúo con AMPC-1305: "Añadir botón de descarga múltiple en OverviewModule"

**Estado actual:**
✅ Subtarea 1: Verificar dependencias - Commit: a1b2c3d
✅ Subtarea 2: Crear tipos e interfaces - Commit: b2c3d4e
⏳ Subtarea 3: Implementar DownloadZipService - VOY A HACER ESTA
⬜ Subtarea 4: Crear hook useDownloadAllVariants - Pendiente
⬜ Subtarea 5: Añadir botón en OverviewModule - Pendiente
⬜ Subtarea 6: Aplicar estilos - Pendiente
⬜ Subtarea 7: Tests de integración - Pendiente
⬜ Subtarea 8: Actualizar Storybook - Pendiente

**Ahora voy a:**
Implementar subtarea 3: Crear servicio DownloadZipService que genere archivos 
ZIP a partir de múltiples Blobs usando JSZip, con validaciones y tests completos.
```

---

### 📋 Plantilla: Chat de QA

```markdown
QA completo de AMPC-XXXX: "[Título del step]"

**Todas las subtareas completadas:**
✅ Subtarea 1: [Título] - Commit: abc123
✅ Subtarea 2: [Título] - Commit: def456
✅ Subtarea 3: [Título] - Commit: ghi789
✅ Subtarea 4: [Título] - Commit: jkl012
✅ Subtarea 5: [Título] - Commit: mno345
✅ Subtarea 6: [Título] - Commit: pqr678
✅ Subtarea 7: [Título] - Commit: stu901
✅ Subtarea 8: [Título] - Commit: vwx234

**Rama:** AMPC-XXXX_[descripcion]

Revisa el código completo antes de crear la versión.
```

---

### 📋 Plantilla: Chat de Versionado

```markdown
Crear versión para AMPC-XXXX: "[Título del step]"

**QA completado:** ✅ Sin errores

**Rama:** AMPC-XXXX_[descripcion]

Crea la versión [minor/patch] e incluye en el changelog.
```

---

## 💡 Tips para Máxima Eficiencia entre Chats

### ✅ Al TERMINAR cada chat

Antes de cerrar la sesión, pídeme:

```markdown
Resume el estado actual de AMPC-XXXX para el próximo chat
```

**Mi respuesta será algo como:**

```markdown
📊 RESUMEN - AMPC-1305

Para el próximo chat, usa este prompt:

═══════════════════════════════════════════════════════════

Continúo con AMPC-1305: "Añadir botón de descarga múltiple"

**Estado actual:**
✅ Subtarea 1: Verificar dependencias - a1b2c3d
✅ Subtarea 2: Crear tipos - b2c3d4e
⏳ Siguiente: Subtarea 3: Implementar DownloadZipService

**Archivos creados hasta ahora:**
• package.json (añadidas dependencias jszip, file-saver)
• src/data-model/ProductFiles/DownloadAllVariants.ts

**Ahora voy a:**
Implementar subtarea 3: DownloadZipService con tests

═══════════════════════════════════════════════════════════

Copia todo esto en el próximo chat.
```

Copia ese resumen y úsalo para iniciar el siguiente chat.

---

### ✅ Al INICIAR cada chat

Incluye siempre:

1. **ID del step**: AMPC-XXXX
2. **Título breve** del step
3. **Estado actual**: Qué está hecho (con commits)
4. **Qué vas a hacer ahora**: Subtarea específica

---

### 🚫 NO hagas esto

❌ "Continúa con AMPC-1305"  
→ No sé qué ya está hecho

❌ "Implementa la siguiente subtarea"  
→ No sé cuál es la siguiente

❌ "Sigue con lo de ayer"  
→ No tengo memoria entre chats

---

### ✅ SÍ haz esto

✅ "Continúo AMPC-1305. Ya hice subtareas 1-2 (commits a1b2c3d, b2c3d4e). Ahora subtarea 3: DownloadZipService"

✅ "AMPC-1305: Análisis completo y crear subtareas de Jira"

✅ "QA de AMPC-1305. Rama: AMPC-1305_download_multiple. 8 subtareas completadas."

---

## 🎯 Flujo Óptimo Multi-Chat

### Chat 1: Análisis y Planificación (15-20 min)

```
Inicio → Análisis → Subtareas → FIN

Al terminar:
"Resume el estado para el próximo chat"
```

**Resultado:** Subtareas en Jira listas para implementar

---

### Chat 2-5: Desarrollo (1-2 subtareas por chat)

```
Inicio con estado → Subtarea X → Commit → Subtarea Y → Commit → FIN

Al terminar:
"Resume el estado para el próximo chat"
```

**Resultado:** Código implementado, tests, commits

---

### Chat 6: QA y Versionado (10-15 min)

```
Inicio con estado completo → QA → Correcciones → Versión → FIN
```

**Resultado:** Versión creada, lista para PR

---

## 📊 Ejemplo Real de Multi-Chat

### 📅 Chat 1 (Lunes)

**Tu prompt:**
```markdown
Tengo el step AMPC-1305: "Añadir botón de descarga múltiple en OverviewModule"

[Descripción completa + criterios]
```

**Al final del chat:**
```markdown
Resume el estado para el próximo chat
```

**Mi resumen:**
```markdown
Para mañana:
Continúo AMPC-1305: "Añadir botón de descarga múltiple"
Estado: Análisis completo ✅, 8 subtareas creadas ✅
Siguiente: Subtarea 1 (Verificar dependencias)
```

---

### 📅 Chat 2 (Martes)

**Tu prompt:**
```markdown
Continúo AMPC-1305: "Añadir botón de descarga múltiple"

Estado: Análisis completo ✅, 8 subtareas creadas ✅
⏳ Voy a hacer: Subtareas 1 y 2
```

**Trabajo:**
- Implemento subtarea 1 → Commit
- Implemento subtarea 2 → Commit

**Al final:**
```markdown
Resume el estado para el próximo chat
```

**Mi resumen:**
```markdown
Para mañana:
Continúo AMPC-1305
✅ Subtarea 1: Dependencias - a1b2c3d
✅ Subtarea 2: Tipos - b2c3d4e
⏳ Siguiente: Subtareas 3 y 4
```

---

### 📅 Chat 3 (Miércoles)

**Tu prompt:**
```markdown
Continúo AMPC-1305: "Añadir botón de descarga múltiple"

✅ Subtarea 1: Dependencias - a1b2c3d
✅ Subtarea 2: Tipos - b2c3d4e
⏳ Voy a hacer: Subtareas 3 y 4
```

Y así sucesivamente...

---

### 📅 Chat 6 (Sábado)

**Tu prompt:**
```markdown
QA completo de AMPC-1305

Todas las subtareas completadas:
✅ Subtarea 1-8 (commits: a1b2c3d...h8i9j0k)

Revisa todo y crea la versión
```

---

## 🎓 Resumen: Reglas de Oro

1. **Siempre incluye el ID del step** (AMPC-XXXX)
2. **Siempre resume qué está hecho** (con commits)
3. **Siempre di qué vas a hacer ahora**
4. **Pide resumen al final de cada chat**
5. **Copia ese resumen para el siguiente chat**

Con esto, puedes trabajar en un step durante días/semanas sin perder contexto.

---

## 📝 Fase 1: Inicio - Análisis del Step

### 🎯 Objetivo
Que yo (el agente) analice completamente el step, entienda el contexto y te proporcione un análisis técnico detallado.

### 📋 Plantilla del Prompt Ideal

```markdown
Tengo el step AMPC-XXXX: "[Título del step]"

**Descripción:**
[Copia la descripción completa de Jira aquí]

**Criterios de aceptación:**
- [Criterio 1]
- [Criterio 2]
- [Criterio 3]

**Diseño:**
[Pega captura de Figma/Zeplin, o enlace]

**Contexto adicional:**
- [Menciona componentes que crees que están relacionados]
- [Cualquier restricción o dependencia conocida]
- [Si es un bug, pega el error completo]
```

### 💬 Ejemplo Real - AMPC-1305

**Tu prompt:**
```markdown
Tengo el step AMPC-1305: "Añadir botón de descarga múltiple en OverviewModule"

**Descripción:**
Los usuarios necesitan poder descargar todas las variantes de un producto a la vez 
en formato ZIP. Actualmente solo pueden descargar una por una, lo que es tedioso 
cuando hay muchas variantes.

El botón debe aparecer en el HeaderOverview junto a los otros controles 
(detach, download individual).

**Criterios de aceptación:**
- Botón "Descargar todas" visible en OverviewModule cuando hay variantes
- Al hacer click, descarga todas las variantes en un archivo ZIP
- Muestra loading state durante la descarga
- Muestra progreso (ej: "Descargando... 50%")
- Muestra notificación de éxito/error
- Maneja errores de red correctamente
- Está deshabilitado cuando no hay variantes
- Funciona con productos que tienen 1-100 variantes
- Límite máximo: 10 variantes por descarga (mostrar error si supera)

**Diseño:**
[Imagen de Figma mostrando el botón]

**Contexto adicional:**
- Ya existe un botón de descarga individual en OverviewModule
- Ya usamos JSZip en otros lugares del proyecto
- El OverviewModule ya tiene props para onDownloadClick
```

### 🤖 Lo que hago automáticamente

Cuando recibo este prompt, yo:

1. **Busco el componente OverviewModule** y entiendo su estructura
2. **Busco funcionalidades similares** de descarga en el código
3. **Identifico servicios existentes** (DownloadProductService, etc.)
4. **Busco hooks relacionados** (useProductFiles, etc.)
5. **Reviso tipos y modelos** de datos relacionados
6. **Verifico dependencias** (JSZip, etc.)
7. **Detecto retos técnicos** (límite de archivos, manejo de errores, etc.)

### 📊 Mi respuesta

```markdown
📊 ANÁLISIS COMPLETO - AMPC-1305

════════════════════════════════════════════════════════════

🎯 COMPONENTE OBJETIVO
────────────────────────────────────────────────────────────
Ubicación: src/components/organisms/OverviewModule/OverviewModule.tsx
Líneas: 249 líneas
Props actual: Ya tiene `onDownloadClick` (línea 65) pero es para descarga individual
Estado: Maneja filtros, búsqueda, tabs, y acciones de detach/download

════════════════════════════════════════════════════════════

✅ RECURSOS DISPONIBLES (Podemos reutilizar)
────────────────────────────────────────────────────────────
📁 Servicios:
  • DownloadProductService (src/services/DownloadProductService/)
    - Ya procesa productos para descarga
    - Ya maneja tags dinámicos y placeholders
  
📁 Utils:
  • Download.ts (src/utils/Download/)
    - downloadFile() ya existe
    - Maneja diferentes formatos (PNG, JPG, PDF, GIF)
  
📁 Core:
  • ProductFiles (src/core/ProductFiles/)
    - getProductFiles() y startProductFileDownloadProcess()
  
📁 Hooks existentes:
  • useProductFiles (src/hooks/useProductFiles/)
    - Ya gestiona archivos de productos
    - Podemos usar patrón similar

📁 Contextos:
  • NotificationContext (src/contexts/NotificationContext/)
    - Para mostrar notificaciones de éxito/error

════════════════════════════════════════════════════════════

📦 DEPENDENCIAS A VERIFICAR
────────────────────────────────────────────────────────────
✓ JSZip: Verificar si está en package.json
✓ file-saver: Para descargar el ZIP generado

════════════════════════════════════════════════════════════

🚧 RETOS TÉCNICOS IDENTIFICADOS
────────────────────────────────────────────────────────────
1. Generación de múltiples archivos en paralelo
   → Solución: Procesar uno por uno con progress tracking
   
2. Límite de memoria del navegador con archivos grandes
   → Solución: Límite de 10 archivos máximo
   
3. Manejo de errores si una variante falla
   → Solución: Mostrar qué variante falló, continuar con el resto
   
4. Creación del ZIP puede ser lenta
   → Solución: Mostrar progreso en %

5. Usuario puede navegar mientras descarga
   → Solución: Cleanup en useEffect

════════════════════════════════════════════════════════════

💡 ARQUITECTURA PROPUESTA
────────────────────────────────────────────────────────────

1. Tipos (data-model):
   DownloadAllVariantsParams
   DownloadProgress
   DownloadAllVariantsResult

2. Servicio nuevo:
   DownloadZipService
   └─ generateZipFromFiles()

3. Hook personalizado:
   useDownloadAllVariants
   └─ Maneja estado: isDownloading, progress, error
   └─ Integra: DownloadZipService

4. Componente:
   OverviewModule (modificar)
   └─ Añadir botón con hook
   └─ Integrar con NotificationContext

5. Estilos:
   OverviewModule.scss
   └─ Usar variables design-system

6. Tests:
   - useDownloadAllVariants.test.ts
   - DownloadZipService.test.ts
   - OverviewModule.test.tsx (actualizar)

════════════════════════════════════════════════════════════

📊 ESTIMACIÓN
────────────────────────────────────────────────────────────
Total Story Points: 20
Subtareas: 8
Tiempo estimado: 4-5 días (1-2 subtareas por día)

════════════════════════════════════════════════════════════
```

### ✅ Siguiente paso

Cuando veas este análisis, puedes:
- Hacer preguntas sobre cualquier punto
- Pedir que cree las subtareas de Jira
- Ajustar la propuesta si algo no te convence

---

## 📋 Fase 2: Planificación - Crear Subtareas en Jira

### 🎯 Objetivo
Generar subtareas detalladas, listas para copiar en Jira, con descripción técnica, criterios de aceptación y story points.

### 📋 Plantilla del Prompt Ideal

```markdown
Crea las subtareas de Jira para AMPC-XXXX

[Opcional: Si quieres ajustar algo del análisis]
- Cambia X por Y
- No incluyas la subtarea Z
- Divide la subtarea W en dos partes
```

### 💬 Ejemplo Real - AMPC-1305

**Tu prompt:**
```markdown
Perfecto el análisis. Crea las subtareas de Jira para AMPC-1305
```

### 🤖 Mi respuesta

```markdown
📋 SUBTAREAS PARA JIRA - AMPC-1305

════════════════════════════════════════════════════════════
Copia cada subtarea como subtarea del step AMPC-1305 en Jira
════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 1: Verificar e instalar dependencias          │
└─────────────────────────────────────────────────────────┘

**Tipo:** Technical Task
**Story Points:** 1
**Prioridad:** Highest (debe hacerse primero)

**Descripción:**
Verificar si JSZip y file-saver están en el proyecto. Si no están, 
instalarlas junto con sus tipos de TypeScript.

**Criterios de Aceptación:**
✓ jszip está en package.json dependencies
✓ file-saver está en package.json dependencies  
✓ @types/jszip está en devDependencies
✓ No hay errores de compilación TypeScript
✓ npm install ejecutado correctamente

**Archivos involucrados:**
• package.json
• package-lock.json

**Comandos a ejecutar:**
```bash
npm install jszip file-saver
npm install --save-dev @types/jszip
```

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 2: Crear tipos e interfaces                   │
└─────────────────────────────────────────────────────────┘

**Tipo:** Technical Task
**Story Points:** 2

**Descripción:**
Crear los tipos TypeScript necesarios para manejar la descarga de 
múltiples variantes: parámetros de entrada, progreso de descarga y resultado.

**Criterios de Aceptación:**
✓ Interface DownloadAllVariantsParams creada
  - productId: string
  - organizationId: string
  - variantIds: string[]
  - fileName: string
✓ Interface DownloadProgress creada
  - current: number
  - total: number
  - percentage: number
✓ Interface DownloadAllVariantsResult creada
  - success: boolean
  - fileName: string
  - error?: string
✓ Tipos exportados correctamente
✓ No hay errores de TypeScript

**Archivos a crear:**
• src/data-model/ProductFiles/DownloadAllVariants.ts

**Dependencias:**
→ Ninguna (puede hacerse en paralelo con subtarea 1)

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 3: Implementar DownloadZipService             │
└─────────────────────────────────────────────────────────┘

**Tipo:** Technical Task
**Story Points:** 3

**Descripción:**
Crear servicio que genere archivos ZIP a partir de múltiples Blobs, 
utilizando JSZip. Debe incluir validaciones y manejo de errores robusto.

**Criterios de Aceptación:**
✓ Servicio acepta array de archivos (nombre + blob)
✓ Genera ZIP correctamente usando JSZip
✓ Descarga automática del archivo ZIP usando file-saver
✓ Validación: archivos no vacíos
✓ Validación: nombres de archivo presentes
✓ Validación: blobs válidos
✓ Manejo de errores con mensajes descriptivos
✓ Opciones de compresión configurables
✓ Tests unitarios incluidos (100% coverage)
  - Test: genera ZIP correctamente
  - Test: valida archivos vacíos
  - Test: valida nombres faltantes
  - Test: valida blobs inválidos

**Archivos a crear:**
• src/services/DownloadZipService/DownloadZipService.ts
• src/services/DownloadZipService/DownloadZipService.test.ts

**Dependencias:**
→ Subtarea 1 (JSZip instalado)

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 4: Crear hook useDownloadAllVariants          │
└─────────────────────────────────────────────────────────┘

**Tipo:** Technical Task
**Story Points:** 5

**Descripción:**
Implementar hook personalizado que gestione el proceso completo de descarga 
de múltiples variantes: estado de carga, progreso, generación de archivos y 
creación del ZIP.

**Criterios de Aceptación:**
✓ Hook retorna: download, isDownloading, progress, error, clearError
✓ Maneja estado de carga (isDownloading: boolean)
✓ Muestra progreso de descarga (DownloadProgress)
✓ Valida límite máximo de 10 archivos
✓ Valida que haya al menos 1 archivo
✓ Procesa archivos uno por uno con progress tracking
✓ Integra con DownloadZipService
✓ Maneja errores apropiadamente
✓ Limpia estado en finally
✓ Usa useCallback para optimización
✓ Tests completos incluidos:
  - Test: inicializa con valores correctos
  - Test: isDownloading true cuando empieza
  - Test: progreso se actualiza correctamente
  - Test: error cuando >10 archivos
  - Test: error cuando 0 archivos
  - Test: manejo de errores de red
  - Test: limpia estado al finalizar
  - Test: clearError funciona
✓ Sigue patrón de hooks del proyecto (carpeta con tests)

**Archivos a crear:**
• src/hooks/useDownloadAllVariants/useDownloadAllVariants.ts
• src/hooks/useDownloadAllVariants/useDownloadAllVariants.test.ts

**Dependencias:**
→ Subtarea 2 (tipos creados)
→ Subtarea 3 (DownloadZipService)

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 5: Añadir botón en OverviewModule             │
└─────────────────────────────────────────────────────────┘

**Tipo:** Development
**Story Points:** 3

**Descripción:**
Integrar el botón "Descargar todas" en el componente OverviewModule,
conectándolo con el hook useDownloadAllVariants y NotificationContext.

**Criterios de Aceptación:**
✓ Botón visible en HeaderOverview
✓ Icono de descarga múltiple (MATERIAL_DESIGN_ICON_ID_DOWNLOAD_MULTIPLE)
✓ Texto: "Descargar todas" (extraído a constante)
✓ Muestra estado de carga: "Descargando... X%"
✓ Está deshabilitado cuando:
  - No hay variantes (data.length === 0)
  - Está descargando (isDownloading)
  - Está en loading general (isLoading)
✓ Integrado con useDownloadAllVariants hook
✓ Muestra notificación de éxito con NotificationContext
✓ Muestra notificación de error con NotificationContext
✓ useEffect para mostrar errores automáticamente
✓ Accesibilidad completa:
  - aria-label descriptivo
  - aria-busy cuando está descargando
✓ Clase CSS para estilos: __download-all-button
✓ Handler async con try/catch

**Archivos a modificar:**
• src/components/organisms/OverviewModule/OverviewModule.tsx

**Dependencias:**
→ Subtarea 4 (hook useDownloadAllVariants)

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 6: Aplicar estilos con design-system          │
└─────────────────────────────────────────────────────────┘

**Tipo:** Development
**Story Points:** 2

**Descripción:**
Añadir estilos al botón de descarga múltiple usando exclusivamente 
variables del design-system. Asegurar responsive design.

**Criterios de Aceptación:**
✓ Imports de design-system:
  - @import '@adsmurai/design-system/scss/config/color'
  - @import '@adsmurai/design-system/scss/config/spacings'
  - @import '@adsmurai/design-system/scss/config/variables'
✓ Usa $spacing-* para todos los espaciados
✓ Usa variables de color ($primary, $gray-*, etc)
✓ No hay valores hardcoded (0 valores en px/rem/em)
✓ Responsive en mobile, tablet y desktop
✓ Loading state estilizado con opacity
✓ Cursor not-allowed cuando disabled
✓ Clase: .e-overview-module__download-all-button
✓ Modifier: .e-overview-module__download-all-button--loading

**Archivos a modificar:**
• src/components/organisms/OverviewModule/OverviewModule.scss

**Dependencias:**
→ Subtarea 5 (botón añadido)

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 7: Tests de integración en OverviewModule     │
└─────────────────────────────────────────────────────────┘

**Tipo:** Testing
**Story Points:** 3

**Descripción:**
Actualizar tests de OverviewModule para verificar el flujo completo 
de descarga múltiple con el nuevo botón.

**Criterios de Aceptación:**
✓ Test: botón visible cuando hay variantes
✓ Test: botón oculto/deshabilitado sin variantes
✓ Test: click en botón activa descarga
✓ Test: muestra loading state durante descarga
✓ Test: muestra progreso (X%)
✓ Test: muestra notificación de éxito
✓ Test: muestra notificación de error
✓ Test: manejo de errores de red
✓ Test: botón deshabilitado durante descarga
✓ Test: cleanup después de unmount
✓ Mock de useDownloadAllVariants
✓ Mock de NotificationContext
✓ Usa act() para actualizaciones de estado
✓ Sigue patrón de tests del proyecto (describe/it)

**Archivos a modificar:**
• src/components/organisms/OverviewModule/OverviewModule.test.tsx

**Dependencias:**
→ Subtarea 5 (botón implementado)
→ Subtarea 6 (estilos aplicados)

════════════════════════════════════════════════════════════

┌─────────────────────────────────────────────────────────┐
│ SUBTAREA 8: Actualizar Storybook                       │
└─────────────────────────────────────────────────────────┘

**Tipo:** Documentation
**Story Points:** 1

**Descripción:**
Añadir stories en Storybook mostrando el botón de descarga múltiple 
con diferentes estados para documentación y testing visual.

**Criterios de Aceptación:**
✓ Story: Estado normal con variantes
✓ Story: Estado loading (descargando)
✓ Story: Sin variantes (botón deshabilitado)
✓ Story: Con progreso (50%)
✓ Story: Con error
✓ Story: Con muchas variantes (cerca del límite)
✓ Controles interactivos para cambiar estados
✓ Documentación de props actualizada

**Archivos a modificar:**
• src/components/organisms/OverviewModule/OverviewModule.stories.tsx

**Dependencias:**
→ Subtarea 5 (botón implementado)

════════════════════════════════════════════════════════════

📊 RESUMEN EJECUTIVO
════════════════════════════════════════════════════════════
Total Story Points:  20 SP
Total Subtareas:     8
Tiempo estimado:     4-5 días

Desglose por tipo:
• Technical Task:    4 subtareas (11 SP)
• Development:       2 subtareas (5 SP)
• Testing:           1 subtarea (3 SP)
• Documentation:     1 subtarea (1 SP)

Orden de ejecución recomendado:
1 → 2 → 3 → 4 → 5 → 6 → 7 → 8
└─┬─┘   │   │   │   │   │   │
  │     └───┴───┘   │   │   │
  Pueden hacerse    │   │   │
  en paralelo       └───┴───┘
                    Pueden hacerse
                    en paralelo

════════════════════════════════════════════════════════════
```

### ✅ Siguiente paso

Copias cada subtarea en Jira y empiezas a implementarlas cuando quieras.

---

## 💻 Fase 3: Desarrollo - Implementar Subtareas

### 🎯 Objetivo
Implementar cada subtarea una por una, en diferentes momentos, con commits granulares.

### 📋 Plantilla del Prompt Ideal

```markdown
Voy a trabajar en AMPC-XXXX subtarea [N]: "[Título de la subtarea]"

[Opcional: Añade contexto si es necesario]
- Preferencia de implementación específica
- Detalles adicionales
- Restricciones
```

### 💬 Ejemplos Reales - Implementando AMPC-1305

---

#### 📅 Día 2: Subtarea 1 - Dependencias

**Tu prompt:**
```markdown
Voy a trabajar en AMPC-1305 subtarea 1: Verificar e instalar dependencias
```

**Mi respuesta:**
```bash
🔍 Verificando dependencias en package.json...

[Busco jszip]
❌ jszip no encontrado en dependencies

[Busco file-saver]
❌ file-saver no encontrado en dependencies

📦 Instalando dependencias...
```

**Ejecuto:**
```bash
npm install jszip file-saver
npm install --save-dev @types/jszip
```

**Mi respuesta:**
```markdown
✅ Dependencias instaladas correctamente

Archivos modificados:
• package.json (jszip, file-saver añadidos)
• package-lock.json (actualizado)

Próximos pasos:
1. Revisa que no haya errores: npm run build
2. Si todo ok: commit
```

**Tu respuesta:**
```markdown
Revisa que no haya errores
```

**Mi respuesta:**
```bash
[Ejecuto npm run build]

✅ Build exitoso sin errores

¿Hago commit?
```

**Tu respuesta:**
```markdown
Sí, haz commit
```

**Ejecuto:**
```bash
git add package.json package-lock.json
git commit -m "AMPC-1305 Add jszip and file-saver dependencies"
```

**Mi respuesta:**
```markdown
✅ Commit creado: a1b2c3d
   "AMPC-1305 Add jszip and file-saver dependencies"

Subtarea 1 completada. 
Marca como Done en Jira: AMPC-1305 subtarea 1
```

---

#### 📅 Día 3: Subtarea 2 - Tipos

**Tu prompt:**
```markdown
AMPC-1305 subtarea 2: Crear tipos e interfaces
```

**Mi acción:**
Creo el archivo completo con todos los tipos.

**Mi respuesta:**
```markdown
✅ Archivo creado: src/data-model/ProductFiles/DownloadAllVariants.ts

Contenido:
```

```typescript
export interface DownloadProgress {
  current: number
  total: number
  percentage: number
}

export interface DownloadAllVariantsParams {
  productId: string
  organizationId: string
  variantIds: string[]
  fileName: string
}

export interface DownloadAllVariantsResult {
  success: boolean
  fileName: string
  error?: string
}
```

```markdown
✓ Todos los tipos creados
✓ Sin errores de TypeScript

¿Hago commit?
```

**Tu respuesta:**
```markdown
Sí
```

**Ejecuto:**
```bash
git add src/data-model/ProductFiles/DownloadAllVariants.ts
git commit -m "AMPC-1305 Add types for multiple variants download"
```

---

#### 📅 Día 4: Subtarea 3 - Servicio

**Tu prompt:**
```markdown
Subtarea 3: Implementar DownloadZipService
```

**Mi acción:**
Creo servicio + tests completos.

**Mi respuesta muestra:**
- Código del servicio (completo, production-ready)
- Código de los tests (todos los casos)
- Resultado de ejecutar los tests

```markdown
✅ Archivos creados:
• src/services/DownloadZipService/DownloadZipService.ts
• src/services/DownloadZipService/DownloadZipService.test.ts

📊 Tests ejecutados:
  ✓ generateZipFromFiles genera ZIP correctamente
  ✓ valida que haya archivos
  ✓ valida nombres de archivo
  ✓ valida blobs válidos
  ✓ maneja errores de JSZip
  
Coverage: 100%

¿Hago commit?
```

---

#### 📅 Día 5: Subtarea 4 - Hook

**Tu prompt:**
```markdown
Subtarea 4: Crear hook useDownloadAllVariants
```

**Mi acción:**
Creo hook completo con todas las validaciones + tests.

**Tu prompt adicional:**
```markdown
Me falta que maneje el caso cuando el usuario se queda sin internet mientras descarga
```

**Mi acción:**
Añado manejo específico para errores de red.

```markdown
✅ Añadido manejo de error de red

Ahora el hook detecta:
• Error de red (NetworkError)
• Timeout
• Conexión perdida

Y muestra mensaje específico: "Error de conexión. Verifica tu internet."

Tests actualizados:
✓ maneja error de red correctamente

¿Hago commit?
```

---

#### 📅 Día 6: Subtarea 5 - Botón en Componente

**Tu prompt:**
```markdown
Subtarea 5: Añadir botón de descarga en OverviewModule
```

**Mi acción:**
Modifico OverviewModule.tsx, integro el hook, añado el botón con todos los requisitos.

**Mi respuesta:**
```markdown
✅ Modificado: src/components/organisms/OverviewModule/OverviewModule.tsx

Cambios realizados:
• Import de useDownloadAllVariants
• Import de NotificationContext  
• Constantes para textos
• Hook integrado
• Handler handleDownloadAll con try/catch
• useEffect para errores
• Botón añadido en HeaderOverview con:
  - aria-label y aria-busy
  - Progreso en % cuando descarga
  - Deshabilitado cuando no hay variantes
  - Integración con notificaciones

Líneas modificadas: +67, -3

¿Reviso si hay linter errors?
```

**Tu respuesta:**
```markdown
Sí, revisa
```

**Mi acción:**
```bash
[Ejecuto linter]

✅ No hay errores de ESLint
✅ No hay errores de TypeScript
✅ Imports ordenados correctamente

¿Hago commit?
```

---

#### 📅 Día 6 (continuación): Subtareas 6, 7, 8

De la misma forma, implemento estilos, tests y storybook, cada uno con su commit.

---

## ✅ Fase 4: QA - Revisión de Código

### 🎯 Objetivo
Revisar todo el código del feature completo antes de crear la versión.

### 📋 Plantilla del Prompt Ideal

```markdown
Revisa el código completo de AMPC-XXXX

[Opcional: Aspectos específicos a revisar]
- Revisa especialmente [área específica]
- Verifica que [requisito específico]
```

### 💬 Ejemplo Real - AMPC-1305

**Tu prompt:**
```markdown
Ya terminé todas las subtareas de AMPC-1305. Revisa el código completo
```

**Mi acción:**
```bash
[Busco todos los archivos modificados en la rama]
git diff origin/main..HEAD --name-only

[Leo cada archivo]
[Ejecuto linters]
[Ejecuto tests]
[Reviso tipos TypeScript]
[Verifico estilos]
[Reviso accesibilidad]
```

**Mi respuesta:**
```markdown
🔍 REVISIÓN COMPLETA - AMPC-1305

════════════════════════════════════════════════════════════

📁 ARCHIVOS REVISADOS (10 archivos)
────────────────────────────────────────────────────────────
✓ package.json
✓ package-lock.json
✓ src/data-model/ProductFiles/DownloadAllVariants.ts
✓ src/services/DownloadZipService/DownloadZipService.ts
✓ src/services/DownloadZipService/DownloadZipService.test.ts
✓ src/hooks/useDownloadAllVariants/useDownloadAllVariants.ts
✓ src/hooks/useDownloadAllVariants/useDownloadAllVariants.test.ts
✓ src/components/organisms/OverviewModule/OverviewModule.tsx
✓ src/components/organisms/OverviewModule/OverviewModule.scss
✓ src/components/organisms/OverviewModule/OverviewModule.test.tsx
✓ src/components/organisms/OverviewModule/OverviewModule.stories.tsx

════════════════════════════════════════════════════════════

✅ LINTERS Y COMPILACIÓN
────────────────────────────────────────────────────────────
✓ ESLint: 0 errores, 0 warnings
✓ Stylelint: 0 errores
✓ TypeScript: Sin errores de tipos
✓ Build: Exitoso

════════════════════════════════════════════════════════════

🧪 TESTS
────────────────────────────────────────────────────────────
✓ DownloadZipService.test.ts: 5/5 tests passing
✓ useDownloadAllVariants.test.ts: 8/8 tests passing
✓ OverviewModule.test.tsx: 12/12 tests passing (incluye 3 nuevos)

Total: 25/25 tests passing
Coverage: 98.5%

════════════════════════════════════════════════════════════

🎨 ESTILOS
────────────────────────────────────────────────────────────
✓ Usa variables del design-system (100%)
✓ No hay valores hardcoded
✓ Responsive design implementado
✓ Estados hover/disabled correctos
✓ Imports de config correctos:
  - @import '@adsmurai/design-system/scss/config/color'
  - @import '@adsmurai/design-system/scss/config/spacings'
  - @import '@adsmurai/design-system/scss/config/variables'

Variables usadas:
• $spacing-3 (margin)
• $unit * 2 (min-width)
• opacity: 0.6 (loading state)

════════════════════════════════════════════════════════════

♿ ACCESIBILIDAD
────────────────────────────────────────────────────────────
✓ aria-label presente: "Descargar todas las variantes en un archivo ZIP"
✓ aria-busy implementado (true cuando isDownloading)
✓ Botón deshabilitado correctamente
✓ Estados visuales claros
✓ Textos descriptivos

════════════════════════════════════════════════════════════

📝 CÓDIGO LIMPIO
────────────────────────────────────────────────────────────
✓ Sin comentarios (código auto-explicativo)
✓ Nombres descriptivos de variables y funciones
✓ Funciones con responsabilidad única
✓ Máximo 3 parámetros (usa objetos cuando necesita más)
✓ Tipos de retorno explícitos en todas las funciones
✓ Constantes extraídas (no magic numbers)
✓ Arrow functions usadas consistentemente
✓ Early returns para evitar else-if
✓ useCallback usado apropiadamente

════════════════════════════════════════════════════════════

🎯 CRITERIOS DE ACEPTACIÓN (del step AMPC-1305)
────────────────────────────────────────────────────────────
✓ Botón "Descargar todas" visible cuando hay variantes
✓ Al hacer click, descarga todas las variantes en ZIP
✓ Muestra loading state durante la descarga
✓ Muestra progreso (ej: "Descargando... 50%")
✓ Muestra notificación de éxito
✓ Muestra notificación de error
✓ Maneja errores de red correctamente
✓ Está deshabilitado cuando no hay variantes
✓ Funciona con productos 1-100 variantes
✓ Límite máximo: 10 variantes (error si supera)

════════════════════════════════════════════════════════════

⚠️  SUGERENCIAS DE MEJORA (Opcional)
────────────────────────────────────────────────────────────
Ninguna. El código está production-ready.

════════════════════════════════════════════════════════════

📊 COMMITS DE LA RAMA
────────────────────────────────────────────────────────────
1. a1b2c3d - AMPC-1305 Add jszip and file-saver dependencies
2. b2c3d4e - AMPC-1305 Add types for multiple variants download
3. c3d4e5f - AMPC-1305 Add DownloadZipService
4. d4e5f6g - AMPC-1305 Add useDownloadAllVariants hook
5. e5f6g7h - AMPC-1305 Add download all button to OverviewModule
6. f6g7h8i - AMPC-1305 Add styles for download all button
7. g7h8i9j - AMPC-1305 Add tests for download all feature
8. h8i9j0k - AMPC-1305 Update Storybook with download all examples

Total: 8 commits (1 por subtarea)

════════════════════════════════════════════════════════════

✅ VEREDICTO FINAL
────────────────────────────────────────────────────────────
El código está LISTO para crear la versión.

No se requieren cambios adicionales.
Todos los criterios de aceptación están cumplidos.
El código sigue todas las reglas del proyecto.

════════════════════════════════════════════════════════════
```

**Tu respuesta:**
```markdown
Perfecto, crea la versión
```

---

## 📦 Fase 5: Versionado - Crear Release

### 🎯 Objetivo
Actualizar changelog, package.json y crear commit de versión siguiendo las convenciones.

### 📋 Plantilla del Prompt Ideal

```markdown
Crea la versión para AMPC-XXXX

[Opcional: Especifica tipo de versión]
- Minor version (nueva funcionalidad)
- Patch version (bug fix)
- Versión específica: X.Y.Z
```

### 💬 Ejemplo Real - AMPC-1305

**Tu prompt:**
```markdown
Crea la versión para AMPC-1305
```

**Mi acción:**
```bash
[Reviso commits de la rama]
git log origin/main..HEAD --oneline

[Identifico tipo de cambio: feature = minor]
[Versión actual: 1.54.6]
[Siguiente versión: 1.55.0]

[Actualizo changelog.md]
[Actualizo package.json]
[Ejecuto npm install]
[Creo commit]
```

**Mi respuesta:**
```markdown
📦 CREANDO VERSIÓN

════════════════════════════════════════════════════════════

📊 ANÁLISIS DE CAMBIOS
────────────────────────────────────────────────────────────
Commits en la rama: 8
Tipo de cambio: Feature (nueva funcionalidad)
Versión actual: 1.54.6
Versión nueva:  1.55.0 (minor bump)

════════════════════════════════════════════════════════════

📝 CHANGELOG ACTUALIZADO
────────────────────────────────────────────────────────────
Añadido al changelog.md:

## [1.55.0] - 2025-10-20

### Added
- Download all variants button in OverviewModule for bulk ZIP download
- Progress indicator showing download percentage
- Notifications for success and error states
- useDownloadAllVariants hook for managing multi-file downloads
- DownloadZipService for generating ZIP files from multiple variants
- Types for DownloadAllVariantsParams, DownloadProgress, and DownloadAllVariantsResult

### Changed
- OverviewModule now shows "Download all" button when variants are available

### Technical
- Added jszip and file-saver dependencies
- Maximum limit of 10 variants per download to prevent memory issues
- Network error handling with specific user messages

════════════════════════════════════════════════════════════

📦 PACKAGE.JSON ACTUALIZADO
────────────────────────────────────────────────────────────
Antes: "version": "1.54.6"
Ahora:  "version": "1.55.0"

════════════════════════════════════════════════════════════

✅ ARCHIVOS ACTUALIZADOS
────────────────────────────────────────────────────────────
• changelog.md
• package.json  
• package-lock.json (ejecutado npm install)

════════════════════════════════════════════════════════════
```

**Ejecuto:**
```bash
git add changelog.md package.json package-lock.json
git commit -m "AMPC-1305 Bump version to v1.55.0"
```

**Mi respuesta:**
```markdown
✅ VERSIÓN CREADA

Commit: i9j0k1l
Mensaje: "AMPC-1305 Bump version to v1.55.0"

════════════════════════════════════════════════════════════

🎉 STEP COMPLETADO
────────────────────────────────────────────────────────────
✓ Todas las subtareas implementadas
✓ QA completo pasado
✓ Versión 1.55.0 creada

SIGUIENTE:
1. Push a la rama: git push
2. Crear Pull Request en GitHub/GitLab
3. Marcar step AMPC-1305 como Done en Jira
4. Esperar code review

════════════════════════════════════════════════════════════
```

---

## 💡 Tips y Buenas Prácticas

### ✅ Mejores formas de comunicarte conmigo

#### 1. Sé específico con los nombres
```
✅ "Modifica OverviewModule.tsx"
❌ "Modifica el componente"
```

#### 2. Incluye el ID del step siempre
```
✅ "AMPC-1305 subtarea 3"
❌ "La subtarea 3"
```

#### 3. Comparte errores completos
```
✅ [Pega todo el stack trace]
❌ "Sale un error"
```

#### 4. Una cosa a la vez
```
✅ "Implementa el servicio"
   Luego: "Ahora haz el hook"
❌ "Implementa el servicio, hook, componente y tests"
```

#### 5. Usa referencias cuando sea útil
```
✅ "Como useProductFiles pero para múltiples archivos"
✅ "Similar al modal de descarga pero inline"
```

### 📷 Puedo leer imágenes

Compárteme directamente:
- Capturas de Figma/Zeplin con diseños
- Mockups y wireframes
- Screenshots de Jira
- Diagramas de flujo
- Capturas de errores de consola

Solo pégalas y te diré qué veo.

### 🎯 Cuándo hacer cada cosa

**Análisis:** Cuando recibes un step nuevo
**Planificación:** Antes de empezar a codear
**Desarrollo:** Una subtarea por sesión (1-2 al día)
**QA:** Cuando completes todas las subtareas
**Versionado:** Después del QA, antes del PR

### ⚡ Comandos que puedo ejecutar

Puedo ayudarte con:
```bash
# Git
git status
git log origin/main..HEAD
git diff

# Tests y build
npm test
npm run lint
npm run build

# Búsquedas
grep -r "patrón" src/
```

### 🚫 Lo que NO hago (y está bien)

❌ NO commiteo sin que me lo pidas  
❌ NO uso valores hardcoded en estilos  
❌ NO añado comentarios (código auto-explicativo)  
❌ NO hago funciones con >3 parámetros  
❌ NO adivino (pregunto si no está claro)  

---

## 📜 Trabajar con .cursorrules

### 🎯 ¿Qué son las .cursorrules?

El archivo `.cursorrules` es el **"manual de estilo y reglas del proyecto"** que yo (el agente) leo automáticamente en cada conversación.

**Ubicación:** Raíz del proyecto
```
/home/javimg/projects/design-system/ui-creatives-library/.cursorrules
```

**Contiene:**
- Reglas de estilo de código (arrow functions, const vs let, etc.)
- Principios arquitecturales (Single Responsibility, máximo 3 parámetros)
- Convenciones del proyecto (sin comentarios, código auto-explicativo)
- Reglas de testing (React Testing Library, estructura de tests)
- Convenciones de Git (formato de commits, proceso de versiones)
- Uso del design-system (variables SCSS obligatorias)
- Organización de archivos (no barrel exports, estructura de hooks)

---

## 🤖 Cómo las uso automáticamente

### En CADA conversación, yo:

1. **Leo el archivo .cursorrules completo** al inicio
2. **Aplico TODAS las reglas** sin que me lo pidas
3. **No genero código que viole las reglas**
4. **Te aviso si algo que pides contradice una regla**

### Ejemplos de aplicación automática:

```typescript
// ❌ NUNCA haré esto (viola .cursorrules):
function oldStyleFunction() {  // Debería ser arrow function
  var x = 10  // Debería ser const
  // This does something  // No comentarios
  return x
}

// ✅ SIEMPRE haré esto (sigue .cursorrules):
const modernFunction = (): number => {
  const x = 10
  return x
}
```

```scss
// ❌ NUNCA haré esto:
.button {
  margin: 10px;  // Valor hardcoded
  color: #3498db;  // Color hardcoded
}

// ✅ SIEMPRE haré esto:
@import '@adsmurai/design-system/scss/config/color';
@import '@adsmurai/design-system/scss/config/spacings';

.button {
  margin: $spacing-4;
  color: $primary;
}
```

```typescript
// ❌ NUNCA haré esto:
const updateUser = (id: string, name: string, email: string, age: number, role: string) => {
  // Más de 3 parámetros
}

// ✅ SIEMPRE haré esto:
interface UpdateUserParams {
  id: string
  name: string
  email: string
  age: number
  role: string
}

const updateUser = (params: UpdateUserParams): void => {
  // Parámetros agrupados en objeto
}
```

---

## 📝 Cuándo actualizar las .cursorrules

### ✅ Actualiza .cursorrules cuando:

#### 1. **Descubres un nuevo patrón que quieres estandarizar**

**Tu prompt:**
```markdown
A partir de ahora, todos los modals deben usar el hook useModalState en vez de 
useState directamente. Guárdalo en las reglas.
```

**Mi respuesta:**
```markdown
Entendido. Voy a:
1. Guardar esta regla en mi memoria
2. Actualizar el archivo .cursorrules

¿Quieres que actualice .cursorrules ahora?
```

**Tu respuesta:** "Sí"

**Yo añado a .cursorrules:**
```
### Modal Management
- Todos los modals deben usar el hook `useModalState` 
- NO usar `useState` directamente para gestionar estado de modals
- El hook está en: `src/hooks/useModalState/useModalState.ts`
```

---

#### 2. **Cambias una convención existente**

**Tu prompt:**
```markdown
Cambio de regla: Ahora los commits pueden estar en español en vez de inglés. 
Actualiza las cursorrules.
```

**Mi respuesta:**
```markdown
Perfecto, actualizo la regla de commits en .cursorrules

ANTES:
"Los mensajes deben estar en inglés"

AHORA:
"Los mensajes pueden estar en español o inglés"

Archivo actualizado ✅
```

---

#### 3. **Añades una nueva herramienta o librería con reglas específicas**

**Tu prompt:**
```markdown
Vamos a usar React Query para todas las llamadas a API. Añádelo a las reglas:
- Usar useQuery para GET
- Usar useMutation para POST/PUT/DELETE
- No usar fetch directamente
```

**Mi respuesta:**
```markdown
Añadido a .cursorrules en nueva sección "React Query Usage":

### React Query
- Usar `useQuery` para todas las peticiones GET
- Usar `useMutation` para POST/PUT/DELETE
- NO usar `fetch` o `axios` directamente
- Los query keys deben seguir patrón: ['entity', 'action', params]
```

---

#### 4. **Defines una nueva estructura de archivos**

**Tu prompt:**
```markdown
Los nuevos componentes complejos deben tener esta estructura:
ComponentName/
  ├─ ComponentName.tsx
  ├─ ComponentName.test.tsx
  ├─ ComponentName.scss
  ├─ hooks/
  │  ├─ useComponentLogic.ts
  │  └─ useComponentLogic.test.ts
  └─ helpers/
     ├─ ComponentName.helpers.ts
     └─ ComponentName.helpers.test.ts

Guárdalo en las reglas.
```

---

### ❌ NO actualices .cursorrules para:

- **Decisiones de un solo step** ("En AMPC-1305 usa este approach")
- **Preferencias personales puntuales** ("Esta vez pon el botón a la izquierda")
- **Contexto temporal** ("Ahora estamos refactorizando X")

Estas cosas van en tu prompt, NO en .cursorrules.

---

## 💡 Tips para mantener las reglas

### 1. **Mantén .cursorrules actualizado**

Cuando yo actualizo .cursorrules, es porque me lo pediste explícitamente. El archivo queda modificado en tu working directory.

**Debes hacer:**
```bash
git add .cursorrules
git commit -m "AMPC-XXXX Update code rules: [descripción del cambio]"
```

Así las reglas quedan versionadas y todo el equipo las ve.

---

### 2. **Revisa .cursorrules periódicamente**

Cada 2-3 meses:

**Tu prompt:**
```markdown
Lee el archivo .cursorrules completo y dime si hay:
- Reglas contradictorias
- Reglas obsoletas
- Áreas que faltan por cubrir
```

**Mi respuesta:**
```markdown
📋 REVISIÓN DE .CURSORRULES

REGLAS CONTRADICTORIAS:
⚠️  Sección "Hooks" dice "usar useState" pero sección "Modal Management" 
    dice "no usar useState para modals". Aclarar la excepción.

REGLAS OBSOLETAS:
⚠️  Sección "Testing" menciona enzyme, pero el proyecto usa React Testing Library.
    Eliminar referencias a enzyme.

ÁREAS QUE FALTAN:
⚠️  No hay reglas sobre:
    - Manejo de errores en APIs
    - Naming de branches
    - Cuándo usar useMemo vs useCallback

RECOMENDACIONES:
✓ Añadir sección de "Error Handling"
✓ Eliminar sección obsoleta de enzyme
✓ Aclarar excepciones en uso de useState
```

---

### 3. **Sincroniza con el equipo**

Si trabajas en equipo, las .cursorrules deben ser consenso del equipo.

**Cuando añado una regla nueva:**
1. Yo actualizo .cursorrules
2. Tú haces commit
3. Creas PR
4. El equipo revisa si está de acuerdo
5. Se mergea a main

**No hagas:**
- Añadir reglas personales que el equipo no sigue
- Cambiar reglas sin consenso
- Mantener .cursorrules solo local

---

### 4. **Sé específico, no genérico**

❌ **Mal:**
```
# Reglas de código
- Escribir código limpio
- Usar buenas prácticas
```

✅ **Bien:**
```
# Reglas de código
- Funciones máximo 3 parámetros. Si necesitas más, agrupa en objeto interface
- Nombres de funciones: verbos en infinitivo (getUserData, createProduct)
- Constantes: UPPER_SNAKE_CASE para valores que nunca cambiarán
```

---

### 5. **Organiza por categorías**

Tu .cursorrules actual ya tiene buena organización:
- Code Style
- Single Responsibility Principle
- Parameter Limit
- TypeScript
- Testing
- Project-Specific Best Practices
- Git Commit Conventions
- Design System Variables

Mantén esta estructura. Cuando añadas reglas, ponlas en la categoría correcta.

---

## 📚 Ejemplos de uso

### Ejemplo 1: Recordatorio automático

**Escenario:** Olvidas usar variables del design-system

```typescript
// Tu código:
const buttonStyle = {
  padding: '10px',
  color: '#3498db'
}
```

**Mi respuesta:**
```markdown
⚠️  Detecté valores hardcoded que violan .cursorrules

Según las reglas del proyecto (sección "Design System Variables"):
- Debes usar variables del design-system para colores y spacing
- NO usar valores hardcoded

Corrección:
```scss
@import '@adsmurai/design-system/scss/config/color';
@import '@adsmurai/design-system/scss/config/spacings';

.button {
  padding: $spacing-4;  // 10px -> $spacing-4 (12px)
  color: $primary;
}
```

---

### Ejemplo 2: Validación antes de implementar

**Tu prompt:**
```markdown
Crea una función que reciba 5 parámetros: userId, userName, userEmail, 
userAge, userRole
```

**Mi respuesta:**
```markdown
⚠️  Esto viola las .cursorrules (sección "Parameter Limit")

La regla dice: "Funciones máximo 3 parámetros. Si necesitas más, agrupa en objeto"

Te propongo esta alternativa:

```typescript
interface CreateUserParams {
  userId: string
  userName: string
  userEmail: string
  userAge: number
  userRole: string
}

const createUser = (params: CreateUserParams): void => {
  // Implementación
}
```

¿Procedo con esta implementación?
```

---

### Ejemplo 3: Aplicación consistente en todo el proyecto

**Tu prompt:**
```markdown
Crea 3 hooks nuevos para el componente Dashboard
```

**Mi respuesta:**
```markdown
Según .cursorrules (sección "React Hooks Organization"):
- Cada hook en su carpeta con tests
- Ubicación: src/components/organisms/Dashboard/hooks/

Voy a crear:

📁 src/components/organisms/Dashboard/
  └─ 📁 hooks/
     ├─ 📁 useDashboardData/
     │  ├─ useDashboardData.ts
     │  └─ useDashboardData.test.ts
     ├─ 📁 useDashboardFilters/
     │  ├─ useDashboardFilters.ts
     │  └─ useDashboardFilters.test.ts
     └─ 📁 useDashboardExport/
        ├─ useDashboardExport.ts
        └─ useDashboardExport.test.ts

¿Procedo?
```

---

### Ejemplo 4: Sugerir actualización de reglas

**Escenario:** Notas que repites el mismo patrón varias veces

**Tu prompt:**
```markdown
He notado que en los últimos 3 steps siempre creo un hook useXyzData con 
la misma estructura. ¿Deberíamos estandarizarlo en las cursorrules?
```

**Mi respuesta:**
```markdown
Excelente observación. He visto que todos los hooks useXyzData siguen este patrón:

```typescript
interface UseXyzDataReturn {
  data: Xyz[]
  isLoading: boolean
  error: string | null
  refetch: () => Promise<void>
}

export const useXyzData = (): UseXyzDataReturn => {
  // Implementación estándar
}
```

RECOMENDACIÓN:
Añadir a .cursorrules en sección "React Hooks Organization":

### Data Hooks Pattern
- Los hooks de datos deben seguir el patrón useEntityData
- Return type debe incluir: data, isLoading, error, refetch
- Usar useQuery de React Query como base
- Tests deben cubrir: loading state, success, error, refetch

¿Quieres que añada esto a .cursorrules?
```

---

## 🎯 Resumen: Relación entre Cursorrules y Yo

```
┌─────────────────────────────────────────────────────────┐
│  .cursorrules = La "Biblia" del proyecto                │
│                                                          │
│  Yo (Agente) = Aplico la biblia automáticamente        │
│                                                          │
│  Tú = Actualizas la biblia cuando algo cambia          │
└─────────────────────────────────────────────────────────┘

FLUJO NORMAL:
1. Tú me pides implementar algo
2. Yo lo implemento siguiendo .cursorrules
3. Todo el código es consistente ✅

FLUJO DE ACTUALIZACIÓN:
1. Descubres nuevo patrón o cambio de regla
2. Me pides actualizar .cursorrules
3. Yo actualizo el archivo
4. Tú commiteas el cambio
5. En futuros steps, yo sigo la nueva regla ✅
```

---

## 🚦 Cuándo preocuparte por .cursorrules

### 🟢 NO te preocupes (lo hago yo automáticamente)
- Aplicar las reglas existentes
- Recordarte las reglas cuando las olvides
- Generar código que las siga

### 🟡 Preocúpate un poco (hazlo 1 vez al mes)
- Revisar si hay reglas contradictorias
- Limpiar reglas obsoletas
- Añadir ejemplos a reglas poco claras

### 🔴 Actúa inmediatamente (cuando pase)
- Descubres un patrón que se repite mucho → Estandariza en .cursorrules
- Cambias una herramienta/librería principal → Actualiza reglas
- El equipo acuerda nuevo estándar → Añádelo a .cursorrules

---

## 🆘 Solución de Problemas

### Problema: "No encuentras el componente que te menciono"

**Tu prompt:**
```markdown
El componente está en src/components/organisms/CustomOverview/
```

Ahora sé dónde buscar.

---

### Problema: "El código que generaste no funciona"

**Tu prompt:**
```markdown
El hook da este error:
[Pega el error completo]
```

Lo leo, identifico el problema y lo corrijo.

---

### Problema: "Quiero cambiar algo de la subtarea"

**Tu prompt:**
```markdown
En la subtarea 4, en lugar de límite de 10, ponlo en 20
```

Ajusto la implementación.

---

### Problema: "¿Por qué hiciste esto así?"

**Tu prompt:**
```markdown
¿Por qué usaste useCallback en vez de una función normal?
```

Te explico el razonamiento.

---

### Problema: "Prefiero otro approach"

**Tu prompt:**
```markdown
Prefiero que el error se muestre en un modal en vez de notificación
```

Cambio la implementación según tu preferencia.

---

### Problema: "Olvidé algo en el step"

**Tu prompt:**
```markdown
También necesitamos que el botón esté en mobile. Añádelo.
```

Lo añado al código existente.

---

## 📋 Template de Inicio Rápido

Copia y rellena cuando tengas un nuevo step:

```markdown
Tengo el step AMPC-XXXX: "[Título]"

**Descripción:**
[Descripción completa de Jira]

**Criterios de aceptación:**
- [Criterio 1]
- [Criterio 2]
- [Criterio 3]

**Diseño:**
[Imagen o enlace]

**Contexto adicional:**
[Lo que sea relevante]
```

---

## 🚀 ¡Empecemos!

Ahora que conoces el proceso completo, simplemente comparte tu step:

```
"Tengo el step AMPC-XXXX: [descripción]"
```

Y yo me encargo del resto. 💪
