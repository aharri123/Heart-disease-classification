## Heart Disease Classification ##


### Business Goal ###

We'll be working with the largest hospital in Massachusetts (The Massachusetts General Hospital). Using various classification algorithms, we'll determine which algorithm provides the most accurate predictions for whether a patient is at risk in 10 years for coronary heart disease (CHD). This will in turn help the hospital create a treatment/preventative plan for at-risk patients early on, and hopefully prevent CHD from developing.





Each attribute is a potential risk factor. There are both demographic, behavioral and medical risk factors.

  Demographic:
  
* male: male (1) or female (0)
* Age: Age of the patient
  
  Behavioral:
• education: Less than High School and High School degrees (0) or College Degree and Higher (1)
• currentSmoker: Whether the patient is a current smoker (1) or not (0)
• cigsPerDay: the number of cigarettes that the person smoked on average in one day. 

  Medical History:
• BPMeds: Whether patient was on blood pressure medication (1) or not (0)
• prevalentStroke: Whether the patient had previously had a stroke (1) or not (0)
• prevalentHyp: Whether the patient was hypertensive (1) or not (0)
• diabetes: Whether the patient had diabetes (1) or not (0)
  
  Medical(current):
• totChol: total cholesterol level
• sysBP: systolic blood pressure
• diaBP: diastolic blood pressure
• BMI: Body Mass Index
• heartRate: heart rate
• glucose: glucose level
  
  Target Variable:
• TenYearCHD: 10 year risk of coronary heart disease or CHD (“1” means “Yes”, “0” means “No”)
