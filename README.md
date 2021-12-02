# Predicting-Features-of-Diabetes-using-Machine-Learning

Team: Zainab Sherani, Amina Lampkin, Intisar Muhammad

## Introduction
According to the Centers for Disease Control and Prevention (CDC), approximately 32.4 
million people in the United States have diabetes which is about 10.5% percent of the population (National Diabetes Statistics Report, 2020). Diabetes is a chronic disease that millions of people live with and learn to manage. Type 1 diabetes is a condition where a person’s pancreas has trouble producing insulin to process sugar in their body. Type 2 diabetes is when a person’s body doesn't use insulin properly and is much more common in diabetes patients. Scientists are unsure of what factors specifically cause the blood glucose imbalance. 

The myth we decided to study was that diabetes is more prevalent for those who identify as low-income, minority, and over 65 years old. There is truth to these assumptions. The American Diabetes Association estimates that 26.8% of Americans age 65 years or older have diabetes and that racial minorities are also at higher risk of having it compared to non-Hispanic Whites (ADA, 2020). We want to see which traits can predict if someone will have diabetes. In addition to income, race/ethnicity, and age, we will also use other markers associated with those who have diabetes such as education, employment status, and rental versus ownership of their home. These features are all related to stereotypes of people who are low-income. 

## Data Cleaning 
The Behavioral Risk Factor Surveillance System (BRFSS) survey is a questionnaire completed via telephone that looks into the “health-related risk behaviors and events, chronic health conditions, and use of preventive services” of Americans (CDC, 2020). It is administered by state health departments throughout the year in all 50 states, District of Columbia, and three US territories with additional technical support provided by the Centers for Disease Control and Prevention. This survey has responses from over 400,000 adults making it one of the largest ongoing health-related surveys. The results from these surveys are used to track health objectives and plan health programs. 

We used results from the 2015 survey that were compiled into a CSV by the Centers for Disease Control and Prevention on Kaggle (Kaggle, 2017). To limit the size of the dataset which had over 400,000 rows, we decided to look at surveys via cellphone from D.C., Maryland,  and Virginia (colloquially known as “the DMV”). The final dataset had 800 rows, 400 rows from those who had diabetes and 400 of those who did not. We removed rows that represented women who had gestational diabetes. We selected 11 features that were stereotypes associated with those who have diabetes. For example, to test whether certain races or socioeconomic levels were at a higher risk, we used the X_RACE and INCOME2 variables, respectively. The following is a list of features we used. 

SEX
Where 1 represents male and 2 represents female

INCOME2 
Where 1 represents someone who makes less than $10,000, 2 represents less than $15,000, etc. to 8 which represents someone who makes $75,000 or more

X_RACE 
Where 1 represents White non-Hispanic, 2 represents Black non-Hispanic, etc. to 8 which represents Hispanic

DIABETE3 
“(Ever told) you have diabetes”
Where 1 represents you have it and 3 is that you don’t have it. We filtered for these two responses 

EDUCA 
“What is the highest grade or year of school you completed?”
Where 1 represents “Never attended school or only kindergarten,” 2 represents “Grades 1 through 8 (Elementary) etc. to 6 which represents “College 4 years or more (College graduate)” 

RENTHOM1 
“Do you own or rent your home? (Home is defined as the place where you live most of the time/the majority of the year.)”
Where 1 represents “Own,” 2 represents “Rent” and 3 represents “Other arrangement”

EMPLOY1
“Are you employed, looking for work, etc.?”
Marked 1-9 where 1 represents employed for wages, and 9 represents refused

X_RFMBMI5
“Adults who have a body mass index greater than 25.00 (Overweight or Obese)”
Where 1 represents “No” and 2 represents “Yes”

CHILDREN
The number of children under 18 living at home

HHADULT
The number of adults living at home

HOUSENUM
The sum of HHADULT and CHILDREN

## Model Results 
Using Weka, we decided to use a pruned decision tree with the REPTree classifier. We tested several other models such as the multilayer perceptron and naive-bayes. However, the pruned decision tree produced the best results, especially when it came to the number of correctly classified instances. 
With the REPTree classifier, the model accurately classified 66.5 percent instances, while 33.5 percent were incorrectly classified. While this is a great start, there is room for improvement. For example, the relative absolute error for the model was 89.4952 percent, indicating that the model was nearly randomly guessing how to classify each instance. The low Kappa statistic supports this phenomenon. The area under the curve (output as the ROC area) indicates that, overall, 70.7 percent of the time an instance will be classified correctly. Again, while this is pretty good, it must be taken with a grain of salt since we know from the Kappa statistic and RAE the model may not really be taking into account the given variables to inform that decision.  
The model had an overall precision and recall of 66.5 percent for each category. The precision rate describes how many items we classified correctly out of how many were classified in total. Recall asks how many of the items that should have been classified did the model actually capture. 

## Conclusion 
The confusion matrix shows that the model did about the same in predicting those who have diabetes and those who did not. According to our model, we can conclude two things. First, the features we used were either not good markers or a combination of using all of them were not good at predicting those who have diabetes. Second, there is some truth that certain features were likely to make someone high-risk. 
a
b
← classified as
258
142
a = Y
126
274
b = N

It’s highly likely that a larger dataset would give different predictive modeling results. The larger dataset would be more representative of the population and could be used to predict whether someone with particular features would be at a higher risk of diabetes. If this project was to be repeated, a larger dataset should be used for increased accuracy. With increased accuracy, models of a similar premise and background can be useful for healthcare providers seeking to take proactive measures to identify at-risk communities for certain diseases. Additionally, with a more developed algorithm, a similar model could possibly help those who are diagnosed as pre-diabetic. If the right lifestyle changes are made, there is a chance that the pre-diabetic diagnosis can be reversed.


## Works Cited

Statistics About Diabetes | ADA. https://www.diabetes.org/resources/statistics/statistics-about-diabetes. Accessed 1 May 2020.

Behavioral Risk Factor Surveillance System | Kaggle. https://www.kaggle.com/cdc/behavioral-risk-factor-surveillance-system#2015.csv. Accessed 30 Apr. 2020.
CDC - BRFSS - BRFSS Frequently Asked Questions (FAQs). https://www.cdc.gov/brfss/about/brfss_faq.htm. Accessed 30 Apr. 2020.
National Diabetes Statistics Report 2020.
        https://www.cdc.gov/diabetes/pdfs/data/statistics/national-diabetes-statistics-report.pdf. 
        Accessed 30 Apr. 2020.   

