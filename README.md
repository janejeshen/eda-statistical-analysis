# EDA-STATISTICAL-ANALYSIS
## Business Problem
Many patients miss medical appointments, causing wasted resources and inefficiency in healthcare systems.

## Key Question
- What factors influence whether a patient shows up or not?

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