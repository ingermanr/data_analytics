# Git Cheat Sheet

Git es el sistema de control de versiones distribuido de código abierto que te permite rastrear cambios en tu código y colaborar con otros desarrolladores.

---

## CONFIGURACIÓN INICIAL
Configurando información de usuario para todos los repositorios locales

| Comando | Descripción |
|---------|-------------|
| `git config --global user.name "[nombre apellido]"` | Establece el nombre que aparecerá en tus commits |
| `git config --global user.email "[email]"` | Establece el email asociado con tus commits |
| `git config --global color.ui auto` | Habilita la colorización en la línea de comandos |
| `git config --list` | Muestra todas las configuraciones actuales |

---

## CREAR REPOSITORIOS
Iniciando un nuevo repositorio o clonando uno existente

| Comando | Descripción |
|---------|-------------|
| `git init` | Inicializa un directorio existente como repositorio Git |
| `git init [nombre-proyecto]` | Crea un nuevo repositorio local con el nombre especificado |
| `git clone [url]` | Descarga un proyecto completo con todo su historial de versiones |
| `git clone [url] [nombre-carpeta]` | Clona un repositorio en una carpeta con nombre personalizado |

---

## STAGE & SNAPSHOT
Trabajando con el área de staging y creando snapshots

| Comando | Descripción |
|---------|-------------|
| `git status` | Muestra los archivos modificados en el directorio de trabajo |
| `git add [archivo]` | Añade un archivo específico al área de staging |
| `git add .` | Añade todos los archivos modificados al área de staging |
| `git add -A` | Añade todos los cambios (nuevos, modificados, eliminados) |
| `git reset [archivo]` | Quita un archivo del staging pero mantiene los cambios |
| `git diff` | Muestra diferencias de lo que cambió pero no está en staging |
| `git diff --staged` | Muestra diferencias de lo que está en staging pero no commiteado |
| `git commit -m "[mensaje descriptivo]"` | Registra los cambios del staging como un nuevo commit |
| `git commit -am "[mensaje]"` | Añade y commitea archivos tracked en un solo comando |

---

## RAMAS Y FUSIONES
Aislando trabajo en ramas y fusionando cambios

| Comando | Descripción |
|---------|-------------|
| `git branch` | Lista todas las ramas locales (marca con * la rama activa) |
| `git branch [nombre-rama]` | Crea una nueva rama en el commit actual |
| `git branch -a` | Lista todas las ramas (locales y remotas) |
| `git branch -d [nombre-rama]` | Elimina una rama local (solo si está fusionada) |
| `git branch -D [nombre-rama]` | Fuerza la eliminación de una rama local |
| `git branch -m [nombre-viejo] [nombre-nuevo]` | Renombra una rama |
| `git checkout [nombre-rama]` | Cambia a la rama especificada |
| `git checkout -b [nombre-rama]` | Crea y cambia a una nueva rama en un solo comando |
| `git switch [nombre-rama]` | Cambia a otra rama (comando más nuevo) |
| `git switch -c [nombre-rama]` | Crea y cambia a una nueva rama |
| `git merge [rama]` | Fusiona la rama especificada con la rama actual |
| `git merge --no-ff [rama]` | Fusiona creando siempre un commit de merge |

---

## HISTORIAL Y REVISIÓN
Navegando e inspeccionando la evolución de archivos

| Comando | Descripción |
|---------|-------------|
| `git log` | Muestra el historial de commits de la rama actual |
| `git log --oneline` | Muestra el historial en formato compacto (una línea por commit) |
| `git log --graph` | Muestra el historial con gráfico de ramas |
| `git log --all --decorate --oneline --graph` | Muestra historial completo con gráfico detallado |
| `git log --follow [archivo]` | Muestra el historial de un archivo, incluyendo renombrados |
| `git log -n [cantidad]` | Muestra los últimos N commits |
| `git log --author="[nombre]"` | Filtra commits por autor |
| `git log --since="[fecha]"` | Muestra commits desde una fecha específica |
| `git show [commit]` | Muestra metadatos y cambios de un commit específico |
| `git diff [rama-a]...[rama-b]` | Muestra diferencias de contenido entre dos ramas |

---

## DESHACER CAMBIOS
Borrando errores y modificando el historial

| Comando | Descripción |
|---------|-------------|
| `git restore [archivo]` | Descarta cambios en el directorio de trabajo |
| `git restore --staged [archivo]` | Quita archivo del staging (sin perder cambios) |
| `git checkout -- [archivo]` | Descarta cambios en un archivo (versión anterior) |
| `git reset [commit]` | Deshace commits después de [commit], manteniendo cambios locales |
| `git reset --soft [commit]` | Mueve HEAD al commit especificado, mantiene staging |
| `git reset --mixed [commit]` | Mueve HEAD al commit, quita del staging pero mantiene cambios |
| `git reset --hard [commit]` | Descarta todo el historial y cambios después del commit |
| `git revert [commit]` | Crea un nuevo commit que deshace los cambios del commit especificado |
| `git commit --amend -m "[nuevo mensaje]"` | Modifica el último commit (mensaje o archivos) |

---

## SINCRONIZACIÓN CON REMOTOS
Recuperando actualizaciones y sincronizando con repositorios remotos

