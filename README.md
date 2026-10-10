# Proyecto Grupo 8 · MCDI501

**Estadística Computacional para la Toma de Decisiones (MCDI501)**
Magíster en Ciencia de Datos e Inteligencia Artificial, Universidad Andrés Bello · 2026

## Integrantes

| Integrante | Usuario GitHub |
| --- | --- |
| Abigail Roblez Chavez | @AbigailRoblesC-github |
| Daniel Pérez Ramirez | @DanielRamirezPerez-github |
| Matias Manriquez Ortiz | @MatiasManriquezO-github |
| Roberto Sánchez Saldivia | @RobertSanchezS-github |

## Problema

Detección temprana del riesgo de deserción en educación superior. Con el conjunto
*Predict Students' Dropout and Academic Success* (UCI, 2021) se busca identificar qué características de los
estudiantes y de su primer año académico se asocian con desertar, para priorizar el apoyo institucional.

- **Variable objetivo del proyecto:** Dropout (1) frente a Graduate (0). Se excluyen los estudiantes Enrolled.
- **Muestra de análisis:** 3.630 estudiantes, 39,1 % desertores.
- **Datos faltantes:** generados al azar (MCAR, 12 %) en la nota de admisión y la edad, según el apunte del curso.

El detalle de los datos y las decisiones está en [`data/README.md`](data/README.md).

## Estructura del repositorio

```
proyecto-grupo8-mcdi501/
├── README.md
├── requirements.txt
├── .gitignore
├── data/
│   ├── README.md                       # fuente, decisiones y diccionario de variables
│   ├── raw/data.csv                    # datos originales
│   └── processed/
│       ├── data_con_faltantes.csv      # versión usada en todo el proyecto
│       └── valores_originales.csv      # valores eliminados, para medir la imputación
├── notebooks/
│   ├── 00_generacion_faltantes.ipynb   # se ejecuta una sola vez
│   └── 01_formativa1_eda_inferencia.ipynb
├── figuras/                            # figuras generadas por los cuadernos
└── docs/
    └── informe/                        # informes entregados
```

## Avance por evaluación

| Evaluación | Fase | Contenido | Estado |
| --- | --- | --- | --- |
| Formativa 1 | 1 | Definición del problema, descriptiva, intervalos de confianza y pruebas de hipótesis | En curso |
| Sumativa 1 | 2 | Análisis exploratorio e inferencial | Pendiente |
| Formativa 2 | 3 | Modelamiento predictivo | Pendiente |
| Sumativa 2 | 3 | Validación, simulación y remuestreo | Pendiente |
| Sumativa 3 | 4 | Modelamiento predictivo integrado | Pendiente |

## Cómo reproducir

Requisitos: Python 3.10 o superior.

```bash
git clone https://github.com/<usuario>/proyecto-grupo8-mcdi501.git
cd proyecto-grupo8-mcdi501
pip install -r requirements.txt
jupyter lab
```

Ejecutar los cuadernos de `notebooks/` en orden. `00_generacion_faltantes.ipynb` solo genera los archivos de
`data/processed/` si todavía no existen, para que los faltantes sean siempre los mismos. Todos los cálculos
aleatorios usan la semilla 42.

## Créditos

Datos: Realinho, V., Vieira Martins, M., Machado, J. y Baptista, L. (2021). *Predict students' dropout and academic
success* [Conjunto de datos]. UCI Machine Learning Repository. Licencia CC BY 4.0.
