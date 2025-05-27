# Reproduction of *Sexism and the Far-Right Vote: The Individual Dynamics of Gender Backlash*  
**By Eva Anduiza & Guillem Rico**  
**Reproduced by Jenna Brooks**

## Overview

This repository contains the reproduction and extension of the study *"Sexism and the Far-Right Vote: The Individual Dynamics of Gender Backlash"* by Eva Anduiza and Guillem Rico (2024). The original study examines the role of sexist beliefs in predicting support for the far-right party Vox in Spain.

In this reproduction, I replicate the authors' main findings using a logistic regression model (Table 1), then extend the analysis by fitting alternative models (probit and cloglog), comparing their in-sample and out-of-sample performance. I also conduct exploratory modeling to investigate interactions between gender, sexism, and voting behavior.

## Contents

- `cleaned.csv` – Cleaned dataset derived from the Spanish Political Attitudes Survey (2019 & 2020 waves) - Stata license was needed to replicate directly from the authors replication_code_1.do. 
- `FINAL_sexism_farright.qmd` – Quarto file containing code and narrative analysis
- `FINAL_sexism_farright.pdf` - Final write up
- `

- Figures:
  - Histogram of intended Vox votes
  - ROC curves comparing model performance

## Data Source

The dataset is derived from the **Spanish Political Attitudes Survey** (Hernández Pérez et al., 2021), a longitudinal online panel survey of Spanish adults (ages 18–56). Only the 2019 and 2020 waves are analyzed in this study to capture the emergence of Vox as a viable far-right party.

The original replication data can be found [**HERE on Dataverse**](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/A11CD5).


## Key Variables

- **Dependent Variable**: `vim_vox` – Intended vote for Vox (1 = Yes, 0 = No)
- **Independent Variables**: 
  - `msexism` – Modern sexism index
  - `ideol` – Ideological self-placement
  - `nativism`, `authoritarian`, `pop6amz`, `orgterr` – Other attitudinal predictors
  - `female`, `age`, `edu3`, `dhincome_all`, `livingpartner`, `intpol` – Sociodemographics and controls

## Reproduction Goals

- Replicate Table 1 (logistic regression results) from the original study
- Fit and compare performance of probit and cloglog models
- Analyze model performance with ROC and AUC metrics
- Discuss implications of sexist attitudes on voting for far right party
