EE461 Project Blog 

- This blog serves as home for project logging, backup and updates for the progress in the coming weeks
- This blog shall be updated fortnightly, containing any relevant advances for the development of the glucose estimation model

Blog update 1 - 31/03/2025 - Week 6
- Creation of blog
- Uploading of files for backup

Blog update 1 - 24/04/2025 - Week 7

Part 1

1. Feature Engineering and Initial Exploration
The analysis began with the selection and visualization of five engineered features. Using MATLAB, basic exploratory techniques such as boxplots and scatter plots were employed to gain an initial understanding of data distributions and the relationships between predictors and the target variable.

2. Principal Component Analysis (PCA)
PCA was applied to both unnormalized and normalized data to assess the variance captured by each principal component. Pareto charts were used to visualize component significance, while 2D and 3D scatter plots facilitated the identification of patterns and potential clustering in reduced-dimensional space. The intrinsic dimensionality of the dataset was estimated using dy/dx plots, indicating a meaningful dimensionality of approximately nine.

3. Correlation Analysis
A heatmap of the normalized dataset was generated to investigate linear correlations between variables. This revealed several features with minimal or no correlation to glucose levels and highlighted collinearity among some variables, suggesting that dimensionality reduction and feature selection would be beneficial.

4. Curvilinear Component Analysis (CCA)
Given the apparent non-linearity in the dataset, Curvilinear Component Analysis was performed. Compared to PCA, CCA provided more informative and balanced low-dimensional representations. The dy/dx plots post-CCA transformation further validated the earlier dimensionality estimates and indicated better-preserved interclass distances.

5. Preliminary Model Testing
MATLAB’s Regression Learner App was used to prototype a narrow neural network model. Initial results demonstrated a root mean square error (RMSE) of approximately 40.7 mg/dL. Visual analysis suggested that this value was influenced by outliers; excluding them could potentially reduce the RMSE to below 20 mg/dL. However, the model exhibited a low R² value (-2.06), indicating that further model refinement is necessary.

Key Findings
Outlier Removal: Boxplots effectively identified outliers, which were removed to improve the reliability of statistical measures. Exceptionally high glucose values (~220 mg/dL) were retained, as they reflect clinically plausible cases.

Feature Relevance: Features such as std_ch3, crestf_ch2, and higher-order statistical moments were found to have weak correlations with the target variable, making them potential candidates for exclusion.

Dimensionality Insight: PCA and CCA confirmed that a small subset of components (approximately nine) captured the majority of useful variance, offering significant opportunities for dimensionality reduction.

Model Behavior: Despite low R² values, the predicted outputs demonstrated clustering in physiologically relevant glucose ranges (90–130 mg/dL), indicating some level of underlying structure that may be captured more effectively with advanced modeling techniques.

Future Work
Following the insights gained during this stage, the next phase of the project will involve:

Refinement of feature selection to eliminate noisy or redundant predictors.

Exploration of more sophisticated models, including deep learning architectures and ensemble methods.

Enhanced model validation through cross-validation and hyperparameter tuning.

Part 2 

GlucoData Analysis and Predictive Modeling
This project presents a systematic approach to analyzing data obtained from a glucometer prototype. The dataset includes measurements and lifestyle information from 461 patients, compiled to support predictive modeling for glucose levels.

1. Dataset Overview
The initial dataset comprises 21 features, including demographic and physiological variables such as:
•	Age
•	Gender
•	Height (cm)
•	Weight (kg)
•	Body Mass Index (BMI)
•	Heart Rate (bpm)
•	Blood Glucose Level (mmol/L)
These features were extracted from the raw data to construct a refined 6-feature dataset focused on lifestyle and health indicators relevant to glucose levels.

3. Data Preprocessing
To enhance data quality and model performance, the following preprocessing steps were applied:
•	Removal of missing values and outliers, resulting in a reduced dataset of 318 valid entries.
•	Normalization using Z-score transformation, which standardizes features to have a mean of 0 and a standard deviation of 1.
Data visualization techniques, including box plots and scatter plots, were used to assess the distribution and detect anomalies in both raw and normalized datasets.

4. Dimensionality Reduction
To reduce data complexity while preserving critical information:
•	Principal Component Analysis (PCA) was performed, reducing the dataset from 6 to 4 dimensions.
•	Visual tools such as Pareto charts and biplots provided insights into the relationships between features.
•	Curvilinear Component Analysis (CCA) was also employed for further dimensionality reduction and visualization, highlighting potential clusters and outliers.

5. Correlation Analysis
A correlation matrix heatmap of the normalized data was used to identify redundancy and interdependencies among features. Notably, BMI and weight exhibited a strong correlation, indicating potential for feature reduction in future modeling efforts.

