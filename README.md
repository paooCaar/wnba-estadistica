# Proyecto Final — Estadística Matemática

Ajuste de modelos paramétricos, estimación, intervalos de confianza y pruebas de hipótesis con estadísticas de jugadoras de la **WNBA** (temporadas regulares 2023–2025).

## Estructura

```
data/
  wnba_jugadoras_2023_2025.csv   # 440 jugadoras-temporada (≥ 10 partidos)
notebooks/
  analisis.ipynb                 # todo el análisis (pasos 2–6)
figuras/                         # histogramas y ajustes (los genera el notebook)
reporte/
  reporte_wnba.pdf               # reporte final con interpretaciones
requirements.txt
```

## Cómo correrlo

```bash
python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

Abre `notebooks/analisis.ipynb` en VS Code (o con `jupyter notebook`), elige el kernel `.venv` y ejecuta **Run All**.

## Contenido del análisis

1. **Datos:** box scores de ESPN publicados por [SportsDataverse](https://github.com/sportsdataverse/sportsdataverse-data) (`wehoop`), agregados a promedios por jugadora y temporada.
2. **Modelos propuestos:** Normal, Exponencial, Gamma, Lognormal y Beta para seis variables (minutos, puntos, rebotes, asistencias, % tiros libres, % tiros de campo).
3. **Estimación:** método de momentos y máxima verosimilitud.
4. **Histogramas** (`density=True`) con las densidades ajustadas; elección visual del mejor modelo, con AIC como apoyo.
5. **Intervalos de confianza al 95%:** exactos (t, χ²) para la Normal; Wald con información de Fisher y bootstrap para Gamma y Beta.
6. **Pruebas de hipótesis:** razón de verosimilitudes y Wald para H₀: α = 1 (¿basta la Exponencial?), prueba t para la media, Wald para la media de una Beta y t de Welch para dos muestras.

## Resultados principales

| Variable | Mejor modelo |
| --- | --- |
| Puntos, rebotes, asistencias por partido | Gamma |
| Minutos (proporción de 40), % tiros libres | Beta |
| % tiros de campo | Normal |
