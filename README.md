# Flight Delay Prediction — Code Execution Instructions

## 🛠 High-Level Code Logic

This project predicts U.S. domestic flight delays using a mix of Spark and scikit-learn. Here’s how the code flows:

---

### 1️⃣ Data Loading & Cleaning (`FlightDelay_EDA.ipynb`)

- **Read data** → Load multiple CSVs using Spark (`spark.read.csv`).  
- **Filter flights** → Keep only completed (non-cancelled, non-diverted) flights.  
- **Create new features** → Convert `FlightDate` to date; extract `DepHour`; cap `ArrDelay` to ±500/–60 min.  
- **Handle nulls** → Drop rows with null `ArrDelay` or `CRSDepTime`.  
- **De-duplicate** → Remove duplicate rows.

---

### 2️⃣ Exploratory Data Analysis (EDA)

- **Descriptive stats** → Use `.describe()` on key variables.  
- **Aggregation** → Group by airline, month, weekday, departure hour to compute average delays.  
- **Identify high-delay routes** → Group by `Origin-Dest` with >50,000 flights.

---

### 3️⃣ Feature Engineering

- **Weather data (optional)** → Join average temperature, precipitation, wind, and pressure for major airports.  
- **One-hot encoding** → Convert categoricals (airline, origin, destination) into numerical features.

---

### 4️⃣ Modeling

- **Split data** → Use train/test split.  
- **Train models** → Fit Random Forest (RF), XGBoost (XGB), Gradient Boosting Trees (GBT) regressors on training data.  
- **Make predictions** → Predict arrival delays on the test set.

---

### 5️⃣ Evaluation

- **RMSE** → Calculate root mean squared error for each model.  
- **Classification accuracy** → Convert delays into binary (delayed/not delayed) and calculate accuracy.  
- **Ensemble** → Average predictions from RF, XGB, and GBT for final RMSE and accuracy.

---
## ▶ How to Run the Code

1. **Install dependencies**
   ```bash
   pip install -r requirements.txt
    ```
2. **Clone Repo**
   
```bash
git clone https://github.com/isha-harish/BigData_Flight_Delay_Presdiction.git
cd BigData_Flight_Delay_Presdiction
```
3. **Run **

Open Main.ipynb in Jupyter or Google Colab.
Run all cells from top to bottom.

### 📈 Key Results
Top Delaying Airline: Southwest (WN) – 10.1 min avg delay

Worst Route: LAX→SFO – 12.4 min avg delay

Peak Delay Periods: Summer afternoons and Friday evenings

Model Performance: Best single RMSE = 39.74 min (GBT); Ensemble RMSE = 39.69 min; Accuracy ≈ 78 %.




      
   
