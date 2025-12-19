# Statistical-Analysis-of-Labour-Analgesia-and-Orthopedic-Anesthesia-Outcomes
This project presents a comprehensive statistical analysis conducted during a data analysis contract at Rivers State University Teaching Hospital (RSUTH). The study evaluates the effectiveness, duration, and patient experience of analgesia during labour, as well as anesthesia types and outcomes among orthopedic patients.
The analysis focuses on pain relief effectiveness, physiological responses, side effects, patient satisfaction, and time-to-analgesia using real-world clinical data.
# Objectives
Assess the effectiveness of labour analgesia over time using the Visual Analogue Scale (VAS)

Compare physiological responses (heart rate, systolic & diastolic blood pressure) across treatment groups

Evaluate maternal satisfaction and informed consent experiences

Analyze anesthesia type, duration, and complications in orthopedic procedures

Identify statistically significant differences across intervention groups

# Dataset Summary

## Labour Analgesia Dataset

Sample size: 1,021 patients

Variables include age, BMI, time to analgesia, VAS pain scores, vitals, side effects, and satisfaction measures

Groups: BF, BFM, BO

## Orthopedic Dataset

Sample size: 3,001 patients

Variables include anesthesia type, surgery type, duration, and complications
All patient data used in this repository is fully anonymized. No personally identifiable information is included.

# Tools & Technologies

## R Programming (tidyverse, stats)

## SPSS

## Microsoft Excel

## Statistical Tests:

## Pearson’s Chi-square and Fisher’s Exact Test(Code Used)
df %>%
  select(vas_baseline_cat, group) %>%
  tbl_cross(
    row = group,
    col = vas_baseline_cat,
    percent = "row",
    margin = "column",
    missing = "no"
  ) %>%
  add_p() %>%
  bold_labels() %>%
  as_flex_table()

## Kruskal–Wallis and Wilcoxon Rank Sum Test (code Used)
library(tidyverse)
library(gtsummary)
library(flextable)
library(sjPlot)
library(dplyr)
library(ggplot2)
library(dlookr) 
library(readxl)
df <- read_excel("Labour Analgesia for R.xlsx")
df %>%
  select(hr_baseline,hr_0mins, hr_30mins, hr_40mins, hr_60mins,  hr_2hr, hr_4hr, group) %>%
  tbl_summary(by = group,
    statistic = list(
      all_categorical() ~ "{n} ({p}%)",
      all_continuous() ~ "{mean} ({sd})"
    ),
    digits = list(
      all_categorical() ~ 1,
      all_continuous() ~ 2
    ),
   label = list(
      hr_baseline ~ "Heartrate baseline",
      hr_0mins ~ "Heartrate in 0min",
      hr_30mins ~ "Heartrate in 30min",
      hr_40mins ~ "Heartrate in 40min",
      hr_60mins ~ "Heartrate in 60min",
      hr_2hr ~ "Heartrate in 2hrs",
      hr_4hr ~ "Heartrate in 4hrs"
     
    ),
    missing_text = "Non-responders"
  ) %>%
  add_p() %>% 
  bold_labels() %>%
  as_flex_table()


Descriptive Statistics (Mean, SD, Frequencies)
df %>%
  select(sbp_baseline,sbp_0mins,  sbp_30mins, sbp_40mins, sbp_60mins, sbp_2hr, sbp_4hr, group) %>%
  tbl_summary(by = group,
    statistic = list(
      all_categorical() ~ "{n} ({p}%)",
      all_continuous() ~ "{mean} ({sd})"
    ),
    digits = list(
      all_categorical() ~ 1,
      all_continuous() ~ 2
    ),
   label = list(
      sbp_baseline ~ "Systolic BP baseline",
      sbp_0mins ~ "Systolic BP in 0min",
      sbp_30mins ~ "Systolic BP in 30min",
      sbp_40mins ~ "Systolic BP in 40min",
      sbp_60mins ~ "Systolic BP in 60min",
      sbp_2hr ~ "Systolic BP in 2hrs",
      sbp_4hr ~ "Systolic BP in 4hrs"
     
    ),# Renaming the Colunm 
    missing_text = "Non-responders" # Avoiding Missing Value and replace then as Non-responders 
  ) %>%


# Key Insights

Labour analgesia provided rapid pain relief within 5 minutes, but effectiveness declined by 4 hours

Significant differences in pain perception and satisfaction were observed across treatment groups

The BFM group consistently showed better pain control and satisfaction

Orthopedic analysis revealed regional anesthesia as the most commonly used method with low complication rates

Time-to-analgesia was significantly associated with pain severity at early follow-up intervals

# Author

Adaobi Roseline Ezechukwu
Data Analyst | Healthcare & Statistical Analysis
Nigeria
