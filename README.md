## Heart Disease Classification ##


### Business Goal ###

We'll be working with the largest hospital in Massachusetts (The Massachusetts General Hospital). Using various classification algorithms, we'll determine which algorithm provides the most accurate predictions for whether a patient is at risk in 10 years for a type of cardiovascular disease called coronary heart disease (CHD). This will in turn help the hospital create a treatment/preventative plan for at-risk patients early on, and hopefully prevent CHD from developing.

### Data ###
The Framingham Heart Study (https://www.framinghamheartstudy.org/fhs-about/) is a long term, ongoing study on cardiovascular diseases. Started in 1948, the study looked at numerous factors such as age, gender, cholesterol levels, etc, and would eventually lead to the identification of several risk factors for cardiovascular disease. We'll be using a Kaggle dataset from this study, which contains multiple risk factors for a type of cardiovascular disease called coronary heart disease (CHD). The dataset also contains a target variable for whether or not a patient is at risk in 10 years for CHD. The risk factors are divided into demographic, behavioral and medical categories, and are listed below.

**Demographic:**
* male: male (1) or female (0)
* Age: Age of the patient
  
**Behavioral:**
* education: Less than High School and High School degrees (0) or College Degree and Higher (1)
* currentSmoker: Whether the patient is a current smoker (1) or not (0)
* cigsPerDay: the number of cigarettes that the person smoked on average in one day. 

**Medical History:**
* BPMeds: Whether patient was on blood pressure medication (1) or not (0)
* prevalentStroke: Whether the patient had previously had a stroke (1) or not (0)
* prevalentHyp: Whether the patient was hypertensive (1) or not (0)
* diabetes: Whether the patient had diabetes (1) or not (0)
  
**Medical(current):**
* totChol: total cholesterol level
* sysBP: systolic blood pressure
* diaBP: diastolic blood pressure
* BMI: Body Mass Index
* heartRate: heart rate
* glucose: glucose level
  
**Target Variable:**
* TenYearCHD: 10 year risk of coronary heart disease or CHD (“1” means “Yes”, “0” means “No”)



**After checking for duplicates and null values, our data looked like:**

![data columns](https://user-images.githubusercontent.com/45251340/202008954-5c6a410f-0165-47a5-92df-089bc46ebce6.JPG)


### Initial Models ###

First we split our data using train-test split, and then scaled our data using StandardScaler. Noticing our data was unbalanced, we used SMOTE, and then moved onto our models.

**1) Logistic Regression**

After fitting and running our model, we printed our training and test model classification reports: 

![log_reg_classification_reports](https://user-images.githubusercontent.com/45251340/202010680-dbae2d3c-c763-4266-a979-6ca6bbb44395.JPG)

We also displayed our test model confusion matrix:


![log_reg_conf_matrix](https://user-images.githubusercontent.com/45251340/202011008-09b88b92-063a-4228-bbc6-0e292fc5d8c3.JPG)


**We can see that our model is slightly overfitting, but let's take a look at our classification summary results.**

For our test model class 1 (meaning the patient is at risk for coronary heart disease) we have a precision score of .28, a recall score of .71, and an f1 score of .40. This means that:

* Out of all the patients that the model predicted would be at risk for CHD, 28% were actually at risk.
* Out of all the patients that were at risk for CHD, the model correctly predicted 71% of them
* Our model has a low f1 score, indicating poor performance on predicting risk of CHD.

**We can also see the true negative, false negative, false positive and true positive values for our test model (from our confusion matrix), where:**

* 586 patients were correctly predicted as not being at risk for CHD
* 45 patients were wrongly predicted as not being at risk for CHD
* 291 patients were wrongly predicted as being at risk for CHD
* 112 patients were correctly predicted as being at risk for CHD


**2) Decision Tree**

After fitting and running our model, we printed our training and test model classification reports as well as the test model confusion matrix: 

![dec_tree_classification_reports](https://user-images.githubusercontent.com/45251340/202012251-6beffb40-991e-4b41-a5a2-d5cb26e8e002.JPG)

![dec_tree_confusion_matrix](https://user-images.githubusercontent.com/45251340/202012424-a09d1eaf-ee0c-49ef-a458-401f432e85c7.JPG)


**This time our model is greatly overfitting. Let's take a look at our classification report results**

For our test model class 1 (meaning the patient is at risk for coronary heart disease) we have a precision score of .23, a recall score of .36, and an f1 score of .28, meaning:

* Out of all the patients that the model predicted would be at risk for CHD, 23% were actually at risk.
* Out of all the patients that were at risk for CHD, the model correctly predicted 36% of them
* Our model has a low f1 score, indicating poor performance on predicting risk of CHD.

**Looking at our test model confusion matrix we can see that:**

* 691 patients were correctly predicted as not being at risk for CHD
* 101 patients were wrongly predicted as not being at risk for CHD
* 186 patients were wrongly predicted as being at risk for CHD
* 56 patients were correctly predicted as being at risk for CHD

**3) Random Forest**

After fitting and running our last model, we printed our training and test model classification reports as well as the test model confusion matrix: 


![rand_forest_classification_reports](https://user-images.githubusercontent.com/45251340/202013129-968cdeed-5969-454c-a2fe-94b484ecef53.JPG)


![rand_forest_confusion_matrix](https://user-images.githubusercontent.com/45251340/202013308-936216ce-55ba-41ed-9ae4-9c1ff93d0ae7.JPG)

**Again, our model is greatly overfitting. Let's take a look at our classification report results**

For our test model class 1 (meaning the patient is at risk for coronary heart disease) we have a precision score of .33, a recall score of .27, and an f1 score of .30, meaning:

* Out of all the patients that the model predicted would be at risk for CHD, 33% were actually at risk.
* Out of all the patients that were at risk for CHD, the model correctly predicted 27% of them
* Our model has a low f1 score, indicating poor performance on predicting risk of CHD.

**For our last model's confusion matrix we can see that:**

* 790 patients were correctly predicted as not being at risk for CHD
* 114 patients were wrongly predicted as not being at risk for CHD
* 87 patients were wrongly predicted as being at risk for CHD
* 43 patients were correctly predicted as being at risk for CHD


### Improving The Models ###


#### 1) Decision Tree ####
We graphed training and test AUC scores for the **max_depth, min_samples_split, and min_samples_leaf** hyperparameters as shown below:

![dec_tree_max_depth_auc_score](https://user-images.githubusercontent.com/45251340/202015172-81f3703d-a0f8-4a9d-96be-3c2d142e803b.JPG)

![min_sample_splits_dec_tree_auc_score](https://user-images.githubusercontent.com/45251340/202015194-9510f20b-967f-4af3-b54c-c805df67a85a.JPG)

![min_sample_leaf_dec_tree_auc_score](https://user-images.githubusercontent.com/45251340/202015211-67bb90e0-1436-4d61-ab97-68f72af4e4a4.JPG)


**From our AUC graphs, we can see that:**

* Our optimized max_depth value is between 1 and 5. Any higher, and the model starts overfitting due to the training model performing better than our test model
* Our optimized min_sample_split value is between 0.2 and 0.4. Any higher and performance for both models does not change
* Our optimized min_samples_leaf value is between 0.1 and 0.13. Any higher and performance decreases before plateauing

**We then created a grid search with these value ranges and printed out our classification reports and confusion Matrix:**

![dec_tree_classification_reports2](https://user-images.githubusercontent.com/45251340/202016807-925a2878-6ccb-4738-83bf-4eec107675b2.JPG)

![dec_tree_confusion_matrix2](https://user-images.githubusercontent.com/45251340/202016818-dd251191-c519-48cf-825a-1a9f9f01ab8f.JPG)

**We can see our model has less overfitting. Let's take a look at our classification report results**

For our test model class 1 (meaning the patient is at risk for coronary heart disease) we have a precision score of .23, a recall score of .69, and an f1 score of .34, meaning:

* Out of all the patients that the model predicted would be at risk for CHD, 23% were actually at risk.
* Out of all the patients that were at risk for CHD, the model correctly predicted 69% of them, which is a drastic improvement from our base model
* Our model has a low f1 score, indicating poor performance on predicting risk of CHD, but has improved from our initial results.

**Looking at our test model confusion matrix we can see that:**

* 508 patients were correctly predicted as not being at risk for CHD
* 49 patients were wrongly predicted as not being at risk for CHD
* 369 patients were wrongly predicted as being at risk for CHD
* 108 patients were correctly predicted as being at risk for CHD


**2) Random Forest**

Two grid searches were ran, using **n_estimators, max_depth, min_samples_split, and min_samples_leaf** as the grid search parameters. 


Both showed reduced overfitting, but the better performing one had the following classification reports and confusion matrix:

![rand_forest_classifcation_reports2](https://user-images.githubusercontent.com/45251340/202256674-a428b516-cb55-4695-9fdb-653fdc8edbac.JPG)

![rand_forest_confusion_matrix2](https://user-images.githubusercontent.com/45251340/202256698-83fd1678-efcf-434d-b40a-e7eac81b5406.JPG)


The better performing Random Forest model had precision score of .26, a recall score of .67, and an f1 score of .37, meaning:

* Out of all the patients that the model predicted would be at risk for CHD, 26% were actually at risk.
* Out of all the patients that were at risk for CHD, the model correctly predicted 67% of them, which is a drastic improvement from our base model
* Our model has a low f1 score, indicating poor performance on predicting risk of CHD, but has improved from our initial results.: 

**Then, Looking at our test model confusion matrix we can see that:**

* 575 patients were correctly predicted as not being at risk for CHD
* 52 patients were wrongly predicted as not being at risk for CHD
* 302 patients were wrongly predicted as being at risk for CHD
* 105 patients were correctly predicted as being at risk for CHD
