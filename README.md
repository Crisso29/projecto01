# 📚 Lab01 — Git & GitHub

> **HOLA, Soy Crisologo Aguilar de serie 400 o 7mo ciclo de mi carrera universitaria en Ingeniería de Sistemas.**
>La verdad no sé cómo llegué a estudiar la carrera, pero ya vamos acabar y la verdad sí me gusta mucho el tema de desarrollo, redes y la ciberseguridad, por eso estamos ahí, aprendiendo ultimamente como loco y con más ganas. Sin mucho previo, les traigo un tutorial de uso de Git y Github de manera más clásica posible con el objetivo de crear un repositorio, cambiar de ramas, subir y bajar tus proyectos de gitHUb. Agarren bien sus teclas y a poner en práctica (ojo: Todos las pasos son verificados):

---

## 📋 Tabla de contenidos

1. [🔧 Instalación y configuración inicial](#1--instalación-y-configuración-inicial)
2. [🔄 El flujo básico de Git](#2--el-flujo-básico-de-git)
3. [☁️ Subir tu proyecto a GitHub](#3-️-subir-tu-proyecto-a-github)
4. [📥 Clonar y mantener actualizado](#4--clonar-y-mantener-actualizado)
5. [🌿 Ramas (Branches)](#5--ramas-branches)
6. [👥 Trabajo en equipo profesional](#6--trabajo-en-equipo-profesional)
7. [💻 Git en VSCode](#7--git-en-vscode)
8. [⚡ Referencia rápida — Cheat Sheet](#8--referencia-rápida--cheat-sheet)

---

## 1. 🔧 Instalación y configuración inicial

> Se hace **una sola vez** en tu computadora.

### Parte A — Instalar Git

| Paso | Qué hacer |
|------|-----------|
| 1 | Ve a **[git-scm.com](https://git-scm.com)** y descarga el instalador para tu sistema operativo |
| 2 | Sigue el asistente con las opciones por defecto. En Windows puedes elegir VSCode como editor predeterminado |
| 3 | Abre **Git Bash** (búscalo en el menú inicio) |

**Verifica que Git quedó instalado:**

```bash
git --version
```

✅ Respuesta esperada:
```
git version 2.43.0.windows.1
```

---

### Parte B — Configurar tu identidad

Git necesita saber quién eres para firmar cada cambio (commit) que hagas.

```bash
# Tu nombre (el que aparecerá en el historial)
git config --global user.name "Juan Pérez"

# Tu correo (usa el mismo que en GitHub)
git config --global user.email "juan@gmail.com"

# Verifica que quedó guardado
git config --list
```

✅ Respuesta esperada:
```
user.name=Juan Pérez
user.email=juan@gmail.com
core.editor=code
```

> 💡 **Tip:** El flag `--global` aplica la configuración a **todos los proyectos** de tu computadora. Si trabajas en un proyecto de empresa con datos distintos, configura sin `--global` dentro de esa carpeta.

---

### Parte C — Crear tu primer repositorio

```bash
# 1. Ve al escritorio
cd Desktop

# 2. Crea una carpeta para tu proyecto
mkdir mi-primer-proyecto

# 3. Entra a la carpeta
cd mi-primer-proyecto

# 4. Inicializa Git
git init
```

✅ Respuesta esperada:
```
Initialized empty Git repository in C:/Users/Juan/Desktop/mi-primer-proyecto/.git/
```

> Después de `git init` verás `(main)` al final de tu ruta en la terminal.  
> Eso confirma que Git está activo en esa carpeta. 🎉

---

## 2. 🔄 El flujo básico de Git

> El ciclo que repetirás miles de veces en tu carrera:

```
📝 Editas archivos  →  git add  →  git commit  →  git push
```

---

### Parte A — Crear archivos y ver el estado

```bash
# Crea archivos desde Git Bash
touch index.html
touch estilos.css
touch app.js

# Revisa el estado del repositorio
git status
```

📋 Resultado — archivos en **rojo** (sin trackear):
```
Untracked files:
        index.html
        estilos.css
        app.js
```

---

### Parte B — git add (Staging Area)

El **Staging Area** es una "lista de espera" — preparas exactamente qué cambios quieres guardar en el próximo commit.

```bash
# Agregar un archivo específico
git add index.html

# Agregar TODOS los archivos a la vez (lo más usado)
git add .
```

Después del `git add .`, haz `git status` de nuevo:

```bash
git status
```

📋 Resultado — archivos en **verde** (listos para commit):
```
Changes to be committed:
        new file:   index.html
        new file:   estilos.css
        new file:   app.js
```

---

### Parte C — git commit (guardar en el historial)

```bash
git commit -m "inicio del proyecto: agrego html, css y js"
```

✅ Respuesta esperada:
```
[main (root-commit) a3f7d21] inicio del proyecto
 3 files changed, 0 insertions(+), 0 deletions(-)
```

> El código `a3f7d21` es el **ID único** de tu commit. Cada commit tiene uno diferente.

**Ver el historial de commits:**

```bash
git log --oneline
```

📋 Resultado:
```
b8c4e12 agrega estructura base del HTML
a3f7d21 inicio del proyecto: agrego html, css y js
```

---

### Parte D — Deshacer cambios

```bash
# Deshacer cambios en un archivo (ANTES del git add)
git restore index.html

# Sacar un archivo del staging (ya hiciste add pero NO commit)
git restore --staged index.html
```

> ⚠️ `git restore` borra los cambios que no guardaste. Úsalo con cuidado.

---

### ❌ Cómo NO escribir mensajes de commit

| ❌ Mal | ✅ Bien |
|--------|---------|
| `"cambios"` | `"agrega validación de formulario de registro"` |
| `"fix"` | `"corrige error en cálculo de totales"` |
| `"asdf"` | `"actualiza estilos del navbar para móviles"` |
| `"cosas"` | `"elimina console.log innecesarios"` |

---

## 3. ☁️ Subir tu proyecto a GitHub

Hay **dos escenarios** según cómo estés empezando:

---

### Opción A — Empiezo desde GitHub (recomendado para principiantes)

```
Crear repo en GitHub  →  git clone  →  Trabajas  →  git push
```

**Pasos:**

1. Ve a [github.com](https://github.com) → botón **"+"** → **"New repository"**
2. Ponle un nombre, activa **"Initialize this repository with a README"**
3. Copia la URL que aparece al hacer clic en el botón verde **"Code"**

```bash
# 4. Clona el repo a tu escritorio
cd Desktop
git clone https://github.com/tu-usuario/mi-proyecto.git
cd mi-proyecto

# 5. Trabaja y sube cambios
git add .
git commit -m "agrego mis archivos iniciales"
git push
```

---

### Opción B — Ya tengo código local, quiero subirlo a GitHub

```
Repo local listo  →  Repo vacío en GitHub  →  git remote add  →  git push -u
```

**Pasos:**

1. En GitHub → New repository → **NO marques** "Initialize with README" (créalo vacío)
2. Copia la URL del repo

```bash
# 3. Conecta tu carpeta local con GitHub
git remote add origin https://github.com/tu-usuario/mi-proyecto.git

# 4. Verifica la conexión
git remote -v

# 5. Sube tu código por primera vez
git push -u origin main
```

✅ Respuesta esperada:
```
Branch 'main' set up to track remote branch 'main' from 'origin'.
Everything up-to-date
```

> 💡 El flag `-u` guarda la relación entre tu rama local y GitHub.  
> Después de esto, solo necesitas escribir `git push` sin más parámetros.

---

### Para todas las actualizaciones siguientes

```bash
git add .
git commit -m "descripción clara de lo que hiciste"
git push
```

---

## 4. 📥 Clonar y mantener actualizado

### git clone — descargar un proyecto por primera vez

```bash
# Forma básica — crea una carpeta con el nombre del repo
git clone https://github.com/usuario/nombre-del-repo.git

# Con nombre de carpeta personalizado
git clone https://github.com/usuario/repo.git mi-nombre

# En la carpeta actual (sin crear subcarpeta)
git clone https://github.com/usuario/repo.git .
```

**Clonar directamente al escritorio:**

```bash
cd /c/Users/TuNombre/Desktop
git clone https://github.com/usuario/repo.git
```

---

### git pull — sincronizarte con tu equipo

```bash
# Trae y aplica los cambios de la rama actual
git pull

# Especificando rama
git pull origin main

# Solo descargar SIN aplicar (para revisar primero)
git fetch origin
```

> ⚠️ **Regla de oro:** Siempre haz `git pull` **antes de empezar a trabajar cada día**.  
> Si no lo haces y tu compañero subió cambios mientras tú también trabajabas, tendrás conflictos difíciles.

---

### Diferencia entre clone, pull y fetch

| Comando | ¿Cuándo usarlo? | ¿Qué hace? |
|---------|-----------------|------------|
| `git clone` | Primera vez | Descarga el proyecto completo |
| `git pull` | Cada día, antes de trabajar | Trae y aplica cambios nuevos |
| `git fetch` | Cuando quieres revisar primero | Descarga pero NO aplica |

---

## 5. 🌿 Ramas (Branches)

> Las ramas son la herramienta más importante para trabajo en equipo.  
> Permiten que cada persona trabaje en su tarea **sin tocar el código principal**.

```
main (código estable)
    │
    ├──► feature/login     ← Juan trabaja aquí
    │         │
    │         └──► commits → Pull Request → merge a main
    │
    └──► feature/registro  ← María trabaja aquí
              │
              └──► commits → Pull Request → merge a main
```

---

### Comandos esenciales de ramas

```bash
# Ver en qué rama estás (el * indica la rama activa)
git branch

# Crear una rama nueva y cambiarte a ella (lo más usado)
git checkout -b feature/mi-funcionalidad

# Cambiarte a una rama existente
git checkout main
git checkout feature/login

# Ver ramas locales Y remotas
git branch -a
```

---

### Flujo completo de una tarea en rama

```bash
# 1. Actualiza main antes de crear tu rama
git checkout main
git pull origin main

# 2. Crea tu rama de tarea
git checkout -b feature/formulario-contacto

# 3. Trabaja y haz commits en tu rama
git add .
git commit -m "agrega estructura HTML del formulario"
# ... más trabajo ...
git add .
git commit -m "agrega validaciones de campos"

# 4. Sube tu rama a GitHub
git push origin feature/formulario-contacto

# 5. En GitHub: aparece el botón "Compare & pull request"
#    → escribe descripción → asigna revisor → envía

# 6. Después del merge aprobado — limpia
git checkout main
git pull origin main
git branch -d feature/formulario-contacto           # borra local
git push origin --delete feature/formulario-contacto # borra en GitHub
```

---

### Convención de nombres de ramas en empresas

| Prefijo | Ejemplo | Cuándo usarlo |
|---------|---------|---------------|
| `feature/` | `feature/login` | Nueva funcionalidad |
| `fix/` | `fix/error-login` | Corrección de bug |
| `hotfix/` | `hotfix/pago-roto` | Arreglo urgente en producción |
| `refactor/` | `refactor/navbar` | Mejorar código sin cambiar funcionalidad |
| `chore/` | `chore/dependencias` | Tareas de mantenimiento |
| `docs/` | `docs/readme` | Solo documentación |

> 🚨 **Nunca trabajes directamente en `main`.**  
> Main es el código que está en producción. Si subes algo roto ahí, afectas a todos.

---

## 6. 👥 Trabajo en equipo profesional

### Las 6 reglas de oro

- ✅ **Nunca trabajes directo en `main`** — siempre crea una rama para tu tarea
- ✅ **`git pull` antes de empezar cada día** — trae los cambios de tus compañeros
- ✅ **Commits pequeños y frecuentes** — un commit = una cosa concreta
- ✅ **Mensajes de commit descriptivos** — tu equipo leerá tu historial
- ✅ **Revisa tu código antes del PR** — no subas `console.log` ni archivos de debug
- ✅ **Sincroniza tu rama con main** — si tu tarea tarda días, haz `merge main` a tu rama cada tanto

---

### Flujo completo de un día laboral real

```bash
# ☀️ MAÑANA — actualiza y crea tu rama de tarea
git checkout main
git pull origin main
git checkout -b feature/nueva-funcionalidad

# ⚙️ DURANTE EL DÍA — guarda tu progreso con commits
git add .
git commit -m "avance: agrega componente de tabla"
# ... más trabajo ...
git add .
git commit -m "agrega estilos responsivos a la tabla"

# ↑ AL TERMINAR — sube y pide revisión
git push origin feature/nueva-funcionalidad
# Luego en GitHub → "Compare & pull request"

# ✅ DESPUÉS DEL MERGE — limpia tu rama
git checkout main
git pull origin main
git branch -d feature/nueva-funcionalidad
```

---

### Resolver conflictos paso a paso

Un conflicto ocurre cuando tú y un compañero editaron **la misma línea del mismo archivo**.

**Paso 1 — Git te avisa:**

```bash
git pull
# CONFLICT (content): Merge conflict in src/app.js
# Automatic merge failed; fix conflicts and then commit.
```

**Paso 2 — El archivo se ve así:**

```
<<<<<<< HEAD
  return precio * 1.18;   // tu versión (IGV 18%)
=======
  return precio * 1.15;   // versión del compañero (15%)
>>>>>>> origin/main
```

**Paso 3 — Edita el archivo, deja solo el código correcto:**

```javascript
// Borras los marcadores (<<<, ===, >>>) y dejas lo correcto:
return precio * 1.18;
```

**Paso 4 — Marca como resuelto:**

```bash
git add src/app.js
git commit -m "resuelve conflicto en cálculo de IGV"
```

> 💡 **En VSCode** aparecen botones visuales para resolver conflictos:  
> `Accept Current Change` / `Accept Incoming Change` / `Accept Both Changes`

---

## 7. 💻 Git en VSCode

VSCode tiene Git integrado — puedes hacer todo **sin escribir comandos**.

| Acción | Cómo hacerlo en VSCode |
|--------|------------------------|
| Abrir panel Git | Ícono `⑂` en la barra lateral o `Ctrl + Shift + G` |
| `git add` (staging) | Pasar el mouse sobre el archivo → clic en `+` |
| `git add .` | Clic en `+` al lado de "Changes" |
| `git commit` | Escribir mensaje en la caja → botón Commit o `Ctrl + Enter` |
| `git push / pull` | Flechas `↑↓` en la barra azul inferior |
| Cambiar de rama | Clic en el nombre de la rama en la barra inferior |
| Abrir terminal | `Ctrl + `` (tilde/acento grave)` |

---

### Extensiones recomendadas para VSCode

| Extensión | Para qué sirve |
|-----------|----------------|
| **GitLens** | Ver quién escribió cada línea, historial inline, comparar ramas |
| **Git Graph** | Árbol visual de ramas y commits del equipo |
| **GitHub Pull Requests** | Gestionar PRs y code reviews desde VSCode |
| **Conventional Commits** | Guía para escribir mensajes de commit con formato estándar |

---

## 8. ⚡ Referencia rápida — Cheat Sheet

### Flujo diario en equipo
```
git pull → checkout -b rama → trabajas → git add . → git commit → git push → Pull Request
```

---

### 🔧 Configuración inicial
```bash
git config --global user.name "Nombre"       # Configura tu nombre
git config --global user.email "email"       # Configura tu correo
git config --list                            # Ver configuración actual
```

### 🚀 Iniciar y conectar
```bash
git init                                     # Inicia repositorio en la carpeta actual
git clone URL                                # Descarga repo completo desde GitHub
git clone URL nombre                         # Clona con nombre de carpeta personalizado
git remote add origin URL                   # Conecta repo local con GitHub
git remote -v                               # Ver remotos configurados
```

### 📊 Estado e historial
```bash
git status                                   # Ver archivos modificados o en staging
git log --oneline                            # Historial resumido de commits
git log                                      # Historial completo con fecha y autor
git diff                                     # Ver exactamente qué líneas cambiaron
git diff --staged                            # Ver cambios en staging
```

### 💾 Guardar cambios
```bash
git add .                                    # Agregar todos los archivos al staging
git add archivo.js                           # Agregar un archivo específico
git commit -m "mensaje"                      # Guardar cambios con un mensaje
git commit --amend -m "nuevo mensaje"        # Corregir el último commit (antes del push)
```

### ☁️ Subir y bajar cambios
```bash
git push                                     # Subir commits al remoto
git push -u origin main                      # Primera vez — configura la relación
git push origin mi-rama                      # Subir una rama específica
git pull                                     # Bajar y aplicar cambios del remoto
git fetch origin                             # Bajar cambios SIN aplicar
```

### 🌿 Ramas (Branches)
```bash
git branch                                   # Listar ramas locales
git branch -a                               # Listar ramas locales y remotas
git checkout -b nombre                       # Crear rama y cambiarte a ella
git checkout nombre                          # Cambiarte a una rama existente
git merge mi-rama                            # Fusionar una rama en la rama actual
git branch -d nombre                         # Eliminar rama local
git push origin --delete nombre              # Eliminar rama del remoto (GitHub)
```

### ⏪ Deshacer y emergencias
```bash
git restore archivo                          # Deshacer cambios (antes del add)
git restore --staged archivo                 # Sacar archivo del staging
git revert HEAD                              # Deshacer último commit (seguro en equipos)
git stash                                    # Guardar cambios temporalmente
git stash pop                                # Recuperar cambios del stash
git stash list                               # Ver todos los stashes guardados
```

### 📁 Navegación en terminal
```bash
cd Desktop                                   # Ir al escritorio
cd nombre-carpeta                            # Entrar a una carpeta
cd ..                                        # Subir un nivel
ls                                           # Listar archivos (Git Bash / Mac / Linux)
mkdir nombre                                 # Crear una carpeta
touch archivo.js                             # Crear un archivo vacío
code .                                       # Abrir carpeta actual en VSCode
```

---


---

> 📌 **Recuerda:** La práctica hace al maestro.  
> Crea repositorios de prueba, rompe cosas, experimenta con ramas.  
> Mientras más lo uses, más natural se vuelve. ¡Mucho éxito! 🚀
