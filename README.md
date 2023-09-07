![ReadME_header][project_logo]
---

<p align="center">
  <a href="#Objective">Objective</a> •
  <a href="#About the Dataset">About the Dataset</a> •
  <a href="#Repository Directories">Repository Directoriese</a> •
  <a href="#Analysis Steps">Analysis Steps</a> •
  <a href="#Results">Results</a> •
</p>

## Objective
The goal here is to identify any trends among a student's demographic profile (race, age, socioeconomic status, etc) and their academic performance. 



---


## About the Dataset
The analysis is based on a dataset provided by the buisness intelligence department at Metropolitan State University of Denver. All students and professors in the dataset have been anonymized.

The data sets contains various demographic information for thousands of MSU Denver students as well as academic performance indicators, such as term GPA and whether that student has dropped out before their graduation. I used their GPA as the main indicator of academic success through out this analysis.

---


## Repository Directories
#### Initial_Data
- Contains the initial csv that was provided before it has been cleaned.
#### Data_Cleaning
- An R markdown file that contains the code used for data cleaning code that is commented to show my thought process throughout the data cleaning process
#### Data_Analysis
- An R markdown file that contains the code used for data cleaning code that is commented to show my thought process throughout the data analysis process
#### Final_Data
- Contains the cleaned data set in csv format
#### Data_Visualization.md
- A markdown file with a snapshot of tableau public dashboard as well as a link to the interactive dashboard.

---


## Analysis Steps

![pipeline_grades][workflow_graphic]

#### Step 1: Identify Goal/ Question
- Question: Does a student's demographic profile influence their academic profile?
#### Step 2: Gather Data
- Data obtained directly from MSU Denver Business Intelligence
#### Step 3: Data Cleaning
- Change data types. Many variables that should have been numerical (such as GPA, age, etc) were actually in char format. My first stepp was to transform these into numerical sata types. I also changed char data types into factors, as this mad it easy to count each input in the categorical variables (how many Males vs. Females).
- Imputation: A significant hurdle to the analysis of this dataset was missing data. I proceeded to Impute missing data with the following steps:
  - Convert certain values to 'NA' (how R recognized a value is missing). Certain values were technically missing, but was input as 'Unkown' or 'unk'. This is a problem because R                would recognize this as another level of the factor variables rather than an empty value. This would prevent my imputation function from replacing them with real values.
  - Extract all varibles that contain missing data and calculate what percent of these columns are missing. Two columns ('total_hrs_earned' and 'act_score') were not imputed as it               contained too many missing values (>50%) and was not used in any analysis.
  - used mice() function in R to impute data
- Recode Some Variables: Some variables were recoded to prepare for analysis. For example, I used the term_GPA to classify a students grade as 'Good', 'Fair', and 'Poor' in a new variable calles 'Grades.' I also converted many two level categorical variables in binary to prepare for regression model.
#### Step 4: Data Analysis
- Used backward stepwise procedure and VIF to create a regression model. The main purpose of the regression model is to identify the most important predictors for GPA as well as           their trands.
#### Step 5: Data Visualization
- Used Tableau to create a dashboard containing the most important trends among GPA for seperate student demographics.

---


## Results
- Race seems to be the most influential predictor of GPA out of all other demographic subgroups
- Black students are the most impacted by their race in terms of GPA
- Other important factors include Age, Sex, First-Gen Status (first-gen = first in family to attend college), and whether the student is a transfer or first-time-freshman.
- While there seems to be some significant trends amongs certain demographic information and GPA, a student's demographic profile seems to only account for 6% of all factors effecting GPA.

  [![dashboard image][dashboard_image]][dashboard_link]





  <!-- Image Links -->

[project_logo]: Proj_images/ReadME_header.jpg
[dashboard_image]: Proj_images/grades_dashboard.jpg
[workflow_graphic]: Proj_images/pipeline_grades.jpg


<!-- External Links -->
[dashboard_link]: https://public.tableau.com/app/profile/gabby.guinard/viz/StudentDemographicsandAcademicSuccess/Dashboard1








