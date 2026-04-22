# EDA-STATISTICAL-ANALYSIS
## Project Overview
Missed medical appointments create inefficiencies in healthcare systems, leading to wasted resources and reduced patient care quality.

This project analyzes patient appointment data to identify the key factors that influence whether a patient shows up or misses their appointment.

## Business Problem
Many patients fail to attend scheduled medical appointments, resulting in operational inefficiencies and lost resources.

## Objectives
- Identify factors that influence appointment attendance  
- Analyze behavioral and operational drivers of no-shows  
- Provide actionable recommendations to reduce missed appointments 

## Dataset
- **Source:** Kaggle [Medical Appointment No Shows Dataset](https://www.kaggle.com/datasets/joniarroba/noshowappointments/data)
- **Records:** 110,527 appointments  
- **Target Variable:** `no_show` (0 = Showed Up, 1 = Missed Appointment)

## Data Cleaning Summary
- Standardized column names (lowercase, consistent naming) and corrected inconsistencies
- Fixed misspelled columns (hipertension → hypertension, handcap → handicap)
- Converted date columns (scheduledday, appointmentday) to datetime format
- Encoded target variable (no_show: Yes → 1, No → 0)
- Removed invalid records:
    - negative age values
    - negative waiting days
- Cleaned and standardized neighbourhood:
    - removed accents and special characters
    - normalized text formatting
- Engineered new features:
    - waiting_days (time between scheduling and appointment)
    - appointment_weekday, scheduled_weekday
    - age_group (categorized age ranges)
    - neighbourhood_grouped (top locations vs others)
    - neighbourhood_risk (segmentation based on no-show rates)
- Resolved binning issue in age_group by including boundary values
- Verified dataset contains no missing values
- Checked and removed duplicate records
- Dropped non-informative identifier columns (patientid, appointmentid)

Full report: `reports/data_cleaning_report.md`

## Exploratory Data Analysis (EDA)

Key patterns were identified through visualization and analysis:

- Longer waiting times are associated with higher no-show rates  
- Younger patients are more likely to miss appointments  
- SMS reminders show mixed effects (possible targeting bias)  
- Medical conditions have minimal influence on attendance  
- Neighbourhood differences suggest geographic impact  
- Day of the week influences appointment attendance  


## Statistical Analysis

Statistical tests were performed to validate EDA findings:

- **Mann-Whitney U Test** confirmed significant differences in:
  - waiting time  
  - age  

- **Chi-Square Tests** showed significant relationships between:
  - SMS reminders and no-show  
  - scholarship status and no-show  
  - appointment weekday and no-show  

### Key Takeaway
Operational factors (especially waiting time) and behavioral patterns are more influential than medical conditions.

---

## Key Insights

## 🔍 Key Insights

- **Waiting time is the strongest predictor** of missed appointments, with longer delays significantly increasing the likelihood of non-attendance.

- **Younger patients are at higher risk** of missing appointments, suggesting differences in availability, priorities, or engagement with healthcare services.

- **SMS reminders show an apparent relationship with no-show rates, but this should be interpreted cautiously.** The data likely reflects **selection bias**, where reminders are sent to patients already considered high-risk (e.g., those with prior missed appointments). As a result, higher no-show rates among these patients do not necessarily indicate that SMS reminders are ineffective.

- **Medical conditions (hypertension, diabetes, alcoholism, handicap)** are relatively weak predictors of attendance, indicating that behavioral and operational factors play a larger role.

- **Location and scheduling patterns influence attendance**, suggesting that geographic and temporal factors may impact patients’ ability or likelihood to attend appointments.

---

> ⚠️ **Note:** These findings are based on observational data. Relationships identified in the analysis may reflect correlation rather than direct causation.

---

## Business Recommendations

Healthcare providers can reduce missed appointments by:

- Minimizing waiting time between scheduling and appointments  
- Identifying high-risk patients (long waiting time, younger age)  
- Improving reminder strategies and timing  
- Implementing targeted interventions in high-risk neighbourhoods  
- Optimizing scheduling based on weekday patterns  

---