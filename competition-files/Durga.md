---
title: "Linear Regression Mini-competition"
output: github_document
---

### INPUT variables according to the survey
---
Reading the excel data and understanding the data, variables in survey
BASMID: A unique identifier for each record
ALLGRADEX: Grade level
EDCPUB: Education in public school (binary variable: 1 = Yes, 2 = No)
SCCHOICE: School choice (categorical variable: 1, 2, 3)
SPUBCHOIX: Public school choice (categorical variable: 1, 2, 3)
SCONSIDR: Considerations for school choice (categorical variable: 1, 2, 3, 4)
SCHLHRSWK: School hours per week
EINTNET: Engaged in internet activities (binary variable: 1 = Yes, 2 = No)
MOSTIMPT: Most important factor (categorical variable: 1, 2, 3, 4)
INTNUM: Number of internet-connected devices
SEENJOY: Enjoyment of school
SEGRADES: Satisfaction with grades
SEABSNT: Absenteeism (binary variable: 1 = Yes, 2 = No)
SEGRADEQ: Grade requirements
FSSPORTX: Participation in sports (binary variable: 1 = Yes, 2 = No)
FSVOL: Volunteering activities (binary variable: 1 = Yes, 2 = No)
FSMTNG: Parent-teacher meetings (binary variable: 1 = Yes, 2 = No)
FSPTMTNG: Parent participation in meetings (binary variable: 1 = Yes, 2 = No)
FSATCNFN: Attendance at school conferences (binary variable: 1 = Yes, 2 = No)
FSFUNDRS: Fundraising activities (binary variable: 1 = Yes, 2 = No)
FSCOMMTE: Participation in community activities (binary variable: 1 = Yes, 2 = No)
FSCOUNSLR: Counseling services at school (binary variable: 1 = Yes, 2 = No)
FSFREQ: Frequency of school communication
FSNOTESX: School notes received (binary variable: 1 = Yes, 2 = No)
FSMEMO: School memos received (binary variable: 1 = Yes, 2 = No)
FCSCHOOL: Child's school satisfaction (categorical variable: 1, 2, 3, 4)
FCTEACHR: Teacher satisfaction (categorical variable: 1, 2, 3, 4)
FCSTDS: Parent involvement in student's school (categorical variable: 1, 2, 3, 4)
FCORDER: Orderliness at home (categorical variable: 1, 2, 3, 4)
FCSUPPRT: Parental support (categorical variable: 1, 2, 3, 4)
FHHOME: Homeownership (binary variable: 1 = Yes, 2 = No)
FHWKHRS: Weekly work hours of the household
FHAMOUNT: Amount of housing expenses
FHCAMT: Monthly mortgage payment
FHPLACE: Location of the household
FHCHECKX: Housing check (binary variable: 1 = Yes, 2 = No)
FHHELP: Housing help received (binary variable: 1 = Yes, 2 = No
---


```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)
```

##Step1 : Load all the required libraries and check packages installed.

```{r}
library(tidyverse)
library(tidymodels)
library(stats)
#install.packages("tidyverse")
#install.packages("tidymodels")
#install.packages("ggplot2")
library(ggplot2)
library(readxl)
```

### Step2: load the excel data from local machine

```{r}
library(readxl)

Testdata <- read_excel("/Users/saranyat/Downloads/Dataset.xlsx",sheet = "curated_2019",n_max = 20)

Testdata

```

## To analyse the data and know the dimensions

```{r}
head(Testdata)

```
## TO remove the missing and bad data from the excel loaded data

```{r}
Testdata <- na.omit(Testdata)
```

### Determing the Target and predictor variables

- The factors that would impact the student success involves school choice
- family engagement in school activities and family engagement in homework
- According to the project requirement the following set of variables can be used as predictor and target variables - 
- Predictor Variables =SCCHOICE SCONSIDR FCSUPPRT FCSTDS FSNOTESX FSCOUNSLR FSPTMTNG
- Target Variables = ALLGRADEX SEGRADES SEGRADEQ
- CASE 1 Target Variables = ALLGRADEX

```{r}
#predictor variables as needed
X <- Testdata[, c("SCCHOICE","SCONSIDR", "FCSUPPRT", "FCSTDS", "FSNOTESX", "FSCOUNSLR", "FSPTMTNG")]

#Target variable

Y <- Testdata$SEGRADES

```


### Split the dataset into training and testing sets. 
- The training set will be used to train the regression model
- The testing set will be used to evaluate its performance.


```{r}
set.seed(123)  # For reproducibility
train_indices <- sample(1:nrow(Testdata), 0.8 * nrow(Testdata))  
# 80% of the data for training
training_data <- Testdata[train_indices, ]
testing_data <- Testdata[-train_indices, ]

```

## Fitting and Building the regression model





```{r}

#Convert the variables to factors:

Testdata$SCCHOICE <- as.factor(Testdata$SCCHOICE)
Testdata$SCONSIDR <- as.factor(Testdata$FSCOUNSLR)
Testdata$SCONSIDR <- as.factor(Testdata$SCHLHRSWK)

```


```{r}

# Check the unique values of SCCHOICE and SCONSIDR
unique(Testdata$SCCHOICE)
unique(Testdata$FSCOUNSLR)
unique(Testdata$SCHLHRSWK)

```


```{r}
library(GGally)

# Subset the data with predictor and target variables
subset_data <- Testdata[c("SCCHOICE", "FSCOUNSLR", "SCHLHRSWK", "ALLGRADEX", "SEGRADES", "SEGRADEQ")]

# Create the ggpairs plot
ggpairs(subset_data, columns = 1:3)


```

```{r}
# Construct the multiple linear regression model
mlr_model1 <- lm(cbind(ALLGRADEX) ~ SCCHOICE + FSCOUNSLR + SCHLHRSWK, data = Testdata)

# Print the summary of the model
summary(mlr_model1)

```


```{r}
# Construct the multiple linear regression model
mlr_model2 <- lm(cbind(SEGRADES) ~ SCCHOICE + FSCOUNSLR + SCHLHRSWK, data = Testdata)

# Print the summary of the model
summary(mlr_model2)


```

```{r}
# Construct the multiple linear regression model
mlr_model3 <- lm(cbind(SEGRADEQ) ~ FHWKHRS + P1HRSWK, data = Testdata)

# Print the summary of the model
summary(mlr_model3)


```

```{r}

# Perform ANOVA to compare the models
anova_result <- anova(mlr_model1, mlr_model2, mlr_model3)
print(anova_result)


```

- To create 3D plots for better understanding of variables distribution and linearity

## creating plots - Co relation matrix for the MLR

```{r}

predictors <- Testdata[, c("SCCHOICE", "FSCOUNSLR", "SCHLHRSWK")]

library(corrplot)

# Compute the correlation matrix
cor_matrix <- cor(predictors)

# Plot the correlation matrix
corrplot(cor_matrix, method = "circle")

```
