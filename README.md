## Flight Delay Prediction — Code Execution Instructions

### High-Level Code Logic

Our project predicts U.S. domestic flight delays using a Spark, scikit-learn, and XGBoost. Below is an overview of the code logic:

#### 1. Data Loading & Cleaning (FlightDelay_EDA.ipynb)

- **Read data**:  Loaded multiple CSVs using Spark (spark.read.csv).  
- **Filtered flights**:  Kept only completed (non-cancelled, non-diverted) flights.  
- **Created new features**: Converted FlightDate to date; extract DepHour; cap ArrDelay to ±500/–60 min.  
- **Handled nulls**: Dropped rows with null ArrDelay or CRSDepTime.  
- **De-duplicated rows**: Removed duplicate rows.

#### 2. Exploratory Data Analysis (EDA)

- **Descriptive statistics**: Used .describe() on key variables.  
- **Aggregation**: Grouped by airline, month, weekday, departure hour to compute average delays.  
- **Identified high-delay routes**: Grouped by Origin-Dest with >50,000 flights.

#### 3. Feature Engineering

- **Weather data**: Joined average temperature, precipitation, wind, and pressure for major airports.  
- **One-hot encoding**: Converted categoricals (airline, origin, destination) into numerical features.

#### 4. Modeling

- **Split data**: Used train/test split.  
- **Trained models**: Fit Random Forest (RF), XGBoost (XGB), Gradient Boosting Trees (GBT) regressors on training data.  
- **Made predictions**: Predicted arrival delays on the test set.

#### 5. Evaluation

- **RMSE**: Calculated root mean squared error for each model.  
- **Classification accuracy**: Converted delays into binary (delayed/not delayed) and calculate accuracy.  
- **Ensemble**: Average predictions from RF, XGB, and GBT for final RMSE and accuracy.

### ▶ How to Run the Code

1. **Install dependencies**
   ```bash
   pip install -r requirements.txt
    ```
2. **Clone Repository**
   
```bash
git clone https://github.com/isha-harish/BigData_Flight_Delay_Presdiction.git
cd BigData_Flight_Delay_Presdiction
```
3. Open Main.ipynb in Jupyter or Google Colab on run all cells from top to bottom.

### Key Results
- Top Delaying Airline: Southwest (WN) – 10.1 min avg delay

- Worst Route: LAX→SFO – 12.4 min avg delay

- Peak Delay Periods: Summer afternoons and Friday evenings

- Model Performance: Best single RMSE = 39.74 min (GBT); Ensemble RMSE = 39.69 min; Accuracy ≈ 78 %.




      
   
