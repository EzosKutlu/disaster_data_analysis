# :mag_right: Disaster Events Analysis (2022–2025)
An exploratory data analysis (EDA) and machine learning project examining synthetic disaster event data across multiple disaster types, years, and geographic regions.


## :open_file_folder: Dataset
**File:** synthetic_disaster_events_2025.csv

### Key Columns

| Column | Description |
| :--- | :--- |
| **disaster_type** | Type of disaster |
| **location** | Country of the event |
| **latitude / longitude** | Geographic coordinates |
| **date** | Date of the event |
| **severity_level** | Severity score from 1 to 10 |
| **affected_population** | Number of people affected |
| **estimated_economic_loss_usd** | Economic loss in USD |
| **response_time_hours** | Hours until disaster response |
| **aid_provided** | Whether financial or material aid was provided in response to the event |
| **infrastructure_damage_index** | Infrastructure damage score |
| **is_major_disaster** | Binary label: **1** = Major, **0** = Non-Major |



## :bulb: Analysis Overview
### Data Preprocessing
•	Parsed date column to datetime format

•	Extracted year from date for time-based grouping

•	Filtered data for 2023–2025 for primary trend analysis

### Exploratory Analysis
•	Yearly economic loss trends by disaster type (line plot)

•	Top 10 disasters by economic loss (styled table)

•	Summary statistics by disaster type (mean, median, sum of losses; mean infrastructure damage index)

•	Economic loss distribution by disaster type (boxplot)

•	Response time distribution across severity levels (boxplot)

• Top 3 locations by disaster type based on event count (grouped ranking table)

• Global spatial distribution of disasters with major/non-major distinction (interactive map)

• Classification model performance for major disaster prediction (accuracy & classification report)



## :books: Exploratory Data Analysis (EDA)
### Year Distribution
The dataset covers 2022–2025. However 2022 accounts for only 2% of all records and was largely excluded from trend analyses. The remaining years (2023–2025) are evenly distributed at roughly 33% each.
### Economic Loss Trends
Yearly economic loss was analyzed by disaster type for 2023–2025. No significant trend was observed across years total losses remained relatively stable which is consistent with the synthetic nature of the dataset.
### Geographic Distribution
Data originates from only 8 countries, visualized on an interactive map using Folium. Major disasters (orange) and non-major disasters (blue) show no meaningful geographic clustering, further indicating artificial data generation.
### Response Time vs. Severity
Response time distributions are nearly identical across all severity levels (1–10). In real world scenarios, higher severity events would demand significantly longer or more variable response times. The absence of this pattern is a strong indicator that this dataset was synthetically generated.
### Major Disaster Rate Over Time
No significant trend observed. The near identical rates across 2023–2025 reflect the artificially balanced nature of the dataset.


## :bookmark: Key Findings
### Finding 1: Suspiciously Uniform Skewness Across Disaster Types
All disaster types exhibit a positive skew in the 0.85–0.90 range. Positive skewness in economic loss data is expected; a small number of catastrophic events pull the mean above the median. However, the near-identical skewness values across all seven disaster types are statistically suspicious.
In real world data, different disaster types would typically show meaningfully different distributional shapes depending on their nature, frequency, and geographic impact. The uniformity supports the hypothesis that this dataset was generated using the same statistical parameters for each category.

### Finding 2: Severity Level Directly Determines Major Disaster Status
Severity level 7 and above always results in a major disaster classification, while levels 6 and below almost never do. This means is_major_disaster is mechanically derived from severity_level, not an independent variable.

### Finding 3: Limited Geographic Scope
Despite representing global disaster events, the dataset contains records from only 8 countries. This significantly limits any geographic or regional analysis.

### Finding 4: Response Time Shows No Variation Across Severity Levels
The boxplot comparing response_time_hours across all severity_level values (1 through 10) reveals a striking pattern: response time distributions are nearly identical at every severity level.
The median, interquartile range, and whiskers remain virtually unchanged from severity 1 to severity 10. In real-world disaster response, one would expect significantly longer or more variable response times for higher-severity events, reflecting greater logistical complexity and resource demands.
This absence of any meaningful trend between severity and response time is one of the strongest indicators that this dataset was synthetically generated or artificially balanced, rather than derived from real-world observations.

## :computer: Machine Learning Model
### Goal
Predict whether a disaster event is a major disaster (is_major_disaster = 1 or 0).

### Approach
A Decision Tree Classifier was used a simple and interpretable model suitable for binary classification.

### Feature Selection
severity_level was intentionally excluded from the model because it directly determines the target variable. Including it would result an unrealistically perfect model.

### Results
The model correctly identifies 90% of real major disasters. In other words, it rarely labels a major disaster as non-major which is the most important outcome in a real disaster response scenario.

## :cd: Tech Stack

• Python 3

• Pandas

• Matplotlib

• Seaborn

• Folium

• Scikit-learn

• Jupyter Notebook (Anaconda)


## :unlock: Overall Conclusion
This dataset was generated for educational purposes and appears to be synthetically generated with artificially balanced distributions across categories. The lack of variation in response times by severity, combined with nearly identical skewness values across disaster types, are patterns inconsistent with real world disaster data.
Furthermore, the analysis revealed that the data came from only 8 countries and that the `is_major_disaster` variable was automatically derived from the `severity_level` variable.

These limitations make the dataset unsuitable for drawing real world conclusions, but it serves well as a practice environment for EDA and machine learning workflows.

## View Notebook
For full rendering including interactive map: (https://nbviewer.org/github/EzosKutlu/disaster_data_analysis/blob/main/Disaster%20Data%20Analysis%20Project.ipynb)
