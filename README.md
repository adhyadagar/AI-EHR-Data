# AI-EHR-Data

# Part 1: Background
Context: EHR data is becoming a key source of real-world evidence (RWE) for the pharmaceutical industry and regulators to make decisions on clinical trials. You are a data scientist for an exciting unicorn healthcare startup that has created a groundbreaking diabetes drug that is ready for clinical trial testing. It is a very unique and sensitive drug that requires administering the drug over at least 5-7 days of time in the hospital with frequent monitoring/testing and patient medication adherence training with a mobile application. You have been provided a patient dataset from a client partner and are tasked with building a predictive model that can identify which type of patients the company should focus their efforts testing this drug on. Target patients are people that are likely to be in the hospital for this duration of time and will not incur significant additional costs for administering this drug to the patient and monitoring.

In order to achieve your goal you must build a regression model that can predict the estimated hospitalization time for a patient and use this to select/filter patients for your study.

# Part 2: Aim
1. To build an Expected Hospitalization Time Regression Model utilizing a synthetic dataset(denormalized at the line level augmentation) built off of the UCI Diabetes readmission dataset.
2. Predict the expected days of hospitalization time and then convert this to a binary prediction of whether to include or exclude that patient from the clinical trial.
3. Perform feature engineering on medical code sets 
4. Analyze and interpret regression model for biases across key demographic groups 

Dataset: For the purpose of this exercise, we are using a dataset from UC Irvine that has been modified for this course.https://archive.ics.uci.edu/ml/datasets/Diabetes+130-US+hospitals+for+years+1999-2008

# Part 3: Methodology
1. Data Analysis: 
      1.1 Use the Tensorflow Dataset API to scalably extract, transform, and load datasets and build datasets aggregated at the line, encounter, and patient data levels(longitudinal)
      1.2 Analyze EHR datasets to check for common issues (data leakage, statistical properties, missing values, high cardinality) by performing exploratory data analysis.
2. Create Categorical Features with TF Feature Columns 
     2.1 Create categorical features from Key Industry Code Sets (ICD, CPT, NDC) and reduce dimensionality for high cardinality features by using embeddings
3. Create Continuous/Numerical Features with TF Feature Columns
     3.1 Create derived features(bucketing, cross-features, embeddings) utilizing Tensorflow feature columns on both continuous and categorical input features
4. Build Deep Learning Regression Model with Sequential API and TF Probability Layers
     4.1 Use the Tensorflow Probability library to train a model that provides uncertainty range predictions that allow for risk adjustment/prioritization and triaging of predictions
5. Evaluating Potential Model Biases with Aequitas Toolkit
     5.1 Analyze and determine biases for a model for key demographic groups by evaluating performance metrics across groups by using the Aequitas framework


# Part 4: Evaluation Metrics 
AUC score :  0.755331729927067
F1 score :  0.770329175435986
Precision score:  0.7709811146936896
Recall score :  0.7709811146936896

            precision    recall  f1-score   support

           0       0.81      0.82      0.82      6683
           1       0.71      0.69      0.70      4172

    accuracy                           0.77     10855
   macro avg       0.76      0.76      0.76     10855
weighted avg       0.77      0.77      0.77     10855

# Part 5: Conclusion and Results

What are some areas of improvement for future iterations?
- We could use a complex model with more layers like LSTM for prediction
- We could impute missing values in the data by mean/mode/median/KNN imputation techniques instead of 0
- We could perform better data preprocessing and feature selection, taking biases and skewness into consideration 
- we could perform hyperparameter optimisation for seleccting better hyperparameters

Considering PPR and TPR metrics, bias can be observed in both race and gender:

- PPR: Predicted Positive Rate (Fraction of all positive predictions across groups that come from specific groups.) If we consider race, can clearly see a bias here since 'Caucasian' has the highest PPR compared to other races by quite a margin.

- TPR: True Positive Rate If we consider gender, the 'Male' is likely to have higher selection relative to 'Female' since TPR is higher for Males. This implies that the model is likely to predict more Male patients for testing than females.



