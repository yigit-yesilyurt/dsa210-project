# Analysis of Socioeconomic Indicators and Traffic Fatalities


## 1. Project Motivation

I am someone who is interested in understanding the underlying reasons and evidence behind rules and assumptions that have become somewhat conventional over time. I often question whether certain practices remain valid under current conditions, even if they are widely accepted without being critically examined.

For this reason, I became interested in exploring the rationale behind regulations such as the prohibition of driving under the influence of alcohol. This naturally led to an investigation of whether alcohol consumption is indeed associated with higher traffic fatality rates.

In addition to that, I aimed to explore how broader socioeconomic factors such as population size and GDP per capita correlate with traffic deaths across different countries.

---

## 2. Project Overview

This project explores the relationship between socioeconomic and health-related factors such as GDP per capita, alcohol consumption, population size, and traffic fatalities. The analysis is conducted at the country level using annual data from 2000 to 2019 to examine how these variables evolve and are related over time.

---

## 3. Data Acquisition & Processing

### 3.1 Data Acquisition

*   **Road Traffic Deaths Dataset:** [Kaggle Dataset](https://www.kaggle.com/datasets/shivkumarganesh/road-traffic-deaths-1990-to-2019)
*   **GDP per Capita:** [World Bank Open Data](https://data.worldbank.org/indicator/NY.GDP.PCAP.CD)
*   **Alcohol Consumption per Capita:** [World Bank Open Data](https://data.worldbank.org/indicator/SH.ALC.PCAP.LI)
*   **Population:** [World Bank Open Data](https://data.worldbank.org/indicator/SP.POP.TOTL)

### 3.2 Data Processing

The datasets were cleaned and merged at the country-year level to create a single merged panel dataset covering the two-decade period (2000 to 2019).

Missing values were handled and variables were aligned to ensure consistency across datasets. The final dataset was used for exploratory data analysis and hypothesis testing.

---

## 4. Methodology & Key Findings

The project followed a complete data science pipeline:
1. **Exploratory Data Analysis (EDA) & Hypothesis Testing:** Initial analysis revealed a heavily right-skewed distribution of global wealth. Surprisingly, the data showed a strong negative correlation between alcohol consumption and traffic death rates. Statistical tests confirmed this confounding relationship, where developed nations with higher alcohol intake also possess significantly safer road infrastructure.
2. **Machine Learning:** To handle non-linear relationships and outliers, a **Random Forest Regressor** was implemented. 
3. **Sensitivity Analysis:** The model was tested by excluding the `Population` feature to prevent mathematical data leakage. Using only `GDP_Per_Capita` and `Alcohol_Per_Capita`, the model successfully explained over 56% of the variance ($R^2$ = 0.5679) in global traffic fatalities. `Alcohol_Per_Capita` consistently emerged as the primary predictive splitter.

*For an in-depth discussion of the methodology, limitations, and findings, please refer to the `final_report.pdf` document in this repository.*

---

## 5. Setup and Reproducibility

### Requirements
* Python 3.10+
* Dependencies listed in `requirements.txt`

### Installation

```bash
# Clone repository
git clone https://github.com/yigit-yesilyurt/dsa210-project
cd dsa210-project

# Install dependencies
pip install -r requirements.txt

# Run notebooks
jupyter notebook
```

### Running the Project

The entire data science pipeline is built using Jupyter Notebooks. To reproduce the results, execute the notebooks:

### Step 1: Data Processing & Merging
The raw datasets from WHO and World Bank are already located in `data/raw/`. This step cleans, handles missing values, and merges them.

```bash
jupyter notebook notebooks/00_data_collection.ipynb
```
*(Running this notebook will generate the processed_dataset.csv inside the data/processed/ directory)*

### Step 2: Exploratory Data Analysis & Hypothesis Testing

```bash
jupyter notebook notebooks/01_exploratory_data_analysis.ipynb
jupyter notebook notebooks/02_hypothesis_testing.ipynb
```

### Step 3: Machine Learning & Sensitivity Analysis

```bash
jupyter notebook notebooks/03_machine_learning.ipynb
```
---

## 6. Repository Structure

```text
dsa210-project/
│
├── data/
│   ├── raw/
│   │   ├── alcohol_consumption.csv
│   │   ├── gdp_per_capita.csv
│   │   ├── population.csv
│   │   └── traffic_deaths.csv
│   │
│   └── processed/
│       └── processed_dataset.csv
│
├── notebooks/
│   ├── 00_data_collection.ipynb
│   ├── 01_exploratory_data_analysis.ipynb
│   ├── 02_hypothesis_testing.ipynb
│   └── 03_machine_learning.ipynb
│
├── charts/
│   ├── eda_chart1.png
│   ├── eda_chart2.png
│   ├── ml_chart1.png
│   └── ml_chart2.png
│
├── requirements.txt
├── proposal.pdf
├── final_report.pdf
└── README.md
