# AI-EHR-Data

This work is a part of Unit 4 of the AI in Healthcare Nanodegree on Udacity. 

Context: EHR data is becoming a key source of real-world evidence (RWE) for the pharmaceutical industry and regulators to make decisions on clinical trials. You are a data scientist for an exciting unicorn healthcare startup that has created a groundbreaking diabetes drug that is ready for clinical trial testing. It is a very unique and sensitive drug that requires administering the drug over at least 5-7 days of time in the hospital with frequent monitoring/testing and patient medication adherence training with a mobile application. You have been provided a patient dataset from a client partner and are tasked with building a predictive model that can identify which type of patients the company should focus their efforts testing this drug on. Target patients are people that are likely to be in the hospital for this duration of time and will not incur significant additional costs for administering this drug to the patient and monitoring.

In order to achieve your goal you must build a regression model that can predict the estimated hospitalization time for a patient and use this to select/filter patients for your study.

Aim: 
1. To build an Expected Hospitalization Time Regression Model utilizing a synthetic dataset(denormalized at the line level augmentation) built off of the UCI Diabetes readmission dataset.
2. Predict the expected days of hospitalization time and then convert this to a binary prediction of whether to include or exclude that patient from the clinical trial.
3. Perform feature engineering on medical code sets 
4. Analyze and interpret regression model for biases across key demographic groups 

Dataset: For the purpose of this exercise, we are using a dataset from UC Irvine that has been modified for this course.https://archive.ics.uci.edu/ml/datasets/Diabetes+130-US+hospitals+for+years+1999-2008

Steps:
1. Data Analysis: 
 * 1.1 Use the Tensorflow Dataset API to scalably extract, transform, and load datasets and build datasets aggregated at the line, encounter, and patient data levels(longitudinal)
 * 1.2 Analyze EHR datasets to check for common issues (data leakage, statistical properties, missing values, high cardinality) by performing exploratory data analysis.
2. Create Categorical Features with TF Feature Columns 
2.1 Create categorical features from Key Industry Code Sets (ICD, CPT, NDC) and reduce dimensionality for high cardinality features by using embeddings
3. Create Continuous/Numerical Features with TF Feature Columns
3.1 Create derived features(bucketing, cross-features, embeddings) utilizing Tensorflow feature columns on both continuous and categorical input features
6. Build Deep Learning Regression Model with Sequential API and TF Probability Layers
6.1 Use the Tensorflow Probability library to train a model that provides uncertainty range predictions that allow for risk adjustment/prioritization and triaging of predictions
7. Evaluating Potential Model Biases with Aequitas Toolkit
7.1 Analyze and determine biases for a model for key demographic groups by evaluating performance metrics across groups by using the Aequitas framework


Conclusion and Results:



