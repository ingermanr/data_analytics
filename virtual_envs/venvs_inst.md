# Ambientes Virtuales en Python — Guía de Referencia (Data/Analytics)

> **¿Por qué?** Aislar dependencias por proyecto evita conflictos
> (p. ej., `pandas==2.x` en un proyecto y `pandas==1.x` en otro).

---

## Índice

| #   | Sección                                              |
| --- | ---------------------------------------------------- |
| 0   | [Comparativa rápida](#comparativa-rápida)            |
| 1   | [venv + pip](#1-venv--pip)                           |
| 2   | [conda / miniconda](#2-conda--miniconda)             |
| 3   | [uv](#3-uv)                                         |
| 4   | [Recetas rápidas](#4-recetas-rápidas)                |
| 5   | [Estructura de proyecto](#5-estructura-de-proyecto)  |
| 6   | [Jupyter + ambientes](#6-jupyter--ambientes)         |
| 7   | [Recomendación práctica](#7-recomendación-práctica)  |

---

## Comparativa rápida

| Característica       | `venv + pip`             | `conda`                       | `uv`                         |
| -------------------- | ------------------------ | ----------------------------- | ---------------------------- |
| Incluido con Python  | ✅ Sí                    | ❌ Instalar aparte            | ❌ Instalar aparte           |
| Velocidad de install | Normal                   | Normal                        | ⚡ Muy rápido                |
| Lockfile nativo      | ❌ (solo `freeze`)       | ❌ (`environment.yml`)        | ✅ `uv.lock`                |
| Deps no-Python (C)   | ❌                       | ✅ Sí                         | ❌                           |
| GPU / CUDA           | Manual                   | ✅ Nativo                     | Manual                       |
| Ideal para           | Proyectos simples / ETL  | Ciencia de datos / ML pesado  | Proyectos modernos / CI-CD   |

---

## 1) venv + pip

> **Cuándo usarlo:** Proyectos "Python puro" (ETL, análisis, notebooks).
> Viene incluido con Python — no necesitas instalar nada extra.

### 1.1 Crear y activar

```bash
# Crear (carpeta oculta, recomendado)
python -m venv .venv
```

```powershell
# Activar — Windows PowerShell
.venv\Scripts\Activate.ps1
```

```bash
# Activar — Linux / macOS
source .venv/bin/activate
```

```bash
# Verificar (sanity check)
which python   # Linux/Mac
where python   # Windows
python -V
pip -V
```

### 1.2 Instalar paquetes típicos de datos

```bash
# Actualizar herramientas base
python -m pip install -U pip wheel setuptools

# Stack de análisis
pip install numpy pandas matplotlib seaborn scikit-learn jupyterlab ipykernel

# Opcionales comunes
pip install pyarrow fastparquet polars duckdb sqlalchemy psycopg2-binary
```

### 1.3 Congelar y recrear dependencias

```bash
# Exportar
pip freeze > requirements.txt

# Recrear en otro equipo / entorno
pip install -r requirements.txt
```

### 1.4 Utilidades de calidad (recomendado)

```bash
pip install ruff black mypy pytest pre-commit
```

### 1.5 Desactivar / eliminar

```bash
deactivate            # Salir del entorno
rm -rf .venv          # Eliminar (Linux/Mac)
```

```powershell
Remove-Item .venv -Recurse -Force   # Eliminar (Windows PowerShell)
```

---

## 2) conda / miniconda

> **Cuándo usarlo:** Dependencias no-Python (C/Fortran, drivers),
> ML con GPU/CUDA, o stacks científicos pesados.
> Reproducibilidad fuerte con `environment.yml`.

### 2.1 Crear y activar

```bash
# Crear (fijar versión de Python)
conda create -n mi_proyecto python=3.11

# Activar
conda activate mi_proyecto

# Verificar
python -V
```

### 2.2 Instalar paquetes típicos

```bash
# Base científica
conda install numpy pandas scipy scikit-learn matplotlib seaborn jupyterlab ipykernel

# Lectura/almacenamiento columnar (conda-forge)
conda install -c conda-forge pyarrow

# Alternativas modernas
conda install -c conda-forge polars duckdb
```

### 2.3 Exportar y recrear entorno

```bash
# Exportar
conda env export > environment.yml

# Recrear en otro equipo
conda env create -f environment.yml
```

### 2.4 Instalar con pip dentro de conda

```bash
# Solo cuando el paquete NO existe en conda
pip install some-package-not-on-conda
```

### 2.5 Comandos útiles

```bash
conda info                          # Info general
conda list                          # Paquetes del entorno activo
conda env list                      # Listar todos los entornos
conda deactivate                    # Salir del entorno
conda remove -n mi_proyecto --all   # Eliminar entorno completo
```

### 2.6 Configurar canal conda-forge (recomendado en DS)

```bash
conda config --add channels conda-forge
conda config --set channel_priority strict
```

---

## 3) uv

> **Cuándo usarlo:** Proyectos modernos (data engineering/analytics)
> donde quieres velocidad, lockfile reproducible y flujo "todo en uno".
> Muy útil en CI/CD y monorepos. Convive bien con `pyproject.toml`.

### 3.1 Instalación

```bash
pip install uv
uv --version
```

### 3.2 Inicializar proyecto + crear venv

```bash
uv init mi_proyecto
cd mi_proyecto

# Crear entorno virtual (.venv)
uv venv
```

```powershell
# Activar — Windows PowerShell
.venv\Scripts\Activate.ps1
```

```bash
# Activar — Linux / macOS
source .venv/bin/activate
```

### 3.3 Agregar dependencias

```bash
# Stack de análisis
uv add numpy pandas scikit-learn matplotlib seaborn jupyterlab ipykernel

# Opcionales data
uv add pyarrow polars duckdb sqlalchemy
```

### 3.4 Sincronizar desde lockfile (reproducibilidad)

```bash
uv sync
```

### 3.5 Ejecutar sin activar (útil en scripts / CI)

```bash
uv run python script.py
uv run pytest
```

### 3.6 Exportar requirements (para deploy clásico)

```bash
uv pip freeze > requirements.txt
```

### 3.7 Dependencias de desarrollo

```bash
uv add --dev ruff black mypy pytest pre-commit
```

### 3.8 Entendiendo `pyproject.toml`

Es el estándar moderno de Python (PEP 621) para declarar metadatos y dependencias
del proyecto. Reemplaza al viejo `setup.py` / `setup.cfg`. Cuando ejecutas `uv init`,
se crea automáticamente. Ejemplo típico:

```toml
[project]
name = "mi-analisis"
version = "0.1.0"
description = "Análisis de ventas Q1"
requires-python = ">=3.11"
dependencies = [
    "pandas>=2.0",
    "matplotlib>=3.8",
    "scikit-learn>=1.4",
]

[project.optional-dependencies]
dev = ["ruff", "pytest", "black"]

[tool.uv]
dev-dependencies = ["ruff", "pytest"]
```

| Sección                          | Para qué sirve                                            |
| -------------------------------- | --------------------------------------------------------- |
| `dependencies`                   | Dependencias directas con rangos flexibles (`>=2.0`)      |
| `requires-python`                | Versión mínima de Python                                  |
| `[tool.uv]`                      | Configuración específica de uv (deps de dev, etc.)        |
| `[tool.ruff]`, `[tool.black]`…   | Configurar otras herramientas en el mismo archivo         |

> **Nota:** `uv add pandas` modifica automáticamente la lista `dependencies`
> en `pyproject.toml`. No necesitas editarlo a mano.

### 3.9 Entendiendo `uv.lock`

Cuando ejecutas `uv add` o `uv sync`, uv genera automáticamente `uv.lock`
en la raíz del proyecto. Este archivo:

- **Fija versiones exactas** de todas las dependencias (directas e indirectas).
  Si tu proyecto usa `pandas` y pandas internamente necesita `numpy>=1.22`,
  el lockfile registra la versión exacta resuelta (ej. `numpy==1.26.4`).
- **Garantiza reproducibilidad:** cualquier persona que clone tu proyecto
  y ejecute `uv sync` obtendrá exactamente las mismas versiones.
- **Es multiplataforma:** puede registrar resoluciones para distintos OS
  y versiones de Python (a diferencia de `pip freeze`).
- **Se commitea a git.** Es parte del proyecto.

Flujo típico:

```bash
uv add pandas        # agrega a pyproject.toml + actualiza uv.lock
uv sync              # instala exactamente lo que dice uv.lock
uv lock --upgrade    # re-resuelve todas las deps a las últimas versiones compatibles
```

### 3.10 ¿Cómo se relacionan los archivos?

| Archivo            | Qué contiene                        | Se commitea | Quién lo edita       |
| ------------------ | ----------------------------------- | ----------- | -------------------- |
| `pyproject.toml`   | Dependencias con rangos flexibles   | ✅ Sí       | Tú (o `uv add`)     |
| `uv.lock`          | Versiones exactas resueltas         | ✅ Sí       | uv automáticamente   |
| `.venv/`           | Los paquetes instalados             | ❌ No       | `uv sync`            |

> **Analogía:** `pyproject.toml` es tu lista de compras ("necesito leche,
> pan, huevos"), `uv.lock` es el ticket con la marca y precio exacto de
> cada producto, y `.venv/` es la bolsa con los productos ya en tu cocina.

---

## 4) Recetas rápidas

### Nuevo proyecto de análisis (venv)

```bash
mkdir mi_analisis && cd mi_analisis
python -m venv .venv
source .venv/bin/activate          # Linux/Mac
# .venv\Scripts\Activate.ps1      # Windows
pip install -U pip
pip install pandas numpy matplotlib seaborn jupyterlab
pip freeze > requirements.txt
```

### Proyecto DS con reproducibilidad fuerte (conda)

```bash
conda create -n ds_proj python=3.11
conda activate ds_proj
conda install -c conda-forge numpy pandas scipy scikit-learn jupyterlab pyarrow
conda env export > environment.yml
```

### Proyecto moderno rápido con lock (uv)

```bash
uv init ds_uv && cd ds_uv
uv venv
uv add pandas numpy scikit-learn jupyterlab pyarrow
uv sync
uv run python -c "import pandas as pd; print(pd.__version__)"
```

---

## 5) Estructura de proyecto

```
mi_proyecto/
├── .venv/                  # Entorno virtual (NO se commitea)
├── .gitignore
├── requirements.txt        # o requirements-dev.txt
├── pyproject.toml          # si usas uv
├── src/                    # Código fuente
│   └── mi_paquete/
├── notebooks/              # Jupyter notebooks
├── data/                   # Datos (no commitear si son pesados)
└── tests/
```

### .gitignore mínimo

```text
.venv/
__pycache__/
.ipynb_checkpoints/
*.pyc
data/*.csv
```

---

## 6) Jupyter + ambientes

Para que Jupyter reconozca tu entorno virtual como un kernel seleccionable:

```bash
# Desde el entorno activado
pip install ipykernel   # si no lo tienes

# Registrar kernel — venv
python -m ipykernel install --user --name mi-proyecto --display-name "Python (mi-proyecto)"

# Registrar kernel — conda
python -m ipykernel install --user --name mi_proyecto --display-name "Python (conda: mi_proyecto)"
```

```bash
# Listar kernels disponibles
jupyter kernelspec list

# Eliminar un kernel
jupyter kernelspec remove mi-proyecto
```

> **Tip VS Code:** Al abrir un notebook, puedes seleccionar el kernel
> directamente desde la esquina superior derecha (botón "Select Kernel").

---

## 7) Recomendación práctica

| Escenario                                       | Herramienta      |
| ----------------------------------------------- | ---------------- |
| Python puro, simplicidad, aprendizaje           | `venv + pip`     |
| Deps del sistema, GPU/CUDA, stacks científicos  | `conda`          |
| Velocidad + lockfile + flujo moderno + CI/CD    | `uv`             |

> **Regla simple:** Si no sabes cuál elegir, empieza con **venv + pip**.
> Si te quedas corto, migra a conda o uv según la necesidad.
