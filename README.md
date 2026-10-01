# Last-Mile Delivery Bottleneck Analysis

## Project Overview

This project analyzes food delivery data to identify the main bottleneck in the last-mile delivery process and explore the factors associated with longer delivery times.

The analysis focuses on separating the delivery process into two main stages:

1. **Preparation Time** — time spent preparing the order.
2. **Post-Preparation Time** — the remaining delivery duration after preparation.

The project combines Python-based data analysis with a Tableau dashboard to communicate the main findings visually.

---

## Business Problem

Food delivery performance can be affected by several operational factors, including delivery distance, traffic conditions, weather, vehicle type, preparation time, and courier experience.

The main business questions addressed in this project are:

* What is the average delivery time?
* How much time is spent on order preparation?
* How much time is spent after preparation?
* Which stage represents the main observed bottleneck?
* How does delivery distance relate to post-preparation delivery time?
* How are traffic conditions associated with delivery time?
* Which combinations of distance and traffic are associated with the highest post-preparation times?
* Do weather and vehicle type show meaningful differences in post-preparation delivery time?

---

## Dataset

The project uses the `Food_Delivery_Times.csv` dataset.

The dataset contains **1,000 delivery records** and includes variables related to:

* Order ID
* Delivery distance
* Weather
* Traffic level
* Time of day
* Vehicle type
* Preparation time
* Courier experience
* Total delivery time

Two additional analytical features were created during the analysis:

* `Distance_Range`
* `Post_Preparation_Time_min`

The Tableau-ready dataset is exported as:

`Food_Delivery_Times_Tableau.csv`

---

## Data Cleaning

The dataset was reviewed and cleaned using Python.

The cleaning process included:

* Inspecting the dataset structure and data types
* Identifying missing values
* Reviewing categorical distributions
* Handling missing categorical values using the mode
* Handling missing courier experience values using the median
* Checking for duplicate rows
* Checking for duplicate Order IDs
* Validating numeric ranges
* Checking for negative or invalid values
* Reviewing potential outliers using the IQR method
* Validating categorical values
* Verifying that preparation time does not exceed total delivery time
* Confirming that the derived post-preparation time is non-negative

After cleaning:

* **Rows:** 1,000
* **Columns:** 11
* **Missing values:** 0
* **Duplicate rows:** 0
* **Duplicate Order IDs:** 0

No rows were removed during the cleaning process.

---

## Feature Engineering

### Distance Range

Raw delivery distance was grouped into four ranges:

* 0–5 km
* 5–10 km
* 10–15 km
* 15–20 km

This grouping makes it easier to compare delivery performance across meaningful distance intervals.

### Post-Preparation Time

A derived metric was created:

`Post_Preparation_Time_min = Delivery_Time_min - Preparation_Time_min`

This metric represents the observed delivery time after the preparation stage.

It is a derived analytical measure and is not a source `Transit_Time` column.

---

## Key Findings

### Overall Delivery Performance

The average delivery time is:

**56.73 minutes**

The average preparation time is:

**16.98 minutes**

The average post-preparation time is:

**39.75 minutes**

When comparing the average time spent in each stage, post-preparation time represents approximately **70.07%** of the average total delivery duration.

---

### Distance and Post-Preparation Time

Delivery distance shows a strong observed association with post-preparation time.

| Distance Range | Avg. Post-Preparation Time |
| -------------- | -------------------------: |
| 0–5 km         |                  17.47 min |
| 5–10 km        |                  31.51 min |
| 10–15 km       |                  47.07 min |
| 15–20 km       |                  62.10 min |

The average post-preparation time increases substantially as the delivery distance increases.

---

### Traffic and Post-Preparation Time

Traffic conditions also show an observed relationship with post-preparation time.

| Traffic Level | Avg. Post-Preparation Time |
| ------------- | -------------------------: |
| Low           |                  35.66 min |
| Medium        |                  39.58 min |
| High          |                  48.07 min |

Higher traffic levels are associated with longer post-preparation delivery times in this dataset.

---

