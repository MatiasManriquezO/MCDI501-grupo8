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
- **Muestra de análisis:** 3.478 estudiantes, 38,6 % desertores (se excluyen 152 registros sin actividad académica).
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
│   ├── 00_generacion_faltantes.ipynb                 # se ejecuta una sola vez
│   ├── 01_formativa1_eda_inferencia.ipynb            # Fase 1 · Formativa 1
│   └── 02_sumativa1_analisis_exploratorio_inferencial.ipynb   # Fase 2 · Sumativa 1
├── figuras/
│   ├── formativa1/                     # figuras del informe de la Formativa 1
│   └── sumativa1/                      # figuras del informe de la Sumativa 1
└── docs/
    ├── checklist_rubricas.md           # dónde se cumple cada criterio de las rúbricas
    └── informe/                        # informes (Word; se exportan a PDF para Canvas)
```

## Avance por evaluación

| Evaluación | Fase | Contenido | Estado |
| --- | --- | --- | --- |
| Formativa 1 | 1 | Definición del problema, descriptiva, intervalos de confianza y pruebas de hipótesis | Informe y notebook listos |
| Sumativa 1 | 2 | Análisis exploratorio e inferencial | Informe y notebook listos |
| Formativa 2 | 3 | Modelamiento predictivo | Pendiente |
| Sumativa 2 | 3 | Validación, simulación y remuestreo | Pendiente |
| Sumativa 3 | 4 | Modelamiento predictivo integrado | Pendiente |

## Cómo reproducir

Requisitos: Python 3.10 o superior.

```bash
git clone https://github.com/MatiasManriquezO/MCDI501-grupo8.git
cd MCDI501-grupo8
pip install -r requirements.txt
jupyter lab
```

Ejecutar los cuadernos de `notebooks/` en orden. `00_generacion_faltantes.ipynb` solo genera los archivos de
`data/processed/` si todavía no existen, para que los faltantes sean siempre los mismos. Todos los cálculos
aleatorios usan la semilla 42.

## Convención de commits

Cada commit debe empezar con un prefijo que indique el **tipo de cambio**, seguido de dos puntos y una
descripción breve en presente. Lo que decide el prefijo es **qué archivo cambia y por qué**, no si el cambio
"corrige algo" o no.

Formato: `prefijo: verbo en presente + qué cambia`, todo en minúsculas y sin tildes
(por ejemplo `docs: agrega informe de la formativa 1`, no `Docs: Se agregó el informe`).

### Definición de cada prefijo

| Prefijo | Úsalo cuando... | No lo uses para... |
|---|---|---|
| `docs` | subes o editas documentación: README, `data/README.md`, informes en `docs/informe/`, checklist de rúbricas, comentarios explicativos en los cuadernos | cambios en los datos o en celdas de código que se ejecutan (aunque el archivo sea texto) |
| `data` | agregas, actualizas o reemplazas archivos de datos en `data/raw/` o `data/processed/` | cambiar cómo se limpian o filtran los datos dentro del cuaderno (eso es `feat` o `fix`) |
| `feat` | implementas algo nuevo: un cuaderno, un análisis, una prueba de hipótesis, un intervalo de confianza, una figura, una carpeta de fase | corregir algo que ya existía y estaba mal (eso es `fix`) |
| `fix` | corriges un error real en el código, en los resultados o en la estructura de archivos (rutas rotas, archivos que no debían subirse, un filtro mal aplicado) | mejorar la redacción o completar información en un informe o README (eso es `docs`) |
| `test` | agregas o ejecutas validaciones: nulos, duplicados, rangos, tipos de dato, que los faltantes sean MCAR, que los archivos se reproduzcan igual con la semilla 42 | escribir el análisis que se está validando (eso es `feat`) |

### Ejemplos de commits

| Prefijo | Mensaje de commit | Qué cambia realmente |
|---|---|---|
| `docs` | `docs: agrega informe de la formativa 1` | se sube el Word del informe a `docs/informe/` |
| `docs` | `docs: actualiza README con la muestra de analisis` | se edita texto explicativo, no código ni datos |
| `docs` | `docs: corrige rango de la tabla 1 en el informe` | aunque "corrige", solo cambia texto del informe |
| `data` | `data: incorpora dataset predict students dropout de UCI` | se agrega `data/raw/data.csv` |
| `data` | `data: agrega datos con faltantes MCAR y valores originales` | se agregan los dos CSV de `data/processed/` |
| `feat` | `feat: agrega notebook de la formativa 1 con descriptiva e inferencia` | se crea un cuaderno nuevo |
| `feat` | `feat: agrega prueba z de dos proporciones para matricula al dia` | se agrega un análisis que no existía |
| `fix` | `fix: excluye registros sin actividad academica del analisis` | se corrige un filtro que dejaba datos que no correspondían |
| `fix` | `fix: elimina archivos txt que no corresponden` | se quita algo que no debía estar versionado |
| `test` | `test: valida con chi cuadrado que los faltantes sean MCAR` | se verifica un supuesto sobre datos ya existentes |
| `test` | `test: verifica que los faltantes se reproduzcan con la semilla 42` | se comprueba que los archivos generados no cambian |

## Créditos

Datos: Realinho, V., Vieira Martins, M., Machado, J. y Baptista, L. (2021). *Predict students' dropout and academic
success* [Conjunto de datos]. UCI Machine Learning Repository. Licencia CC BY 4.0.
