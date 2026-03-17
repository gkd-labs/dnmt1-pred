## DNMT1pred is a machine learning-based DNMT1 bioactivity predictive web application 

This repository provides comprehensive machine learning pipelines used for predicting bioactivity of chemical compounds against DNA methyltransferase 1 (DNMT1). Models were trained, evaluated and validated using extracted features from 43 RDKit molecular descriptors and 167 MACCS fingerprints. The pipeline includes meticulous data preprocessing, chemical space analysis, feature selection, model training, rigorous evaluation, and applicability domain assessment.

**Key step-by-step events employed in the script**.

1. **Data Curation**: Processes raw DNMT1 bioactivity data from PubChem, focusing on relevant assay types and activity statuses.
2. **Feature Generation**: Computes 43 RDKit molecular descriptors and 167 MACCS fingerprints for each compound.
3. **Chemical Space Analysis**: Visualizes molecular weight and logP distributions, with Z-score-based outlier removal (with threshold of |Z|=3.0) to ensure data quality and model robustness.
4. **Feature Selection**: Employs `Chi-square statistical test` to select the top 50 most informative MACCS fingerprints.
5. **Data Scaling**: Applies `MinMaxScaler` to normalize all molecular features (descriptors and fingerprints).
6. **Linear Regression Based Soft Filter**: Applies Linear Regression as a soft filter to remove molecules that pose high level of prediction uncertainties. The filter molecules are those that are likely to fall on the decision boundary. This method improved model performance and robustness. This study compared the performances of models in seprate notebooks for when this filter was used and when it wasn't used.
7. **Model Training**: Implements and evaluates 5 well known chemoinformatics-based performing machine learning classifiers, including: eXtreme Gradient Boosting (XGBoost), Support Vector Machine (SVM), Logistic Regression (LR), Gaussian Naive Bayes (GNB), and Gradient Boosting Machines (GBM)
8. **Comprehensive Evaluation**: Reports key classification metrics such as Accuracy, Precision, Recall, F1-Score, AUC, MCC, Balanced Accuracy, and also performs 10-fold cross-validation for robust performance estimation.
9. **Applicability Domain (AD) Analysis**: Generates Williams plots for each model to visualize their applicability domain, indicating the region within which predictions are considered reliable.

All model weights including the linear regression soft filter weights, the Chi square object and the scaler object were saved for inference and deployment.

** To systematically replicate the experiment conducted and presented in this repository, follow these key steps:

1.  **Clone this repository** .
2. Open the notebook file of your choice from the notebooks folder in this repository and systematically execute each cell. The scripts have been organized in a step-by-step manner and easy to follow. The DNMT1 bioactivity data retrieved from PubChem together with the downloaded molecule data from PubChem from which the SMILES were obtained have also been provided in the datasets folder in the repository. Ensure all directories have been set to your preferred path.


**Logistic regression and XGBoost, which were the best performing models have been deployed as a web application and is available at https://dnmt1pred.onrender.com/**
