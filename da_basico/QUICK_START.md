# Guía de Inicio Rápido

## Empezar en 5 minutos

### 1. Instalar Python
Descarga e instala Python 3.9+ desde [python.org](https://www.python.org/downloads/).

### 2. Crear un entorno virtual
```bash
python -m venv venv
```

### 3. Activar el entorno
```bash
# Windows
venv\Scripts\activate
# Linux / Mac
source venv/bin/activate
```

### 4. Instalar dependencias
```bash
pip install -r requirements.txt
# o lo esencial para empezar:
pip install numpy pandas matplotlib seaborn scipy scikit-learn jupyter
```

### 5. Iniciar Jupyter
```bash
jupyter lab
```

### 6. Abrir el primer notebook
Empieza por `01_fundamentos_matematicos_estadisticos.ipynb` y avanza en orden.

---

## Ruta de aprendizaje recomendada

Sigue los notebooks **en orden numérico** (01 → 18). Este plan de 8 semanas es una guía; ajústalo a tu ritmo.

### Semana 1 — Fundamentos
- [ ] `01_fundamentos_matematicos_estadisticos` *(solo conceptos, sin código)*
- [ ] `02_programacion_python`

### Semana 2 — Manipulación de datos
- [ ] `03_manipulacion_datos_numpy`
- [ ] `04_analisis_datos_pandas`

### Semana 3 — Preparación y exploración
- [ ] `05_limpieza_preparacion_datos`
- [ ] `06_analisis_exploratorio_datos`

### Semana 4 — Comunicar y obtener datos
- [ ] `07_visualizacion_datos`
- [ ] `08_sql_bases_datos`

### Semana 5 — Herramientas de negocio
- [ ] `09_excel_analisis_datos`
- [ ] `10_herramientas_bi`

### Semana 6 — Flujo de trabajo y herramientas modernas
- [ ] `11_control_versiones`
- [ ] `12_ingenieria_datos_basicos`
- [ ] `13_librerias_modernas`

### Semana 7 — Modelado predictivo
- [ ] `14_fundamentos_modelado_predictivo`
- [ ] `15_regresion_y_clasificacion_basica`
- [ ] `16_evaluacion_modelos_y_decisiones_negocio`

### Semana 8 — Cierre y práctica
- [ ] `17_soft_skills_metodologia`
- [ ] `18_proyectos_aplicados`

---

## Tips importantes

### Recomendaciones
- **Ejecuta TODO el código** mientras lees — no solo leas.
- **Modifica los ejemplos** — experimenta con distintos valores.
- **Toma notas** — añade celdas markdown con tus observaciones.
- **Practica a diario** — mejor 1 hora/día que 7 horas de golpe.
- **Únete a comunidades** — r/dataanalysis, Kaggle, Stack Overflow.

### Errores comunes a evitar
- No instalar bien las dependencias (activa el entorno virtual antes de `pip install`).
- Saltarte notebooks sin completar los anteriores (rompe la gradualidad).
- Solo leer sin ejecutar el código.
- Abandonar cuando algo no funciona — persiste y busca el error.

---

## Solución de problemas

### Python no se reconoce
Añade Python al PATH durante la instalación, o manualmente en Variables de entorno (Windows).

### Jupyter no inicia
```bash
pip install --upgrade jupyter jupyterlab
```

### Error al importar librerías
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### Notebooks lentos
- Reinicia el kernel: Menú → Kernel → Restart Kernel.
- Cierra notebooks que no estés usando.
- Libera memoria: `del variable_grande`.

---

## ¿Completaste el curso?

### Próximos pasos
1. **Construye tu portafolio** — sube tus proyectos a GitHub (ver notebook 11).
2. **Elige un reto** del notebook 18 y constrúyelo de punta a punta.
3. **Participa en Kaggle** — aprende de notebooks públicos.
4. **Comparte en LinkedIn** — cuenta el *insight* y su impacto, no el código.
5. **Aplica a trabajos** — ¡ya tienes las bases para ser Data Analyst!

---

*Si tienes dudas, consulta el `README.md` completo.*