6. Machine Learning and Model Evaluation
The Regression Learner App in MATLAB was utilized to train and evaluate various regression models:
•	The Ensemble Regression model yielded the best performance, though with modest results:
o	Training R² = 0.06
o	Testing R² = 0.12
Despite limited predictive accuracy, the model serves as a foundational benchmark for future improvements.

7. Performance Visualization
•	Predicted vs. actual plots revealed significant variance, indicating low predictive precision.
•	A response plot illustrated substantial prediction errors, likely due to non-linear relationships and weak feature-response correlations.

Future Work
To improve the predictive performance of the model, future efforts will focus on:
•	Advanced feature engineering
•	Hyperparameter optimization
•	Implementation of non-linear and deep learning models
•	Expansion of the dataset, if possible, to enhance training efficacy


Week 9 & Week 10- 28/03/2025 to 08/05/2025

Used Feature Diagnotic Designer to calculate, Rank and extract the best features
Applied feature extraction to all quick to train models in order compare performance increase
- highest model found was R^2 value of 0.14, 14% increase from Previous Neurla Network Model
- implemented using voltage sensor data

Attempted to design and implement ANN
- model accuracy was found to be 55% on both validation and test data.
- this model was implemented using the lifestyle data, showing promise for model development

Advancing Non-Invasive Blood Glucose Prediction Through AI: A Progress Report
As diabetes rates continue to rise globally, so does the urgency for less intrusive blood glucose monitoring systems. Our project takes on this challenge by harnessing artificial intelligence (AI) to estimate glucose levels non-invasively using sensor and lifestyle data—no needles, no strips.

In this second progress report, we delve into our latest findings, comparing the performance of various machine learning and deep learning models to uncover the best path forward for real-time, AI-powered glucose prediction.

🔍 Project Goal: Smarter, Simpler Glucose Monitoring
Our aim in this phase was clear: evaluate and compare the performance of Artificial Neural Networks (ANN), Long Short-Term Memory (LSTM) networks, and Curvilinear Component Analysis (CCA)-based regression models.

We tested each approach across three input configurations:
Voltage-only sensor data
Lifestyle data (e.g., diet, activity, sleep)

A combined dataset of both
Ultimately, we're working toward identifying the most accurate yet computationally lightweight model suitable for integration into a portable, real-time glucometer system.

🛠️ Methodology in a Nutshell
Preprocessing: We cleaned the data by handling missing values, removing outliers, and applying z-score normalization.
Dataset Split: 70% training, 15% validation, and 15% testing.
Model Training: MATLAB was used for model development and evaluation.

🤖 AI Models in Focus
🔹 Artificial Neural Networks (ANN)
Structure: Two hidden layers, with neurons scaled to match input complexity.
Strength: Good at capturing non-linear patterns.

Results:
Voltage Data: R² = 0.53 – decent correlation with true glucose levels.
Lifestyle Data: R² = 0.07 – poor performance; lifestyle alone doesn't cut it.
Combined Data: R² = 0.5 – only a slight boost, indicating potential noise from lifestyle variables.

🔸 Long Short-Term Memory Networks (LSTM)
Structure: Memory cells and gates to model time-dependent patterns.

Results:
Voltage Data: RMSE = 0.16, R² ≈ 0.70 – outperforms ANN thanks to temporal pattern recognition.
Lifestyle Data: R² ≈ 0.36 – again underwhelming, but better than ANN.
Combined Data: R² ≈ 0.83 – best deep learning outcome; LSTM effectively integrates diverse inputs.

⚙️ CCA-Based Regression Models
Approach: Reduced 20 features to 9 using CCA, then applied regression.

Results:
Linear Regression: R² = 0.99 (validation), R² = 1 (test) with RMSE <2% of the response range.
These results highlight both efficiency and high accuracy, making CCA-based models highly attractive for embedded systems.

📊 Key Takeaways
LSTM models shine in capturing complex, time-dependent glucose trends—especially with combined inputs.
ANNs underperform when lifestyle data is used alone or even in combination.
CCA-based linear regression delivers outstanding accuracy with minimal computational overhead, making it the front-runner for real-time deployment.

🔮 What's Next?
Our next steps will focus on:

Hyperparameter tuning
Exploring ensemble models
Conducting Clarke’s Error Grid analysis to assess clinical relevance
Embedding the best-performing model into a hardware prototype for real-time testing
We’re getting closer to an accessible, non-invasive glucose monitoring solution powered by intelligent data modeling—and we’re excited to keep pushing forward.
