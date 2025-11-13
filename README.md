# Production Efficiency Analysis
A data analysis project focused on understanding machine performance, operator efficiency and overall production behavior in a manufacturing environment.

This project simulates realistic factory data and demonstrates how basic data analysis and machine learning can be used to optimize operations.

---
# Project Overview
The main goal of this project was to analyze production efficiency across machines, operators and shifts.

By using simulated manufacturing data, we explored how downtime, material type and energy affect overall efficiency.

The notebook includes:
- Data exploration and visualization
- Correlation analysis between production metrics
- Simple predictive modeling using **Linear Regression** and **Random Forest**

---
# Data description
The dataset was generated to resemble real world factory environment with 100 production records. Each row represents one production session with the following fields:
- **Date** - Production date
- **MachineID** - Unique identifier for the machine
- **MachineType** - Type of machine (Drill, Lathe, Milling)
- **OperatorID** - ID of the operator in charge
- **MaterialType** - Material used (Steel, Aluminium, Plastic)
- **Shift** - Work shift (Day, Evening, Night)
- **Operator efficiency** - Operator efficiency score (0-1 scale)
- **Downtime(min)** - Duration of machine downtime
- **Errors** - Number of production errors
- **Energy(kWh)** - Energy consumed during operation
- **UnitsProduced** - Number of produced units in that session

---
# Tools and Libraries
- **Python 3.12.12**
- **Pandas** - data processing
- **Matplotlib/Seaborn** - visualization
- **Scikit-Learn** - modeling and evaulation
- **NumPy** - numerical operations

---
## Project Workflow
- **Data Cleaning** - handle missing values, check data types
- **Exploratory Data Analysis** -visualize efficiency per machine, operator and shift
- **Feature Engineering** - encode categorical features
- **Modeling** - compare Linear Regression and Random Forest models
- **Evaluation** - calculate R² and MAE scores
- **Key insights** - summarize patterns and observations

# Key Visulizations and Insights

### 1. Operator Efficiency by Machine Type
- **Drill machines** had the highest operator efficiency
- **Milling machines** showed slightly lower averages

### 2. Efficiency by Shift
- The **Day shift** had the highest operator efficiency
- The **Evening shift** showed slightly lower averages

### 3. Operator Comparison
- **Operator 4(Op4)** performed best on average
- **Operator 1(Op1)** had the lowest overall efficiency

## 4. Errors by Material Type
- **Steel** showed the highest number of errors
- **Aluminium** had the least errors

## 5. Downtime Distribution
- Most downtime events lasted around **30 minutes** with fewer longer stops.

## 6. Energy Usage per Shift
- **Day and evening shifts** had similar energy usage
- **Night shift** consumed the least energy

## 7. Units Produced by Material
- **Aluminium** resulted in the most produced units
- **Steel** showed the lowest number of produced units

## 8. Correlation heatmap

- Downtime/Efficiency - **-0.90**
- Errors/Efficiency - **-0.32**
- UnitsPoduced/Efficiency - **0.82**
- Energy/Errors - **-0.17**

These correlations clearly show that:
- More downtime and more errors decrease efficiency
- Higher unit production is strongly linked with better operator efficiency

---
## Predictive Modeling

To explore predictive insights, two models were trained using:
- **Features:** Downtime(min), Errors
- **Target:** Operator Efficiency

### Linear Regression
 - **R²:** 0.984
 - **MAE:** 0.006
 The linear model fits the data very well, showing a strong linear relationship between downtime/errors and efficiency.
 Both coefficients were slightly negative, meaning that as downtime or errors increase, efficiency decreases.

 ### Random Forest Regressor
 - **R²: ** 0.991
 - **MAE: ** 0.004
 The Random Forest model provided even higher accuracy and lower error, showing that it can capture more complex, nonlinear relationships between production variables.

 **Conclusion:**
 Random Forest performed better, confirming that production efficiency depends on multiple nonlinear relationships between operator, machine and downtime.

 ## Example Code Snippet
 ```python
from sklearn.ensemble import RandomForestRegressor
from sklearn.metrics import r2_score, mean_absolute_error

rf_model = RandomForestRegressor(random_state=33)
rf_model.fit(X_train, y_train)
y_pred_rf = rf_model.predict(X_test)

print("R²:", r2_score(y_test, y_pred_rf))
print("MAE:", mean_absolute_error(y_test, y_pred_rf))
```

