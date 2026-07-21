# Ruta de Analista de Datos Básico con Python

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![License](https://img.shields.io/badge/License-MIT-green.svg)
![Notebooks](https://img.shields.io/badge/Notebooks-18-orange.svg)
![Status](https://img.shields.io/badge/Status-Completado-success.svg)

Curso práctico y gradual para convertirte en **Analista de Datos** desde cero. **18 notebooks** interactivos, en secuencia, que van de los fundamentos matemáticos y estadísticos hasta proyectos aplicados listos para tu portafolio.

---

## Estructura del curso

Los notebooks están numerados en **orden de aprendizaje**: sigue del `01` al `18` sin saltos. Cada uno construye sobre el anterior, respetando los prerrequisitos.

| # | Notebook | Qué aprendes |
|---|----------|--------------|
| 01 | `01_fundamentos_matematicos_estadisticos` | Estadística e intuición cuantitativa (solo conceptos, sin código) |
| 02 | `02_programacion_python` | La herramienta: sintaxis, estructuras de datos, control de flujo, funciones |
| 03 | `03_manipulacion_datos_numpy` | Arrays y cálculo vectorizado con NumPy |
| 04 | `04_analisis_datos_pandas` | El `DataFrame`, la estructura central del análisis |
| 05 | `05_limpieza_preparacion_datos` | Faltantes, outliers, normalización, codificación |
| 06 | `06_analisis_exploratorio_datos` | EDA: encontrar patrones, relaciones e *insights* |
| 07 | `07_visualizacion_datos` | Matplotlib y Seaborn; comunicar con gráficos |
| 08 | `08_sql_bases_datos` | SQL para consultar datos donde viven |
| 09 | `09_excel_analisis_datos` | Excel para análisis, y su equivalente en Pandas |
| 10 | `10_herramientas_bi` | Power BI y Tableau; dashboards de negocio |
| 11 | `11_control_versiones` | Git y GitHub para versionar y colaborar |
| 12 | `12_ingenieria_datos_basicos` | ETL/ELT, pipelines, formatos, APIs, data warehousing |
| 13 | `13_librerias_modernas` | Polars, Plotly, Streamlit y Dash |
| 14 | `14_fundamentos_modelado_predictivo` | Del análisis descriptivo al predictivo (ML básico) |
| 15 | `15_regresion_y_clasificacion_basica` | Los dos tipos de problema del aprendizaje supervisado |
| 16 | `16_evaluacion_modelos_y_decisiones_negocio` | Métricas, umbrales y costo de negocio |
| 17 | `17_soft_skills_metodologia` | Pensar, comunicar, colaborar y decidir con ética |
| 18 | `18_proyectos_aplicados` | Capstone: 2 proyectos guiados end-to-end + 3 retos de portafolio |

> **Sobre el orden:** el curso respeta los prerrequisitos. Aprendes Python (02) antes de NumPy (03); NumPy y Pandas (03-04) antes de limpiar datos (05); y a visualizar (07) antes de modelar (14-16). El notebook 01 es solo conceptual (sin código) para separar la estadística de la programación.

---

## Inicio rápido

### Prerrequisitos
- Python 3.9 o superior
- pip
- Git (opcional)

### Instalación

1. **Clonar o descargar el repositorio**
   ```bash
   git clone <repository-url>
   cd da_basico
   ```

2. **Crear y activar un entorno virtual (recomendado)**
   ```bash
   python -m venv venv

   # Windows
   venv\Scripts\activate
   # Linux / Mac
   source venv/bin/activate
   ```

3. **Instalar dependencias**
   ```bash
   # Opción 1: instalación completa
   pip install -r requirements.txt

   # Opción 2: solo lo esencial para empezar
   pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
   ```

4. **Iniciar Jupyter y abrir el notebook 01**
   ```bash
   jupyter lab
   # o
   jupyter notebook
   ```

---

## Cómo usar este curso

1. Empieza por **`01`** y avanza en orden numérico hasta el **`18`**.
2. **Ejecuta todo el código** mientras lees, no solo leas.
3. **Modifica los ejemplos**: cambia valores, rompe cosas a propósito y observa qué pasa.
4. Toma notas en celdas markdown con tus propias observaciones.

### Cada notebook incluye
- Explicaciones claras con la estructura ¿Qué es? / ¿Para qué sirve? / ¿Cómo se usa?
- Código ejecutable y comentado (excepto el 01, que es conceptual)
- Cajas de *tips* y errores comunes de alto valor
- Ejercicios prácticos y un glosario de referencia

---

## ¿Qué aprenderás?

### Habilidades técnicas
- Python para análisis de datos
- NumPy y Pandas (manipulación de datos)
- Estadística descriptiva e inferencial
- Limpieza, preparación y *feature engineering*
- Visualización con Matplotlib, Seaborn y Plotly
- SQL y bases de datos
- Excel avanzado y herramientas de BI (Power BI, Tableau)
- Ingeniería de datos básica (ETL, pipelines, formatos)
- Modelado predictivo básico (regresión, clasificación, evaluación)
- Control de versiones con Git

### Habilidades de negocio
- Pensamiento analítico estructurado
- Comunicación y *storytelling* con datos
- Traducir métricas a impacto y decisiones
- Ética y responsabilidad en el uso de datos

---

## Tecnologías y librerías

| Categoría | Librerías |
|-----------|-----------|
| **Core** | NumPy, Pandas, Polars |
| **Visualización** | Matplotlib, Seaborn, Plotly |
| **Estadística / ML** | SciPy, Scikit-learn |
| **Bases de datos** | SQLite, SQLAlchemy |
| **Apps y dashboards** | Streamlit, Dash |
| **Excel** | OpenPyXL, XlsxWriter |
| **Notebooks** | Jupyter Lab |

---

## Proyectos destacados (notebook 18)

**Proyecto 1 — E-commerce: optimización de conversión**
Análisis de *funnel*, segmentación y priorización de mejoras por impacto/esfuerzo.

**Proyecto 2 — FinTech: análisis de churn y retención**
*Risk scoring*, segmentación por riesgo y estrategia de retención con análisis de ROI.

Además, el notebook 18 incluye **tres retos guiados** (Marketing, HR y un sistema integrado) con su enunciado, para que construyas tu propio portafolio.

---

## Notas

- **Datos:** todos los datasets son **simulados pero realistas**; se generan dentro de cada notebook.
- **Entorno:** el código está probado con versiones recientes de las librerías (Python 3.9+, Pandas 2/3, Scikit-learn).
- **Reproducibilidad:** usa un entorno virtual por proyecto (ver notebook 02 y 11).

---

## Contribuciones

Este es un proyecto educativo abierto. Si encuentras errores o quieres mejorar el contenido, abre un *issue* o un *pull request*.

## Licencia

Bajo la Licencia MIT — ver el archivo `LICENSE` para más detalles.
