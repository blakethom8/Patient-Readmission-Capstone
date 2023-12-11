# Patient-Readmission-Capstone
***Predicting Hospital Readmissions in Congestive Heart Failure Patients***

*Project Overview*
  This project aims to develop a predictive model for inpatient, hospital readmissions based on data from the Beth Israel Deaconess Medical Center. The MIMIC-IV dataset is a rich collection of de-identified patient data from Beth Israel Deaconess Medical Center and we hope to develop a model that can identify patients at risk of readmission and determine the factors that most contribute to readmission identification.
  
  After initial exploration, we determined that an appropriate patient population for model prediction is patients diagnosed with Unspecified Congestive Heart Failure (ICD9 code:4280). We have assigned the readmission status to be a patient that is readmitted for Congestive Heart Failure within 90-days post-discharge. 
  
  Our final dataset included 14,432 patients, of which 3,068 fall into the Readmit Category (21%)

  *Discussion*
  We were able to structure a feature set of patients admitted to Beth Israel Medical Center and attempted to predict hospital readmission using different classification machine learning models. However, none of our models were able to show strong predictive performance and performed no better than random selection of patient outcomes as assessed via area under curve. The main models tested were Random Forest, Logistic Regression, Support Vector Machine, and Gradient Boosting. We made several attempts at various Feature Selection, Feature Engineering, and Parameter Tuning but were unable to increase the performance of the models.
We predict that we were unable to develop a rich enough feature set to enable predictive performance. Results showed that the admission length of stay was by far the most impactful feature in the model, which does make sense given that a patient's time in the hospital would indicate the severity of their illness. This leads me to believe that information providing insights to the severity of the patient's first hospital admission would increase the performance of the models. We had some other features that would describe the patient's state during the first hospital admission, including their BMI, blood pressure, and the number of medications they received during their visit. However, we lack information such as what procedures were done to a patient, what type of medications did the patient receive, and vital signs that would indicate the strength of patient's heart.  
Aside from improving the feature set, I believe there are various techniques that we could have explored to increase model performance. I believe techniques such as bagging and over-sampling could have increased the representation of Readmitted Patients into our sampe size, which could increase performance. We also believe there is further Feature Engineering and Parameter Tuning that could be done to increase the performance of the models. However, given the poor performance of the initial models, I do not think Feature Engineering and Parameter Tuning would lead to significant improvement in the model results. 
Thus, to improve performance moving forward, we would first seek to see if we could deploy other machine-learning techniques (i.e. Bagging, Neural Networks, etc) to see initial improvements in model performance. If those do not result in significant performance gains, than I would work with physicians to better understand the available data in the MIMIC-IV dataset and develop a richer set of features for predictive learning. Once we have seen substantial model improvement (i.e. AUC results >0.70), then we would work on fine-tuning the model with Feature Engineering and Parameter Tuning.

