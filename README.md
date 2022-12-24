# Predict-Seasonal-Flu-Vaccine

Maryam Ghaffari
<p align="center">
<img src="https://user-images.githubusercontent.com/101681195/206234077-c82c5a0e-abd4-4676-bb6d-0858ad5ee13c.png">
</p>

# Introduction
The COVID-19 pandemic is a global outbreak of a new coronavirus that is very different from current and recently circulating human seasonal influenza viruses. Vaccines are a critical public health measure to fight infectious diseases like COVID-19. They provide immunization for individuals, and enough immunization in a community can further reduce the spread of diseases through "herd immunity." As the world struggles to vaccinate the global population against COVID-19, understanding how people’s backgrounds, opinions, and health behaviors are related to their personal vaccination patterns can provide guidance for future public health efforts.

# Problem Statement and Mission
Vaccines for H1N1 were first publicly available in the United States in October 2009, when the United States government began a vaccination campaign. U.S. Department of Health & Human Services collected the national 2009 H1N1 Flu Survey data to monitor vaccination rates during that campaign. This phone survey asked people whether they had received H1N1 and seasonal flu vaccines, in conjunction with the information they shared about their lives, opinions, and behaviors. U.S. Department of Health & Human Services has commissioned us to predict whether people got H1N1 and seasonal flu vaccines using data collected in the National 2009 H1N1 Flu Survey. My task is to provide accurate predictions for the people who receive the seasonal vaccine or not. I will conduct this task by doing data wrangling on the Flu survey data and generating classification models which predict with high accuracy whether the survey respondent received the seasonal flu vaccine. 

#  Evaluation Metrics
The model will be a ***binary classifier***, meaning that there are two potential classes (receiving and not receiving vaccines) that can be placed. If the model incorrectly predicts a receiving vaccine's state, I am more concerned with false positives than false negatives. Models that predict that some people are vaccinated while others do not may expose communities to the risk of low vaccination coverage. However, if the model predicted that people would not be vaccinated while they vaccinated, the health system would allocate resources to problems that do not currently exist, and those resources could be used for another segment of society. Therefore, for the purposes of this work, a ***low false-positive*** rate has more value than a low false-negative rate. ***Precision*** and ***recall*** are two of the most basic evaluation metrics available to us. Precision is one of the most basic evaluation metrics to quantify the performance of classifiers when False Positives are more costly than False Negatives. Precision measures how precise the predictions are, while Recall indicates what percentage of the classes we're interested in was actually captured by the model (True Positive Rate). On the other hand, ***accuracy*** is the most common metric for classification that provides a complete picture of the model's overall performance. The ***evaluation metrics*** that used in this study are defined as:

***Table 1. List of metrics and their definitions***
$$\text{Metric}$$ | $$\text{Formola} $$
:---------|:-------------
$$\text{Accuracy}$$ | $$\frac{\text{Number of True Positives + Number of True Negative}}{\text{Total Observation}}$$
$$\text{Precision}$$| $$\frac{\text{Number of True Positives}}{\text{Number of Predicted Positives}}$$
$$\text{Recall}$$ | $$\frac{\text{Number of True Positives}}{\text{Number of Actual Total Positives}}$$
$$\text{F1}$$ | $$2\frac{\text{Precision x Recall}}{\text{Precision + Recall}}$$
                                 

# Methodology
The general research strategy in this project is to use the OSEMN framework on the survey dataset. The process includes the below steps:

 - Obtain data: The very first step of the project is to obtain data. We obtain the data from the National 2009 H1N1 Flu Survey collected to monitor vaccination rates during that campaign. Obtaining data starts with importing needed libraries.
 - Scrub:   The second step is to make data operational which is dealing with messy data. This step includes dealing with missing values, inconsistent formatting, malformed records, or nonsensical outliers.
 - Explore: This step will help stakeholders to get accurate, actionable insights from our data analytic.
 - Model: In this step we use classification to identify values.
 - iNterpret: The most crucial step of a data science project is interpreting models and data. In this step, the results and insights represent for non-technical audiance. 
 
 # Exploration
 Explore the data start by inspecting some analytical questions. This step includes below substeps:

