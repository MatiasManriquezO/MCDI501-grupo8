# Datos

## Dataset: Predict Students' Dropout and Academic Success

Datos de 4.424 estudiantes de pregrado de una institución de educación superior de Portugal, con información
demográfica, socioeconómica, macroeconómica y de desempeño académico en los dos primeros semestres.

- **Fuente:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/697/predict+students+dropout+and+academic+success) (Realinho et al., 2021). Licencia CC BY 4.0.
- **Archivo original:** `raw/data.csv` (separado por punto y coma, 4.424 filas y 37 columnas).
- **Variable objetivo original:** `Target`, con tres clases: Graduate (2.209), Dropout (1.421) y Enrolled (794).

## Decisiones que aplican a todo el proyecto

1. **Objetivo binario:** Dropout (1) frente a Graduate (0). Se excluyen los 794 estudiantes Enrolled, porque siguen
   matriculados y su desenlace todavía no se conoce. Quedan 3.630 estudiantes, 39,1 % desertores.
2. **Datos faltantes generados:** el archivo original no tiene faltantes. Siguiendo el apunte del curso, se eliminó
   al azar (MCAR) el 12 % de `Admission grade` y de `Age at enrollment` (531 valores cada una), con semilla 42.
   Lo hace una sola vez el cuaderno `notebooks/00_generacion_faltantes.ipynb`.
3. **Notas en cero:** `Curricular units 1st/2nd sem (grade)` vale 0 cuando el estudiante no aprobó ninguna unidad.
   Ese 0 se trata como ausencia de nota.

## Estructura

| Carpeta / archivo | Contenido |
| --- | --- |
| `raw/data.csv` | Datos originales, sin modificar |
| `processed/data_con_faltantes.csv` | Versión con faltantes generados; se usa en todo el proyecto. Agrega la columna `id_estudiante` |
| `processed/valores_originales.csv` | Valores eliminados (`id_estudiante`, `variable`, `valor_original`), para medir el error de imputación |

## Clasificación de variables

| Tipo | Variables |
| --- | --- |
| Cuantitativas continuas | Admission grade, Previous qualification (grade), Curricular units 1st/2nd sem (grade), Unemployment rate, Inflation rate, GDP |
| Cuantitativas discretas | Age at enrollment; Curricular units 1st/2nd sem: credited, enrolled, evaluations, approved, without evaluations |
| Cualitativas binarias | Daytime/evening attendance, Displaced, Educational special needs, Debtor, Tuition fees up to date, Gender, Scholarship holder, International |
| Cualitativa ordinal | Application order |
| Cualitativas nominales | Marital status, Application mode, Course, Previous qualification, Nacionality, Mother's/Father's qualification, Mother's/Father's occupation |

La columna `Daytime/evening attendance` trae un tabulador al final del nombre en el archivo original; los cuadernos
lo eliminan al cargar los datos.
