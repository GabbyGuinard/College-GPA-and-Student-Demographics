![ReadME_header](https://github.com/GabbyGuinard/College-GPA-and-Student-Demographics/assets/129466367/2465b88a-8601-4da7-8928-e88facfcd733)
---


## Objective
The goal here is to determine if a student's demographic profile (race, age, socioeconomic status, etc) tends to influence their academic performance. 



---
## About the Dataset
The analysis is based on a dataset provided by the buisness intelligence department at Metropolitan State University of Denver. All students and professors in the dataset have been anonymized.

The data sets contains various demographic information for thousands of MSU Denver students as well as academic performance indicators, such as term GPA and whether that student has dropped out before their graduation. I used their GPA as the main indicator of academic success through out this analysis.

---
## Repository Directories
#### 01_initialData
Contains the initial csv that was provided before it has been cleaned.
#### 02_dataCleaning
Contains 2 files:
1. A raw R file that contains the code used for data cleaning with light commentary
2. A markdown file that contains snippets of the above R code as well as extensive commentary to show my thought process throughout the data cleaning process
#### 03_Analysis
Contains 2 files:
1. A raw R file that contains the code used for data analysis with light commentary
2. A markdown file that contains snippets of the above R code as well as extensive commentary to show my thought process throughout the data analysis process
#### 04_finalData
Contains the cleaned data set in csv format
#### 05_visualization
Contains a markdown file with a snapshot of tableau public dashboard as well as a link to the interactive dashboard.



---
## Steps of Analysis

![pipeline_grades](https://github.com/GabbyGuinard/College-GPA-and-Student-Demographics/assets/129466367/fb9604a1-4932-4d16-86d4-7a691e533323)

#### Step 1: Identify Goal/ Question
Question: Does a student's demographic profile influence their academic profile?
#### Step 2: Gather Data
Data obtained directly from MSU Denver Business Intelligence
#### Step 3: Data Cleaning
  1. Change data types. Many variables that should have been numerical (such as GPA, age, etc) were actually in char format. My first stepp was to transform these into numerical sata types. I also changed char data types into factors, as this mad it easy to count each input in the categorical variables (how many Males vs. Females).
  2. Imputation: A significant hurdle to the analysis of this dataset was missing data. I proceeded to Impute missing data with the following steps:
   - Convert certain values to 'NA' (how R recognized a value is missing). Certain values were technically missing, but was input as 'Unkown' or 'unk'. This is a problem because R would       recognize this as another level of the factor variables rather than an empty value. This would prevent my imputation function from replacing them with real values.
   - Extract all varibles that contain missing data and calculate what percent of these columns are missing. Two columns ('total_hrs_earned' and 'act_score') were not imputed as it           contained too many missing values (>50%) and was not used in any analysis,
   - used mice() function in R to impute data
3. Recode Some Variables: Some variables were recoded to prepare for analysis. For example, I used the term_GPA to classify a students grade as 'Good', 'Fair', and 'Poor' in a new variable calles 'Grades.' I also converted many two level categorical variables in binary to prepare for regression model.
#### Step 4: Data Analysis
  1. Use cleaned dataset to create new table containing various statistics to identify trends.
  2. Used backward stepwise procedure and VIF to create a regression model. The main purpose of the regression model is to identify the most important predictors for GPA.
#### Step 5: Data Visualization
  1. Used Tableau to create a dashboard containing the most important trends among GPA for seperate student demographics.



## Results
- Race seems to be the most influential predictor of GPA out of all other demographic subgroups
- Black students are the most impacted by their race in terms of GPA
- Other important factors include Age, Sex, First-Gen Status (first-gen = first in family to attend college), and whether the student is a transfer or first-time-freshman.
- While there seems to be some significant trends amongs certain demographic information and GPA, a student's demographic profile seems to only account for 6% of all factors effecting GPA.

  ![grades_dashboard](https://github.com/GabbyGuinard/College-GPA-and-Student-Demographics/assets/129466367/85815501-b7ba-48a4-af6a-7d0c7a49d1b5)







