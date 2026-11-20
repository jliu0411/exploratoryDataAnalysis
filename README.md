# Exploratory Data Analysis and Agentic AI

**CMPE 255 — Data Preparation and Analysis | Fall 2026**

This project explores data preparation, exploratory data analysis (EDA), machine learning, and AI-powered data analysis using Google Colab.

The assignment consists of two parts:

- **Part 1:** Perform EDA, visualization, data cleaning, clustering, anomaly detection, feature engineering, and AutoML modeling on tabular and time-series datasets.
- **Part 2:** Use a Gemini-powered AI agent to automatically perform exploratory data analysis through natural-language queries and function calling.

## Project Structure

```text
exploratoryDataAnalysis/
├── Airbnb_EDA.ipynb
├── Bike_Sharing_Demand_EDA.ipynb
├── Part2_Agentic_EDA_Bike_Sharing (1).ipynb
└── README.md
```

## Part 1 — Data Preparation and AutoML

### 1A. NYC Airbnb — Tabular Data Analysis

**Dataset:** [NYC Airbnb Open Data (Kaggle)](https://www.kaggle.com/datasets/dgomonov/new-york-city-airbnb-open-data)

**Notebook:** `Airbnb_EDA.ipynb`

**Objective:** Analyze Airbnb listings in New York City and build machine learning models to predict listing prices.

Implementation includes:

- Exploratory data analysis and visualization
- Missing-value analysis and data cleaning
- Feature engineering and preprocessing
- KMeans clustering
- Isolation Forest anomaly detection
- Feature selection
- Regression modeling using AutoViML

**AutoViML Results**

| Model | MAE | RMSE |
|---|---:|---:|
| Linear | 49.73 | 88.07 |
| Linear-run Ensemble | 47.13 | 80.24 |
| Forests | 49.31 | 80.45 |

The linear-run ensemble achieved the lowest validation RMSE of **80.24**, improving approximately 8.9% over the standalone linear model.

### 1B. Bike Sharing Demand — Time-Series Analysis

**Dataset:** [Bike Sharing Demand (Kaggle)](https://www.kaggle.com/competitions/bike-sharing-demand/data)

**Notebook:** `Bike_Sharing_Demand_EDA.ipynb`

**Objective:** Analyze historical hourly bicycle rental demand in Washington, D.C., and develop models to predict rental counts.

Implementation includes:

- Time-series EDA and visualization
- Hourly, daily, and seasonal demand analysis
- Data cleaning and missing-value checks
- Clustering and anomaly detection
- Calendar and cyclical feature engineering
- Feature selection
- Regression modeling using AutoViML

**AutoViML Results**

| Model | MAE | RMSE |
|---|---:|---:|
| Linear | 90.49 | 139.41 |
| Linear-run Ensemble | 70.35 | 102.81 |
| Forests | 53.26 | 77.57 |

The Forests model achieved the lowest validation RMSE of **77.57**, approximately 44.4% lower than the standalone Linear model.

**Note:** The AutoViML results for both datasets are based on internal validation. A separate chronological holdout evaluation would provide a stronger assessment of future bike-sharing forecasting performance.

## Part 2 — Agentic Exploratory Data Analysis

**Notebook:** `Part2_Agentic_EDA_Bike_Sharing (1).ipynb`

**Dataset:** Bike Sharing Demand

**Technology:** Google Gemini API, Python, Pandas, Matplotlib, and Seaborn.

**Objective:** Demonstrate how an AI agent can automatically investigate a dataset, execute analysis functions, and generate data-grounded findings in response to natural-language instructions.

### Agent Workflow

1. The user submits a natural-language EDA question.
2. Gemini determines which analysis tools to use.
3. The agent calls Python functions to inspect the dataset and calculate statistics.
4. Results are returned to the agent.
5. Gemini generates a written interpretation of the findings.
6. Findings can be checked against independent Pandas calculations.

The agent supports tasks such as dataset inspection, missing-value analysis, correlation analysis, demand grouping, temperature analysis, and identification of extreme rental counts.

### Agentic EDA Findings

The agent analyzed 10,886 hourly bicycle rental observations covering 2011–2012.

Key findings reported by the agent:

- Highest average demand: **5 PM — 468.77 rentals**
- Second-highest average demand: **6 PM — 430.86 rentals**
- Lowest average demand: **4 AM — 6.41 rentals**
- Mean hourly demand: **191.57 rentals**
- Temperature correlation with demand: **0.394**
- No missing values or duplicate timestamps reported

The agent also identified seasonal demand changes, weather relationships, unusual rental peaks, and gaps in calendar coverage caused by the Kaggle dataset partitioning.

The main agent analysis recorded **nine function calls across five distinct analysis tools**, demonstrating tool-based data analysis rather than text generation alone.

### Limitations

- Agent-generated conclusions require independent verification.
- The dataset contains network-wide rental counts, not station-level demand.
- The original Kaggle training data omits the final days of each month.
- Correlation does not establish causation.
- The `casual` and `registered` columns are excluded from predictive features because they sum to the target `count`.

## How to Run

All three notebooks can be executed using [Google Colab](https://colab.research.google.com/). VS Code is not required.

1. Download or open the desired `.ipynb` notebook in Google Colab.
2. Run the setup and installation cells.
3. Load the dataset using the notebook's download instructions.
4. Execute the remaining cells in order.
5. Review the generated visualizations, model metrics, or agent responses.

**Part 1:** AutoViML requires compatible Python and package versions. The notebooks were developed using a Python 3.12-compatible environment for AutoViML.

**Part 2:** A Gemini API key is required. Obtain one from [Google AI Studio](https://aistudio.google.com/apikey), then add it to Google Colab's Secrets panel under `GEMINI_API_KEY` and enable notebook access.

Never commit API keys to GitHub.

## YouTube Walkthroughs

The assignment requires detailed walkthroughs explaining the code snippets, implementation, findings, and user journeys.

### Part 1 — EDA, Data Preparation, and AutoML

**YouTube:** 
Part 1A: https://youtu.be/UWhqr9QkEEc  
Part 1B: https://youtu.be/vdZiXQKVa2w  

The video will cover:

- Loading the Airbnb and Bike Sharing datasets
- EDA and visualizations
- Missing-value handling and cleaning
- Clustering and anomaly detection
- Feature engineering and selection
- AutoViML model training and comparisons
- Results, conclusions, and limitations

**User Journey:** A data analyst loads raw tabular or time-series data, investigates its quality and patterns, prepares it for modeling, trains predictive models, and evaluates the results.

### Part 2 — Gemini Agentic EDA

**YouTube:** https://youtu.be/1D2CIUWHx8s

The video will cover:

- Gemini API and Colab setup
- Agent architecture and available analysis tools
- Natural-language EDA questions
- Automatic function calling
- Agent-generated findings and visualizations
- Validation of numerical results
- Limitations and possible business applications

**User Journey:** A user asks an analysis question in natural language. The Gemini agent selects appropriate tools, analyzes the dataset, and returns quantitative findings and explanations without requiring the user to manually write each analysis operation.

## Tools and Technologies

- Python
- Google Colab
- Pandas and NumPy
- Matplotlib and Seaborn
- Scikit-learn
- AutoViML
- Google Gemini API
- Kaggle
- GitHub

## Conclusion

Part 1 demonstrated the importance of exploratory analysis, data cleaning, feature engineering, clustering, anomaly detection, and automated machine learning. Multiple AutoViML configurations were evaluated for Airbnb price prediction and hourly bicycle rental demand.

Part 2 extended traditional EDA by using a Gemini-powered agent to select analysis tools and answer natural-language questions with quantitative findings.

Together, the two parts demonstrate the differences between manual data preparation workflows and AI-assisted exploratory analysis, while emphasizing the importance of validating model performance and AI-generated conclusions.
