## Reto: **"Construyendo un ETL de exploración y pre-procesado"**

**Objetivo del Reto:**  
Evolucionar la solución para convertirlo en un ETL que use Numpy y Pandas para realizar un Análisis Exploratorio de Datos (EDA) para identificar patrones en el historial de fallos, manejo de valores faltantes y creación de variables adicionales. El objetivo es comprender las características que pueden afectar el rendimiento y desgaste de los equipos.

Para ello, PowerGen nos ha provisto de 3 fuentes de datos para obtener la información que necesitamos: *Historicos de Ordenes de Trabajo*, *Caracteristicas de los Equipos*, y *Registros de Condiciones*.

Nuestra misión es analizar y visualizar los datos de mantenimiento de los equipos de una planta energética, para comprender patrones de fallos, identificar relaciones entre las condiciones operativas de los equipos y sus características, y generar visualizaciones que ayuden a prever posibles fallos o necesidades de mantenimiento.


### **Tareas del Reto:**

#### **1. Limpieza y Preprocesamiento de Datos con Python**

  **Objetivo:** Limpiar y preprocesar los tres datasets para que los datos estén listos para su análisis.
  
  **Tareas:**
  - Cargar los tres datasets:
    - `Historicos_Ordenes.csv` (Órdenes de trabajo)
    - `Registros_Condiciones.csv` (Registros de condiciones operativas)
    - `Caracteristicas_Equipos.csv` (Características de los equipos)

  - Opcional: Cargar los datasets de datalake (ver connection string)
   
  
  - Identificar y manejar **valores nulos** en las columnas clave (por ejemplo, `Costo_Mantenimiento`, `Temperatura_C` y `Horas_Operativas`).
  
  - Eliminar **duplicados** y corregir **inconsistencias de formato** (como valores erróneos en campos numéricos).
  
  - Agregar nuevas columnas relevantes como:
    - **Frecuencia de mantenimiento**: Número de mantenimientos realizados por equipo.
    - **Vida útil estimada**: Estimación de la vida útil de los equipos basada en las horas operativas.
  
#### **2. Análisis Exploratorio de Datos con Python**

  **Objetivo:** Analizar las relaciones entre las características de los equipos, el historial de órdenes de trabajo y las condiciones operativas.

  **Tareas:**
  - Realizar un **análisis descriptivo** de los datos:
    - Estadísticas básicas como la media, mediana y desviación estándar de las horas operativas, el costo de mantenimiento, y la frecuencia de fallos.
    - Detectar **outliers** en las columnas clave (por ejemplo, en `Costo_Mantenimiento` y `Horas_Operativas`).
  
  - Analizar la **distribución de fallos** y **tipos de mantenimiento** (correctivo/preventivo) de los equipos.
  
  - Establecer posibles **correlaciones** entre las variables, como la relación entre las **condiciones operativas** (temperatura, vibración) y las **horas de operación**.
  
  - **Recomendación:** Usar técnicas como `groupby()`, `corr()`, visualización de **histogramas** y **diagramas de dispersión** para detectar patrones y correlaciones.

#### **3. Mezcla y Combinación de Datos**

  **Objetivo:** Combinar los tres datasets en un único conjunto de datos que contenga toda la información relevante de cada equipo, las condiciones operativas y las órdenes de mantenimiento.

  **Tareas:**
  - **Merge**: Utilizar la función `merge()` de `pandas` para combinar los tres datasets en un único dataframe. Las combinaciones deben realizarse a través de la columna `ID_Equipo` (o cualquier otro identificador único de equipo).
  
  - Asegurarse de que las columnas combinadas estén correctamente alineadas y que no haya **valores nulos** o **duplicados** tras la combinación.
  
  - Crear nuevas columnas combinadas que representen relaciones clave:
    - **Tiempo hasta fallo**: ¿Cuánto tiempo de operación transcurre hasta que un equipo requiere mantenimiento?
    - **Relación entre condiciones operativas y fallos**: ¿Cómo impactan la vibración o temperatura en la probabilidad de un fallo?
  
  - **Recomendación:** Usar `pandas` para realizar los **joins o merges** y la combinación de datasets, además de limpiar los datos resultantes para asegurarse de que no haya errores en los valores.

