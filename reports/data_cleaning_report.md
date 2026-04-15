# Data Cleaning Report
## 1. Overview

The dataset contains 110,527 medical appointment records with 14 variables describing patient demographics, health conditions and appointment scheduling details. The target variable (no_show) indicates whether a patient attended their appointment.

## 2. Column Standardization
- Converted all column names to lowercase
- Replaced special characters with underscores
- Corrected misspelled columns:
    * hipertension - hypertension
    * handcap - handicap

## 3. Data Type Corrections
- Converted scheduledday and appointmentday to datetime format
- Converted patientid to integer format
- Encoded the target variable:
    * no_show: Yes - 1, No - 0
- Converted categorical variables such as gender and neighbourhood to appropriate types
## 4. Data Quality Issues Addressed
*Invalid Values*
- Removed records where age < 0
- Removed records with negative waiting_days

*Neighbourhood Cleaning*
- Removed accents and special characters
- Standardized text formatting (lowercase, trimmed spaces)
- Created:
    * neighbourhood
    * neighbourhood_grouped (top locations vs others)
    * neighbourhood_risk (based on no-show rates)

## 5. Feature Engineering

The following features were created:

- waiting_days: Difference between appointment and scheduling date
- appointment_weekday: Day of the week of the appointment
- scheduled_weekday: Day the appointment was scheduled
- age_group: Categorized age into groups
- neighbourhood: Standardized location names
- neighbourhood_grouped: Top neighbourhoods vs others
- neighbourhood_risk: Segmentation based on no-show behavior

## 6. Handling Binning Issue in age_group

Missing values were observed in the age_group variable despite no missing values in age. This was due to boundary exclusion in the binning process (pd.cut()), where age = 0 was not included in any interval.

This issue was resolved by enabling include_lowest=True to ensure all values were properly categorized.

## 7. Missing Values

No missing values were found in the dataset after cleaning.

## 8. Duplicate Records

There were no duplicate values in the dataset.

## 9. Removed Columns

The following columns were removed:

* patientid
* appointmentid

These identifiers do not contribute to analytical insights or predictive modeling.

## 10. Final Dataset

The cleaned dataset is consistent, structured, and enriched with additional features, making it suitable for exploratory data analysis, statistical testing, and predictive modeling.