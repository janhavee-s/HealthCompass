# 🏥 HealthCompass: Risk-Aware Healthcare Navigator

## Overview

HealthCompass is an intelligent healthcare recommendation system designed to help patients identify the most suitable healthcare facility based on their symptoms, age, location, and insurance status. Unlike diagnostic systems, HealthCompass focuses on healthcare accessibility, urgency assessment, affordability, and safe navigation to appropriate medical facilities.

The system combines machine learning-based risk assessment, location intelligence, healthcare facility filtering, cost estimation, and multi-factor ranking to deliver personalized and explainable healthcare recommendations.

---

## Objectives

* Assess patient urgency using age and reported symptoms.
* Recommend appropriate healthcare facilities based on risk level.
* Provide location-aware hospital recommendations.
* Estimate treatment costs using symptom severity.
* Incorporate insurance information as an affordability signal.
* Rank healthcare facilities using multiple decision factors.
* Ensure safe fallback recommendations in sparse data scenarios.
* Improve healthcare accessibility through intelligent decision support.

---

## Dataset

The system utilizes multiple healthcare datasets, including:

* Hospital Information
* Hospital Location Data
* Insurance Coverage Data
* Symptom Severity Mapping
* Treatment Cost Information
* Healthcare Facility Metadata

---

## Technologies Used

* **Python**
* **Streamlit**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Geopy**
* **Machine Learning**
* **Rule-Based Decision Systems**

---

## Project Architecture

```text
User Input
     ↓
Risk Assessment Model
     ↓
Hospital Filtering Engine
     ↓
Distance Calculation
     ↓
Cost Estimation
     ↓
Insurance Evaluation
     ↓
Risk-Aware Ranking
     ↓
Top Hospital Recommendations
```

---

## Project Workflow

### 1. User Input Collection

The Streamlit interface collects:

* Patient Age
* Multiple Symptoms
* Geographic Location
* Insurance Availability

The system converts user-provided locations into geographic coordinates for distance calculations.

---

### 2. Risk Assessment

A machine learning model evaluates:

* Age-related risk
* Symptom severity
* Combined symptom impact

The model categorizes patients into:

* Low Risk
* Medium Risk
* High Risk

---

### 3. Hospital Filtering

Healthcare facilities are filtered according to urgency level.

| Risk Level | Recommended Facilities           |
| ---------- | -------------------------------- |
| High       | Hospitals, Medical Colleges      |
| Medium     | Hospitals, Medical Colleges      |
| Low        | Clinics, Dispensaries, Hospitals |

This ensures recommendations remain medically appropriate.

---

### 4. Distance Calculation

Location intelligence is used to:

* Calculate distance between patients and hospitals.
* Prioritize nearby facilities.
* Improve emergency accessibility.

Distance is measured using latitude and longitude coordinates.

---

### 5. Treatment Cost Estimation

Estimated treatment costs are generated using:

* Symptom severity
* Multiple symptom combinations
* Healthcare facility type
* Government vs Private ownership

Examples:

* Fever → Lower outpatient cost
* Chest Pain + Breathing Difficulty → Higher emergency treatment cost

---

### 6. Insurance-Aware Evaluation

Insurance availability acts as a soft recommendation factor.

The system:

* Improves affordability scoring.
* Slightly boosts eligible hospitals.

The system does not:

* Verify insurance claims.
* Guarantee coverage.
* Exclude hospitals based on insurance.

---

### 7. Hospital Ranking Engine

Hospitals are ranked using multiple criteria:

* Distance
* Estimated Treatment Cost
* Insurance Availability
* Medical Urgency Level

Risk-aware weighting ensures that the most important factors change depending on patient urgency.

---

## Key Features

* Machine Learning-Based Risk Assessment
* Multi-Symptom Evaluation
* Location-Aware Hospital Recommendations
* Cost Estimation Engine
* Insurance-Aware Ranking
* Explainable Decision Support
* Healthcare Accessibility Optimization
* Safe Fallback Recommendation Strategy

---

## Repository Structure

```text
HealthCompass/
│
├── data/
│   ├── clean_pune_hospitals.csv
│   ├── costs.csv
│   ├── hospitals_with_insurance.csv
│   ├── Hospitals.csv
│   ├── insurance.csv
│   └── symptoms.csv
│
├── logic/
│   ├── cost_logic.py
│   ├── hospital_filter.py
│   ├── insurance_logic.py
│   ├── scoring.py
│   └── symptom_map.py
│
├── ml/
│   └── risk_model.py
│
├── project/
│   └── orchestrator.py
│
├── utils/
│   └── geo.py
│
├── app.py
├── README.md
└── .gitignore
```

---

## Installation & Setup

### Prerequisites

Make sure you have the following installed:

* Python 3.9+
* pip
* Virtual Environment (recommended)

### Clone the Repository

```bash
git clone https://github.com/janhavee-s/HealthCompass.git
cd HealthCompass
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Run the Application

From the root directory of the project, start the Streamlit application:

```bash
streamlit run app.py
```

### Access the Application

After launching, open your browser and navigate to:

```text
http://localhost:8501
```

The HealthCompass dashboard will be available for healthcare facility recommendations and risk assessment.

---

## Key Insights

* Healthcare accessibility depends on both urgency and proximity.
* Multi-symptom analysis provides more reliable risk assessment than single-symptom evaluation.
* Cost-aware recommendations improve healthcare affordability.
* Insurance can influence accessibility without restricting options.
* Risk-aware ranking produces safer and more practical healthcare recommendations.

---

## Future Enhancements

* Real-Time Hospital Bed Availability
* Doctor & Specialist Recommendation System
* Appointment Scheduling Integration
* Emergency Route Optimization
* Predictive Healthcare Demand Forecasting
* Explainable AI Dashboard
* Multi-City Healthcare Coverage

---

## Skills Demonstrated

* Machine Learning
* Healthcare Analytics
* Decision Support Systems
* Geospatial Analysis
* Data Processing & Feature Engineering
* Recommendation Systems
* Streamlit Application Development
* Explainable AI
* Risk Assessment Modeling

---

## Author

**Janhavee Singh**

B.Tech Computer Science | Artificial Intelligence | Machine Learning | Data Analytics

HealthCompass demonstrates the integration of machine learning, healthcare analytics, location intelligence, and decision-support systems to improve patient navigation and healthcare accessibility through intelligent hospital recommendations.