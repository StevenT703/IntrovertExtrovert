# Executive summary
The study aimed to provide a method of predicting an introverted or extroverted personality type based upon the answering of key questions. 
A logistic regression model was developed to predict the result following the answering of seven key questions which produced a balanced accuracy of 91.37%.
The model was deemed successful in making this prediction, but methods in which the model and its validity can be improved have been suggested.


# Introduction
The study tests the hypothesis that personality type could be identified through the answering of key questions. It aimed to provide a data-driven method of self-identifying a personality type into the categories of introverted and extroverted.

# Data Infrastructure and tools

The model has been built using a dataset available on Kaggle and was chosen due to its comprehensive size. This dataset contains 2,900 rows and 8 columns of structured data and was originally gathered through a project utilising Google Forms.
## Method used
The analyst used a logistic regression model to complete the project. This has been used to estimate how probable it is that a Google Form submission belongs to a particular outcome (Geron, 2022). Whether the person answering the survey is introverted or extroverted.

There are a number of applications that the analyst has chosen to use for this project.

## Microsoft Excel
Microsoft Excel was used to help understand the dataset. It was chosen due to the analyst’s familiarity with this application and because the dataset is in CSV format which is native to Microsoft Excel. Using Microsoft Excel, the analyst completed the first part of their exploratory data analysis (EDA) in an application that they are comfortable with, using it to visualise the data and the data types that have been used. 
## Python
Python and several Python libraries (such as Seaborn and Pandas), accessed through Jupyter Notebooks, have been used for this study. Firstly, it was used to complete the EDA and then to cleanse the dataset. Three columns in the dataset use strings and Python was used to encode these values before building the model. Once completed, the logistic regression model was built in Python.

Python provides the benefit of allowing the model to be used again in the event of further data becoming available.

 
# Method
## ETL
The analyst has used the following process when preparing their data for the model.

<img width="579" height="182" alt="image" src="https://github.com/user-attachments/assets/ec493665-4921-44f1-b6ff-94e122437bb3" />


## Exploratory data analysis
The dataset was assessed according to the data quality dimensions in Gov.uk (2020). Here the analyst shows application of the ‘completeness’ and ‘validity’ dimensions.

The original dataset was opened in Microsoft Excel to understand and visualise the data.



<img width="940" height="246" alt="image" src="https://github.com/user-attachments/assets/c4d981f5-7060-4735-bba6-24d58fae3410" />  


Filters were applied to the dataset and blank values were identified in all seven columns.    


<img width="407" height="406" alt="image" src="https://github.com/user-attachments/assets/8bb3bd34-1572-4641-b728-d77c004b2ef8" />    


Each numerical column has a minimum and maximum value. The data was checked to ensure that values were within the constraints.      


<img width="296" height="458" alt="image" src="https://github.com/user-attachments/assets/4dd7d8c3-228c-442b-967c-0470ed900616" />    


In Python, the number of nulls was investigated.   


<img width="509" height="314" alt="image" src="https://github.com/user-attachments/assets/e7b52260-0a6b-4f13-9377-059bc7e4694b" />    


There are null values in each column. The choice was taken to remove any rows with null values, resulting in 423 rows being removed. 


<img width="432" height="438" alt="image" src="https://github.com/user-attachments/assets/1ca25f43-6798-4627-b5d7-9fdc172ec3d9" />    


## Encoding
String values are encoded into binary values and original columns are dropped. 


<img width="940" height="448" alt="image" src="https://github.com/user-attachments/assets/46ee6838-0963-4bc6-824b-fb839d96b635" />  


<img width="940" height="439" alt="image" src="https://github.com/user-attachments/assets/29fc32a6-5093-498a-b8ce-b28dbe344d92" />  


<img width="940" height="445" alt="image" src="https://github.com/user-attachments/assets/c49b93ae-778d-46ba-93b7-c069b540e52b" />    


The data is checked again for any string values, none are found. Here the analyst can again see that all rows are ‘non-null’. 


<img width="633" height="427" alt="image" src="https://github.com/user-attachments/assets/4717fbef-a5ab-46b8-933d-9344f2aca260" />    


Using the Seaborn library, the analyst now visualises the balancing of the outcome variable. The overall dataset is not overly unbalanced.


<img width="764" height="644" alt="image" src="https://github.com/user-attachments/assets/2aacd46e-fb6d-494f-88d6-be6169bc15a2" />    


## Test/Train split
The first step in the data analysis was to split the data into test and train sets and ensure that a balanced outcome variable is present in both sets, which is the case. 


<img width="940" height="316" alt="image" src="https://github.com/user-attachments/assets/7c78ef9a-cdaa-4d50-95a3-e8d5fbb45b63" />    


Further EDA is then performed on the train set.

Using the Seaborn heatmap, the analyst shows the correlation that the outcome has with the features. There appears to be strong correlation with most variables - both positive and negative. 
 


<img width="725" height="638" alt="image" src="https://github.com/user-attachments/assets/331c064f-98fc-4aad-8e34-29c4fcdb3c08" />  

# Results
Once the EDA was completed, the analyst built the model and assessed the results.

The analyst identified balanced accuracy as the best measure for the study. This is because the study places equal importance on both negative and positive outcomes. If F1 score was used, only the positive outcomes would be measured. 