- Inspect the data and its properties: Different data types like numerical data, categorical data, ordinal and nominal data require different treatments.
- Compute descriptive statistics: Extract features and test significant variables.
- Data visualization: Identify significant patterns and trends in the data.

The below questions might help to have better insight into the database.
## Question 1. What is the relationship between demographic information and receiving vaccine?
To answer this question, some demographic information were categorized on the basis of being vaccinated or not. Then the results were plotted.


 ![image](https://user-images.githubusercontent.com/101681195/206749743-ccd25525-8cdf-4b69-a764-4dff40176de1.png)

***Fig 1. Correlations between demographic features and vaccination***

>Examination of the dataset revealed that several traits were predictive of individual vaccination patterns. For example, gender and marital status did not affect individual vaccination patterns, whereas age, race, education and employment status did. This plot showed demographic features are correlated with vaccination.


# Model Interpretation
In order to find the best model that can predict values with high accuracy, I run a Sci-Kit learn pipeline on several models [1].The following metrics results help to choose the best model to perform hyperparameter tuning, and finally make predictions on the original test set.

***Table 2. Compering evaluation metrics in different models and XGBoost***
![image](https://user-images.githubusercontent.com/101681195/209416293-06e48532-80de-49fa-9e5d-272ce0c5ab59.png)





It can be seen that most of the models had accuracy levels higher than 70 %, with the best performing being Gradient Boosting and Ada Boost, two powerful ensemble methods. Since Extreme Gradient Boosting (XGBoost) is a more regularized form of Gradient Boosting it was chosen to hyperparameter tuning and make a prediction on the test sets. The model achieved an accuracy rating of 83.37 % in the traning sets and accuracy rating of 77.44 % in test sets which is higher than other models. This model was able to maintain a relatively low false positive rate. The resulting confusion matrix was showed below:


![image](https://user-images.githubusercontent.com/101681195/209416445-88308d4c-d243-494a-a637-5a0a98a75533.png)



***Fig 4. Confusion matrix results for XGBoost model on test set beside feature importances.***


>Regarding feature importance, the XGBoost Classifier concluded that people's openinon about efficacy and risk of vaccination were the most important features for predicting vaccination pattern. The doctor recommendation was also a valuable feature that used to explore data. Two other features were also considered most important were age and race.

## How might doctor's recommendations change people's attitudes towards vaccination?

According to the feature importance results, the role of people's mindset in deciding whether to vaccinate or not is likely to be more specific. A doctor's recommendation is also an important feature. By examining the relationship between people's opinions and physician recommendations, the role of physician recommendations can be clarified. 


![image](https://user-images.githubusercontent.com/101681195/209416775-aea2df56-3d99-4a91-832f-2e6d9b3c09a2.png)



***Fig 2. Individuals' immunization patterns in relation to their attitudes to risk of getting sick with seasonal flu without vaccine,
the effectiveness of immunization and worriness of getting sick from taking seasonal flu vaccine the risks of immunization in settings with or without physician recommendations.***


>In the chart that shows people's opinion regarding the efficacy of vaccination it can be seen that physician recommendations can change the population's perception of vaccination, even in groups who strongly believed vaccination was not effective. Additionally, doctors may change an individual's opinion about the risks of vaccination. Doctors' recommendation also can enhance vaccination even in groups that have very worry about getting sick from taking seasonal flu vaccine. 




# Recommendation
People's opinions about vaccination are an important predictor of vaccination patterns in societies. Raising public awareness of the benefits of vaccination is key to increasing vaccination coverage. Physician recommendations, on the other hand, can make a big difference in people's attitudes toward vaccination. Below are recommendations that the U.S. Department of Health and Human Services may make to improve vaccination coverage:
>- Put more effort into groups that are more likely to be unvaccinated, such as men, blacks and Hispanics.
>- Ask doctors for advice about immunizations during the patients' routine check-up.


  ## Repository Structure


```
├── Code : final_student.ipynb includ modeling
├── Data : Data used for modeling, includes training_set_features.csv and training_set_labels.csv files
├── Images : Images used in Phase 3 Project Presentation.pdf and README
├── Phase 3 Project Presentation.pdf : Presentation for stakeholders
└── README.md : Project information and repository structure
```
