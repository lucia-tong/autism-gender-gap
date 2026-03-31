# Brecha de Género en el Diagnóstico del TEA

Un análisis de datos a escala global (194 paises) para cuantificar la brecha de género en el diagnóstico del Trastorno del Espectro Autista: edad de diagnóstico, prevalencia reportada y acceso a terapias, cruzados con indicadores socioeconómicos por país.

## qué hace

* construye un dataset consolidado a partir de fuentes públicas (GBD/IHME, Our World in Data, WHO Atlas, Banco Mundial, PNUD)
* analiza la distribución de la brecha de diagnóstico por género y región
* identifica correlaciones entre la brecha y variables como el GII, el PIB o el gasto en salud mental
* entrena modelos de regresión para predecir la edad de diagnóstico en mujeres
* clasifica países según probabilidad de diagnóstico tardío (variable binaria)
* segmenta países con K-Means en 4 perfiles de inequidad diagnóstica
* genera visualizaciones exportables a `outputs/`

## estructura

```
tfm-autism-gender-gap/
├── autism_gender_gap.ipynb   # pipeline completo: EDA, modelos, clustering
├── requirements.txt
└── README.md
```

## cómo ejecutarlo

```bash
pip install -r requirements.txt
jupyter notebook autism_gender_gap.ipynb
```

el notebook genera automáticamente la carpeta `outputs/` con todos los gráficos.

## variables principales del dataset

* `age_gap` — brecha en edad de diagnóstico (mujeres − hombres, en años)
* `diagnosis_gap` — brecha de prevalencia reportada (hombres − mujeres, por 100k)
* `gii` — Gender Inequality Index (PNUD)
* `mental_health_exp` — gasto en salud mental como % del gasto sanitario (WHO)
* `late_diagnosis` — variable binaria: 1 si age_gap supera el percentil 75

## modelos aplicados

* regresión: Ridge, Random Forest
* clasificación: Regresión Logística, Random Forest (AUC-ROC target: 0.89)
* clustering: K-Means K=4 con validación por Silhouette Score y método del codo
* explicabilidad: importancia de variables por Random Forest (SHAP en el pipeline completo)

## fuentes de datos

* GBD Study — IHME (prevalencia TEA por país y género)
* Our World in Data — Autism dataset
* WHO Mental Health Atlas 2020
* Banco Mundial — World Development Indicators
* PNUD — Human Development Reports

## stack

python · pandas · numpy · scikit-learn · matplotlib · seaborn
