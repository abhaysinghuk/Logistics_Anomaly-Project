# Logistics_Anomaly-Project
Logistics Anomaly Detection and Risk Analytics

An end-to-end analytics project that applies machine learning, SQL, and Power BI to investigate shipment irregularities, operational delays, SLA breaches, and additional logistics costs.

1. Project Overview

Logistics operations involve multiple carriers, shipping routes, delivery schedules, and cost factors. Delays and operational disruptions can affect service-level agreements (SLAs), increase expenses, and reduce supply chain efficiency.

This project analyzes 32,065 international shipment records across 8 carriers and 10 shipping routes to identify unusual shipment behavior, investigate potential operational risk factors, and communicate findings through interactive Power BI dashboards.

An unsupervised Isolation Forest model is used to flag unusual observations. The resulting risk indicators are combined with SQL analysis, statistical investigation, and dashboard reporting to support data-driven operational decisions.

2. Business Objectives

The project aims to:

Detect shipments with unusual delays, costs, or operational characteristics.
Monitor carrier and route performance against available SLA criteria.
Identify patterns associated with additional logistics expenses.
Investigate geographic and seasonal differences in shipment anomalies.
Rank potentially problematic shipments and accounts for further review.
Present operational KPIs and analytical findings through interactive dashboards.
3. Project Highlights
Processed 32,065 shipment records across 8 carriers and 10 routes.
Developed 110+ engineered features for shipment-level analysis.
Applied Isolation Forest with a configured contamination rate of 10%.
Flagged 3,207 shipments as anomalous.
Analyzed 3,147 SLA breaches, representing approximately 9.8% of the dataset.
Identified approximately $34.27 million in additional costs according to the project's cost calculations.
Created a Power BI dashboard with 5 analytical views covering overall performance, carriers, routes, anomalies, and temporal patterns.

Note on model evaluation: The anomaly count and configured contamination rate describe the model's output. Precision and recall must be calculated against clearly defined reference labels and evaluation procedures. The reported precision of 92.5% should be verified against the underlying evaluation code before being presented as validated model performance.

4. Technology Stack
Technology	Purpose
Python	Data processing, feature engineering, and anomaly detection
Pandas	Data cleaning, transformation, and aggregation
NumPy	Numerical calculations
Scikit-learn	Isolation Forest and feature scaling
Matplotlib and Seaborn	Exploratory charts and diagnostic visualizations
SQLite	Structured data storage and querying
SQL	Operational analysis, aggregation, and performance ranking
Power BI Desktop	Interactive dashboards and reporting
DAX	KPI calculations and analytical measures
Joblib	Saving and loading trained models and preprocessing objects
5. Project Workflow
Step 1: Data Exploration and Preparation

The initial analysis examines shipment records, available features, data types, and data quality.

Key activities include:

Inspecting shipment records and identifying potential data inconsistencies.
Reviewing delay, cost, carrier, route, and SLA-related fields.
Preparing the base dataset for downstream processing.
Storing intermediate and final datasets for reproducible analysis.
Step 2: Feature Engineering

Created additional features to describe shipment behavior and operational performance.

Feature groups include:

Temporal attributes such as month, quarter, and day of the week.
Carrier-level and route-level performance summaries.
Cost and efficiency ratios.
Differences between individual shipments and historical averages.
Interaction features that capture relationships between operational variables.

The engineered dataset contains 110+ features, according to the supplied project documentation.

Step 3: Machine Learning-Based Anomaly Detection

Implemented the Isolation Forest algorithm from scikit-learn to identify observations that differ from typical shipment patterns.

The configured model uses:

Algorithm: Isolation Forest
Number of estimators: 100
Contamination parameter: 0.10
Random state: 42
Preprocessing: StandardScaler, as configured in the pipeline

The model flags observations based on their relative isolation in feature space. These flags can help prioritize operational investigation, but an anomalous shipment is not necessarily a failed delivery or a confirmed SLA violation.

Step 4: SLA and Operational Risk Analysis

Compared shipment behavior with the available SLA definitions and analyzed operational indicators associated with delays and additional costs.