#### **4. Visualización de Datos**

  **Objetivo:** Crear visualizaciones interesantes para mostrar los hallazgos encontrados durante el análisis y la combinación de datos.

  **Tareas:**
  - Crear **gráficas de barras** para mostrar la distribución del costo de mantenimiento por tipo de equipo.
  
  - Crear **diagramas de dispersión** para visualizar la relación entre las condiciones operativas (por ejemplo, temperatura y vibración) y las horas de operación o fallos.
  
  - Crear un **diagrama de caja** para identificar los **outliers** en las horas operativas o costos de mantenimiento.
  
  - Generar una **visualización de la frecuencia de mantenimiento** por tipo de equipo y la relación con el tipo de mantenimiento (correctivo/preventivo).
  

#### **5. Carga y Almacenamiento**

  **Objetivo:** Crear visualizaciones interesantes para mostrar los hallazgos encontrados durante el análisis y la combinación de datos.
  **Tareas:**
  - Guardar el dataset final en:
    - 📂 CSV limpio para análisis exploratorio.
    - 🗄️ PostgreSQL para almacenamiento estructurado.
  - Opcional: Guardar en formato Parquet para optimizar rendimiento.


#### **6. Conclusiones**

  **Objetivo:** Generar un resumen sobre la calidad de los datos y los insights encontrados.
  **Tareas:**
  - Redacta las conclusiones del análisis y limpieza de datos


#### **NOTAS:** 
- Todas las soluciones en Python deben implementarse mediante funciones. Las funciones deben invocarse al final para ejecutar el proceso deseado.
- Usar el kernel: **Python 3.8 - AzureML (Python 3.10.11)**


### **Estructura de carpetas:**
- Carpeta **src** para los `jupyter notebooks` y `archivos` de trabajo  
- Carpeta **dist** para *exportar los jupyter notebooks a módulos*. (Opcional).
- Los **output** para almacenar archivos *csv*
- Ejemplo: 

```
.
└── reposiutorio/
    ├── output/
    │   └── [archivos csv o parquet]
    ├── dist/
    │   └── [módulos python]
    └── src/
        └── [archivos jupyter y python]
```


### **Trabajo en equipo:**  
   - Usar un repositorio el común.
      - Trabajar en la rama "etapa 2"
   - Trabajo por pares:
      - Recomendable abordar las tareas por pares.
   - Dividir las tareas.
   - Recomendaciones:
      - Evitar trabajar en el mismo archivo a la vez. Especialmente los jupyter notebooks.
      - Comunicarse cuando haya commits y pushes para realizar pulls. Evitar en lo posible conflictos.

### **Entregables:**

1. **Código Python** con la limpieza, preprocesamiento y análisis de datos.
2. **Jupyter Notebook** o archivo de texto que contenga todo el análisis exploratorio realizado, incluyendo los insights obtenidos.
3. **Visualizaciones** generadas para mostrar los patrones y relaciones entre las variables clave.
4. **Conjunto de datos final** (combinado) que puede ser utilizado para realizar modelado predictivo o más análisis.
5. **Almacenamiento final** versión almacenada de los datos (csv, db, parquet) 

### **Criterios de Evaluación:**  

- **Claridad en la limpieza de datos**: Asegurarse de que no hay valores nulos, duplicados ni inconsistencias.
- **Profundidad en el análisis exploratorio**: Evaluación de si se han identificado patrones y relaciones importantes en los datos.
- **Calidad de las visualizaciones**: Gráficos claros, informativos y bien estructurados.
- **Calidad de la combinación de los datasets**: La combinación de datos ha sido exitosa y que el conjunto de datos resultante está listo para los siguientes pasos de modelado predictivo.
