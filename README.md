# Diabetes Screening from BRFSS 2024

CS 74 final project by Catherine Chun and Carys Kirlew.

## Overview

We build a diabetes screening model from survey answers in the CDC's 2024 Behavioral Risk Factor Surveillance System (BRFSS), a national telephone survey of about 434,000 U.S. adults. The model estimates each person's chance of reporting a diabetes diagnosis from information that is cheap to collect: demographics, income and education, health-care access (insurance, a regular doctor, a recent checkup), and health and lifestyle answers such as BMI, general health, physical activity, smoking and alcohol use. People whose estimated risk is above a cutoff are flagged as higher-risk. We compare logistic regression and random forest models on four nested feature sets, from age and sex alone (M0) up to the full set with seven social determinants of health questions, such as food insecurity, trouble paying bills and lack of transportation (M3). We then ask two questions: does one model work equally well across age, sex, race/ethnicity, income and urban/rural groups, and does adding social determinants of health improve predictions? Because the outcome is a diagnosis people report, the model learns to recognize people who look like those already diagnosed; it is not shown to find undiagnosed cases.

## Contents

| Path | What it is |
|---|---|
| `01_Data_Preprocessing.ipynb` | Cleans the raw survey data and splits it into training (70%), validation (10%) and test (20%) sets |
| `02_Model_Training.ipynb` | Trains, tunes and evaluates the models, and makes every table and figure |
| `data/raw/LLCP2024XPT.zip` | Original CDC data file (zipped) |
| `data/derived/` | The cleaned training/validation file and the test file |
| `outputs/` | All result tables (CSV) and figures (PNG) |

## How to run

1. Install Python 3.12 and the packages:
   ```bash
   pip install pandas==2.3.1 numpy==1.26.4 scikit-learn==1.7.1 matplotlib==3.10.0 jupyter
   ```
2. Run `02_Model_Training.ipynb` from top to bottom. The split data is already in `data/derived/`, so this works right away.
3. To rebuild the data from scratch first, unzip `data/raw/LLCP2024XPT.zip` inside `data/raw/` (keep the file name as is, including its trailing space), then run `01_Data_Preprocessing.ipynb` before notebook 02.

## Main results (test set, 86,793 people)

- The M2 logistic regression model (demographics plus health and lifestyle answers) reached ROC-AUC 0.82.
- At a 0.15 probability cutoff it found 79% of people with diabetes (precision 0.32). At 0.50 it found only 15% (precision 0.54).
- Recall differed widely across groups, for example 11% for ages 18–34 vs 86% for ages 65 and over.
- Adding the SDOH questions made almost no difference (ROC-AUC changed by less than 0.001).
- Logistic regression and random forest performed almost identically.

The test set was used only once, after every modeling choice was fixed.
