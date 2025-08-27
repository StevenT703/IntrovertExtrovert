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
![Screenshot1](/Screenshots/Screenshot1.png)



## Exploratory data analysis
The dataset was assessed according to the data quality dimensions in Gov.uk (2020). Here the analyst shows application of the ‘completeness’ and ‘validity’ dimensions.

The original dataset was opened in Microsoft Excel to understand and visualise the data.


![Screenshot2](/Screenshots/Screenshot2.png)



Filters were applied to the dataset and blank values were identified in all seven columns.    

![Screenshot3](/Screenshots/Screenshot3.png)
 


Each numerical column has a minimum and maximum value. The data was checked to ensure that values were within the constraints.      

![Screenshot4](/Screenshots/Screenshot4.png)
  


In Python, the number of nulls was investigated.   

![Screenshot5](/Screenshots/Screenshot5.png)
 


There are null values in each column. The choice was taken to remove any rows with null values, resulting in 423 rows being removed. 

![Screenshot6](/Screenshots/Screenshot6.png)
  


## Encoding
String values are encoded into binary values and original columns are dropped. 

![Screenshot7](/Screenshots/Screenshot7.png)


![Screenshot8](/Screenshots/Screenshot8.png)


![Screenshot9](/Screenshots/Screenshot9.png)
   


The data is checked again for any string values, none are found. Here the analyst can again see that all rows are ‘non-null’. 

![Screenshot10](/Screenshots/Screenshot10.png)
 


Using the Seaborn library, the analyst now visualises the balancing of the outcome variable. The overall dataset is not overly unbalanced.

![Screenshot11](/Screenshots/Screenshot11.png)



## Test/Train split
The first step in the data analysis was to split the data into test and train sets and ensure that a balanced outcome variable is present in both sets, which is the case. 

![Screenshot12](/Screenshots/Screenshot12.png)
  


Further EDA is then performed on the train set.

Using the Seaborn heatmap, the analyst shows the correlation that the outcome has with the features. There appears to be strong correlation with most variables - both positive and negative. 
 

![Screenshot13](/Screenshots/Screenshot13.png)
  

# Results
Once the EDA was completed, the analyst built the model and assessed the results.

The analyst identified balanced accuracy as the best measure for the study. This is because the study places equal importance on both negative and positive outcomes. If F1 score was used, only the positive outcomes would be measured. 

Balanced accuracy has been used over accuracy to ensure that even if an unbalanced dataset was used for any retraining of the model, it would still provide results that could be relied upon (Couto,2024).    

![Screenshot14](/Screenshots/Screenshot14.png)
 

The model has a balanced accuracy of 91.37%, meaning that the model is accurately predicting the outcome variable in 91.37% of instances. 

A confusion matrix was produced to see these scores more granularly.
![Screenshot15](/Screenshots/Screenshot15.png)
  


The analyst could see that the true positives value is just slightly higher than true negatives, both being very high. It could also be seen that predicting somebody is introverted when they are in fact extroverted, is just slightly higher than the other way around.

An ROC curve is also used to visualise these results.


![Screenshot16](/Screenshots/Screenshot16.png)
   

The ROC curve shows positive results with the area under curve score being 0.91.

The coefficients of each feature can be seen below.
![Screenshot17](/Screenshots/Screenshot17.png)
  


Being drained after socialising and having stage fear is a strong indicator that the outcome would result in an introverted personality type. It is only ‘time spent alone’ that has a positive importance, meaning that an increase in this value will increase the likeliness for an outcome of ‘extroverted’.

## Model comparison
To validate the use of the logistic regression model, the LazyClassifier engine was used to compare the model to others. 
![Screenshot18](/Screenshots/Screenshot18.png)
 


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



