# Project README

## Overview
This project analyzes a weather dataset using Python. The analysis includes data cleaning, outlier detection, and visualization of various meteorological variables.

## Key Steps
1. **Data Loading and Inspection**: Load the dataset and inspect its structure.
2. **Statistical Summary**: Calculate mean, standard deviation, min, max, and median for numeric columns.
3. **Missing Values and Duplicates**: Check for null values and duplicates; drop columns with more than 50% missing data.
4. **Outlier Handling**: Detect and replace outliers based on a z-score threshold.
5. **Visualization**:
   - Boxplots to identify outliers.
   - Time series plot for GHI, DNI, and DHI.
   - Correlation heatmap.
   - Scatter matrix for wind conditions and solar irradiance.
   - Polar plot for wind speed and direction.
   - Joint plots for temperature analysis.
   - Histograms to visualize frequency distributions.
   - Bubble chart to explore relationships between GHI, temperature, wind speed, and humidity.

## Dependencies
- `pandas`
- `numpy`
- `seaborn`
- `matplotlib`