*Impact Statement*
  Heart Failure admissions have a significant financial impact for patients and the healthcare system. The average length of stay for heart failure admissions is 4 to 7 days, and results in $22k-$40k in charges. (https://www.jmcp.org/doi/10.18553/jmcp.2022.28.2.157#:~:text=Charge%20per%20HHF%20ranged%20from,and%20$7%2C860%20to%20$10%2C551%2C%20respectively)
  The ability to accurately predict hospital readmissions, especially for patients with cardiovascular heart disease, holds significant potential for enhancing patient care and optimizing healthcare resources. By identifying patients at a higher risk of readmission within 90 days of discharge, healthcare providers can tailor follow-up care and interventions more effectively, potentially reducing the likelihood of complications and readmissions. This proactive approach not only improves patient outcomes but also alleviates the strain on healthcare systems by reducing unnecessary hospitalizations.

*Dataset*
  The MIMIC-IV dataset encompasses comprehensive patient data, including demographics, chart events, admission information, and more. MIMIC-IV is one of the most robust, publically available datasets with patient data. Credentialing is required to access the data. For this project
  
  Patient Population: Approximately 20,000 patients with 45,000 patient visits for the diagnosis code 4280.
  Data Segmentation: Patients are categorized into two groups: those readmitted within 90 days and those not readmitted within this period
  Sample Sizes: After excluding for some null values, we ended up with 14,432 total patients of which, 3,068 were readmitted within 90-days for CHD
  Features-List: We developed a list of features across multiple tables in the MIMIC-IV dataset. This included static patient information (i.e. age, insurance provider), information about their medical history (i.e. prior number of hospital admission), information about the first admission for CHD (i.e. admission location, bmi, blood pressure).
  
  The total list of features in the final model included:
    admission_type, admission_location, discharge_location, insurance, language, marital_status, 
      race, Readmit Flag, num_prior_admissions_x, prior_length_of_stay_x, gender, anchor_age, total_medications, 
      total_hcpcs, admit_LOS, bmi, systolic_bp, diastolic_bp, bp_ratio

*Objectives*
  To identify key predictors of hospital readmission within 90 days for patients with cardiovascular heart disease.
  To evaluate the performance of various machine learning models in predicting readmissions.

*Methodology*
  Data Preparation: In general, we cleaned, transformed, and structured a number of features for analysis. This included aggregating information about their medical history and summarizing information related to their first hospital admission. Once aggregated, we explored the object features to assess if we needed to combine categories. The Language feature was the object feature that required the most re-categorization. 
  Feature Selection: After initial results, we did go back and add BMI and Blood Pressure data to the model. This showed modest improvement in model performance. After adding in the features, we explored reducing the number of features and selecting only the top 10 features that are most impactful in the model. However, reducing the number of features did not result in improvement of overall model performance.
  Feature Engineering: We created OneHot Encoding for the categorical features and StandardScaler for the numerical features. In addition, we explored using PolynomialFeatures for the numerical features. Interestingly, adding PolynomialFeatures to the pipeline decreased the performance of the models. 
  Model Development: We experimented primarily with 4 different classification models. These included Random Forest, Logistic Regression, Support Vector Machines, and Gradient Boosting. We also experimented with AdaBoostClassifier.  
  Validation: We assessed the model performance by assessing the Area-Under-Curve and analyzing the confusion matrix from the results.  

*Results* 
Unfortunately, all of our models showed poor performance. The AUC metrics performed around the ~0.5 threshold, showing little to no performance over random selection. Further assessing the Confusion Matrixes of the models, it appears that the Logistic Regression, SVM, Gradient Boosting, and AdaBoostClassifier classified almost all of the patients as Not Readmitted patients. Random Forest showed the greatest diversity of selections in the Confusion Matrix. Results from the Models is shared below. 

As part of the project, we also wanted to assess which features have the greatest impact on decision-making. Based on the outcomes of the Random Forest model, Admit_LOS had the greatest impact on the performance, followed by Medications, Patient Age, and Prior Length of Stay time. 

Model Performance Results: 
  Random Forest - Accuracy: 0.75, AUC: 0.51
  Confusion Matrix for Random Forest:
  [[1775   81]
   [ 530   22]]
  
   Logistic Regression - Accuracy: 0.77, AUC: 0.47
  Confusion Matrix for Logistic Regression:
  [[1856    0]
   [ 551    1]]
  
   Support Vector Machine - Accuracy: 0.77, AUC: 0.48
  Confusion Matrix for Support Vector Machine:
  [[1856    0]
   [ 552    0]]
  
   Gradient Boosting - Accuracy: 0.77, AUC: 0.53
  Confusion Matrix for Gradient Boosting:
  [[1849    7]
   [ 550    2]]
  
   AdaBoostClassifier - Accuracy: 0.77, AUC: 0.52
  Confusion Matrix for AdaBoostClassifier:
  [[1848    8]
   [ 549    3]]