| Comando | Descripción |
|---------|-------------|
| `git remote` | Lista los remotos configurados |
| `git remote -v` | Lista los remotos con sus URLs |
| `git remote add [alias] [url]` | Añade una URL remota como alias |
| `git remote remove [alias]` | Elimina un remoto |
| `git fetch [alias]` | Descarga todas las ramas del remoto sin fusionar |
| `git fetch --all` | Descarga cambios de todos los remotos |
| `git pull` | Descarga y fusiona cambios del remoto a la rama actual |
| `git pull origin [rama]` | Descarga y fusiona una rama remota específica |
| `git push [alias] [rama]` | Sube los commits locales al repositorio remoto |
| `git push -u origin [rama]` | Sube la rama y establece tracking con el remoto |
| `git push --all` | Sube todas las ramas al remoto |
| `git push --delete [alias] [rama]` | Elimina una rama del repositorio remoto |

---

## STASH (GUARDADO TEMPORAL)
Guardando cambios temporalmente para cambiar de contexto

| Comando | Descripción |
|---------|-------------|
| `git stash` | Guarda temporalmente archivos modificados y tracked |
| `git stash save "[mensaje]"` | Guarda cambios con un mensaje descriptivo |
| `git stash -u` | Guarda cambios incluyendo archivos untracked |
| `git stash list` | Lista todos los stashes guardados |
| `git stash pop` | Aplica el stash más reciente y lo elimina de la lista |
| `git stash apply` | Aplica el stash más reciente sin eliminarlo |
| `git stash apply stash@{n}` | Aplica un stash específico |
| `git stash drop` | Elimina el stash más reciente |
| `git stash clear` | Elimina todos los stashes guardados |

---

## GESTIÓN DE ARCHIVOS
Versionando eliminación y movimiento de archivos

| Comando | Descripción |
|---------|-------------|
| `git rm [archivo]` | Elimina el archivo del proyecto y prepara la eliminación para commit |
| `git rm --cached [archivo]` | Elimina del control de versiones pero mantiene el archivo local |
| `git mv [ruta-original] [ruta-nueva]` | Mueve o renombra un archivo y prepara el cambio |
| `git clean -n` | Muestra qué archivos untracked se eliminarían |
| `git clean -f` | Elimina archivos untracked del directorio de trabajo |
| `git clean -fd` | Elimina archivos y directorios untracked |

---

## IGNORAR PATRONES
Previniendo staging o commits accidentales

| Comando | Descripción |
|---------|-------------|
| `git config --global core.excludesfile [archivo]` | Configura un archivo .gitignore global |

**Crear archivo .gitignore:**
```
# Ignorar logs
*.log
logs/

# Ignorar archivos de configuración
*.env
config/secrets.json

# Ignorar directorios de dependencias
node_modules/
venv/

# Ignorar archivos temporales
*.tmp
temp-*
```

---

## REBASE Y REORGANIZACIÓN
Reorganizando historial de commits

| Comando | Descripción |
|---------|-------------|
| `git rebase [rama]` | Aplica commits de la rama actual sobre la rama especificada |
| `git rebase -i [commit]` | Rebase interactivo para editar, combinar o eliminar commits |
| `git rebase --continue` | Continúa el rebase después de resolver conflictos |
| `git rebase --abort` | Cancela el rebase y vuelve al estado anterior |

---

## ETIQUETAS (TAGS)
Marcando puntos específicos en el historial

| Comando | Descripción |
|---------|-------------|
| `git tag` | Lista todas las etiquetas |
| `git tag [nombre-tag]` | Crea una etiqueta ligera en el commit actual |
| `git tag -a [nombre-tag] -m "[mensaje]"` | Crea una etiqueta anotada con mensaje |
| `git tag -a [nombre-tag] [commit]` | Crea una etiqueta en un commit específico |
| `git push origin [nombre-tag]` | Sube una etiqueta al remoto |
| `git push origin --tags` | Sube todas las etiquetas al remoto |
| `git tag -d [nombre-tag]` | Elimina una etiqueta local |
| `git push --delete origin [nombre-tag]` | Elimina una etiqueta del remoto |

---

## COMANDOS ÚTILES ADICIONALES

| Comando | Descripción |
|---------|-------------|
| `git help [comando]` | Muestra ayuda detallada sobre un comando |
| `git archive --format=zip HEAD > archivo.zip` | Exporta el proyecto como archivo ZIP |
| `git blame [archivo]` | Muestra quién modificó cada línea de un archivo |
| `git shortlog` | Resume el historial de commits por autor |
| `git reflog` | Muestra historial de referencias (útil para recuperar commits) |

---

## RESOLUCIÓN DE CONFLICTOS

| Comando | Descripción |
|---------|-------------|
| `git status` | Identifica archivos con conflictos |
| `git diff` | Muestra los conflictos en detalle |
| `git merge --abort` | Cancela el merge y vuelve al estado anterior |
| `git checkout --ours [archivo]` | Acepta tu versión del archivo en conflicto |
| `git checkout --theirs [archivo]` | Acepta la versión entrante del archivo |

---

## TIPS PARA ANÁLISIS DE DATOS

**Commits frecuentes y descriptivos:**
```bash
git commit -m "feat: añade análisis exploratorio de ventas"
git commit -m "fix: corrige cálculo de medias en script limpieza"
git commit -m "docs: actualiza README con instrucciones de ejecución"
```

**Ignorar archivos grandes de datos:**
```
# En .gitignore
*.csv
*.xlsx
*.parquet
data/raw/*
!data/raw/.gitkeep
```

**Versionado de notebooks:**
```bash
# Limpiar outputs antes de commit
jupyter nbconvert --clear-output --inplace notebook.ipynb
git add notebook.ipynb
git commit -m "update: análisis de segmentación de clientes"
```
