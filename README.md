# Ecological Dataset Analysis

NYC-focused exploratory analysis of air quality measurements (2005–2023) and long-term Central Park weather summaries (1994–2024). The repository contains the raw CSVs and a starter notebook for cleaning, merging, and probing ecological trends.

## Contents
- `python_final.ipynb`: Jupyter notebook scaffold with path constants for loading the datasets using pandas.
- `air_quality.csv`: City-level air quality readings with columns such as `Name`, `Measure`, `Geo Place Name`, `Time Period`, `Start_Date`, and `Data Value`.
- `monthly_from_1994-1996.csv` … `monthly_from_2022-2024.csv`: Monthly Central Park climate summaries (station id, location, month, heating/cooling degree days, extremes, avg/max/min temperature).

## Getting Started
1. Create a virtual environment (optional but recommended):
   ```bash
   python3 -m venv .venv
   source .venv/bin/activate
   ```
2. Install dependencies:
   ```bash
   pip install pandas numpy jupyter
   ```
3. Launch the notebook:
   ```bash
   jupyter notebook python_final.ipynb
   ```

## Data Access
- The notebook currently points to `data/air_quality/air_quality_data.csv` and `data/weather/*.csv`. Either move the CSVs into that structure or update the `CSV_FILE_AIR_QUALITY` and `CSV_FILE_WEATHER_DIR` constants in the first code cell to match their current locations in the project root.
- All CSVs load cleanly with `pandas.read_csv`; parse dates in `Start_Date` (air quality) and `DATE` (weather) for time-series work.

## Suggested Analysis Steps
- Concatenate the weather CSVs into one DataFrame, ensuring `DATE` is converted to a monthly period or timestamp.
- Profile missing values and outliers in both datasets; standardize units and naming where needed.
- Join air quality and weather metrics by month/year to explore correlations (e.g., ozone vs. temperature, particulate matter vs. humidity proxies).
- Visualize temporal trends and seasonal patterns; highlight notable anomalies (heat waves, spikes in pollutants).

## Notes
- Keep the CSVs under version control only if size limits allow; otherwise consider using `.gitignore` and documenting the download source.
- If you add scripts beyond the notebook, prefer a `src/` directory with reusable loaders and plotting helpers.

## Sources
- Bai, X., Wang, Y., Gui, L., Tao, M., & Zeng, M. (2025). Comparing the influences on NO2 changes in terms of inter-annual and seasonal variations in different regions of China: Meteorological and anthropogenic contributions. *Remote Sensing, 17*(1), 121. https://www.mdpi.com/2072-4292/17/1/121
- Environmental Protection Agency. (n.d.). Particulate matter (PM) basics. U.S. Environmental Protection Agency. https://www.epa.gov/pm-pollution/particulate-matter-pm-basics
- Kwong, C. F., Tzortziou, M., Goldberg, D., Schiferl, L., Commane, R., Abuhassan, N., Szykman, J. J., & Valin, L. C. (2022). Declines and peaks in NO2 pollution during the multiple waves of the COVID-19 pandemic in the New York Metropolitan Area. *Atmospheric Chemistry and Physics, 22*(4), 2637–2652. https://pmc.ncbi.nlm.nih.gov/articles/PMC9798457/
- Luo, H., & Lu, C.-H. (2024). Impacts of local circulations on ozone pollution in the New York Metropolitan Area: Evidence from three summers of observations. *Journal of Geophysical Research: Atmospheres, 129*(17), e2023JD039206. https://agupubs.onlinelibrary.wiley.com/doi/full/10.1029/2023JD039206
- Cichowicz, R., Wielgosiński, G., & Fetter, W. (2017). Dispersion of atmospheric air pollution in summer and winter season. *Environmental Monitoring and Assessment, 189*(11), 571. https://pmc.ncbi.nlm.nih.gov/articles/PMC5671516/
- Wang, L., Chen, B., Ouyang, J. O., Mu, Y., Zhen, L., Yang, L., Xu, W., & Tang, L. (2025). Causal-inference machine learning reveals the drivers of China’s 2022 ozone rebound. *The Innovation, 6*(1), 100674. https://www.sciencedirect.com/science/article/pii/S266649842500002X
