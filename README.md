# flightpath-fractures
Analysis of the NASA Anomaly Detection Dataset (SMAP/MSL) focusing on labeled spacecraft telemetry anomalies. This notebook investigates anomaly characteristics, visualizes time series data, and addresses data quality challenges related to out-of-bounds anomaly indices.

# NASA Spacecraft Anomaly Detection Dataset Exploration and Analysis
## Project Overview
This project explores and analyzes the "NASA Anomaly Detection Dataset (SMAP/MSL)" available on KaggleHub. The dataset contains labeled anomalies from NASA's SMAP (Soil Moisture Active Passive) and MSL (Mars Science Laboratory) missions, providing valuable real-world spacecraft telemetry data for understanding and potentially detecting anomalies.

## The primary objective of this notebook is to:

* Load and explore the dataset.
* Analyze the characteristics of the labeled anomalies (e.g., class distribution, duration).
* Visualize time series data and highlight anomaly segments.
* Perform quantitative analysis on anomaly segments.
* Identify and document any data quality issues.
* Summarize key findings and suggest future research directions.

## Dataset
The dataset is accessed via KaggleHub (patrickfleith/nasa-anomaly-detection-dataset-smap-msl). 

## It primarily consists of:
* A CSV file detailing labeled anomaly sequences with start and end time points, associated channel IDs, spacecraft, and anomaly classes.
* .npy files: NumPy binary files containing the actual time series telemetry data for each channel.

## Analysis Steps and Findings
The notebook follows a structured approach to explore and analyze the data:

## Dataset Download and Exploration: 
The dataset was downloaded using kagglehub, and the file structure was inspected to locate the relevant data files.

## Loading Anomaly Labels: The labeled_anomalies.csv file was loaded into a pandas DataFrame (anomalies_df).

## Initial Anomaly Analysis:
* Unique spacecraft and anomaly classes were identified (point, contextual).
* The distribution of anomaly classes was counted.
* The durations of anomaly sequences were calculated and their distribution visualized (e.g., using a histogram), showing a wide range of anomaly lengths.
  
## Time Series Visualization: 
For selected channels, the corresponding .npy time series data was loaded, and the data was plotted with the labeled anomaly segments highlighted.

## Investigation of Data Discrepancy: 
A significant data quality issue was discovered where many anomaly sequence indices in labeled_anomalies.csv were found to be out of bounds for the actual length of the .npy time series data files for several channels. This highlights a potential inconsistency in the dataset labeling or versions.

## Quantitative Analysis of Valid Anomaly Segments: 
Focusing on anomaly segments whose indices were confirmed to be within the bounds of their respective time series data, a quantitative analysis was performed. Measures such as duration, mean value, standard deviation, minimum value, and maximum value were calculated for each valid segment.

## Visualization of Anomaly Characteristics: 
Box plots (using Pygal and Matplotlib/Seaborn) were generated to visualize the distribution of the calculated quantitative measures (Minimum Value, Mean Value, Standard Deviation) across all valid anomaly segments. These plots provided visual insights into the central tendency, spread, and outliers of these characteristics.

# Key Findings Summarized

## Based on the analysis of the valid anomaly segments:
* A subset of labeled anomalies were successfully identified and analyzed within the data bounds.
* Anomalies exhibit diverse characteristics in terms of duration, mean value, and internal variability.
* A significant data quality issue exists with out-of-bounds anomaly indices for a notable portion of the labeled segments in the dataset.
  
## Conclusion and Future Work
This project provided valuable insights into the characteristics of labeled anomalies in the NASA spacecraft telemetry dataset, focusing on the reliably available data.
**The identification and handling of the data discrepancy were crucial steps.

For more in-depth analysis or building robust anomaly detection models using this dataset, further research is highly recommended to verify the data collection methods, labeling process, and potential versioning issues that led to the out-of-bounds indices. Future work could focus on addressing this data quality issue or concentrating analysis on channels with confirmed accurate labeling.

Note: This README is based on the analysis performed in the accompanying Jupyter/Colab notebook, where the code and visualizations can be viewed and executed.