The analysis examines:

SLA breach frequency and duration.
Carrier-level anomaly rates.
Route-level performance differences.
Shipment delays and associated expenses.
Operational patterns that may warrant further investigation.

SLA breach metrics and machine learning anomaly flags are treated as separate measures because they represent different concepts.

Step 5: SQL-Based Analysis

Used SQLite and SQL queries to summarize operational performance and prepare reporting datasets.

The SQL workflow supports:

Ranking carriers by anomaly rate and associated costs.
Comparing shipping routes by performance and financial impact.
Aggregating shipment records by month and risk category.
Extracting expensive anomalies and lengthy delays for review.
Preparing summarized datasets for Power BI.
Step 6: Root Cause Investigation

Investigated relationships between operational conditions, shipment delays, and additional costs.

The supplied analysis identifies delay duration, SLA breach duration, route complexity, and customs-related delays as areas of interest.

These findings represent observed relationships in the dataset. Establishing causal root causes would require additional validation and appropriate investigation.

Step 7: Power BI Reporting

Created an interactive dashboard to help users explore performance differences and prioritize shipments for review.

The dashboard contains five analytical views:

Executive Summary: Shipment volume, flagged anomalies, additional costs, and monthly trends.
Carrier Performance: Carrier comparisons, anomaly rates, and cost summaries.
Route Analysis: Geographic patterns, route-level metrics, and cost comparisons.
Anomaly Investigation: High-cost flagged shipments, risk categories, and detailed records.
Temporal Analysis: Monthly, quarterly, and day-of-week patterns.
6. Key Findings
Shipment Anomalies

The model flagged 3,207 of 32,065 shipments, corresponding to approximately 10.0% of the dataset.

These records can be used to identify unusual shipment patterns and prioritize further review. They should not automatically be classified as fraudulent or operationally unsuccessful.

SLA Performance

The analysis identified 3,147 SLA breaches, approximately 9.8% of the shipment records.

Monitoring these breaches alongside anomaly scores can help distinguish contractual service failures from other unusual operational behavior.

Carrier Performance

The supplied results indicate that CMA CGM had an anomaly rate of 12.2%, while UPS had an anomaly rate of 7.5%.

These differences provide a starting point for investigating carrier-level performance, shipment mix, and operational conditions. They do not, by themselves, establish the cause of the differences.

Route-Level Risk

The Mumbai–Dubai route showed an anomaly rate of 16.1%, with approximately $3.82 million in associated costs in the supplied analysis.

This route may warrant closer review of delays, route-specific operating conditions, and cost drivers.

Seasonal Patterns

December 2024 had the highest reported monthly anomaly rate at 15.4%, while July 2025 had the lowest at 8.2%.

These patterns may help identify periods for additional monitoring, subject to validation of monthly shipment volumes and seasonal effects.

Additional Cost Analysis

The project reports approximately $34.27 million in additional costs. The analysis also attributes substantial portions of the reported total to customs, congestion, weather, and other disruptions.

These values depend on the project's cost calculation rules and should be interpreted as estimated costs within the analyzed dataset rather than independently verified financial losses.

7. Operational Recommendations

Based on the reported findings, the following actions could support further investigation:

