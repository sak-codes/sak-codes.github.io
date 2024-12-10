---
author:
- |
  **Sakshi Oza**\
  University of California, Los Angeles, CA, USA
title: "**From Data to Insights: A Machine Learning Approach to
  Cardiovascular Risk Prediction**"
---
# From Data to Insights: ML Approach to Cardiovascular Risk Prediction

## Introduction

Cardiovascular diseases (CVDs) are one of the leading causes of death
worldwide, placing a heavy burden on public health systems. Identifying
individuals at risk early is essential to preventing these diseases and
improving health outcomes. Factors like age, gender, BMI, blood
pressure, and dietary habits are known to influence the risk of
developing CVD, but understanding how these factors interact can be
challenging.

This study aims to examine how demographic (age), physiological (BMI,
blood pressure), and dietary (calorie intake) factors contribute to CVD
risk. Using methods like Principal Component Analysis (PCA), K-means
clustering, and LASSO logistic regression, this analysis seeks to
identify high-risk groups and the most important predictors of CVD.

By combining these techniques, the study evaluates the ability of
machine learning methods to predict CVD risk and highlights their
potential to guide public health strategies. The findings can help
create better prevention plans by focusing on the most important
factors.

## Methods and Materials

### Data Information

The data for this study were obtained from the National Health and
Nutrition Examination Survey (NHANES), conducted by the Division of
Health and Nutrition Examination Surveys (DHANES) at the National Center
for Health Statistics (NCHS), part of the Centers for Disease Control
and Prevention (CDC). NHANES has been operational since the early 1960s,
transitioning to a continuous survey format in 1999. Each year,
approximately 5,000 individuals from all age groups are interviewed at
home and undergo health examinations in a standardized mobile
examination center (MEC), ensuring high-quality data collection. For
this study, demographic, dietary, and examination datasets were merged
using the unique participant identifier (`SEQN`).The variables chosen
for this analysis, such as Age, BMI, Systolic BP, Diastolic BP, and
Calories, were selected based on their established relevance to
cardiovascular health. Age and blood pressure are well-known risk
factors, while BMI is a proxy for obesity, a significant contributor to
CVD. Dietary components like Calories reflect nutritional status,
another determinant of cardiovascular health. Variables like HDL, LDL,
and Total Cholesterol were excluded due to incomplete data and to
maintain model simplicity.

### Study Population

The study population was derived from the 2013--2014 NHANES dataset,
which targets the noninstitutionalized civilian resident population of
the United States. To improve the precision of estimates for subgroups
of public health interest, the NHANES 2011--2014 cycles oversampled
specific subgroups, including Hispanic persons, non-Hispanic black
persons, non-Hispanic Asian persons, non-Hispanic white and other
persons at or below 130% of the poverty level, and non-Hispanic white
and other persons aged 80 years or older.

After applying inclusion criteria---adults aged 18--80 with complete
data for key variables---a final sample of 6,488 participants was
included in the analysis.

| **Variable** | **N**  | **Mean** | **Median** | **SD**  | **Min** | **Max**   |
|--------------|--------|----------|------------|---------|---------|-----------|
| Age          | 6488   | 38.51    | 37.00      | 21.66   | 8.00    | 80.00     |
| BMI          | 6488   | 27.18    | 26.20      | 7.31    | 12.30   | 77.50     |
| Sys.BP       | 6488   | 118.04   | 116.00     | 17.70   | 66.00   | 228.00    |
| Dia.BP       | 6488   | 65.87    | 68.00      | 14.80   | 0.00    | 120.00    |
| Calories     | 6488   | 2085.47  | 1917.00    | 999.45  | 117.00  | 12108.00  |


Key demographic, physiological, and dietary variables were analyzed,
including Age, BMI, blood pressure, and calorie
intake(Table [1](#table:summary_stats){reference-type="ref"
reference="table:summary_stats"}).

### Statistical Methods

#### Creation of CVD Risk Variable

To assess cardiovascular disease (CVD) risk, a binary variable
(`CVD_Risk`) was created based on clinical thresholds. Individuals were
classified as being at high CVD risk (`CVD_Risk = 1`) if they met either
of the following criteria: systolic blood pressure (`Systolic_BP`)
greater than 130 mmHg or body mass index (BMI) greater than 30 kg/m².
Otherwise, individuals were classified as low CVD risk (`CVD_Risk = 0`).

#### Principal Component Analysis (PCA)

Principal Component Analysis (PCA) was employed to reduce dimensionality
and address potential multicollinearity among predictors. : $$Z = XW$$
where $Z$ represents principal components, $X$ is the standardized data
matrix, and $W$ contains eigenvectors.

#### K-Means Clustering

Clustering was performed using PCA scores to identify distinct
subgroups. The method minimizes within-cluster variance:
$$\underset{\mu}{\text{arg min}} \sum_{i=1}^{k} \sum_{x \in C_i} || x - \mu_i ||^2$$
where $C_i$ represents clusters and $\mu_i$ their centroids. The Elbow
method validated the choice of three clusters.ANOVA was used to test
differences in Age, BMI, and Systolic BP across clusters, with partial
eta squared as a measure of effect size. Pearson's Chi-squared test
evaluated the association between clusters and CVD Risk, with Cramér's V
used to measure effect strength.

