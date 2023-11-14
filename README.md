# Patient-Readmission-Capstone
***Predicting Hospital Readmissions in Congestive Heart Failure Patients***

*Project Overview*
This project aims to develop a predictive model for inpatient, hospital readmissions based on data from the Beth Israel Deaconess Medical Center. After initial exploration, the patient population for model prediction is focused on those diagnosed with Unspecified Congestive Heart Failure (ICD9 code:4280). We will explore various readmission date cutoff thresholds, including predictions at 30-, 60-, and 90-days post-discharge. Utilizing the MIMIC-IV dataset, a rich collection of de-identified health data from Beth Israel Deaconess Medical Center, the model seeks to identify patterns and factors contributing to readmissions.

*Impact Statement*
Heart Failure admissions have a significant financial impact for patients and the healthcare system. The average length of stay for heart failure admissions is 4 to 7 days, and results in $22k-$40k in charges. (https://www.jmcp.org/doi/10.18553/jmcp.2022.28.2.157#:~:text=Charge%20per%20HHF%20ranged%20from,and%20$7%2C860%20to%20$10%2C551%2C%20respectively)
The ability to accurately predict hospital readmissions, especially for patients with cardiovascular heart disease, holds significant potential for enhancing patient care and optimizing healthcare resources. By identifying patients at a higher risk of readmission within 90 days of discharge, healthcare providers can tailor follow-up care and interventions more effectively, potentially reducing the likelihood of complications and readmissions. This proactive approach not only improves patient outcomes but also alleviates the strain on healthcare systems by reducing unnecessary hospitalizations.

*Dataset*
The MIMIC-IV dataset encompasses comprehensive patient data, including demographics, chart events, admission information, and more. MIMIC-IV is one of the most robust, publically available datasets with patient data. Credentialing is required to access the data. For this project:

Patient Population: Approximately 20,000 patients with 45,000 patient visits for the diagnosis code 4280.
Data Segmentation: Patients are categorized into two groups: those readmitted within XX days and those not readmitted within this period.
Features-List: _Note to add the list of features_

*Objectives*
To identify key predictors of hospital readmission within 90 days for patients with cardiovascular heart disease.
To evaluate the performance of various machine learning models in predicting readmissions.

*Methodology*
Data Preparation: Cleaning, transforming, and structuring data for analysis.
Feature Selection: Identifying relevant features that influence readmissions.
Model Development: Experimenting with different machine learning models for the best predictive accuracy.
Validation: Assessing the model's performance using appropriate metrics.

*Models Explored*
Logistic Regression
Decision Trees
Random Forest

*Results* 