Review shipments flagged by multiple independent indicators.
Investigate carrier and route performance using volume-adjusted comparisons.
Examine customs-related delays and their contribution to calculated additional costs.
Monitor monthly changes in SLA breaches and anomaly rates.
Establish alert thresholds based on validated operational requirements.
Review false positives before using anomaly flags to trigger operational decisions.
Track performance over time to determine whether corrective actions improve delivery outcomes.
8. Dataset Summary
Metric	Reported Value
Total shipments	32,065
Analysis period	September 2024 – September 2025
Carriers	8
Shipping routes	10
Original features	54
Engineered features	110+
Flagged anomalies	3,207
SLA breaches	3,147
Reported additional costs	$34,271,734.98
Configured contamination rate	10%
Model estimators	100
9. Repository Structure
text
logistics-anomaly-detection/
│
├── data/
│   ├── logistics_base.csv
│   ├── logistics_sla_rules.csv
│   ├── logistics_augmented.csv
│   ├── logistics_features_engineered.csv
│   ├── logistics_with_anomalies.csv
│   └── logistics_analytics.db
│
├── scripts/
│   ├── 01_explore_data.py
│   ├── 02_setup_database.py
│   ├── 03_feature_engineering.py
│   ├── 04_anomaly_detection.py
│   ├── 05_root_cause_analysis.py
│   └── 06_powerbi_preparation.py
│
├── models/
│   ├── isolation_forest_model.pkl
│   └── feature_scaler.pkl
│
├── sql/
│   ├── dashboard_query.sql
│   ├── carrier_performance.sql
│   └── route_analysis.sql
│
├── powerbi/
│   ├── logistics_dashboard_data.csv
│   ├── carrier_performance_summary.csv
│   ├── route_performance_summary.csv
│   ├── monthly_trends.csv
│   ├── risk_analysis.csv
│   ├── top_10_expensive_anomalies.csv
│   ├── top_10_longest_delays.csv
│   ├── dashboard_metrics.csv
│   ├── temporal.pbix
│   └── POWER_BI_SETUP_GUIDE.txt
│
├── outputs/
│   ├── reports/
│   └── visualizations/
│
└── README.md

10. Installation and Execution
Prerequisites
Python 3.10 or later
Power BI Desktop for viewing the dashboard

Install Dependencies
bash
pip install pandas numpy scikit-learn matplotlib seaborn joblib scipy

Run the Analysis Pipeline

Execute the scripts in the following order:

bash
python scripts/01_explore_data.py
python scripts/02_setup_database.py
python scripts/03_feature_engineering.py
python scripts/04_anomaly_detection.py
python scripts/05_root_cause_analysis.py
python scripts/06_powerbi_preparation.py


The commands assume the repository uses the directory structure shown above and that each script supports standalone execution. Verify the actual file paths and dependencies before running the pipeline.

Open the Dashboard

Open powerbi/temporal.pbix in Power BI Desktop. If data connections require configuration, follow the included setup guide.

11. Limitations
Anomaly detection identifies unusual observations, not confirmed operational failures.
Isolation Forest's contamination parameter influences the expected proportion of flagged observations.
Model precision and recall require an explicitly defined evaluation target and reliable reference labels.
Additional costs depend on the project's calculation assumptions and are not independently verified financial losses.
Correlations between shipment characteristics and costs do not establish causation.
Carrier and route comparisons may be affected by shipment volume, route complexity, and differences in operational conditions.
Historical patterns may not generalize to future periods without additional validation.
12. Future Improvements

Potential extensions include:

Evaluating alternative anomaly detection algorithms.
Establishing a labeled evaluation dataset for model validation.
Adding time-series forecasting for shipment delays.
Developing automated alerts for high-priority operational anomalies.
Integrating external weather or congestion data where available.
Building an API or lightweight application for reviewing flagged shipments.
Tracking model drift and operational performance over time.
13. Skills Demonstrated

Data Analytics: Data Cleaning, Exploratory Data Analysis, Feature Engineering, Statistical Analysis, Root Cause Investigation.

Risk Analytics: Anomaly Detection, Operational Risk Identification, SLA Monitoring, Exception Analysis, Risk Prioritization.

Technical Skills: Python, Pandas, NumPy, Scikit-learn, SQL, SQLite, Power BI, DAX, Excel-compatible reporting workflows.

Business Intelligence: KPI Reporting, Carrier Performance Analysis, Route Analytics, Cost Analysis, Dashboard Development, Data-Driven Recommendations.

14. Conclusion

This project demonstrates how shipment data can be transformed into operational risk indicators through data engineering, unsupervised machine learning, SQL analysis, and interactive reporting.

By combining anomaly screening with SLA monitoring, cost analysis, and carrier and route comparisons, the project provides a foundation for investigating unusual logistics activity and supporting evidence-based operational decisions.

License and Attribution

Retain the original repository's license and attribution requirements. If this repository is based on another person's project, acknowledge the original author and comply with the applicable license. Update the author and project details to reflect your actual contributions.
