
# StockSense — Smart Inventory Planning and Demand Forecasting

StockSense is a machine learning-powered inventory planning system designed for NeuralShop. It forecasts product demand using historical sales data and generates data-driven inventory recommendations to help reduce stockouts and unnecessary inventory holding costs.

## Why StockSense?

Currently, NeuralShop relies on hard-coded logic for certain inventory-related decisions. Such logic cannot dynamically adapt to changing demand patterns, seasonal trends, or promotional effects.

StockSense explores how machine learning can make inventory planning more intelligent by forecasting future demand and recommending when and how much stock should be replenished.

**The objective is to gradually move from static inventory rules toward data-driven inventory decisions.**

> StockSense currently serves as a standalone forecasting prototype. Integration with NeuralShop's backend is a planned enhancement, not an existing feature.

## Key Features

- Historical retail sales analysis
- Data preprocessing and exploratory data analysis
- Feature engineering for demand forecasting
- Sales prediction using Random Forest Regressor
- Safety stock calculation
- Reorder point calculation
- Recommended order quantity generation
- Interactive Streamlit dashboard
- KPI cards and business insights
- Actual vs. predicted sales visualization
- Exportable forecast and inventory recommendation results

## Technology Stack

- **Language:** Python
- **Data Processing:** Pandas, NumPy
- **Machine Learning:** Scikit-learn
- **Model Persistence:** Joblib
- **Visualization:** Matplotlib
- **Dashboard:** Streamlit

## Machine Learning Approach

StockSense uses a Random Forest Regressor to predict sales demand from historical retail data.

### Input Features

- Price
- Promotion indicator
- Weekday, day, month, and year
- Previous-day sales
- Sales from seven days earlier
- Seven-day average sales

**Target:** Predicted sales quantity.

The model is trained using historical data and can be evaluated by comparing actual sales against predicted sales. Forecast accuracy depends on data quality, feature engineering, and validation methodology.

## Inventory Optimization

StockSense converts demand forecasts into practical inventory recommendations.

### 1. Safety Stock

Additional inventory maintained to help absorb unexpected demand or supply delays.

### 2. Reorder Point

The inventory level at which replenishment should be initiated.

**Formula:**

Reorder Point = Average Daily Demand × Lead Time + Safety Stock

### 3. Recommended Order Quantity

Estimates the additional stock required to reach the desired inventory level.

**Formula:**

Recommended Order = max(0, Target Stock Level − Current Stock)

The target stock level should account for forecast demand over the relevant replenishment period and any required safety stock.

> Inventory calculations depend on the units and time horizon of the forecast, supplier lead time, and available stock data. These assumptions must be configured consistently.

## Project Structure

```text
StockSense/
├── app/
│   └── streamlit_app.py
├── data/
│   └── raw/
│       └── retail_sales_sample.csv
├── models/
│   └── retail_forecast_model.pkl
├── outputs/
│   ├── forecast_results.csv
│   └── inventory_recommendations.csv
├── images/
│   ├── dashboard.png
│   ├── kpi_cards.png
│   ├── actual_vs_predicted.png
│   ├── inventory_recommendation.png
│   └── final_dashboard.png
├── src/
│   ├── data_preprocessing.py
│   ├── feature_engineering.py
│   ├── inventory_logic.py
│   ├── train_model.py
│   └── visualize.py
├── main.py
├── requirements.txt
├── .gitignore
└── README.md
```

*Adjust this structure to match the files actually present in the repository.*

## Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/kushagraawasthi37/StockSense.git
cd StockSense
```

### 2. Create a Virtual Environment

**Windows**

```bash
python -m venv venv
venv\Scripts\activate
```

**macOS/Linux**

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run the Dashboard

```bash
streamlit run app/streamlit_app.py
```

Open the local URL displayed in the terminal to access the dashboard.

## Dashboard Metrics

The dashboard is designed to display:

- Forecast sales
- Current stock
- Reorder point
- Recommended order quantity
- Actual vs. predicted sales

Example values should be treated as illustrative unless generated from a real model run.

## Planned NeuralShop Integration

StockSense can be integrated into NeuralShop as a separate Python-based forecasting service while keeping the existing Node.js backend responsible for core e-commerce operations.

A possible integration workflow:

1. Collect historical sales and product inventory data from NeuralShop.
2. Prepare and validate the data for forecasting.
3. Generate demand predictions using the trained ML model.
4. Calculate reorder points and recommended order quantities.
5. Expose forecasts through a Python API.
6. Allow NeuralShop's backend to consume the recommendations.
7. Display inventory insights in the admin dashboard.
8. Introduce low-stock alerts and purchase order suggestions.

The integration should be implemented and tested before these capabilities are described as live features.

## Future Enhancements

- Product-level and multi-store forecasting
- Festival, holiday, and seasonal demand analysis
- Promotion and price impact modelling
- Model evaluation and comparison with XGBoost, ARIMA, and Prophet
- Inventory anomaly detection
- Supplier lead-time optimization
- Low-stock alerts and automated replenishment workflows
- PostgreSQL integration for inventory and sales data
- Cloud deployment
- Explainable forecasts and feature importance
- Conversational inventory insights

## Business Value

StockSense explores how machine learning can help retail and e-commerce businesses:

- Anticipate future product demand
- Reduce stockout risk
- Minimize excess inventory
- Improve replenishment planning
- Make more informed purchasing decisions

## Author

**Kushagra**

Developed as part of the NeuralShop ecosystem to explore machine learning applications in retail demand forecasting and inventory optimization.