Balanced accuracy has been used over accuracy to ensure that even if an unbalanced dataset was used for any retraining of the model, it would still provide results that could be relied upon (Couto,2024).    


<img width="870" height="339" alt="image" src="https://github.com/user-attachments/assets/62050b90-f48e-4e57-bbf6-f259aa532534" />  

The model has a balanced accuracy of 91.37%, meaning that the model is accurately predicting the outcome variable in 91.37% of instances. 

A confusion matrix was produced to see these scores more granularly.

<img width="940" height="734" alt="image" src="https://github.com/user-attachments/assets/85f4225e-ded0-40f6-bb61-3695f012461d" />    


The analyst could see that the true positives value is just slightly higher than true negatives, both being very high. It could also be seen that predicting somebody is introverted when they are in fact extroverted, is just slightly higher than the other way around.

An ROC curve is also used to visualise these results.



<img width="902" height="706" alt="image" src="https://github.com/user-attachments/assets/63b14029-8bc3-43c2-a85e-7027a190bb27" />    

The ROC curve shows positive results with the area under curve score being 0.91.

The coefficients of each feature can be seen below.

<img width="940" height="455" alt="image" src="https://github.com/user-attachments/assets/574323d7-525f-481a-9c7f-0bd4f6b28f55" />    


Being drained after socialising and having stage fear is a strong indicator that the outcome would result in an introverted personality type. It is only ‘time spent alone’ that has a positive importance, meaning that an increase in this value will increase the likeliness for an outcome of ‘extroverted’.

## Model comparison
To validate the use of the logistic regression model, the LazyClassifier engine was used to compare the model to others. 

<img width="772" height="580" alt="image" src="https://github.com/user-attachments/assets/ff887043-c6c6-4adf-9545-27e845197447" />    


From the results of this, it can be seen that the model used in this study is amongst the most well performing.

# Summary
The hypothesis set at the start of the study was to test that personality type could be identified through the answering of key questions. Balanced accuracy was set as the key metric of measuring the success of the model. With a balanced accuracy of 91.37%, it has been determined that the model can accurately predict personality type using the questions asked in the study.

The confusion heatmap provides visibility of the predictions, showing only small percentages of false positives and false negatives which are evenly split. The nature of the study means that small values in these categories are acceptable and do not invalidate the success of the model.

# Future improvements and recommendations
There are improvements that could be made to enhance this model. The dataset was initially collected as part of a student research project. This could introduce bias, such as:
-	The institutions that were used as part of the study – is this indicative of just students and students from these institutions only?
-	Location – answers to features such as ‘going outside’ could be impacted by the person’s location, weather and their responsibilities.
-	Culture – with countries such as Australia banning children under 16 from using social media, features such as ‘(social media) post frequency’ will be skewed.

To test potential bias, another dataset could be obtained that aims to remove this bias and the model accuracy then being tested again.

Two features, ‘social event attendance’ and ‘(social media) post frequency’ have little importance on the outcome. It would be useful to test whether removing these questions reduces the accuracy of the model. This would be similar to a study undertaken by So (2020), who, when predicting introverts and extrovert personality traits, reduced a dataset of 94 features to 10 features with only a 1% loss in accuracy.

Additionally, the use of Excel has the drawback of having to use multiple systems as the method progresses through Python instead and means that this part of the method is not automated. Furthermore, opening the data in an editable format opens the potential for the data to be accidentally amended.

In the EDA, it was decided to drop rows with nulls values. It may have been less destructive to impute values for any null values (Geron, 2022), something which is echoed in Scikit-Learn (2018) where it is stated that this is a better strategy. Geron (2022), explains how this can be done using the Scikit-Learn class ‘SimpleImputer’.


# Conclusion
The model has provided an accurate method of predicting personality types and, for this dataset at least, the hypothesis has been proven. Providing a model for this can help people to learn about their personality types and encourage them to investigate further into elements such as which learning styles and motivational techniques work best for them.

There are limitations to the dataset, however, and as such, further testing should be completed, and a larger dataset used to further validate the model. 


# References

Couto, M. (2024). A Data Scientist’s Guide to Balanced Accuracy - Train in Data’s Blog. Train in Data’s Blog. Available at: https://www.blog.trainindata.com/a-data-scientists-guide-to-balanced-accuracy/.

‌Geron, A. (2022). Hands-On Machine Learning With Scikit-Learn, Keras, And Tensorflow 3E. S.L.: O’Reilly UK Limited.

GOV.UK (2020) The Government Data Quality Framework. Available at https://www.gov.uk/government/publications/the-government-data-quality-framework/the-government-data-quality-framework (Accessed 20 August 2025).

Kapilavayi, R. (2025). Extrovert vs. Introvert Behavior Data. Kaggle.com. Available at: https://www.kaggle.com/datasets/rakeshkapilavai/extrovert-vs-introvert-behavior-data/data.

Scikit-Learn (2018). 6.4. Imputation of missing values — scikit-learn 0.22.2 documentation. scikit-learn.org. Available at: https://scikit-learn.org/stable/modules/impute.html.

So, C. (2020). Are You an Introvert or Extrovert? Accurate Classification With Only Ten Predictors. arXiv (Cornell University), 2, pp.693–696. 