#### LASSO Logistic Regression

LASSO regression adds a penalty term to the logistic regression loss
function, shrinking less important coefficients to zero:
$$\underset{\beta_0, \beta}{\text{minimize}} \; \left\{ \sum_{i=1}^n \left( y_i - \beta_0 - \sum_{j=1}^p \beta_j x_{ij} \right)^2 + \lambda \sum_{j=1}^p |\beta_j| \right\}$$

Cross-validation determined the optimal regularization parameter
($\lambda = 0.0004$). All statistical analyses were conducted using R
version 4.4.1, and statistical tests were performed at a 95% confidence
level (CI).

## Results

### Principal Component Analysis (PCA)

By summarizing variance into a few principal components, PCA captures
the most significant patterns in the data

![PCA Biplot illustrating variable contributions and
separations.](pca_plot.jpg){#fig:pca width="\\linewidth" height="15em"}

The PCA biplot (Figure [1](#fig:pca){reference-type="ref"
reference="fig:pca"}) illustrates the variable contributions and
separations. The first two components explained 63.2% of the total
variance, with PC1 accounting for 42.8% and PC2 explaining 20.4%. Age
and BMI influenced PC1, while PC2 captured variability in Systolic and
Diastolic BP. Individuals with high `CVD_Risk` align with higher Age,
BMI, and Systolic BP vectors, confirming these predictors' significance
in assessing cardiovascular risk.PCA outputs were then used as inputs
for clustering to improve cluster separation and interpretability.

### K-Means Clustering

K-Means clustering segmented the population into three clusters based on
PCA components.

![K-Means clustering of PCA components highlighting distinct
subgroups.](kmeans_cluster_plot.jpg){#fig:kmeans width="\\linewidth"
height="15em"}

The K-Means clustering diagram reveals three distinct subgroups based on
demographic and health characteristics. The Elbow Method validated the
choice of three clusters, and the cluster visualization in
Figure [2](#fig:kmeans){reference-type="ref" reference="fig:kmeans"}
reinforces the separation between these groups.The quality of clustering
was assessed using silhouette analysis. A mean silhouette width of 0.56
for three clusters indicated good separation between clusters.

::: {#table:cluster}
  **Cluster**   **Avg Age**   **Avg BMI**   **Avg SBP**   **CVD Proportion**
  ------------- ------------- ------------- ------------- --------------------
                                                          
                                                          
                                                          

  : Cluster Characteristics
:::

These clusters revealed distinct subgroups with varying demographic and
health profiles (Table [2](#table:cluster){reference-type="ref"
reference="table:cluster"}): - Cluster 1: Young individuals (Avg Age =
21.2), low BMI (23.0), and low Systolic BP (105.5). The CVD risk
proportion is only 10.9%. - Cluster 2: Middle-aged individuals (Avg Age
= 35.7), moderate BMI (27.5), and intermediate Systolic BP (117.1). The
CVD risk proportion is 36.1%. - Cluster 3: Older individuals (Avg Age =
56.3), higher BMI (31.0), and elevated Systolic BP (130.4). This group
has the highest CVD risk proportion (71.8%).ANOVA confirmed significant
differences in Age, BMI, and Systolic BP across clusters (p-values \<
2.22e-16), with moderate to strong effect sizes (Age = 0.24, BMI = 0.40,
Systolic BP = 0.27). The Chi-squared test revealed a significant
association between clusters and CVD Risk (p-value \< 2.2e-16),
supported by a moderate to strong Cramér's V value of 0.56.

### LASSO Regression

LASSO regression identified Age, BMI, and Systolic BP as the most
influential predictors of `CVD_Risk`.

![ROC Curve for LASSO Logistic Regression.](ROC_plot.jpg){#fig:roc
width="17em" height="17em"}

The ROC curve demonstrates the strong predictive capability of the LASSO
model, achieving an AUC of 0.975. This indicates good discrimination
between individuals with high and low CVD risk, supported by high
sensitivity = 88.2 and specificity = 93.2.

::: {#table:lasso}
  **Variable**   **Coefficient**
  -------------- -----------------
  Age            
  BMI            
  Systolic BP    
  Diastolic BP   
  Calories       

  : LASSO Regression Coefficients
:::

As shown in the (Table [3](#table:lasso){reference-type="ref"
reference="table:lasso"}),The LASSO regression revealed BMI = 0.6004 and
Systolic BP = 0.1643 as the strongest predictor of CVD risk,
highlighting the critical roles of obesity and hypertension. BMI's high
coefficient indicates a substantial increase in risk with higher body
mass, while Systolic BP underscores the impact of elevated blood
pressure. Age = 0.0008 contributes modestly, reflecting cumulative risk
over time. Diastolic BP and Calories had negligible coefficients,
suggesting their effects are minimal.

## Discussion

The findings highlight the interplay of demographic, physiological, and
dietary factors in predicting CVD risk. PCA revealed clear separations
among individuals based on their CVD risk levels while clustering
identified distinct subpopulations that can benefit from targeted public
health interventions. For instance, Cluster 3, comprising older
individuals with higher BMI and elevated blood pressure, represents the
highest-risk group requiring immediate attention.

LASSO regression validated Age, BMI, and Systolic BP as the most
influential predictors of CVD risk. These results align with established
clinical research, emphasizing the importance of managing obesity and
hypertension to reduce cardiovascular risk [@lassoTibshirani]. The
model's high sensitivity (88.2%) and specificity (93.2%

The statistical validation further reinforced these insights. ANOVA
results demonstrated significant differences in key predictors across
clusters, justifying their use in segmentation. Cramér's V indicated a
strong association between clusters and CVD risk, enhancing the
robustness of the clustering approach.

## Conclusion

This study integrates PCA, clustering, and LASSO regression to create a
comprehensive framework for predicting CVD risk. The analysis provides
actionable insights for public health strategies by identifying key
predictors and high-risk subpopulations.

Cluster 3, representing older individuals with higher BMI and blood
pressure, should be the primary focus of intervention programs. The
results also highlight the predictive accuracy of LASSO regression,
making it a reliable tool for risk assessment. Future research could
incorporate longitudinal data and additional predictors to refine the
model further.

::: thebibliography
99 Centers for Disease Control and Prevention (CDC). National Health and
Nutrition Examination Survey (NHANES). Retrieved from
<https://www.kaggle.com/datasets/cdc/national-health-and-nutrition-examination-survey>

Tibshirani, R. (1996). Regression shrinkage and selection via the Lasso.
Journal of the Royal Statistical Society: Series B (Methodological),
58(1), 267--288.

McDonald, J. H. (2014). *Handbook of Biological Statistics* (3rd ed.).
Sparky House Publishing, Baltimore, Maryland.

Cramér, H. (1946). *Mathematical Methods of Statistics*. Princeton
University Press.

World Health Organization (WHO). (2021). Cardiovascular diseases (CVDs)
fact sheet. Retrieved from
<https://www.who.int/news-room/fact-sheets/detail/cardiovascular-diseases-(cvds)>
:::

## Appendix {#appendix .unnumbered}

### Source Data File

The NHANES dataset comprises publicly available data from the Kaggle,
including demographic, dietary, examination, and laboratory
measurements.

### SAS Data Set

-   demographic.csv

-   diet.csv

-   lab.csv

### R Code

``` {#lst:table_code caption="R Code for Tables: Summary Statistics, Cluster Analysis, and LASSO Coefficients" label="lst:table_code"}
,basicstyle=\scriptsize]
# Table 1: Summary Statistics
summary_table <- data.frame(
  Variable = c("Age", "BMI", "Systolic_BP", "Diastolic_BP", "Calories"),
  N = sapply(selected_vars, function(x) sum(!is.na(x))),
  Mean = sapply(selected_vars, function(x) mean(x, na.rm = TRUE)),
  Median = sapply(selected_vars, function(x) median(x, na.rm = TRUE)),
  SD = sapply(selected_vars, function(x) sd(x, na.rm = TRUE)),
  Min = sapply(selected_vars, function(x) min(x, na.rm = TRUE)),
  Max = sapply(selected_vars, function(x) max(x, na.rm = TRUE))
) %>%
  mutate(across(Mean:Max, round, 2)) 

# Table 2: Cluster Analysis
cluster_summary <- nhanes %>%
  group_by(Cluster) %>%
  summarise(
    Avg_Age = mean(Age, na.rm = TRUE),
    Avg_BMI = mean(BMI, na.rm = TRUE),
    Avg_Systolic_BP = mean(Systolic_BP, na.rm = TRUE),
    CVD_Risk_Proportion = mean(CVD_Risk, na.rm = TRUE)
  )

# Table 3: LASSO Coefficients
lasso_coef <- as.data.frame(as.matrix(coef(lasso_model, s = lasso_lambda)))
names(lasso_coef) <- "Coefficient"
print(lasso_coef)
```

``` {#lst:figure_code caption="R Code for Figures: PCA Biplot, K-Means Clustering, and ROC Curve" label="lst:figure_code"}
,basicstyle=\scriptsize]
# Figure 1: PCA Biplot
fviz_pca_biplot(pca_model, label = "var", habillage = nhanes$CVD_Risk, 
                addEllipses = TRUE, ellipse.level = 0.95)
# Figure 2: K-Means Clustering
fviz_cluster(kmeans_model, data = nhanes %>% select(PC1, PC2), geom = "point")
# Figure 3: LASSO ROC Curve
plot(lasso_roc, col = "blue", lwd = 2, main = "ROC Curve for LASSO Regression")
abline(a = 0, b = 1, col = "gray", lty = 2)
```
