# Warp Terminal - Guía Completa para Análisis de Datos

## Tabla de Contenidos
1. [Funciones Principales](#funciones-principales)
2. [Agents 3.0 y Capacidades Avanzadas](#agents-30-y-capacidades-avanzadas)
3. [Comandos AI y Generación](#comandos-ai-y-generación)
4. [Comandos para Análisis de Datos](#comandos-para-análisis-de-datos)
5. [Atajos de Teclado Esenciales](#atajos-de-teclado-esenciales)
6. [Gestión de Bloques](#gestión-de-bloques)
7. [Navegación y Páneles](#navegación-y-páneles)
8. [Editor de Comandos](#editor-de-comandos)
9. [Integraciones y Ambient Agents](#integraciones-y-ambient-agents)

---

## Funciones Principales

### Warp AI (Agent Mode)
- **Descripción**: Asistente AI integrado para sugerencias de comandos y resolución de problemas
- **Activación**: `Ctrl + \`` o hacer clic en el ícono de AI
- **Uso**: Escribe preguntas en lenguaje natural para obtener comandos ejecutables
- **Full Terminal Use**: Permite que el agente interactúe con aplicaciones activas (psql, mysql, debuggers)

### Command Search
- **Descripción**: Búsqueda global que abarca historial, workflows, variables de entorno y notebooks
- **Activación**: `Ctrl + R` (macOS/Linux/Windows)
- **Filtros disponibles**:
  - `history:` o `h:` - Buscar en historial de comandos
  - `workflows:` o `w:` - Buscar workflows guardados
  - `prompts:` o `p:` - Buscar prompts
  - `notebooks:` o `n:` - Buscar notebooks
  - `ai_history:` o `a:` - Buscar historial de AI

### Command Palette
- **Descripción**: Acceso rápido a workflows, notebooks, shortcuts y acciones
- **Activación**: `Cmd + P` (macOS) / `Ctrl + Shift + P` (Linux/Windows)
- **Uso**: Buscar cualquier acción o comando sin salir del teclado

### Warp Drive
- **Descripción**: Espacio de trabajo compartido para workflows, notebooks y variables de entorno
- **Activación**: `Cmd + \\` (macOS) / `Ctrl + Shift + \\` (Linux/Windows)
- **Funcionalidad**: Sincronizar configuraciones entre dispositivos y compartir con equipos

---

## Agents 3.0 y Capacidades Avanzadas

### Agents con Capacidades Completas de Terminal
**Agents 3.0** es la última evolución de Warp, permitiendo que los agentes interactúen completamente con aplicaciones en ejecución.

#### Características Clave:
- **Full Terminal Use**: Los agentes pueden interactuar con aplicaciones interactivas (psql, mysql, debuggers, REPLs)
- **Detección automática**: Warp detecta si estás escribiendo lenguaje natural o comandos
- **Multi-agent Management**: Ejecuta múltiples agentes simultáneamente
- **Notificaciones inteligentes**: Los agentes te alertan cuando necesitan tu input
- **Panel unificado**: Visualiza todos tus agentes activos en un solo lugar

### Code Review Integrado
Warp ahora incluye revisión de código con diffs integrados:

```bash
# Flujo de trabajo:
# 1. El agente genera cambios de código
# 2. Warp muestra un diff integrado
# 3. Puedes refinar con lenguaje natural
# 4. Aplica los cambios cuando estés listo
```

### Entrada Universal (Universal Input)
- Escribe naturalmente sin cambiar de modo
- Warp entiende contexto y intención
- Solicita fixes o explicaciones sin sintaxis especial
- Los agentes se invocan automáticamente cuando es necesario

### Modelos de AI Disponibles
Warp soporta múltiples modelos LLM:

| Modelo | Proveedor | Uso Recomendado |
|--------|-----------|------------------|
| **Claude 3.5 Sonnet** | Anthropic | Por defecto, tareas generales |
| **Claude Haiku** | Anthropic | Respuestas rápidas |
| **GPT-4o** | OpenAI | Tareas complejas de razonamiento |
| **BYOLLM** | Custom | Solo Enterprise: Trae tu propio modelo |

**Configuración**: Settings > AI > Model Selection

### Límites y Planes
- **Free**: 100 requests/mes por usuario
- **Pro**: Límites más altos + características adicionales
- **Team**: Límites compartidos + colaboración
- **Enterprise**: Zero Data Retention + BYOLLM

---

## Comandos AI y Generación

### Generación de Comandos con AI

#### Método 1: Usando el símbolo '#'
```bash
# Escribe '#' seguido de tu descripción en lenguaje natural
# Warp sugerirá comandos mientras escribes

# Ejemplo:
# find all python files modified today
# → Warp sugiere: find . -name "*.py" -mtime 0

# search for error in log file and save to new file
# → Warp sugiere: grep "ERROR" application.log > errors.txt
```

#### Método 2: Usando Ctrl + `
```bash
# Activar AI Generation
Ctrl + `

# Ejemplos de prompts en lenguaje natural:
"list all docker containers with their status"
"find files larger than 100MB modified in the last week"
"create a Python virtual environment and install pandas"
"analyze memory usage of all python processes"
```

### AI Autofill para Workflows
```bash
# Crear workflow parametrizado automáticamente
# Warp AI analiza el comando y sugiere parámetros reutilizables

# Ejemplo de comando que AI puede parametrizar:
git cherry-pick <commit-hash>
# AI sugerirá: git cherry-pick ${commit}
```

### Agent Mode para Debugging
```bash
# Opción 1: Adjuntar comando fallido como contexto
# Click derecho en el bloque de error > "Ask Warp AI"

# Opción 2: Usar entrada natural
# Escribe directamente: "why did this command fail?"

# El agente analizará:
# - Errores de sintaxis
# - Permisos faltantes
# - Dependencias no instaladas
# - Configuraciones incorrectas
# - Variables de entorno faltantes
# - Conflictos de versiones
```

### AI Autofill con '#' para Sugerencias Rápidas
```bash
# Activa escribiendo '#' al inicio de la línea
# Las sugerencias aparecen automáticamente mientras escribes

# Ejemplo de flujo:
# "find large files" → encuentra archivos grandes
# "check disk space" → df -h
# "kill process on port 3000" → kill -9 $(lsof -t -i:3000)
```

### Inspeccionar Comandos
- **Activación**: `Cmd + I` (macOS) / `Ctrl + I` (Linux/Windows)
- **Funcionalidad**: Obtiene explicación detallada del comando antes de ejecutarlo

---

## Comandos para Análisis de Datos

### Procesamiento de Archivos CSV
```bash
# Leer primeras líneas de CSV
head -n 10 data.csv

# Contar registros (excluyendo header)
tail -n +2 data.csv | wc -l

# Extraer columnas específicas (ejemplo: columnas 1 y 3)
awk -F',' '{print $1, $3}' data.csv

# Filtrar filas por condición
awk -F',' '$3 > 1000 {print $0}' data.csv
```

### Análisis de Logs
```bash
# Procesar logs grandes (aprovecha GPU acceleration de Warp)
cat application.log | grep "ERROR" | wc -l

# Analizar logs con timestamps
awk '/2026-02-05/ {print}' application.log | tail -n 50

# Extraer patrones específicos
grep -oP '(?<=user_id":")[^"]*' api.log | sort | uniq -c
```

### Comandos de Bases de Datos
```bash
# Exportar tabla a CSV
psql -d database_name -c "COPY (SELECT * FROM table_name) TO STDOUT CSV HEADER" > output.csv

# Contar registros en tabla
psql -d database_name -c "SELECT COUNT(*) FROM table_name"

# Ejecutar query desde archivo
psql -d database_name -f query.sql > results.txt
```

### Monitoreo de Recursos para Pipelines
```bash
# Verificar uso de memoria de proceso
ps aux | grep python | awk '{sum+=$4} END {print sum"%"}'

# Monitorear uso de disco
df -h | grep -E 'Filesystem|/data'

# Ver procesos por consumo de CPU
top -b -n 1 | head -n 20
```

### Transformación y Limpieza de Datos
```bash
# Remover duplicados
sort data.csv | uniq > data_unique.csv

# Convertir delimitadores
sed 's/;/,/g' input.csv > output.csv

# Extraer y transformar columnas con awk
awk -F',' '{print tolower($1), $2*1.1}' OFS=',' input.csv > output.csv
```

### Docker para Análisis de Datos
```bash
# Ejecutar Jupyter notebook en container
docker run -p 8888:8888 -v $(pwd):/home/jovyan/work jupyter/datascience-notebook

# Ejecutar script Python con dependencias
docker run --rm -v $(pwd):/app -w /app python:3.11 python analysis.py

# Ejecutar container PostgreSQL temporal
docker run --rm -e POSTGRES_PASSWORD=pass -p 5432:5432 postgres:15
```

---

## Atajos de Teclado Esenciales

### Navegación General

| Atajo | Función | Descripción |
|-------|---------|-------------|
| `Cmd/Ctrl + P` | Command Palette | Acceso rápido a todas las acciones |
| `Ctrl + R` | Command Search | Búsqueda en historial y workflows |
| `Cmd/Ctrl + L` | Focus Input | Volver al editor de comandos |
| `Cmd/Ctrl + K` | Clear Blocks | Limpiar bloques de la terminal |
| `Ctrl + L` | Clear Screen | Limpiar pantalla manteniendo historial |

### Gestión de Tabs

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Cmd + T` | `Ctrl + Shift + T` | Nueva tab |
| `Cmd + W` | `Ctrl + W` | Cerrar tab |
| `Shift + Cmd + T` | `Ctrl + Alt + T` | Reabrir tab cerrada |
| `Cmd + 1-9` | `Ctrl + 1-9` | Ir a tab específica |
| `Shift + Cmd + {/}` | `Ctrl + PageUp/Down` | Tab anterior/siguiente |

### Gestión de Páneles

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Cmd + D` | `Ctrl + Shift + D` | Split pane derecho |
| `Shift + Cmd + D` | `Ctrl + Shift + E` | Split pane abajo |
| `Alt + Cmd + ←/→/↑/↓` | `Ctrl + Alt + ←/→/↑/↓` | Navegar entre páneles |
| `Shift + Cmd + Enter` | `Ctrl + Shift + Enter` | Maximizar pane activo |
| `Cmd + W` | `Ctrl + W` | Cerrar pane actual |

### Búsqueda y Selección

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Cmd + F` | `Ctrl + Shift + F` | Buscar en output |
| `Cmd + G` | `F3` | Siguiente ocurrencia |
| `Shift + Cmd + G` | `Shift + F3` | Ocurrencia anterior |
| `Cmd + A` | `Ctrl + Shift + A` | Seleccionar todos los bloques |

---

## Gestión de Bloques

Los bloques son unidades discretas que agrupan comando + output. Son fundamentales en Warp.

### Atajos de Bloques

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Cmd + ↑` | `Ctrl + ↑` | Seleccionar bloque anterior |
| `Cmd + ↓` | `Ctrl + ↓` | Seleccionar bloque siguiente |
| `Shift + ↑/↓` | `Shift + ↑/↓` | Expandir selección de bloques |
| `Cmd + I` | `Ctrl + Shift + I` | Reingresar comando seleccionado |
| `Shift + Cmd + I` | Re-input con sudo | Ejecutar con permisos elevados |
| `Cmd + B` | `Ctrl + Shift + B` | Bookmark del bloque |
| `Alt + ↑/↓` | `Alt + ↑/↓` | Ir a bookmark más cercano |

### Operaciones con Bloques

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Shift + Cmd + C` | `Ctrl + Shift + C` | Copiar comando |
| `Alt + Shift + Cmd + C` | `Ctrl + Shift + Alt + C` | Copiar output |
| `Shift + Cmd + S` | `Ctrl + Shift + S` | Compartir bloque |
| `Ctrl + M` | `Ctrl + M` | Abrir menú contextual del bloque |

### Workflows con Bloques
```bash
# Crear workflow desde bloque
# 1. Ejecutar comando
# 2. Seleccionar bloque exitoso
# 3. Click derecho > "Save as Workflow"
# 4. AI puede sugerir nombre, descripción y parámetros

# Ejemplo de workflow parametrizado:
docker exec -it ${container_name} bash
```

---

## Navegación y Páneles

### Redimensionar Páneles

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Ctrl + Cmd + ←` | - | Mover divisor izquierda |
| `Ctrl + Cmd + →` | - | Mover divisor derecha |
| `Ctrl + Cmd + ↑` | - | Mover divisor arriba |
| `Ctrl + Cmd + ↓` | - | Mover divisor abajo |

### Configuración de Páneles
```bash
# Layout recomendado para análisis de datos:
# 1. Panel principal: Editor y ejecución de comandos
# 2. Panel derecho: Monitoreo de logs en tiempo real
# 3. Panel inferior: Consultas SQL o procesos de larga duración

# Comando ejemplo para panel de monitoreo:
tail -f application.log | grep --line-buffered "ERROR"
```

---

## Editor de Comandos

Warp incluye un editor similar a IDE con capacidades avanzadas.

### Navegación en el Editor

| Atajo | Función | Descripción |
|-------|---------|-------------|
| `Ctrl + A` | Inicio de línea | Ir al principio del comando |
| `Ctrl + E` | Fin de línea | Ir al final del comando |
| `Ctrl + B` | Mover cursor izquierda | Un carácter |
| `Ctrl + F` | Mover cursor derecha | Un carácter / Aceptar sugerencia |
| `Alt/Ctrl + ←/→` | Saltar palabra | Navegar por palabras |
| `Ctrl + P/N` | Cursor arriba/abajo | En comandos multilínea |

### Edición Avanzada

| Atajo | Función | Descripción |
|-------|---------|-------------|
| `Ctrl + K` | Cortar al final | Desde cursor hasta el final |
| `Ctrl + U` | Cortar línea completa | Copiar y limpiar |
| `Ctrl + W` | Cortar palabra izquierda | Eliminar palabra anterior |
| `Alt + D` | Cortar palabra derecha | Eliminar palabra siguiente |
| `Ctrl + J` | Nueva línea | Insertar salto de línea |
| `Meta + .` | Insertar última palabra | Del comando anterior |

### Selección Múltiple

| Atajo (macOS) | Atajo (Linux/Windows) | Función |
|---------------|----------------------|---------|
| `Ctrl + Shift + ↑/↓` | `Ctrl + Shift + ↑/↓` | Agregar cursor arriba/abajo |
| `Ctrl + G` | `Ctrl + G` | Seleccionar siguiente ocurrencia |
| `Cmd + A` | `Ctrl + A` | Seleccionar todo |

### Autocompletado y Sugerencias
```bash
# Warp proporciona:
# - Autocompletado contextual de comandos
# - Sugerencias de parámetros basadas en man pages
# - Historial inteligente basado en contexto
# - Sugerencias de AI en tiempo real

# Activar sugerencia: Ctrl + F (aceptar)
# Ignorar sugerencia: Continuar escribiendo
```

---

## Mejores Prácticas

### Para Análisis de Datos
1. **Usar Workflows parametrizados** para consultas recurrentes
2. **Aprovechar Agent Mode** para debugging de pipelines complejos
3. **Bookmark bloques críticos** con resultados importantes
4. **Crear notebooks** para documentar análisis paso a paso
5. **Compartir bloques** con el equipo para colaboración

### Para Productividad
1. **Command Search (`Ctrl + R`)** debe ser tu primera opción para comandos frecuentes
2. **Configurar hotkey global** para acceso rápido a Warp
3. **Usar AI autofill** para crear workflows en segundos
4. **Aprovechar Full Terminal Use** para sesiones interactivas (psql, mysql, debuggers)
5. **Sincronizar configuración** con Warp Drive entre dispositivos

### Optimización de Workflow
1. Guardar comandos complejos como workflows reutilizables
2. Usar variables de entorno en workflows para flexibilidad
3. Aprovechar split panes para monitoreo paralelo
4. Documentar workflows críticos en notebooks compartidos
5. Configurar launch configurations para proyectos específicos

---

## Recursos Adicionales

### Documentación Oficial
- Warp Docs: https://docs.warp.dev
- Keyboard Shortcuts: https://docs.warp.dev/getting-started/keyboard-shortcuts
- Warp AI Features: https://www.warp.dev/warp-ai

### Configuración Personalizada
- Remapear shortcuts: `Settings > Keyboard Shortcuts`
- Editar keybindings por archivo: Ver repositorio de keysets
- Temas personalizados: `Ctrl + Cmd/Alt + T`

---

## Integraciones y Ambient Agents

### Ambient Agents (Beta)
Agentes que se ejecutan de forma asíncrona en la nube para tareas en segundo plano.

#### Casos de Uso:
- **PR Review**: Revisión automática de pull requests
- **Issue Triage**: Clasificación y priorización de issues
- **Dependency Updates**: Actualización automática de dependencias
- **Repo Maintenance**: Mantenimiento rutinario del repositorio
- **Event-driven tasks**: Tareas activadas por eventos específicos

#### Activación:
```bash
# Los Ambient Agents se configuran desde Warp Platform
# Acceso: Settings > Platform > Ambient Agents
```

### Integraciones Disponibles

#### Slack
- Ejecutar workflows desde Slack
- Recibir notificaciones de agentes
- Trigger agents desde canales

#### Linear
- Crear issues desde terminal
- Sincronizar estados de tareas
- Ejecutar workflows basados en issues

#### GitHub Actions
- Trigger workflows desde Warp
- Monitorear ejecuciones
- Integrar con CI/CD pipeline

#### Configuración de Integraciones:
```bash
# Acceder a integraciones
# Settings > Integrations > Connect Service

# Ejemplo: Conectar Slack
# 1. Settings > Integrations > Slack
# 2. Autorizar workspace
# 3. Seleccionar canales para notificaciones
```

### Warp Platform
Infraestructura que potencia Ambient Agents e integraciones:

- **CLI**: Línea de comandos para gestión
- **Agent API/SDK**: Construye tus propios agentes
- **Orchestration**: Coordinación de múltiples agentes
- **Environments**: Entornos de ejecución aislados
- **Secrets Management**: Gestión segura de credenciales
- **Observability**: Monitoreo y logs de agentes

---

## Privacidad y Seguridad de Datos

### Política de Zero Data Retention (Enterprise)
- OpenAI y Anthropic **no retienen datos** en plan Enterprise
- En todos los planes: **datos nunca usados para entrenamiento**
- Datos pasan directamente a APIs sin interferencia de Warp
- Terminal input/output **nunca almacenado** en servidores Warp

### Cumplimiento:
- OpenAI no entrena con datos de API Platform
- Anthropic comprometido a no usar input/output para entrenamiento
- Free plan: 30 días de retención por políticas de OpenAI/Anthropic
- Enterprise: **Zero retención** en cualquier período

---

## Recursos Adicionales y Comunidad

### Documentación Oficial
- **Warp Docs**: https://docs.warp.dev
- **Keyboard Shortcuts**: https://docs.warp.dev/getting-started/keyboard-shortcuts
- **Warp AI Features**: https://www.warp.dev/warp-ai
- **Agents Documentation**: https://docs.warp.dev/agent-platform/agent/agents-overview
- **Warp University**: https://app.gitbook.com/s/c5dAwvMCRiTxUOdDicqy

### Comunidad
- **Blog**: https://www.warp.dev/blog
- **Slack Community**: https://go.warp.dev/join-preview
- **YouTube**: https://www.youtube.com/@warpdotdev
- **TikTok**: https://www.tiktok.com/@warp.dev
- **Twitter/X**: https://twitter.com/warpdotdev
- **GitHub**: https://github.com/warpdotdev
- **Discord**: https://discord.com/invite/warpdotdev

### Instalación
```powershell
# Windows (winget)
winget install Warp.Warp

# O descargar desde:
# https://app.warp.dev/get_warp?package=exe_x86_64
```

---

**Última actualización**: Febrero 2026  
**Versión**: 2.0 - Actualizado con Agents 3.0 y características 2026