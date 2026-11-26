# Financial Sentiment Analysis 

<div align="justify">
  
## Objectives 



## Data Pre-processing 


## Study Design


<br><br>
<p align="left">
  <img src="Figures/" width="600">
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


<br><br>
<p align="left">
  <img src="Figures/" height="500">
</p>
<br><br>

Moving across stages there is a significant improvement in TPR, whereas the TNR always remains high due to class imbalance.  

## Model Key Highlights



<br><br>
<p align="left">
  <img src="Figures/all_losscurves.png" width="1000">
</p>
<br><br>



<br><br>
<p align="left">
  <img src="Figures/NN_all_CMs.png" width="700">
</p>
<br><br>

## Summary & Conclusions



</div>
