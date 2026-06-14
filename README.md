🏥 HealthCompass - Healthcare Navigator
A Risk-Aware Hospital Recommendation System

📌 Project Overview
HealthCompass is a decision-support system that helps users find the safest and most suitable healthcare facility based on:
Age
One or multiple symptoms
Location (human-readable area → mapped to coordinates)
Insurance availability
The system is not diagnostic.
It focuses on navigation, urgency awareness, and affordability, ensuring that every input always produces an output, even in sparse data scenarios.


🎯 Key Objectives
Assess medical urgency (risk level) using age and symptoms
Recommend appropriate healthcare facilities (clinic / hospital / govt hospital)
Estimate realistic treatment cost
Use insurance as a soft affordability signal
Guarantee safe fallback recommendations (never return empty results)


HACKX/
│
├── data/                          # Dataset files
│   ├── clean_pune_hospitals.csv
│   ├── costs.csv
│   ├── hospitals_with_insurance.csv
│   ├── Hospitals.csv
│   ├── insurance.csv
│   └── symptoms.csv
│
├── logic/                         # Core business logic layer
│   ├── __init__.py
│   ├── cost_logic.py
│   ├── hospital_filter.py
│   ├── insurance_logic.py
│   ├── scoring.py
│   └── symptom_map.py
│
├── ml/                            # Machine learning components
│   ├── __init__.py
│   └── risk_model.py
│
├── project/                       # Application layer
│   ├── __init__.py
│   └── orchestrator.py
│
├── utils/                         # Utility functions
│   ├── __init__.py
│   └── geo.py
│
├── app.py                         # Streamlit entry point (root-level)
├── README.md
└── .gitignore


🧠 Role of Each Component
1️⃣ app.py – User Interface (Streamlit)
Takes user inputs:
Age
Multiple symptoms
Area (human-readable)
Insurance option
Maps area → latitude & longitude
Calls recommend_hospitals() from orchestrator.py
Displays:
Risk level
Hospital name
Hospital type
Distance
Estimated cost
Insurance status

2️⃣ orchestrator.py – System Brain (Pipeline Controller)
This file connects everything.
Responsibilities:
Load datasets once
Call risk model
Apply filtering
Compute distance
Attach cost & insurance
Rank hospitals

3️⃣ ml/risk_model.py – Risk Assessment
Uses age + symptoms
Outputs:
Low
Medium
High

4️⃣ logic/hospital_filter.py – Facility Selection
Filters hospitals based on risk level:
Risk Level	Allowed Facilities
High	Hospital, Medical College
Medium	Hospital, Medical College
Low	Clinic, Dispensary, Hospital
Ensures some care is always suggested

5️⃣ logic/cost_logic.py – Cost Estimation
Cost is computed using:
Most severe symptom
Incremental increase for multiple symptoms
Facility ownership adjustment:
Government → subsidized
Private → premium
Example:
Fever → low OPD cost
Chest pain + breathing difficulty → higher emergency cost

6️⃣ logic/insurance_logic.py – Insurance Role
Insurance is treated as a soft signal, not a hard constraint.
What it does:
Slightly boosts ranking when insurance is selected
Improves affordability perception
What it does NOT do:
No claim approval
No coverage guarantees
No hospital exclusion

7️⃣ logic/scoring.py – Final Ranking Engine
Combines multiple signals:
Distance (safety & speed)
Estimated cost (affordability)
Insurance signal
Risk-aware weighting
Different risk levels change importance of factors.
The output is the Top 5 safest options, never empty.

8️⃣ utils/geo.py – Distance Calculation
Uses latitude & longitude
Computes distance in kilometers
Enables location-aware recommendations


🔁 End-to-End Pipeline Flow
User Input
   ↓
Risk Assessment (age + symptoms)
   ↓
Risk-based Hospital Filtering
   ↓
Distance Calculation
   ↓
Cost Estimation (multi-symptom aware)
   ↓
Insurance Influence
   ↓
Risk-Aware Ranking
   ↓
Final Safe Recommendations