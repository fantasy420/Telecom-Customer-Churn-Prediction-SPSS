# Telecom Customer Churn Prediction Using IBM SPSS Modeler

## 📌 Project Overview
This repository contains the complete data-mining workflow to predict customer churn in the telecommunications sector using IBM SPSS Modeler. By analyzing historical usage statistics, this project builds a predictive CHAID model to identify customers at high risk of churning, allowing for proactive retention campaigns.

---

## 📂 Repository Structure
* **`telco x modeling data.xlsx`**: The historical training dataset containing customer background info and usage statistics.
* **`telco x deployment data.xlsx`**: The deployment dataset used to evaluate and test the final trained model.
* **`Churn_Prediction_Stream.str`**: The fully configured IBM SPSS Modeler Stream file containing the complete dual-pipeline workflow (Modeling & Deployment).
* **`README.md`**: Detailed project documentation.

---

## 🛠️ Data Mining & Deployment Workflow

### 1. Data Import & Filtering
* **Modeling Pipeline**: Imported `telco x modeling data.xlsx`. Configured Filter nodes to process correct customer predictors.
* **Deployment Pipeline**: Imported `telco x deployment data.xlsx`. Set up operational mapping filters to ensure field properties perfectly match the main model definitions.

### 2. Metadata Configuration & Model Ingestion
* **Target Mapping**: Configured the target role node to predict the `churn` column.
* **Algorithm**: Executed the **CHAID (Chi-squared Automatic Interaction Detection)** node to auto-generate the updated operational model nugget.

### 3. Model Deployment & Scoring Pipeline
* Integrated the updated model nugget into the lower deployment line to automatically score the target records.
* Routed the finalized churn logic directly into an active **Table Node** to generate the comprehensive evaluation matrix.

---

## 📊 Stream Architecture Map (Visual Workflow)
```text
 [Excel Source: Modeling] ➔ [Filter Node] ➔ [Type Node] ➔ [CHAID Model Ingestion Node]
                                                                       ⬇ (Generated Model Nugget)
 [Excel Source: Deployment] ➔ [Operational Filter Node] ➔ ➔ ➔ ➔ ➔ [churn Model Nugget] ➔ [Table Output]