### Distance × Traffic

The highest observed combination occurs for:

**15–20 km distance + High traffic**

with an average post-preparation time of approximately:

**70.17 minutes**

The lowest observed combination is:

**0–5 km distance + Low traffic**

with an average post-preparation time of approximately:

**13.33 minutes**

---

### Other Factors

Weather and vehicle type were also examined.

Weather showed a wider range of average post-preparation times than vehicle type.

Vehicle type showed relatively smaller differences:

| Vehicle Type | Avg. Post-Preparation Time |
| ------------ | -------------------------: |
| Scooter      |                  38.85 min |
| Bike         |                  39.72 min |
| Car          |                  41.21 min |

These differences are smaller than the observed differences associated with delivery distance and traffic.

---

## Bottleneck Analysis

The analysis identifies the **post-preparation stage** as the main observed bottleneck area in the dataset.

The average post-preparation time is substantially higher than the average preparation time:

* Preparation: **16.98 min**
* Post-preparation: **39.75 min**

Distance shows the largest observed difference in post-preparation time, while traffic also shows a noticeable relationship with delivery delays.

The combination of longer delivery distances and higher traffic conditions is associated with the highest observed post-preparation times.

These findings describe **observed associations in the dataset and do not establish causation**.

---

## Recommendations

Based on the observed patterns, the following operational areas could be investigated:

* Focus on the post-preparation stage because it represents the largest share of average delivery duration.
* Pay particular attention to longer-distance deliveries.
* Consider traffic conditions when planning and monitoring deliveries.
* Investigate operational causes of delays after order preparation.
* Collect additional process-level data to better understand where post-preparation delays occur.
* Monitor post-preparation delivery time over time to evaluate whether operational improvements lead to measurable changes.

These recommendations should be validated with additional operational data before implementation.

---

## Tableau Dashboard

A Tableau dashboard was developed to communicate the main analytical findings.

The dashboard includes:

* Average Delivery Time KPI
* Average Preparation Time KPI
* Average Post-Preparation Time KPI
* Post-Preparation Time by Distance Range
* Post-Preparation Time by Traffic Level
* Distance × Traffic heatmap
* Post-Preparation Time by Weather
* Post-Preparation Time by Vehicle Type

The dashboard is designed to provide a concise view of the main delivery bottleneck and the factors associated with longer post-preparation times.

---

## Tools & Technologies

* **Python**
* **Pandas**
* **Matplotlib**
* **Jupyter Notebook**
* **Tableau**
* **Git**
* **GitHub**

---

## Project Structure

```text
last-mile-delivery-analysis/
│
├── Food_Delivery_Times.csv
├── Food_Delivery_Times_Tableau.csv
├── delivery_bottleneck_analysis.ipynb
└── README.md
```

---

## How to Run

### 1. Clone the repository

```bash
git clone https://github.com/Saraseraji/last-mile-delivery-analysis.git
cd last-mile-delivery-analysis
```

### 2. Open the notebook

Open:

```text
delivery_bottleneck_analysis.ipynb
```

using Jupyter Notebook, JupyterLab, or VS Code.

### 3. Run the analysis

Run the notebook cells from top to bottom.

The notebook performs:

* Data loading
* Data cleaning
* Data validation
* Exploratory analysis
* Feature engineering
* Bottleneck analysis
* Key findings
* Recommendations
* Tableau data preparation

### 4. Open the Tableau-ready dataset

Use:

```text
Food_Delivery_Times_Tableau.csv
```

to build or explore the Tableau dashboard.

---

## Conclusion

This project demonstrates a complete data analysis workflow for investigating last-mile delivery performance.

The analysis shows that the post-preparation stage represents the largest portion of average delivery duration. Delivery distance and traffic conditions show the most noticeable observed relationships with post-preparation delivery time.

The combination of Python analysis and Tableau visualization provides both detailed analytical investigation and an accessible business-oriented view of the results.

All conclusions in this project are based on observed patterns in the available dataset and should not be interpreted as causal findings without additional operational data.
