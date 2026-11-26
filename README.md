# Financial Sentiment Analysis 

<div align="justify">
  
## Objectives 
The project involves comprehensive data exploration, preprocessing, and feature engineering to ensure 
high-quality input for the machine learning (ML) models. Multiple predictive algorithms, such as 
eXtreme Gradient Boosting (XGBoost) and a neural network (NN) model, are employed and compared 
to determine the most effective approach for predicting student dropout.

## Background 
A tabular dataset was studied to predict student dropout using two supervised ML approaches: 
eXtreme Gradient Boosting (XGBoost) and a neural network (NN) model. The dataset contained demographic 
and administrative records of over 25,000 international students. To predict student dropout, the dataset 
was pre-processed and analysed in three distinct stages, each reflecting the real-world 
progression of data acquisition: 

1. Applicant and course information 
2. Student and engagement data 
3. Academic performance data 

## Data Pre-processing 
The processing steps included: 
* Removal of features with high cardinality (> 200) and high percentages of 
missing values (> 50%) were removed. 
* Imputing missing values of numerical features via the median. 
* One-hot and ordinal encoding of categorical features where applicable. 
* Assessment of the target variable for class imbalance. 
* Standard scaling of continuous numerical features, to improve model performance and preserve
interpretability across the encoded categorical variables.

*Before model training, a train-test split of 80-20% was applied, followed by a 10% split of 
the training dataset as the validation dataset. Stratification was implemented in both 
splits to address the class imbalance.*

## Study Design
Following data processing at each stage, a baseline XGBoost and a NN model was 
instantiated and hyperparameter tuned. The tuned model at a given stage formed the 
baseline model of the next as depicted in the figure below.

<br><br>
<p align="left">
  <img src="Figures/workflow.png" width="600">
</p>
<br><br>

## Model Performance Assessment 
* To assess model performance, several metrics described in the table below was used:
  
| Metric    | Description | 
|-----------|--------------------------------------------------------------------|
| Accuracy  | The proportion of correct predictions out of the total predictions.|
| Precision | The proportion of true positive predictions out of all instances predicted as positive.|
| Recall / Sensitivity / True Positive Rate (TPR)|The proportion of true positive predictions out of all actual positive instances.| 
| F1 Score  |  The harmonic mean of precision and recall.|
| Area Under the Curve (AUC)| The ability of a classifier to distinguish between classes, given by the summary score of the ROC (Receiver Operating Characteristic) curve.|
  
* Confusion matrix plots were included to encapsulate the classification process. 
* During the optimisation process, the tuners were configured with the AUC metric to better 
incorporate the class imbalance.

## XGBoost Model Key Highlights

The confusion matrix plots obtained following optimisation of the XGBoost classifiers, 
representing the best model obtained at each stage: 

<br><br>
<p align="left">
  <img src="Figures/XGB_CMs_all.png" height="500">
</p>
<br><br>

Moving across stages there is a significant improvement in TPR, whereas the TNR always remains high due to class imbalance.  

## NN-Based Model Key Highlights

The figure below depicts the AUC-score plots (left) and the loss curves (right) acquired for the NN models created at 
each stage. As the titles indicate, the training pattern of each baseline model is directly compared to its hyperparameter-tuned 
counterpart. Notably, the validation datasets start from a higher AUC value which can be considered a sign of class imbalance, as the 
model can consistently but randomly predict a negative class and achieve a high TNR. 

<br><br>
<p align="left">
  <img src="Figures/all_losscurves.png" width="1000">
</p>
<br><br>

The resulting AUC scores indicate a significant increase moving from stage 2 to 3 
which based on the confusion matrix plots presented in the figure below cannot be attributed to 
hyperparameter optimisation alone. 

<br><br>
<p align="left">
  <img src="Figures/NN_all_CMs.png" width="700">
</p>
<br><br>

## Summary & Conclusions

A ML learning framework incorporating XGBoost and NNs was developed for predicting 
student dropout. Moving from stage 1 to 2, the dataset was enriched with additional 
features relating to student engagement and at stage 3, features relating to academic 
performance was introduced. 

At each stage, an XGBoost and a NN-based model was instantiated, trained and 
evaluated. Next, hyperparameter tuning was performed using several approaches 
including grid search, Bayesian and hyperband optimisation. 

The AUC scores along with further metrics such as TPR was used for model comparisons. 
The final models surpassed the 75% TPR  threshold indicating well-performing models in 
a relatively low-stake scenario. To achieve higher sensitivities, further hyperparameter 
tuning and incorporation of traditional regularisation techniques would be highly 
recommendable.  

Remarkably, it was found that while hyperparameter optimisation led to improvements 
ranging from 1.1 − 4.3% moving from stage 1 to stage 2, the biggest improvement was 
achieved through the enrichment of the dataset at stage 3 upon the addition of the more 
context-specific features (roughly 19% increase for both methods). 

In contrast, the feature importance plots (excluded for confidentiality) did not entirely capture 
this enhancement. While the consistent prevalence of specific features in the top 5 (and 20) 
was notable, the inter-feature student dropout rates were found to be highly variable.

To understand what leads to student dropout, the collective and isolated interaction of input 
features with the outcome variable must be studied to reveal the intricate patterns, 
especially for early intervention. An obvious approach would be to use the SHAP values method whereas 
an alternative would be to use a permutation-based analysis where each feature is randomly shuffled 
to capture the change in the model’s performance. 

</div>
