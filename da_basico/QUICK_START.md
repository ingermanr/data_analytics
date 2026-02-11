# ■ GUÍA DE INICIO RÁPIDO

## ▸ Empezar en 5 Minutos

### ① Instalar Python
Descarga e instala Python 3.9+ desde [python.org](https://www.python.org/downloads/)

### ② Crear Ambiente Virtual
```bash
python -m venv venv
```

### ③ Activar Ambiente
**Windows:**
```bash
venv\Scripts\activate
```

**Linux/Mac:**
```bash
source venv/bin/activate
```

### ④ Instalar Dependencias Básicas
```bash
pip install numpy pandas matplotlib seaborn scipy jupyter
```

### ⑤ Iniciar Jupyter
```bash
jupyter lab
```

### ⑥ Abrir Primer Notebook
Navega a: `01_fundamentos/01_fundamentos_matematicos_estadisticos.ipynb`

---

## ▪ Ruta de Aprendizaje Recomendada

### Semana 1-2: Fundamentos
- [ ] 01_fundamentos_matematicos_estadisticos.ipynb
- [ ] 02_programacion_python.ipynb

### Semana 3-4: Manipulación de Datos
- [ ] 03_manipulacion_datos_numpy.ipynb
- [ ] 04_analisis_datos_pandas.ipynb
- [ ] 05_limpieza_preparacion_datos.ipynb

### Semana 5-6: Exploración y Visualización
- [ ] 06_analisis_exploratorio_datos.ipynb
- [ ] 07_visualizacion_datos.ipynb

### Semana 7-8: Herramientas Adicionales
- [ ] 08_sql_bases_datos.ipynb
- [ ] 09_excel_analisis_datos.ipynb
- [ ] 10_herramientas_bi.ipynb

### Semana 9-10: Tecnologías Modernas
- [ ] 11_control_versiones.ipynb
- [ ] 12_ingenieria_datos_basicos.ipynb
- [ ] 13_librerias_modernas.ipynb

### Semana 11-12: Integración y Proyectos
- [ ] 14_soft_skills_metodologia.ipynb
- [ ] 15_proyectos_aplicados.ipynb

---

## ▪ Tips Importantes

### □ Recomendaciones
- **Ejecuta TODO el código** mientras lees - no solo leas
- **Modifica los ejemplos** - experimenta con diferentes valores
- **Toma notas** - añade celdas markdown con tus observaciones
- **Practica diariamente** - mejor 1 hora/día que 7 horas un solo día
- **Únete a comunidades** - r/datascience, Kaggle, Stack Overflow

### ✕ Errores Comunes
▸ No instalar las dependencias correctamente
▸ Saltar notebooks sin completar los anteriores
▸ Solo leer sin ejecutar código
▸ No practicar con datasets propios
▸ Abandonar cuando algo no funciona (¡persiste!)

---

## ▸ Solución de Problemas

### ¿Python no se reconoce?
Añade Python al PATH durante la instalación o manualmente:
- Windows: Variables de entorno > Path > Agregar ruta de Python

### ¿Jupyter no inicia?
```bash
pip install --upgrade jupyter jupyterlab
```

### ¿Error al importar librerías?
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

### ¿Notebooks muy lentos?
- Reinicia el kernel: Menú > Kernel > Restart Kernel
- Cierra notebooks no usados
- Libera memoria: `del variable_grande`

---

## ▪ Recursos Adicionales

### Documentación Oficial
- [Python](https://docs.python.org/3/)
- [NumPy](https://numpy.org/doc/)
- [Pandas](https://pandas.pydata.org/docs/)
- [Matplotlib](https://matplotlib.org/stable/contents.html)

### Práctica
- [Kaggle](https://www.kaggle.com/) - Competencias y datasets
- [DataCamp](https://www.datacamp.com/) - Ejercicios interactivos
- [LeetCode](https://leetcode.com/) - Problemas de Python

### Comunidades
- [r/learnpython](https://www.reddit.com/r/learnpython/)
- [r/datascience](https://www.reddit.com/r/datascience/)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/python)

---

## ▪ ¿Completaste el Curso?

### Próximos Pasos:
1. **Construye tu portfolio** - Sube proyectos a GitHub
2. **Kaggle competitions** - Participa y aprende de otros
3. **Contribuye a open source** - Mejora proyectos existentes
4. **Networking** - LinkedIn, meetups, conferencias
5. **Aplica a trabajos** - ¡Estás listo para ser Data Analyst!

---

**¡Mucho éxito en tu journey como Data Analyst!** ▸

*Si tienes preguntas, consulta el README.md completo*
