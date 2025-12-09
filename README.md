# Middlesex Air Quality (PM2.5) - 2020 and 2021

Daily PM2.5/AQI from EPA AQS for Middlesex County, NJ, paired with daily weather from Open-Meteo. The notebook pulls data, cleans/merges on `date_local`, explores patterns, and fits baseline linear checks plus tree-based regressors (RandomForest, Gradient Boosting, Extra Trees), including an out-of-time test on 2021.

## Data
- `pm25_middlesex_2020_daily.json`: EPA AQS daily PM2.5/AQI for 2020 (Middlesex County).
- `pm25_middlesex_2021_daily.json`: EPA AQS daily PM2.5/AQI for 2021.
- `meteo_middlesex_2020_daily.json`: Open-Meteo daily weather for 2020.
- `meteo_middlesex_2021_daily.json`: Open-Meteo daily weather for 2021.

## Notebook workflow (main.ipynb)
1. Fetch PM2.5/AQI (EPA AQS) and weather (Open-Meteo) for Middlesex County.
2. Merge on `date_local`; clean: dedupe by date, coerce numerics, drop negatives, drop rows with missing modeling fields.
3. EDA: correlation heatmaps, PM2.5 vs temp/humidity plots, residuals, feature importances.
4. Models:
   - Linear fits on single features.
   - RandomForest/Gradient Boosting/Extra Trees with 2020 train/test split for in-year metrics.
   - RandomForest trained on all 2020, tested on 2021 (out-of-time).
5. Outputs: R²/MSE, feature importances, and plots.

## Requirements
- Python 3, pandas, numpy, matplotlib, seaborn, scikit-learn, requests.
- Install via pip:
  ```
  pip install pandas numpy matplotlib seaborn scikit-learn requests
  ```

## Running
- Open `main.ipynb` in Jupyter/VS Code.
- Run cells in order; network access is needed for the API fetch steps, or use the provided JSON files to skip fetching.
