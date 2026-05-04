# 🐙 Tutorial completo — GitHub

> **Todo lo que necesitas saber para usar GitHub como un profesional.**  
> Issues, Pull Requests, Projects, Actions, Wiki, Releases y más.

---

## 📋 Tabla de contenidos

1. [🌐 ¿Qué es GitHub y cómo está organizado?](#1--qué-es-github-y-cómo-está-organizado)
2. [🔴 Issues — Gestión de tareas y bugs](#2--issues--gestión-de-tareas-y-bugs)
3. [🟣 Pull Requests — Revisión y fusión de código](#3--pull-requests--revisión-y-fusión-de-código)
4. [🟦 Projects — Tablero de gestión del equipo](#4--projects--tablero-de-gestión-del-equipo)
5. [⚙️ Actions — Automatización](#5-️-actions--automatización)
6. [📖 Wiki y Releases](#6--wiki-y-releases)
7. [👤 Tu perfil de GitHub](#7--tu-perfil-de-github)
8. [🏢 Flujo real de trabajo en empresa](#8--flujo-real-de-trabajo-en-empresa)

---

## 1. 🌐 ¿Qué es GitHub y cómo está organizado?

> **Git** guarda el historial en tu PC.  
> **GitHub** es la plataforma en la nube donde subes ese historial para colaborar con el mundo.

---

### Las pestañas principales de un repositorio

| Pestaña | Qué contiene |
|---------|-------------|
| **Code** | Tus archivos, carpetas, README y historial de commits |
| **Issues** | Reportes de bugs, tareas pendientes y solicitudes de funcionalidades |
| **Pull Requests** | Solicitudes para fusionar ramas — aquí se revisa el código |
| **Projects** | Tablero tipo Trello/Jira integrado con tus Issues y PRs |
| **Actions** | Automatización: tests, despliegues, verificaciones de código |
| **Wiki** | Documentación del proyecto: guías, arquitectura, onboarding |
| **Insights** | Estadísticas: contribuciones, commits por semana, tráfico |
| **Settings** | Permisos, colaboradores, protección de ramas, webhooks |

---

### Público vs Privado

| | Repositorio Público | Repositorio Privado |
|--|---------------------|---------------------|
| Quién lo ve | Cualquier persona en internet | Solo tú y colaboradores invitados |
| Cuándo usarlo | Portafolio, código abierto, tareas | Proyectos de empresa, código sensible |
| Costo | Gratis | Gratis (con límites en la versión free) |

> 💡 Tu perfil de GitHub es tu **currículum como desarrollador**. Los reclutadores revisan tus repos, cuántos commits haces y cómo colaboras. Mantenlo activo y ordenado.

---

## 2. 🔴 Issues — Gestión de tareas y bugs

Un **Issue** es un ticket de trabajo. Puede ser:
- 🐛 Un **bug** reportado por alguien
- ✨ Una **funcionalidad nueva** que se quiere agregar
- 📝 Una **tarea** pendiente del proyecto
- ❓ Una **pregunta** técnica del equipo

---

### Partes de un Issue

```
Título:      #4 El formulario de login no valida el email
Estado:      Open / Closed
Descripción: Qué pasó, qué se esperaba, cómo reproducirlo
Assignee:    Quién es responsable de resolverlo
Labels:      bug, urgent, enhancement, documentation...
Project:     A qué tablero pertenece
Milestone:   A qué versión o fecha límite apunta
```

---

### Labels (etiquetas) más usadas en empresas

| Label | Color | Cuándo usarla |
|-------|-------|---------------|
| `bug` | 🔴 Rojo | Algo no funciona como debería |
| `enhancement` | 🔵 Azul | Mejora o funcionalidad nueva |
| `documentation` | 🟣 Morado | Cambios en README u otros documentos |
| `good first issue` | 🟢 Verde | Tarea sencilla para quien recién entra |
| `urgent` | 🟡 Amarillo | Necesita atención inmediata |
| `help wanted` | 🟢 Verde claro | El autor necesita apoyo del equipo |
| `wontfix` | ⚫ Gris | Se decidió no resolver este problema |
| `duplicate` | ⚫ Gris | Ya existe otro Issue igual |

---

### Cómo crear un Issue paso a paso

| Paso | Qué hacer |
|------|-----------|
| 1 | Ve a la pestaña **Issues** → botón verde **"New issue"** |
| 2 | Escribe un **título claro**: "El botón de pago falla en móviles iOS" |
| 3 | Describe el problema: qué pasó, qué esperabas, cómo reproducirlo |
| 4 | Adjunta capturas, logs de error o fragmentos de código si los tienes |
| 5 | Asigna **Labels**, **Assignee** y vincula al **Project** |
| 6 | Haz clic en **"Submit new issue"** |

---

### Cerrar un Issue automáticamente desde un commit o PR

Escribe esto en el mensaje del commit o en la descripción del PR:

```bash
git commit -m "corrige validación de email — Closes #4"
```

O en la descripción del Pull Request:

```
Closes #4
Fixes #7
Resolves #12
```

> ✅ GitHub cierra el Issue automáticamente cuando el PR es mergeado. Muy profesional y muy usado en equipos reales.

---

### Ejemplo de un buen Issue vs uno malo

| ❌ Issue malo | ✅ Issue bueno |
|--------------|---------------|
| Título: "bug" | Título: "El formulario acepta emails sin @ en iOS 16" |
| Descripción vacía | Pasos para reproducir + captura de pantalla + versión del sistema |
| Sin label ni assignee | Label: bug, urgent · Assignee: juan_dev |

---

## 3. 🟣 Pull Requests — Revisión y fusión de código

Un **Pull Request (PR)** es una solicitud para fusionar tu rama con `main`. Antes de que el código entre a producción, el equipo lo revisa, comenta, pide cambios y aprueba.

```
Tu rama lista  →  Crear PR  →  Revisión del equipo  →  Aprobado  →  Merge a main
```

---

### Cómo crear un Pull Request paso a paso

| Paso | Qué hacer |
|------|-----------|
| 1 | Sube tu rama: `git push origin feature/mi-rama` |
| 2 | En GitHub aparece el banner **"Compare & pull request"** — haz clic |
| 3 | Escribe un **título claro** y una **descripción** de qué cambios trae |
| 4 | En la descripción escribe `Closes #N` para vincular el Issue que resuelve |
| 5 | Asigna **Reviewers** (quién va a revisar tu código) |
| 6 | Haz clic en **"Create pull request"** |
| 7 | Espera los comentarios — respóndelos y haz los cambios que pidan |
| 8 | Una vez aprobado → **"Merge pull request"** |

---

### Ejemplo de diff en un PR

```diff
  function validarFormulario() {
-   if (email.length > 0) {          // ← código viejo (en rojo)
+   const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;   // ← código nuevo (en verde)
+   if (regex.test(email)) {
      enviarFormulario();
    }
  }
```

> Las líneas en **rojo** (`-`) son lo que se elimina.  
> Las líneas en **verde** (`+`) son lo que se agrega.

---

### Estados de un Pull Request

| Estado | Qué significa |
|--------|---------------|
| `Open` | Abierto — esperando revisión o cambios |
| `Draft` | En borrador — aún no está listo para revisión |
| `Changes requested` | El revisor pidió modificaciones |
| `Approved` | Aprobado — listo para merge |
| `Merged` | Fusionado con la rama destino |
| `Closed` | Cerrado sin merge (se descartó) |

---

### Los 3 tipos de merge en GitHub

| Tipo | Qué hace | Cuándo usarlo |
|------|----------|---------------|
| **Merge commit** | Crea un commit que une las dos ramas. Conserva todo el historial. | El más usado — default en equipos |
| **Squash and merge** | Aplasta todos tus commits en uno solo antes de mergear | Para limpiar el historial de main |
| **Rebase and merge** | Pone tus commits encima del historial de main, sin commit de merge | Para un historial completamente lineal |

---

### Buenas prácticas en Pull Requests

- ✅ El PR debe resolver **una sola cosa** — no mezcles 5 funcionalidades
- ✅ Escribe una **descripción clara** de qué hiciste y por qué
- ✅ Vincula siempre el **Issue** que resuelve con `Closes #N`
- ✅ El PR debe tener **nombre de rama descriptivo**: `feature/login`, `fix/validacion-email`
- ✅ **Responde los comentarios** del revisor en menos de 24 horas
- ❌ Nunca hagas merge directamente a `main` sin PR en proyectos en equipo
- ❌ No subas PRs con `console.log`, archivos de debug o dependencias innecesarias

---

## 4. 🟦 Projects — Tablero de gestión del equipo

**GitHub Projects** es el tablero de gestión de tareas integrado en GitHub. Funciona como Trello o Jira, pero conectado directamente a tus Issues y Pull Requests.

---

### Vista de tablero (Board) — la más usada

```
┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
│   To Do      │  │ In Progress  │  │  In Review   │  │    Done      │
├──────────────┤  ├──────────────┤  ├──────────────┤  ├──────────────┤
│ #3 Modo      │  │ #4 Validar   │  │ PR #8 Login  │  │ #2 README    │
│ oscuro       │  │ email        │  │ validation   │  │ actualizado  │
├──────────────┤  ├──────────────┤  └──────────────┘  ├──────────────┤
│ #5 Página    │  │ #7 Responsive│                     │ #1 Setup     │
│ de perfil    │  │ móviles      │                     │ inicial      │
└──────────────┘  └──────────────┘                     └──────────────┘
```

---

### Vistas disponibles en Projects

| Vista | Para qué sirve |
|-------|----------------|
| **Board** | Columnas Kanban con tarjetas arrastrables. Ver el flujo de trabajo del equipo |
| **Table** | Vista spreadsheet — filtrar y ordenar por campos personalizados |
| **Roadmap** | Línea de tiempo tipo Gantt con fechas. Planificación mensual |
| **Backlog** | Lista priorizada de tareas pendientes para planificar sprints |

---

### Cómo crear un Project

| Paso | Qué hacer |
|------|-----------|
| 1 | Ve a la pestaña **Projects** → **"New project"** |
| 2 | Elige una plantilla — **Board** es la más popular |
| 3 | Crea tus columnas: To Do, In Progress, In Review, Done |
| 4 | Clic en **"+"** en una columna → busca el Issue por número o título |
| 5 | Arrastra las tarjetas según el avance del trabajo |

---

### Campos personalizados que puedes agregar

- **Priority** → Alta / Media / Baja
- **Size** → S / M / L (tamaño de la tarea)
- **Sprint** → Sprint 1, Sprint 2...
- **Due date** → Fecha límite
- **Estimate** → Horas estimadas

> 💡 Cuando un PR es mergeado y cierra un Issue, la tarjeta de ese Issue se mueve automáticamente a "Done" en el tablero. Menos trabajo manual, más foco en programar.

---

## 5. ⚙️ Actions — Automatización

**GitHub Actions** ejecuta tareas automáticas en tu proyecto. Cada vez que alguien hace push, abre un PR o crea un release, puedes correr scripts automáticamente.

---

### ¿Para qué sirve Actions?

| Uso | Descripción |
|-----|-------------|
| **CI — Tests automáticos** | Corre los tests cada vez que alguien hace push. Si algo falla, bloquea el PR |
| **CD — Deploy automático** | Sube la app a producción cuando se mergea a main. Sin hacer deploy manual |
| **Linting** | Verifica que el código sigue las reglas de estilo del equipo |
| **Notificaciones** | Avisa en Slack o email cuando algo falla o se hace un deploy |
| **Generar documentación** | Construye y publica la documentación automáticamente |

---

### Ejemplo real — workflow que corre tests en cada push

```yaml
# .github/workflows/tests.yml

name: Correr tests

on:
  push:
    branches: ["main", "feature/*"]
  pull_request:
    branches: ["main"]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Instalar dependencias
        run: npm install

      - name: Correr tests
        run: npm test
```

---

### Cómo se ve un workflow ejecutándose

```
✓  Checkout del repositorio          2s
✓  Instalar dependencias            18s
✓  Correr tests (24 passed)         12s

Status: Success ✓
```

Si un test falla:

```
✓  Checkout del repositorio          2s
✓  Instalar dependencias            18s
✗  Correr tests (2 failed)          15s

Status: Failure ✗  — PR bloqueado hasta corregir
```

---

### Conceptos clave de Actions

| Término | Qué es |
|---------|--------|
| **Workflow** | El archivo YAML que define qué hacer y cuándo |
| **Event** | Lo que dispara el workflow: push, pull_request, schedule... |
| **Job** | Un conjunto de steps que corren en el mismo servidor |
| **Step** | Una tarea específica dentro del job |
| **Runner** | El servidor donde corre el workflow (ubuntu-latest, windows, mac) |
| **Action** | Un step reutilizable creado por la comunidad (`actions/checkout@v3`) |

---

## 6. 📖 Wiki y Releases

---

### Wiki — Documentación del proyecto

La **Wiki** es un sistema de documentación integrado en tu repositorio. Sirve para escribir guías que no cambian frecuentemente.

**¿Qué va en la Wiki?**

```
📖 Inicio
   ├── Instalación y configuración
   ├── Arquitectura del proyecto
   ├── Guía de contribución
   ├── Decisiones técnicas
   └── Glosario
```

| | Wiki | README.md |
|--|------|-----------|
| **Para qué** | Documentación detallada y técnica | Presentación rápida del proyecto |
| **Extensión** | Múltiples páginas | Un solo archivo |
| **Cuándo usarlo** | Guías de setup, arquitectura, onboarding | Qué es el proyecto, cómo instalarlo |

---

### Releases — Versiones oficiales

Los **Releases** son versiones estables y oficiales de tu proyecto. Se usan para marcar hitos: "Esta es la v1.0 que entregamos al cliente".

**Cómo crear un Release:**

```bash
# 1. Crea un tag en Git
git tag -a v1.0.0 -m "primera versión estable"

# 2. Sube el tag a GitHub
git push origin v1.0.0
```

Luego en GitHub:
1. Ve a **Releases** → **"Draft a new release"**
2. Elige el tag que creaste
3. Escribe las notas de la versión
4. Publica

**Ejemplo de notas de release:**

```markdown
## v1.2.0 — Sistema de login completo

### Novedades
- Validación de email con regex
- Modo oscuro en navbar
- Página de perfil de usuario

### Bugs corregidos
- Fix: formulario aceptaba emails inválidos
- Fix: navbar se rompía en pantallas menores a 375px
```

**Convención de versiones (SemVer):**

```
v  1  .  2  .  0
   │     │     └── PATCH — corrección de bugs
   │     └──────── MINOR — nueva funcionalidad (retrocompatible)
   └────────────── MAJOR — cambio que rompe compatibilidad
```

---

## 7. 👤 Tu perfil de GitHub

### Qué debes tener en tu perfil

| Campo | Por qué importa |
|-------|-----------------|
| **Foto** | Humaniza tu perfil — da más confianza |
| **Nombre real** | Los reclutadores buscan por nombre, no por username |
| **Bio** | Una línea: "Estudiante de Ing. Software · Apasionado por el frontend" |
| **Ubicación** | Útil para oportunidades locales |
| **Link** | LinkedIn, portafolio o CV en línea |

---

### Los cuadraditos verdes (contribution graph)

```
Más oscuro = más actividad ese día

  ░ Sin actividad
  🟩 1-3 contribuciones
  🟩 4-6 contribuciones  (más oscuro)
  🟩 7-9 contribuciones  (más oscuro)
  🟩 10+ contribuciones  (más oscuro)
```

**Qué cuenta como contribución:**
- Hacer un commit
- Abrir un Issue
- Crear o mergear un PR
- Hacer un code review

> 💡 Mejor hacer **pocos commits diarios** que un volcado masivo cada mes. La consistencia importa más que la cantidad.

---

### El README de tu perfil

Puedes crear un repo con **exactamente tu mismo username** y poner un `README.md` — aparece en tu perfil como una tarjeta de presentación personalizada.

```bash
# Si tu usuario es Crisso29:
# Crea el repo: Crisso29/Crisso29
# El README.md de ese repo aparece en tu perfil
```

**Ejemplo de README de perfil:**

```markdown
# Hola, soy Crisso 👋

Estudiante de Ingeniería de Software en Ayacucho, PE.
Aprendiendo desarrollo web y herramientas de colaboración.

## 🛠️ Tecnologías que estoy aprendiendo
- HTML · CSS · JavaScript
- Git · GitHub
- Visual Studio Code

## 📌 Proyectos destacados
- [projecto01](https://github.com/Crisso29/projecto01) — Mi primer repositorio

## 📫 Contacto
LinkedIn: linkedin.com/in/crisso29
```

---

### Cómo pinear tus mejores repositorios

1. Ve a tu perfil de GitHub
2. Haz clic en **"Customize your pins"**
3. Selecciona hasta **6 repositorios** que quieras destacar
4. Los repos pineados son lo primero que ve un reclutador

> ✅ Pinea proyectos que tengan: README completo, commits frecuentes, código limpio y descripción clara.

---

## 8. 🏢 Flujo real de trabajo en empresa

Así trabaja un equipo profesional de principio a fin:

---

### El ciclo completo

```
1. Issue creado
   └── "Agregar pantalla de registro" → label: feature, priority: alta

2. Asignado en Projects
   └── Entra al tablero en "To Do" → asignado a Juan

3. Juan crea su rama y trabaja
   └── git checkout -b feature/registro
   └── commits... → tarjeta pasa a "In Progress"

4. Juan abre el Pull Request
   └── git push origin feature/registro
   └── En GitHub: "Closes #8" → Reviewer: María

5. María revisa el código
   └── Comenta, pide un cambio
   └── Juan corrige, hace push → tarjeta pasa a "In Review"

6. María aprueba → Merge a main
   └── Issue #8 se cierra automáticamente
   └── Tarjeta pasa a "Done"

7. GitHub Actions despliega automáticamente
   └── Detecta push a main → corre tests → despliega al servidor
```

---

### Glosario de términos que escucharás en el trabajo

| Término | Qué significa |
|---------|---------------|
| **PR / MR** | Pull Request (GitHub) / Merge Request (GitLab) — lo mismo |
| **Code Review** | Revisión del código de un PR por un compañero |
| **CI/CD** | Integración continua / Despliegue continuo — automatización |
| **Workflow** | El proceso de trabajo del equipo de principio a fin |
| **Sprint** | Período de trabajo de 1-2 semanas con tareas definidas |
| **Backlog** | Lista priorizada de todas las tareas pendientes |
| **Milestone** | Hito del proyecto — agrupa Issues hacia una fecha o versión |
| **Fork** | Copia de un repo ajeno en tu cuenta para modificarlo |
| **Clone** | Descarga del repo a tu computadora |
| **Merge** | Fusión de dos ramas en una |
| **Rebase** | Reorganizar commits para un historial más limpio |
| **Stash** | Guardar cambios temporalmente sin hacer commit |
| **Tag** | Marca en un commit específico — se usa para releases |
| **Deploy** | Publicar la aplicación al servidor de producción |
| **Branch protection** | Regla que impide hacer push directo a main sin PR aprobado |

---

### Diferencia entre GitHub, GitLab y Bitbucket

| | GitHub | GitLab | Bitbucket |
|--|--------|--------|-----------|
| **Más popular en** | Proyectos open source, startups | Empresas medianas, CI/CD | Empresas con Atlassian (Jira) |
| **CI/CD nativo** | GitHub Actions | GitLab CI | Bitbucket Pipelines |
| **Precio** | Gratis con límites | Gratis con límites | Gratis con límites |
| **Lo que aprendiste aquí** | Aplica directamente | Aplica con nombres distintos | Aplica con nombres distintos |

> 📌 Lo que aprendiste en GitHub te sirve en todos. Los conceptos son los mismos — solo cambian algunos nombres y la interfaz.

---

## 🎯 Cómo subir este archivo a tu repositorio

```bash
# 1. Asegúrate de estar en la carpeta correcta
cd mi-proyecto

# 2. Verifica que el archivo existe
ls

# 3. Agrega al staging
git add GITHUB_TUTORIAL.md

# 4. Haz el commit
git commit -m "agrego tutorial completo de GitHub"

# 5. Sube a GitHub
git push origin main
```

---
>**That´s all my babies, thank you**