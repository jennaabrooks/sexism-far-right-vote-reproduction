# Demographic and Ideological Influence on Voter Intent in Spanish Elections

**Authors**  
Jenna Brooks, Sara Hamidi, Shirley Augustin, Allison Park

---

## Overview

This project investigates whether the beliefs of Spanish citizens regarding sexism and immigration can predict their voting intentions in Spanish elections. Spain's pluralistic and decentralized political system features over 20 active political parties, many of which differentiate themselves on ideological issues such as immigration and gender equality.

We used survey data from the *Spanish Political Attitudes* dataset to classify respondents’ voting intentions for six major political parties using demographic and ideological indicators. Our main hypothesis was that far-left and far-right parties, which tend to mobilize polarizing issues, would be easier to classify than centrist parties.

---
## Files 
- `mini-proj-1.qmd` is a Quarto document containing the code and final write up 
- `df_clean.csv` contains variables of interest and 6 political parties of interest
- `knn_model.qmd` is a Quarto document containing K Nearest Neighbors (KNN) initial analysis
- `multinomial_regression.rdm` is an R studio file exploring multinomial regression analysis
- `Project Proposal.pdf` is a pdf containing the initial project proposal with appendix with more information on 6 political parties of interest
- `Replication Data` folder contains the original data from the authors, original paper, and code book for survey responses


## Dataset

**Source**: Spanish Political Attitudes dataset (Hernández Pérez et al. 2021)  
**Sample Size**: 7,850 individuals aged 18–56  
**Cleaned Sample Size**: 3,034 respondents (after filtering and removing missing values)
- cleaned data with variables of interest can be found in `df_clean.csv`
**Unit of Analysis**: Individual voters

**Covariates Used**:
- `dincome_all` (Income)
- `female` (Gender)
- `nativism` (Anti-immigration attitude)
- `msexism` (Modern sexism scale)
- `femdemonstrate` (Participation in Women’s Day protests)

**Target Variable**: `voteintentionspain`  
We classified responses for the following six political parties:
- PSOE (1) - Center-Left
- PP (2) - Center-Right
- Podemos (3) - Far-Left
- Ciudadanos (4) - Centrist
- ERC (7) - Catalonia-based Left
- Vox (23) - Far-Right

---

## Methodology

We tested multiple classification algorithms to predict vote intention:

### 1. **Multinomial Logistic Regression**
- Used as a baseline model
- Achieved ~40% accuracy
- Useful for interpretability, but output is probabilistic

### 2. **Random Forest Classifier**
- Config: 500 trees, 3 variables considered per split
- Accuracy: 37.5% on the test set
- Variable Importance:
  - `msexism` (most important)
  - `nativism` (second most important)
- Output: Confusion matrix and variable importance plot

### 3. **K-Nearest Neighbors (KNN)**
- Baseline: `k = 3`, Accuracy = 33.3%
- Tuned: Best `k = 63`, Accuracy = 40.2%
- Performance doubled that of random guessing (16%)
- Heavily biased toward majority classes
- No predictions for minority classes like ERC in best-k model

---

## Results

- **Random Forest** and **KNN** both performed similarly (~37–40% accuracy)
- **Class Imbalance** significantly impacted prediction accuracy:
  - PSOE: 30.8%
  - Ciudadanos: 22.5%
  - Podemos: 19.6%
  - Remaining classes: under 13%
- **Most Influential Variables**: `msexism`, `nativism`
- **Prediction Bias**: All models tended to overpredict for majority classes

---

## Conclusions

This project demonstrates that ideological beliefs—particularly attitudes about sexism and immigration—are key predictors of vote intention in Spain. While classification accuracy remains limited due to class imbalance, models like Random Forest provide valuable insights into which features drive political alignment. This reinforces the notion that far-left and far-right parties benefit from ideologically motivated support, whereas centrist parties draw more diverse bases that are harder to predict algorithmically.

---

## Appendix

For additional context on Spain's political spectrum and detailed variable descriptions, see **Appendix A** in the full project report.
