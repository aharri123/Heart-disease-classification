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


