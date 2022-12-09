# Predict-Seasonal-Flu-Vaccine

Maryam Ghaffari
![image](https://user-images.githubusercontent.com/101681195/206234077-c82c5a0e-abd4-4676-bb6d-0858ad5ee13c.png)

# Introduction
The COVID-19 pandemic is a global outbreak of a new coronavirus that is very different from current and recently circulating human seasonal influenza viruses. Vaccines are a critical public health measure to fight infectious diseases like COVID-19. They provide immunization for individuals, and enough immunization in a community can further reduce the spread of diseases through "herd immunity." As the world struggles to vaccinate the global population against COVID-19, understanding how people’s backgrounds, opinions, and health behaviors are related to their personal vaccination patterns can provide guidance for future public health efforts.

# Problem statement and mission
Vaccines for H1N1 were first publicly available in the United States in October 2009, when the United States government began a vaccination campaign. U.S. Department of Health & Human Services collected the national 2009 H1N1 Flu Survey data to monitor vaccination rates during that campaign. This phone survey asked people whether they had received H1N1 and seasonal flu vaccines, in conjunction with the information they shared about their lives, opinions, and behaviors. U.S. Department of Health & Human Services has commissioned us to predict whether people got H1N1 and seasonal flu vaccines using data collected in the National 2009 H1N1 Flu Survey. My task is to provide accurate predictions for the people who receive the seasonal vaccine or not. I will conduct this task by doing data wrangling on the Flu survey data and generating classification models which predict with high accuracy whether the survey respondent received the seasonal flu vaccine. 

#  Evaluation Metrics
The model will be a ***binary classifier***, meaning that there are two potential classes (receiving and not receiving vaccines) that can be placed. If the model incorrectly predicts a receiving vaccine's state, I am more concerned with false positives than false negatives. Models that predict that some people are vaccinated while others do not may expose communities to the risk of low vaccination coverage. However, if the model predicted that people would not be vaccinated while they vaccinated, the health system would allocate resources to problems that do not currently exist, and those resources could be used for another segment of society. Therefore, for the purposes of this work, a ***low false-positive*** rate has more value than a low false-negative rate. ***Precision*** and ***recall*** are two of the most basic evaluation metrics available to us. Precision is one of the most basic evaluation metrics to quantify the performance of classifiers when False Positives are more costly than False Negatives. Precision measures how precise the predictions are, while Recall indicates what percentage of the classes we're interested in was actually captured by the model (True Positive Rate). On the other hand, ***accuracy*** is the most common metric for classification that provides a complete picture of the model's overall performance. The ***evaluation metrics*** that used in this study are defined as:

$$\text{Metric}$$ | $$\text{Formola} $$ 
:---------|:-------------
$$\text{Accuracy}$$ | $$\frac{\text{Number of True Positives + Number of True Negative}}{\text{Total Observation}}$$
$$\text{Precision}$$| $$\frac{\text{Number of True Positives}}{\text{Number of Predicted Positives}}$$
$$\text{Recall}$$ | $$\frac{\text{Number of True Positives}}{\text{Number of Actual Total Positives}}$$
$$\text{F1}$$ | $$2\frac{\text{Precision x Recall}}{\text{Precision + Recall}}$$
                                         

# Methodology
The general research strategy in this project is to use the OSEMN framework on the King County House Sales dataset. The process includes the below steps:

 - Obtain data: The very first step of the project is to obtain data. We obtain the data from We will look at data from the National 2009 H1N1 Flu Survey collected to monitor vaccination rates during that campaign. Obtaining data starts with importing needed libraries
 - Scrub:   The second step is to make data operational which is dealing with messy data. This step includes dealing with missing values, inconsistent formatting, malformed records, or nonsensical outliers.
 - Explore: This step will help stakeholders to get accurate, actionable insights from our data analytic
 - Model: In this step we use regression and predictions for forecasting future values, and classification to identify, and clustering to group values.
 - iNterpret: The most crucial step of a data science project is interpreting models and data. In this step, the results and insights represent for non-technical audiance. 
 
 # Exploration
 Explore the data start by inspecting some analytical questions . This step includes below substeps:

 - Inspect the data and its properties: Different data types like numerical data, categorical data, ordinal and nominal data require different treatments.
- Compute descriptive statistics: Extract features and test significant variables
- Data visualization: Identify significant patterns and trends in our data

The below questions might help better to have insight into our database
## Qustion 1. What is the relationship between demographic information and receiving vaccine?



 

