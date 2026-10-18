# HELIX_PM606

Download PM606Report.html to look at interactive report.

Analysis of Environmental Exposures, Diet, and Metabolomics on Child BMI Z-Score
Abstract
Background: Identifying the key predictors of childhood Body Mass Index (BMI) is crucial for informing effective health interventions, given the significant impacts of diet, chemical exposures, and metabolomic profiles on health outcomes. Understanding the multifactorial influences is crucial for developing effective interventions and policies.

Objective: This study aims to predict childhood BMI Z-scores by integrating comprehensive data on postnatal diet, chemical exposures, and serum metabolomics, using advanced statistical models.

Methods: Data from the HELIX study, including 1301 mother-child pairs aged 6-11 years, were analyzed. Data was split into training (70%) and test (30%) sets. Various modeling approaches, including LASSO, ridge, elastic net, decision tree, random forest, and gradient boosting machine (GBM), with 10-fold cross-validation used to evaluate model performance and ensure robustness. Models were evaluated based on their Root Mean Squared Error (RMSE) and the significance of the predictors identified.

Results: The results demonstrate that models incorporating a comprehensive set of variables (diet, chemicals, metabolomics, and covariates) consistently outperformed those with fewer variables. The inclusion of metabolomic data significantly improved model performance. GBM model with all variables demonstrated the best performance with a cross-validated RMSE of 0.9537, followed closely by the group LASSO model with an RMSE of 0.8748. Key predictors identified across the models included age and sex, specific metabolites such as metab_161 (coefficient 3.5751), metab_95 (1.3657), and metab_160 (-3.2241), along with chemical exposures like polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2). The random forest model also showed strong performance with an RMSE of 1.0047.

Conclusion: Integrating demographic, dietary, chemical, and metabolomic data provides robust predictions for BMI in children. Advanced machine learning techniques, particularly GBM and Random Forest, significantly enhance predictive performance. These findings underscore the importance of utilizing diverse data types to understand and address childhood obesity effectively.

Introduction
Background
The impact of postnatal environmental exposures on childhood health outcomes is critical for understanding long-term health implications in children. Understanding the multifactorial influences on childhood BMI is crucial for developing effective interventions and policies to combat this issue. This study aims to understand the impact of postnatal environmental exposures, dietary habits, and covariates on the BMI Z-score of children aged 6-11 years.

Research indicates that postnatal exposure to endocrine-disrupting chemicals (EDCs) such as phthalates, bisphenol A (BPA), and polychlorinated biphenyls (PCBs) can significantly influence body weight and metabolic health (Junge et al., 2018). These chemicals, commonly found in household products and absorbed through dietary intake, are linked to detrimental effects on metabolic health in children. This hormonal interference can lead to an increased body mass index (BMI) in children, suggesting a potential pathway through which exposure to these chemicals contributes to the development of obesity.

The study by Harley et al. (2013) investigates the association between prenatal and postnatal Bisphenol A (BPA) exposure and various body composition metrics in children aged 9 years from the CHAMACOS cohort. The study found that higher prenatal BPA exposure was linked to a decrease in BMI and body fat percentages in girls but not boys, suggesting sex-specific effects. Conversely, BPA levels measured at age 9 were positively associated with increased adiposity in both genders, highlighting the different impacts of exposure timing on childhood development.

A 2016 study by Caspersen et al. investigated the determinants of plasma levels of polychlorinated biphenyls (PCBs), brominated flame retardants, and organochlorine pesticides in pregnant women and 3-year-old children. In pregnant women, significant predictors of increased plasma concentrations of persistent organic pollutants (POPs) included age, low parity, and low pre-pregnant BMI. With the 3-year-olds, prolonged breastfeeding duration was a major determinant of increased POP concentrations. Diet was a significant predictor of PCB levels in children. By examining environmental exposures and their influence on BMI, this project aims to extend the understanding of how specific dietary patterns and chemical exposures during early childhood contribute to BMI variations, aligning with the findings that diet significantly predicts POP levels in children.

These studies collectively illustrate the critical role of environmental exposures in shaping metabolic health outcomes in children, highlighting the necessity for ongoing research and policy intervention to mitigate these risks.

Hypothesis
How are postnatal environmental exposures, specifically those found in household products and dietary intake, along with specific serum metabolomics profiles, associated with the BMI Z-score of children aged 6-11 years? Specifically, which metabolites associated with chemical exposures and dietary patterns serve as biomarkers for the risk of developing obesity, while controlling for age and other relevant covariates?

Methods
Data Description
The HELIX (Human Early-Life Exposome, Vrijheid, M. et al., 2014) project investigates the comprehensive environmental exposures (exposome) from conception through childhood. It combines data on various environmental hazards affecting mothers and children, examining their impacts on health, growth, and development. Utilizing six European birth cohort studies (BiB, EDEN, INMA, KANC, MoBa, Rhea), HELIX integrates extensive existing data with new high-tech measurements of chemical, physical, and molecular exposures. Methods include smartphone-based pollution tracking and advanced lab techniques for detecting chemical contaminants. The study comprises three levels: a broad cohort of 31,472 mother-child pairs, a subcohort of 1,301 pairs with detailed biomarker and health outcome data at ages 6-11, and repeat-sampling studies involving 150 children and 150 pregnant women for personal exposure data collection. This multilevel approach helps in understanding the cumulative effect of various exposures on disease risk.

This project utilizes data from the subcohort of 1301 mother-child pairs in the HELIX study for whom complete exposure and outcome data were available. Exposure data included detailed dietary records after pregnancy and concentrations of various chemicals in child blood samples. There are categorical and numerical variables, which will include both demographic details and biochemical measurements. This dataset allows for robust statistical analysis to identify potential associations between chemical exposure and changes in BMI Z-scores, considering confounding factors such as age, gender, or socioeconomic status. There are no missing data so there is not need to impute the information. Child BMI Z-scores were calculated based on WHO growth standards.

In terms of adding the metabolomic serum data with the rest of the dataset, 103 (about 8% of the data) values were excluded. Some data entries had no information when combined with the metabolomic data and therefore could not be imputed with the mean or median. While this may pose as a risk, including rows with missing values can lead to inaccurate or biased results. This is relevant since many statistical methods and machine learning algorithms require complete data to function correctly. The proportion of missing data of 8% is relatively small, making the exclusion of these rows a feasible approach. This minimizes the loss of valuable information while still maintaining a dataset of sufficient size for meaningful analysis.

Variable Selection
When selecting variables, elastic net will be applied into the available diet and chemical variables in the HELIX data. Elastic net was utilized for variable selection and further analysis.

Chemicals Data
Chemicals will be analyzed for the best variables using enet methods.The features for chemicals were selected due to the feature selections of elastic net. LASSO might simplify the dimensionality, so elastic net was chosen since feature importance is uncertain.

Postnatal Diet Data
Like with the chemical variables, the postnatal diet of children will be analyzed for the best variables using the regression methods.

Statistical Models
To analyze the impact of dietary, chemical, and demographic variables on BMI Z-scores, various statistical models were employed, each chosen for their unique strengths in handling different aspects of the data. These models were analyzed and performed with a 70-30% split in order to train models and predict the performance. Using a 10-fold cross validation was also applied to avoid overfitting and offer a reliable measure of a model’s predictive power and generalizability.

The correlation plot for the selected variables indicates notable multicollinearity among various chemical variables and the child age covariate. Using grouped regression models like LASSO, ridge, and elastic net allows for the collective handling of these highly correlated variables. This approach helps with overfitting.

LASSO (Least Absolute Shrinkage and Selection Operator) applies L1 regularization to minimize the absolute sum of coefficients. It was used to perform variable selection and regularization, effectively identifying the most significant predictors while setting less important ones to zero. Ridge regression is particularly useful for handling multicollinearity among predictors, ensuring that all variables contribute to the prediction without being overly penalized. Elastic net balances the benefits of both LASSO ridge, so by handling both variable selection and multicollinearity, elastic net is well-suited for high-dimensional datasets where predictors are correlated. Since the data gets correlated with each other when combined (adding diet, chemicals and the metabolomic serum), group LASSO, ridge, and elastic net were applied.

Decision tree (with pruning) splits the data into subsets based on the value of input features, with pruning applied to prevent overfitting. This provides an interpretable structure for understanding the relationships between variables and the outcome, though it can be prone to overfitting without pruning. Pruning gets applied to enhance generalizability. Random forest constructs multiple decision trees and merges them to obtain a more accurate and stable prediction. By averaging the predictions from numerous trees, this model reduces overfitting and captures complex interactions among variables. Gradient Boosting Machine (GBM) builds an ensemble of trees in a sequential manner, where each tree corrects the errors of its predecessors. This approach is highly effective in improving predictive accuracy by focusing on the residuals of previous trees, making it powerful for capturing non-linear relationships. These ensemble methods (razndom forest and GBM) were chosen for their robustness and high predictive accuracy. Random forest reduces variance by averaging multiple trees, while GBM improves model performance through iterative refinement.

In this study, the Root Mean Squared Error (RMSE) is used as the primary performance metric to evaluate and compare the predictive models. Using RMSE allows for straightforward comparisons between different models and datasets. Since RMSE is in the same units as the outcome variable, it facilitates direct assessment of how well different models perform in predicting BMI Z-scores, making it easier to identify the model that provides the most accurate predictions. By employing a diverse set of models, this analysis aims to identify the most significant predictors of BMI Z-scores and understand the complex interactions between dietary intake, chemical exposures, and metabolomic serum data. The combination of regularization techniques and ensemble methods ensures a comprehensive and reliable assessment of the data.

Results
Baseline (Covariates)
LASSO


## 10 x 1 sparse Matrix of class "dgCMatrix"
##                              s1
## (Intercept)          0.87326347
## hs_child_age_None   -0.05738585
## e3_sex_Nonefemale    .         
## e3_sex_Nonemale      .         
## e3_yearbir_None2004  .         
## e3_yearbir_None2005  .         
## e3_yearbir_None2006  .         
## e3_yearbir_None2007  .         
## e3_yearbir_None2008  .         
## e3_yearbir_None2009  .
## Baseline Lasso RMSE: 1.152017
## 10-Fold CV Lasso RMSE: 1.152017
The LASSO model for covariates only shows the selection of significant variables with their coefficients, with the optimal lambda chosen near log(λ) ≈ -4. This indicates the point where the model achieves the best balance between bias and variance, minimizing the mean squared error. The cross-validated RMSE is 1.152, indicating the model’s predictive accuracy on unseen data. Among the covariates, only the child’s age (hs_child_age_None) has a significant negative coefficient (-0.057), suggesting that as the child’s age increases, the BMI Z-score slightly decreases. The other variables (sex and birth years) were not selected as significant predictors in this model. This demonstrates that age is the most influential covariate in predicting BMI Z-score, while the other covariates did not have a significant impact.

Ridge


## 10 x 1 sparse Matrix of class "dgCMatrix"
##                                s1
## (Intercept)          8.732635e-01
## hs_child_age_None   -5.738585e-02
## e3_sex_Nonefemale   -3.110211e-38
## e3_sex_Nonemale      3.110211e-38
## e3_yearbir_None2004 -1.463782e-37
## e3_yearbir_None2005  2.704907e-38
## e3_yearbir_None2006 -9.332751e-39
## e3_yearbir_None2007 -5.445405e-38
## e3_yearbir_None2008  3.129795e-38
## e3_yearbir_None2009  3.620840e-37
## Baseline Ridge RMSE: 1.152017
## 10-Fold CV Ridge RMSE: 1.149128
The ridge regression model for the covariates focuses on minimizing model complexity to avoid overfitting. The mean squared error (MSE) plot against log(lambda) values shows the model’s performance across various regularization levels. The optimal lambda is selected where MSE is minimized, balancing complexity and accuracy. The baseline ridge model yields an RMSE of 1.152, with a cross-validated RMSE of 1.149, indicating stable performance. The child’s age (hs_child_age_None) shows a negative association with BMI Z-score, suggesting older children tend to have slightly lower BMI Z-scores. Other covariates, like sex and year of birth, have near-zero coefficients, indicating minimal impact.

Elastic Net


## 10 x 1 sparse Matrix of class "dgCMatrix"
##                              s1
## (Intercept)          0.87326347
## hs_child_age_None   -0.05738585
## e3_sex_Nonefemale    .         
## e3_sex_Nonemale      .         
## e3_yearbir_None2004  .         
## e3_yearbir_None2005  .         
## e3_yearbir_None2006  .         
## e3_yearbir_None2007  .         
## e3_yearbir_None2008  .         
## e3_yearbir_None2009  .
## Baseline Elastic Net RMSE: 1.152017
## 10-Fold CV Elastic Net RMSE: 1.152017
The elastic net model, which combines LASSO and ridge penalties for variable selection and coefficient shrinkage, achieved a baseline RMSE of 1.152. This model maintained an RMSE of 1.152 after 10-fold cross-validation, indicating stable performance. The optimal lambda was selected near log(λ) ≈ -3, suggesting minimal coefficient shrinkage. The model identified the child’s age (hs_child_age_None) as a significant variable with a coefficient of -0.0574, indicating a slight negative association with the BMI Z-score. Other covariates like sex and birth year did not show significant contributions.

Decision Tree


## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova")
## 
## Variables actually used in tree construction:
## [1] hs_child_age_None
## 
## Root node error: 1328.8/913 = 1.4554
## 
## n= 913 
## 
##         CP nsplit rel error xerror     xstd
## 1 0.011581      0   1.00000 1.0026 0.051032
## 2 0.010000      1   0.98842 1.0130 0.051854


## Baseline Unpruned Decision Tree RMSE: 1.155427
## Optimal cp value: 0.01158106


## Baseline Pruned Decision Tree RMSE: 1.148665
Pruning prior to cross-validation proved ineffective as it retained the full tree. However, cross-validation effectively identified the minimal cp value, ensuring the pruned tree was optimal for generalizing the model performance across unseen data. The emphasis on a single variable underscores the simplicity yet potential power of the decision tree in modeling BMI outcomes based on age.

## Best cp value from cross-validation: 0.007


## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova")
## 
## Variables actually used in tree construction:
## [1] hs_child_age_None
## 
## Root node error: 1328.8/913 = 1.4554
## 
## n= 913 
## 
##         CP nsplit rel error xerror     xstd
## 1 0.011581      0   1.00000 1.0028 0.050936
## 2 0.010000      1   0.98842 1.0048 0.051009




## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova", 
##     control = rpart.control(cp = best_cp))
## 
## Variables actually used in tree construction:
## [1] hs_child_age_None
## 
## Root node error: 1328.8/913 = 1.4554
## 
## n= 913 
## 
##         CP nsplit rel error xerror     xstd
## 1 0.011581      0   1.00000 1.0034 0.050969
## 2 0.007000      1   0.98842 1.0159 0.050969


## Unpruned Decision Tree RMSE: 1.155427
## Pruned Decision Tree RMSE with Best cp: 1.155427
The baseline decision tree model, which solely used the variable “hs_child_age_None,” yielded an RMSE of 1.155. This indicates the initial model’s error rate when predicting BMI Z-scores. Pruning the tree with the optimal complexity parameter (cp) of 0.0116, derived from the cross-validation, improved the RMSE to 1.149, demonstrating reduced overfitting and better performance.

After cross-validation, the optimal cp value was identified as 0.007. The pruned tree with this cp value did not further reduce the RMSE compared to the initial pruning, indicating the previous pruning was already optimal.

The pruned decision tree using cross-validation emphasizes the significance of “hs_child_age_None” in predicting BMI Z-scores. It splits the data based on whether the child’s age is greater than or equal to 6.5 years. Children younger than 6.5 years have a higher BMI Z-score (0.64) compared to older children (0.34), suggesting age as a critical factor influencing BMI.

Random Forest


## Baseline Random Forest RMSE: 1.157731
## note: only 8 unique complexity parameters in default grid. Truncating the grid to 8 .
## 10-Fold CV Random Forest RMSE: 1.154789
For the random forest model, the RMSE of the baseline model was 1.158, and after performing 10-fold cross-validation, the RMSE slightly improved to 1.155. The model identified all three significant variables: child’s age (hs_child_age_None), year of birth (e3_yearbir_None), and sex (e3_sex_None). These variables contributed the most to the model’s prediction accuracy. The child’s age showed the highest importance, indicating that the age of the child is the most influential factor in predicting BMI Z-score. The year of birth and sex also played notable roles but with lesser importance compared to age.

GBM

 
 
var
<chr>
rel.inf
<dbl>
hs_child_age_None	hs_child_age_None	79.575251
e3_yearbir_None	e3_yearbir_None	14.719111
e3_sex_None	e3_sex_None	5.705638
3 rows


## Baseline GBM RMSE: 1.14888
## 10-Fold CV GBM RMSE: 1.149695
The GBM model produced a baseline RMSE of 1.1488 and a 10-fold cross-validated RMSE of 1.1497, showing good accuracy. Key variables include child age (hs_child_age_None), year of birth (e3_yearbir_None), and sex (e3_sex_None), with child age being the most influential. The relative influence of child age (79.6) far exceeds that of birth year (14.7) and sex (5.7), indicating its dominant role in predicting BMI Z-score. The model’s performance demonstrates that these covariates significantly impact BMI predictions in children.

Model Comparison:
Child age consistently emerged as the most influential predictor across all models, demonstrating its strong association with BMI Z-score. While the ridge model and GBM provided slightly better performance, the choice between models may depend on the desired balance between interpretability (decision tree, LASSO) and predictive power (random forest, GBM). The ridge and elastic Net models offer a balance, retaining some influence from additional covariates, albeit minimal.

Diet + Covariates
LASSO


## 34 x 1 sparse Matrix of class "dgCMatrix"
##                                        s1
## (Intercept)                    0.87326347
## hs_child_age_None             -0.05738585
## e3_sex_Nonefemale              .         
## e3_sex_Nonemale                .         
## e3_yearbir_None2004            .         
## e3_yearbir_None2005            .         
## e3_yearbir_None2006            .         
## e3_yearbir_None2007            .         
## e3_yearbir_None2008            .         
## e3_yearbir_None2009            .         
## h_bfdur_Ter(10.8,34.9]         .         
## h_bfdur_Ter(34.9,Inf]          .         
## hs_bakery_prod_Ter(2,6]        .         
## hs_bakery_prod_Ter(6,Inf]      .         
## hs_break_cer_Ter(1.1,5.5]      .         
## hs_break_cer_Ter(5.5,Inf]      .         
## hs_dairy_Ter(14.6,25.6]        .         
## hs_dairy_Ter(25.6,Inf]         .         
## hs_fastfood_Ter(0.132,0.5]     .         
## hs_fastfood_Ter(0.5,Inf]       .         
## hs_org_food_Ter(0.132,1]       .         
## hs_org_food_Ter(1,Inf]         .         
## hs_proc_meat_Ter(1.5,4]        .         
## hs_proc_meat_Ter(4,Inf]        .         
## hs_total_fish_Ter(1.5,3]       .         
## hs_total_fish_Ter(3,Inf]       .         
## hs_total_fruits_Ter(7,14.1]    .         
## hs_total_fruits_Ter(14.1,Inf]  .         
## hs_total_lipids_Ter(3,7]       .         
## hs_total_lipids_Ter(7,Inf]     .         
## hs_total_sweets_Ter(4.1,8.5]   .         
## hs_total_sweets_Ter(8.5,Inf]   .         
## hs_total_veg_Ter(6,8.5]        .         
## hs_total_veg_Ter(8.5,Inf]      .
## Diet + Covariates Lasso RMSE: 1.138756
## 10-Fold CV Lasso RMSE: 1.139468
The LASSO regression model for the combination of diet and covariates yielded an RMSE of 1.139, with a cross-validated RMSE of 1.140, indicating consistency in model performance. The optimal lambda value was determined to be near log(λ) ≈ -3, as shown in the plot. In this model, the variable child’s age was the only significant variable, with a coefficient of -0.0574, indicating that as the child’s age increases, the BMI Z-score decreases. This suggests that age plays a crucial role in predicting BMI Z-score in the presence of diet and covariate factors. Other variables, such as dietary intake categories, did not show significant coefficients, implying limited influence on BMI Z-score within the context of this model.

Ridge


## 34 x 1 sparse Matrix of class "dgCMatrix"
##                                          s1
## (Intercept)                    8.732635e-01
## hs_child_age_None             -5.738585e-02
## e3_sex_Nonefemale             -3.392957e-38
## e3_sex_Nonemale                3.392957e-38
## e3_yearbir_None2004           -1.596853e-37
## e3_yearbir_None2005            2.950807e-38
## e3_yearbir_None2006           -1.018118e-38
## e3_yearbir_None2007           -5.940442e-38
## e3_yearbir_None2008            3.414322e-38
## e3_yearbir_None2009            3.950007e-37
## h_bfdur_Ter(10.8,34.9]         1.959443e-37
## h_bfdur_Ter(34.9,Inf]         -1.196150e-37
## hs_bakery_prod_Ter(2,6]        2.102760e-37
## hs_bakery_prod_Ter(6,Inf]     -1.896677e-37
## hs_break_cer_Ter(1.1,5.5]      9.801144e-39
## hs_break_cer_Ter(5.5,Inf]     -2.286856e-37
## hs_dairy_Ter(14.6,25.6]        5.634165e-38
## hs_dairy_Ter(25.6,Inf]         8.216707e-41
## hs_fastfood_Ter(0.132,0.5]     1.215262e-37
## hs_fastfood_Ter(0.5,Inf]      -6.235230e-38
## hs_org_food_Ter(0.132,1]       8.146218e-38
## hs_org_food_Ter(1,Inf]        -1.900266e-37
## hs_proc_meat_Ter(1.5,4]        1.193171e-37
## hs_proc_meat_Ter(4,Inf]       -1.994408e-38
## hs_total_fish_Ter(1.5,3]      -8.902720e-38
## hs_total_fish_Ter(3,Inf]       2.141752e-38
## hs_total_fruits_Ter(7,14.1]    2.168036e-37
## hs_total_fruits_Ter(14.1,Inf] -2.040600e-37
## hs_total_lipids_Ter(3,7]      -9.170321e-39
## hs_total_lipids_Ter(7,Inf]    -2.153479e-37
## hs_total_sweets_Ter(4.1,8.5]  -7.677763e-38
## hs_total_sweets_Ter(8.5,Inf]  -1.716694e-38
## hs_total_veg_Ter(6,8.5]        2.132182e-38
## hs_total_veg_Ter(8.5,Inf]     -1.282604e-37
## Diet + Covariates Ridge RMSE: 1.130793
## 10-Fold CV Ridge RMSE: 1.129036
For the ridge regression model, the optimal lambda was identified at approximately log(λ) = 0. The baseline RMSE for this model is 1.131, and the 10-fold cross-validated RMSE is 1.129, indicating consistent model performance. Important variables in this model include hs_child_age_None with a coefficient of -0.057, suggesting that as the age of the child increases, the BMI Z-score tends to decrease. Other dietary variables and covariates, such as various food intake categories (e.g., bakery products, dairy, fast food), did not show significant coefficients, suggesting that they have less influence in this ridge regression model for predicting BMI Z-score.

Elastic Net


## 34 x 1 sparse Matrix of class "dgCMatrix"
##                                        s1
## (Intercept)                    0.87326347
## hs_child_age_None             -0.05738585
## e3_sex_Nonefemale              .         
## e3_sex_Nonemale                .         
## e3_yearbir_None2004            .         
## e3_yearbir_None2005            .         
## e3_yearbir_None2006            .         
## e3_yearbir_None2007            .         
## e3_yearbir_None2008            .         
## e3_yearbir_None2009            .         
## h_bfdur_Ter(10.8,34.9]         .         
## h_bfdur_Ter(34.9,Inf]          .         
## hs_bakery_prod_Ter(2,6]        .         
## hs_bakery_prod_Ter(6,Inf]      .         
## hs_break_cer_Ter(1.1,5.5]      .         
## hs_break_cer_Ter(5.5,Inf]      .         
## hs_dairy_Ter(14.6,25.6]        .         
## hs_dairy_Ter(25.6,Inf]         .         
## hs_fastfood_Ter(0.132,0.5]     .         
## hs_fastfood_Ter(0.5,Inf]       .         
## hs_org_food_Ter(0.132,1]       .         
## hs_org_food_Ter(1,Inf]         .         
## hs_proc_meat_Ter(1.5,4]        .         
## hs_proc_meat_Ter(4,Inf]        .         
## hs_total_fish_Ter(1.5,3]       .         
## hs_total_fish_Ter(3,Inf]       .         
## hs_total_fruits_Ter(7,14.1]    .         
## hs_total_fruits_Ter(14.1,Inf]  .         
## hs_total_lipids_Ter(3,7]       .         
## hs_total_lipids_Ter(7,Inf]     .         
## hs_total_sweets_Ter(4.1,8.5]   .         
## hs_total_sweets_Ter(8.5,Inf]   .         
## hs_total_veg_Ter(6,8.5]        .         
## hs_total_veg_Ter(8.5,Inf]      .
## Diet + Covariates Elastic Net RMSE: 1.136809
## 10-Fold CV Elastic Net RMSE: 1.138767
The elastic net model’s optimal lambda value, near log(λ) ≈ -3, minimizes the mean squared error. Important variables identified include “hs_child_age_None” with a coefficient of -0.057, suggesting that older age is associated with a lower BMI Z-score, while other covariates like sex and year of birth showed no significant impact. The baseline RMSE of 1.137 and the cross-validated RMSE of 1.139 indicate the model’s performance and consistency.

Decision Tree


## Diet + Covariates Decision Tree RMSE: 1.152094
## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova")
## 
## Variables actually used in tree construction:
## [1] hs_bakery_prod_Ter  hs_break_cer_Ter    hs_child_age_None  
## [4] hs_total_lipids_Ter
## 
## Root node error: 1328.8/913 = 1.4554
## 
## n= 913 
## 
##         CP nsplit rel error xerror     xstd
## 1 0.011773      0   1.00000 1.0010 0.050839
## 2 0.010484      3   0.96468 1.0155 0.052218
## 3 0.010000      4   0.95420 1.0156 0.052011




## Pruned Diet + Covariates Decision Tree RMSE: 1.148665
## Best cp value from cross-validation: 0.1




## Unpruned Decision Tree RMSE: 1.152094
## Pruned Decision Tree RMSE with Best cp: 1.148665
The decision tree model for diet and covariates demonstrates that the initial unpruned model has an RMSE of 1.153, which slightly improves to 1.149 after pruning. Pruning helps by eliminating less important branches, which reduces overfitting and enhances the model’s generalization capability. The complexity parameter (cp) of 0.011 was identified as the optimal value for pruning, minimizing cross-validation error. Key variables influencing the BMI Z-score include the child’s age (hs_child_age_None), and dietary factors such as high consumption of bakery products (hs_bakery_prod_Ter), breakfast cereals (hs_break_cer_Ter), and lipids (hs_total_lipids_Ter). These results indicate the significant role of both age and specific dietary patterns in predicting BMI outcomes in children.

Random Forest


##                     IncNodePurity
## hs_child_age_None       233.57368
## e3_sex_None              34.19375
## e3_yearbir_None          97.75201
## h_bfdur_Ter              65.45676
## hs_bakery_prod_Ter       64.03655
## hs_break_cer_Ter         65.99478
## hs_dairy_Ter             69.72797
## hs_fastfood_Ter          55.45883
## hs_org_food_Ter          65.89629
## hs_proc_meat_Ter         68.85280
## hs_total_fish_Ter        63.72114
## hs_total_fruits_Ter      64.85756
## hs_total_lipids_Ter      65.79002
## hs_total_sweets_Ter      66.74543
## hs_total_veg_Ter         69.89130
## Diet + Covariates Random Forest RMSE: 1.139899
## 10-Fold CV Random Forest RMSE: 1.129478
The random forest model yielded an RMSE of 1.140, with a 10-fold cross-validated RMSE of 1.129, indicating robust model performance. The most influential variable in this model was the child’s age (hs_child_age_None), followed by the year of birth (e3_yearbir_None), and sex (e3_sex_None). Dietary variables also played significant roles, such as the total vegetable intake (hs_total_veg_Ter), processed meat intake (hs_proc_meat_Ter), bakery products (hs_bakery_prod_Ter), breakfast cereal intake (hs_break_cer_Ter), and fruit consumption (hs_total_fruits_Ter). These dietary factors, alongside the covariates, contributed to the prediction accuracy, highlighting the model’s ability to capture the multifactorial influences on the BMI Z-score in children.

GBM

 
 
var
<chr>
rel.inf
<dbl>
hs_child_age_None	hs_child_age_None	27.745725
e3_yearbir_None	e3_yearbir_None	12.544772
hs_break_cer_Ter	hs_break_cer_Ter	6.345294
hs_total_lipids_Ter	hs_total_lipids_Ter	5.984165
hs_bakery_prod_Ter	hs_bakery_prod_Ter	5.949027
hs_total_veg_Ter	hs_total_veg_Ter	5.771130
hs_org_food_Ter	hs_org_food_Ter	5.598324
hs_total_fruits_Ter	hs_total_fruits_Ter	5.275858
hs_proc_meat_Ter	hs_proc_meat_Ter	5.031984
hs_total_fish_Ter	hs_total_fish_Ter	4.810174
1-10 of 15 rows


## Diet + Covariates GBM RMSE: 1.137923
## 10-Fold CV GBM RMSE: 1.136542
The GBM modelyielded an RMSE of 1.138, with a cross-validated RMSE of 1.136, demonstrating strong predictive accuracy. The variable “hs_child_age_None” had the highest relative influence (27.745752), indicating its significant impact on the model. Other important variables included “e3_yearbir_None” (12.544772) and “hs_break_cer_Ter” (6.344034), reflecting their substantial contributions to the model’s performance. The diet-related variables such as “hs_total_lipids_Ter” (5.849461), “hs_bakery_prod_Ter” (5.394027), and “hs_total_veg_Ter” (5.773139) also played crucial roles in predicting BMI Z-score, highlighting the importance between dietary habits and covariates in influencing childhood BMI outcomes.

Model Comparison:
Overall, “hs_child_age_None” consistently emerged as the most influential variable across all models, highlighting its critical role in predicting BMI Z-score. Dietary variables such as “hs_bakery_prod_Ter,” “hs_break_cer_Ter,” and “hs_total_lipids_Ter” were also significant in multiple models, underscoring the interplay between diet and child age in influencing BMI outcomes. The GBM model, with the lowest RMSE, suggests the highest predictive accuracy among the methods evaluated.

Chemicals + Covariates
LASSO


## 29 x 1 sparse Matrix of class "dgCMatrix"
##                                s1
## (Intercept)          -1.201642945
## hs_child_age_None    -0.042729967
## e3_sex_Nonefemale     .          
## e3_sex_Nonemale       .          
## e3_yearbir_None2004  -0.040205226
## e3_yearbir_None2005   .          
## e3_yearbir_None2006   .          
## e3_yearbir_None2007   .          
## e3_yearbir_None2008   .          
## e3_yearbir_None2009   .          
## hs_cd_c_Log2         -0.011319810
## hs_co_c_Log2          .          
## hs_cs_c_Log2          .          
## hs_cu_c_Log2          0.260654501
## hs_hg_c_Log2          .          
## hs_mo_c_Log2         -0.069199903
## hs_pb_c_Log2          .          
## hs_dde_cadj_Log2     -0.041339092
## hs_pcb153_cadj_Log2  -0.125818759
## hs_pcb170_cadj_Log2  -0.043143964
## hs_dep_cadj_Log2     -0.003677983
## hs_pbde153_cadj_Log2 -0.036720000
## hs_pfhxs_c_Log2       .          
## hs_pfoa_c_Log2       -0.097979410
## hs_pfos_c_Log2        .          
## hs_prpa_cadj_Log2     .          
## hs_mbzp_cadj_Log2     0.007077421
## hs_mibp_cadj_Log2    -0.025837249
## hs_mnbp_cadj_Log2    -0.004654193
## Chemical + Covariates Lasso RMSE: 1.040557
## 10-Fold CV Lasso RMSE: 1.040727
The LASSO regression model for chemical and covariate data includes variables such as age, sex, year of birth, and various chemical concentrations. The optimal lambda (log(λ) ≈ -3) minimizes the cross-validated error, ensuring a balance between bias and variance. The model shows a cross-validated RMSE of 1.041, indicating reasonable prediction accuracy. Important variables include hs_child_age_None (-0.04273), hs_cu_c_Log2 (0.26065), and hs_pfoa_c_Log2 (-0.0978), highlighting their significant contributions to predicting the outcome. Negative coefficients suggest an inverse relationship with the BMI Z-score, whereas positive coefficients indicate a direct relationship.

Ridge


## 29 x 1 sparse Matrix of class "dgCMatrix"
##                                s1
## (Intercept)          -1.609471669
## hs_child_age_None    -0.054184972
## e3_sex_Nonefemale    -0.023174163
## e3_sex_Nonemale       0.023148148
## e3_yearbir_None2004  -0.128309522
## e3_yearbir_None2005   0.028409105
## e3_yearbir_None2006   0.053001523
## e3_yearbir_None2007  -0.027948121
## e3_yearbir_None2008  -0.015135402
## e3_yearbir_None2009   0.235538660
## hs_cd_c_Log2         -0.036089222
## hs_co_c_Log2         -0.030180059
## hs_cs_c_Log2          0.066973465
## hs_cu_c_Log2          0.319809539
## hs_hg_c_Log2         -0.014578657
## hs_mo_c_Log2         -0.071569755
## hs_pb_c_Log2         -0.039355400
## hs_dde_cadj_Log2     -0.048885680
## hs_pcb153_cadj_Log2  -0.115503946
## hs_pcb170_cadj_Log2  -0.036730018
## hs_dep_cadj_Log2     -0.011840831
## hs_pbde153_cadj_Log2 -0.027003858
## hs_pfhxs_c_Log2      -0.026465601
## hs_pfoa_c_Log2       -0.101071688
## hs_pfos_c_Log2       -0.025692420
## hs_prpa_cadj_Log2     0.001538225
## hs_mbzp_cadj_Log2     0.039172212
## hs_mibp_cadj_Log2    -0.035550506
## hs_mnbp_cadj_Log2    -0.039493899
## Chemical + Covariates Ridge RMSE: 1.035505
## 10-Fold CV Ridge RMSE: 1.035411
The ridge regression model for the combination of chemicals and covariates yields an RMSE of 1.036, demonstrating its predictive accuracy. The optimal lambda is chosen at a value near log(λ) ≈ -2, which balances the bias-variance tradeoff effectively. Significant variables influencing BMI Z-scores include the child’s age, sex, and birth year, as well as the concentrations of various chemicals. For instance, higher levels of cadmium (hs_cd_c_Log2) and copper (hs_cu_c_Log2) show notable positive associations with BMI Z-scores. Conversely, higher concentrations of lead (hs_pb_c_Log2) and specific PCBs (hs_pcb153_cadj_Log2) are negatively associated with BMI Z-scores.

Elastic Net


## 29 x 1 sparse Matrix of class "dgCMatrix"
##                               s1
## (Intercept)          -1.30722494
## hs_child_age_None    -0.04475073
## e3_sex_Nonefemale     .         
## e3_sex_Nonemale       .         
## e3_yearbir_None2004  -0.06251662
## e3_yearbir_None2005   .         
## e3_yearbir_None2006   .         
## e3_yearbir_None2007   .         
## e3_yearbir_None2008   .         
## e3_yearbir_None2009   .         
## hs_cd_c_Log2         -0.01538343
## hs_co_c_Log2          .         
## hs_cs_c_Log2          .         
## hs_cu_c_Log2          0.27721103
## hs_hg_c_Log2          .         
## hs_mo_c_Log2         -0.07149465
## hs_pb_c_Log2          .         
## hs_dde_cadj_Log2     -0.04498749
## hs_pcb153_cadj_Log2  -0.12563741
## hs_pcb170_cadj_Log2  -0.04301914
## hs_dep_cadj_Log2     -0.00523836
## hs_pbde153_cadj_Log2 -0.03600515
## hs_pfhxs_c_Log2       .         
## hs_pfoa_c_Log2       -0.10302534
## hs_pfos_c_Log2        .         
## hs_prpa_cadj_Log2     .         
## hs_mbzp_cadj_Log2     0.01485361
## hs_mibp_cadj_Log2    -0.02916026
## hs_mnbp_cadj_Log2    -0.01195464
## Chemical + Covariates Elastic Net RMSE: 1.040324
## 10-Fold CV Elastic Net RMSE: 1.035456
The elastic net model’s optimal lambda, chosen around log(λ) ≈ -2.3, minimizes the mean-squared error, ensuring the best fit for the model. Significant variables included child age, with a negative coefficient indicating that older age is associated with a lower BMI Z-score. Higher log-transformed copper levels showed a strong positive association with BMI Z-score, while other chemicals such as cadmium, lead, and PCBs (polychlorinated biphenyls) displayed negative associations. The model’s baseline RMSE was 1.040, and the 10-fold cross-validated RMSE was 1.036, indicating good predictive performance. The optimal lambda helped minimize prediction error, ensuring robust model accuracy.

Decision Tree


## Chemical + Covariates Decision Tree RMSE: 1.108581
## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova")
## 
## Variables actually used in tree construction:
## [1] hs_cu_c_Log2         hs_dde_cadj_Log2     hs_mbzp_cadj_Log2   
## [4] hs_mnbp_cadj_Log2    hs_pbde153_cadj_Log2 hs_pcb170_cadj_Log2 
## [7] hs_pfoa_c_Log2      
## 
## Root node error: 1328.8/913 = 1.4554
## 
## n= 913 
## 
##          CP nsplit rel error  xerror     xstd
## 1  0.077388      0   1.00000 1.00089 0.050861
## 2  0.032769      1   0.92261 0.93652 0.048377
## 3  0.032579      2   0.88984 0.91682 0.046750
## 4  0.025008      3   0.85726 0.91218 0.046570
## 5  0.014062      4   0.83226 0.89795 0.045241
## 6  0.013674      6   0.80413 0.89837 0.046138
## 7  0.013602      7   0.79046 0.89907 0.046094
## 8  0.013517      8   0.77686 0.89907 0.046094
## 9  0.011314      9   0.76334 0.90679 0.046317
## 10 0.011047     11   0.74071 0.91227 0.047148
## 11 0.010329     12   0.72967 0.92524 0.047400
## 12 0.010000     14   0.70901 0.92466 0.047181




## Pruned Chemical + Covariates Decision Tree RMSE: 1.089746
## Best cp value from cross-validation: 0.023




## Unpruned Decision Tree RMSE: 1.108581
## Pruned Decision Tree RMSE with Best cp: 1.089746
The decision tree model for predicting BMI z-scores using chemical and covariate data yielded an RMSE of 1.108, indicating the model’s prediction accuracy. The primary variables used in the tree construction include log-transformed concentrations of PCB170, PBDE153, DDE, and MBZP, among others. Pruning the tree improved the RMSE to 1.090, highlighting the benefits of removing less significant branches. The optimal complexity parameter (cp) value from cross-validation was 0.023. This pruned model indicates a more generalized fit by reducing overfitting, evident from the lower cross-validated RMSE. The decision tree structure reflects the hierarchical influence of these chemical variables on BMI z-scores, with PCB170 and PBDE153 being crucial decision nodes in both the pruned and unpruned trees.

Random Forest


##                      IncNodePurity
## hs_child_age_None        48.822971
## e3_sex_None               6.356073
## e3_yearbir_None          34.327078
## hs_cd_c_Log2             49.069793
## hs_co_c_Log2             51.682060
## hs_cs_c_Log2             42.322759
## hs_cu_c_Log2             66.200851
## hs_hg_c_Log2             53.722138
## hs_mo_c_Log2             59.137163
## hs_pb_c_Log2             46.948933
## hs_dde_cadj_Log2         81.399724
## hs_pcb153_cadj_Log2      86.076191
## hs_pcb170_cadj_Log2     132.902458
## hs_dep_cadj_Log2         55.402055
## hs_pbde153_cadj_Log2    100.134593
## hs_pfhxs_c_Log2          44.500787
## hs_pfoa_c_Log2           60.306554
## hs_pfos_c_Log2           51.809387
## hs_prpa_cadj_Log2        50.765210
## hs_mbzp_cadj_Log2        57.448789
## hs_mibp_cadj_Log2        45.657870
## hs_mnbp_cadj_Log2        53.036576
## Chemical + Covariates Random Forest RMSE: 1.031425
## 10-Fold CV Random Forest RMSE: 1.031669
The random forest model shows a robust performance with an RMSE of 1.031 and a cross-validated RMSE of 1.032, indicating consistency and reliability. The model’s significant variables include PCB-170, PBDE-153, and PCB-153, which have high importance in predicting the outcome. Additionally, other influential variables such as DDE, copper, and PFOA are also prominent in the model. The RMSE values suggest that the model is effective at predicting the BMI Z-score based on these chemical exposures and covariates, providing insights into the factors influencing child BMI. The minimal difference between the pruned and unpruned models indicates that pruning does not significantly enhance model performance, suggesting that the initial model is already optimized. The cross-validation further confirms the model’s stability and predictive accuracy.

GBM

 
 
var
<chr>
rel.inf
<dbl>
hs_pcb170_cadj_Log2	hs_pcb170_cadj_Log2	38.6339946
hs_pbde153_cadj_Log2	hs_pbde153_cadj_Log2	18.5483112
hs_dde_cadj_Log2	hs_dde_cadj_Log2	8.0310582
hs_cu_c_Log2	hs_cu_c_Log2	7.1919723
hs_pfoa_c_Log2	hs_pfoa_c_Log2	5.4130522
hs_pcb153_cadj_Log2	hs_pcb153_cadj_Log2	4.6664329
hs_mbzp_cadj_Log2	hs_mbzp_cadj_Log2	3.0140988
hs_mnbp_cadj_Log2	hs_mnbp_cadj_Log2	2.2531427
hs_mo_c_Log2	hs_mo_c_Log2	2.1303316
hs_pb_c_Log2	hs_pb_c_Log2	1.5787988
1-10 of 22 rows


## Chemical + Covariates GBM RMSE: 1.076264
## 10-Fold CV GBM RMSE: 1.040439
The GBM model’s relative influence plot shows that polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2), polybrominated diphenyl ether-153 (hs_pbde153_cadj_Log2), and dichlorodiphenyldichloroethylene (hs_dde_cadj_Log2) have the highest relative influence on the model’s predictions. These chemicals were found to have the highest relative influence on the model’s predictions, contributing to its accuracy. In terms of model performance, the cross-validated GBM showed improved predictive accuracy compared to the baseline, reflecting the robustness of the model in handling different data subsets. The GBM model has an RMSE of 1.076, and the cross-validated RMSE is 1.040, indicating good predictive accuracy and generalization to unseen data.

Model Comparison:
Overall, the models for chemical and covariates data highlight the significant role of specific chemicals in predicting outcomes. The random forest model, while also effective, showed slightly higher RMSEs. Decision tree models benefited from pruning, which improved their performance, but still lagged behind the ensemble methods. The LASSO, ridge, and elastic net models provided useful insights into variable importance but had higher RMSEs compared to the GBM, reflecting the trade-off between interpretability and predictive power. Ridge regression and elastic net provide lower RMSE values, suggesting better generalization compared to LASSO.

In summary, the models consistently identified polychlorinated biphenyl-170, polybrominated diphenyl ether-153, dichlorodiphenyldichloroethylene, copper, and perfluorooctanoic acid as crucial variables for predicting BMI Z-scores.

Diet + Chemical + Covariates
Group LASSO
## Group Lasso RMSE: 1.042529
## Optimal lambda: 0.02299869
Variable
<chr>
Coefficient
<dbl>
hs_child_age_None	-0.022329032
e3_sex_Nonefemale	-0.022039377
e3_sex_Nonemale	0.022039377
e3_yearbir_None2004	-0.169283184
e3_yearbir_None2005	0.003249107
e3_yearbir_None2006	0.036243679
e3_yearbir_None2007	0.047086464
e3_yearbir_None2008	0.064626655
e3_yearbir_None2009	0.347838320
h_bfdur_Ter(10.8,34.9]	0.105851305
1-10 of 52 rows
## Group LASSO RMSE with 10-fold CV: 1.031241
The cross-validated RMSE of 1.031 indicates consistent performance across different data subsets. Significant variables identified in the group LASSO model include e3_yearbir_None2009, which, with a positive coefficient of 0.349, suggests that being born in 2009 is linked to an increased BMI Z-score. Higher levels of copper (hs_cu_c_Log2) with a coefficient of 0.478 are strongly associated with an increase in BMI Z-score, while higher cadmium levels (hs_cd_c_Log2) and MiBP (hs_mibp_cadj_Log2) are linked to a decrease in BMI Z-score, with coefficients of -0.047 and -0.077, respectively. Additionally, consuming fruits within the range of 7 to 14.1 servings (hs_total_fruits_Ter(7,14.1]) is associated with an increase in BMI Z-score, as indicated by a coefficient of 0.059. These variables significantly influence the outcome based on the group LASSO model coefficients.

Group Ridge
## Group Ridge RMSE: 1.042024
## Optimal lambda: 0.04019086
Variable
<chr>
Coefficient
<dbl>
e3_yearbir_None2004	-0.173018538
e3_yearbir_None2005	0.057173234
e3_yearbir_None2006	0.122527983
e3_yearbir_None2007	0.103272458
e3_yearbir_None2008	0.122247525
e3_yearbir_None2009	0.465001939
h_bfdur_Ter(10.8,34.9]	0.127483755
h_bfdur_Ter(34.9,Inf]	0.120181314
hs_bakery_prod_Ter(2,6]	-0.004273319
hs_bakery_prod_Ter(6,Inf]	-0.215016029
1-10 of 30 rows
## Group Ridge RMSE with 10-fold CV: 1.03338
The group ridge model produced a RMSE of 1.042. After performing 10-fold cross-validation, the optimal lambda value identified was 0.0402, resulting in an RMSE of 1.033. Significant variables in this model included the year of birth (e3_yearbir_None2009) with a positive coefficient of 0.465, indicating that being born in 2009 is associated with an increased BMI Z-score. Copper levels (hs_cu_c_Log2) also showed a strong positive association with a coefficient of 0.606. Higher levels of mono-benzyl phthalate (hs_mbzp_cadj_Log2) were associated with an increase in the response variable, evidenced by a coefficient of 0.110. Conversely, a high intake of breakfast cereals (hs_break_cer_Ter(5.5, Inf]) was linked to a decrease in BMI Z-score with a coefficient of -0.115. Lastly, higher levels of polychlorinated biphenyl-153 (hs_pbcb153_cadj_Log2) were associated with a decrease in the response variable, indicated by a negative coefficient of -0.199.

Group Elastic Net
## Group Elastic Net RMSE: 1.043394
## Optimal lambda: 0.03662041
Variable
<chr>
Coefficient
<dbl>
hs_child_age_None	-0.010980716
e3_sex_Nonefemale	-0.011625911
e3_sex_Nonemale	0.011625911
e3_yearbir_None2004	-0.124602467
e3_yearbir_None2005	0.015990826
e3_yearbir_None2006	0.050171823
e3_yearbir_None2007	0.042775798
e3_yearbir_None2008	0.056133552
e3_yearbir_None2009	0.267269861
h_bfdur_Ter(10.8,34.9]	0.087026371
1-10 of 33 rows
## Group Elastic Net RMSE with 10-fold CV: 1.032168
The group elastic net model initially produced an RMSE of 1.043. After performing 10-fold cross-validation, the optimal lambda value identified was 0.037, resulting in an RMSE of 1.032. Significant variables in this model included the birth year 2009 (e3_yearbir_None2009) with a positive coefficient of 0.2673, indicating an association with increased BMI Z-score. Higher log-transformed copper levels (hs_cu_c_Log2) showed a strong positive association with a coefficient of 0.544. The breastfeeding duration category (h_bfdur_Ter(10.8,34.9])) was also positively associated with an increase in the outcome variable, as suggested by a coefficient of 0.087. Conversely, higher log-transformed lead levels (hs_pb_c_Log2) were negatively associated with the outcome, indicated by a coefficient of -0.096. The birth year 2004 (e3_yearbir_None2004) was negatively associated with the outcome, as evidenced by a coefficient of -0.125.

Decision Tree


## Diet + Chemical + Covariates Decision Tree RMSE: 1.128749
## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova")
## 
## Variables actually used in tree construction:
## [1] hs_cu_c_Log2         hs_dde_cadj_Log2     hs_fastfood_Ter     
## [4] hs_mnbp_cadj_Log2    hs_pbde153_cadj_Log2 hs_pcb170_cadj_Log2 
## [7] hs_pfoa_c_Log2      
## 
## Root node error: 1328.8/913 = 1.4554
## 
## n= 913 
## 
##          CP nsplit rel error  xerror     xstd
## 1  0.077388      0   1.00000 1.00089 0.050861
## 2  0.032769      1   0.92261 0.93652 0.048377
## 3  0.032579      2   0.88984 0.91682 0.046750
## 4  0.025008      3   0.85726 0.91218 0.046570
## 5  0.015671      4   0.83226 0.90443 0.045712
## 6  0.013674      5   0.81658 0.91485 0.047377
## 7  0.013602      6   0.80291 0.91478 0.047609
## 8  0.013517      7   0.78931 0.91478 0.047609
## 9  0.011314      8   0.77579 0.93397 0.049086
## 10 0.011047     10   0.75317 0.96270 0.050245
## 11 0.010296     11   0.74212 0.98215 0.050293
## 12 0.010000     12   0.73182 0.98607 0.050369




## Pruned Diet + Chemical + Covariates Decision Tree RMSE: 1.089746
## Best cp value from cross-validation: 0.023




## Unpruned Decision Tree RMSE: 1.128749
## Pruned Decision Tree RMSE with Best cp: 1.089746
The unpruned decision tree model for predicting BMI Z-score in children had an RMSE of 1.129, indicating the initial model’s error rate. After applying pruning to the decision tree and with cross-validation of 10 folds, the RMSE improved to 1.090, demonstrating enhanced model performance by reducing overfitting. Pruning, which involves trimming less critical branches, helps in creating a more generalized model. Key variables identified in the decision tree include log-transformed concentrations of PCBs (hs_pcb170_cadj_Log2 and hs_pbde153_cadj_Log2), which were crucial in splitting the data. The pruned tree reveals the hierarchical influence of these variables and others such as log-transformed levels of DDE (dichlorodiphenyldichloroethylene), MiBP (Mmno-isobutyl phthalate), and PFOA (perfluorooctanoic acid) on the BMI Z-score outcomes. The best complexity parameter (cp) value from cross-validation was 0.023, indicating the optimal point at which further pruning did not improve model performance.

Random Forest


##                      IncNodePurity
## hs_child_age_None        41.267546
## e3_sex_None               5.540866
## e3_yearbir_None          31.564485
## h_bfdur_Ter              13.136212
## hs_bakery_prod_Ter       20.689578
## hs_break_cer_Ter         13.679182
## hs_dairy_Ter             11.181729
## hs_fastfood_Ter          11.895794
## hs_org_food_Ter          10.856862
## hs_proc_meat_Ter         10.827847
## hs_total_fish_Ter        10.984827
## hs_total_fruits_Ter      13.977047
## hs_total_lipids_Ter      12.980031
## hs_total_sweets_Ter      10.749403
## hs_total_veg_Ter         12.258026
## hs_cd_c_Log2             44.886048
## hs_co_c_Log2             45.054544
## hs_cs_c_Log2             34.878871
## hs_cu_c_Log2             60.387604
## hs_hg_c_Log2             43.835480
## hs_mo_c_Log2             50.597285
## hs_pb_c_Log2             39.126962
## hs_dde_cadj_Log2         71.115165
## hs_pcb153_cadj_Log2      74.294671
## hs_pcb170_cadj_Log2     130.998985
## hs_dep_cadj_Log2         50.333164
## hs_pbde153_cadj_Log2     92.865989
## hs_pfhxs_c_Log2          38.593526
## hs_pfoa_c_Log2           53.392093
## hs_pfos_c_Log2           44.360304
## hs_prpa_cadj_Log2        43.848750
## hs_mbzp_cadj_Log2        49.661827
## hs_mibp_cadj_Log2        38.399318
## hs_mnbp_cadj_Log2        45.955350
## Diet + Chemical + Covariates Random Forest RMSE: 1.024848
## 10-Fold CV Random Forest RMSE: 1.025544
The random forest model yielded an RMSE of 1.025 and a cross-validated RMSE of 1.026, demonstrating robust performance. Key variables contributing to this model’s effectiveness include polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2), polybrominated diphenyl ether-153 (hs_pbde153_cadj_Log2), dichlorodiphenyldichloroethylene (hs_dde_cadj_Log2), copper (hs_cu_c_Log2), and perfluorooctanoic acid (hs_pfoa_c_Log2). These variables were identified as having the highest importance, significantly influencing the model’s predictive accuracy by reducing prediction errors and providing valuable insights into the factors affecting childhood BMI.

GBM

 
 
var
<chr>
rel.inf
<dbl>
hs_pcb170_cadj_Log2	hs_pcb170_cadj_Log2	35.4330180
hs_pbde153_cadj_Log2	hs_pbde153_cadj_Log2	19.7849701
hs_dde_cadj_Log2	hs_dde_cadj_Log2	7.6514887
hs_pcb153_cadj_Log2	hs_pcb153_cadj_Log2	6.7808127
hs_pfoa_c_Log2	hs_pfoa_c_Log2	5.8643210
hs_cu_c_Log2	hs_cu_c_Log2	5.2890641
hs_mbzp_cadj_Log2	hs_mbzp_cadj_Log2	2.5382805
hs_bakery_prod_Ter	hs_bakery_prod_Ter	2.1928474
hs_mo_c_Log2	hs_mo_c_Log2	2.0194567
hs_dep_cadj_Log2	hs_dep_cadj_Log2	2.0147669
1-10 of 34 rows


## Diet + Chemical + Covariates GBM RMSE: 1.072432
## 10-Fold CV GBM RMSE: 1.048183
The RMSE for the GBM model is 1.072, with a cross-validated RMSE of 1.048, demonstrating good accuracy and improvement over iterations. Key variables in the model include polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2), polybrominated diphenyl ether-153 (hs_pbde153_cadj_Log2), dichlorodiphenyldichloroethylene (hs_dde_cadj_Log2), perfluorooctanoic acid (hs_pfoa_c_Log2), and copper (hs_cu_c_Log2). These variables exhibit the highest relative influence, significantly contributing to reducing prediction errors and highlighting their importance in the model’s predictive capability.

Model Comparison:
The GBM model demonstrated the best overall performance with a cross-validated RMSE of 1.048, slightly better than the random forest model’s cross-validated RMSE of 1.026. This suggests that GBM’s iterative boosting approach may be more effective in capturing the complex relationships within the data.

Another notable observation is the consistent importance of certain variables across all models. Variables such as PCBs (hs_pcb170_cadj_Log2), PBDE-153 (hs_pbde153_cadj_Log2), DDE (hs_dde_cadj_Log2), copper (hs_cu_c_Log2), and PFOA (hs_pfoa_c_Log2) consistently emerged as significant predictors, highlighting their strong influence on childhood BMI Z-scores.

The decision tree model’s pruning process and cross-validation led to a substantial reduction in overfitting, improving its performance, as shown by the decrease in RMSE from 1.129 to 1.090. This underscores the importance of model regularization techniques in enhancing predictive accuracy.

The comparison between the group LASSO, ridge, and elastic net models highlights the effectiveness of regularization techniques in handling high-dimensional data. The elastic net model, with an RMSE of 1.032 after cross-validation, effectively balanced the inclusion of significant predictors, combining the strengths of both LASSO and ridge penalties.

Overall, each model revealed significant predictors of BMI Z-scores, with environmental chemicals, dietary factors, and demographic covariates playing critical roles in influencing childhood BMI.

Diet + Chemical + Metabolomic + Covariates
Group LASSO
## Group Lasso Test RMSE: 0.9334466
## Optimal lambda: 0.01400055
Variable
<chr>
Coefficient
<dbl>
hs_child_age_None	-0.0916926302
e3_sex_Nonefemale	-0.1389478308
e3_sex_Nonemale	0.1389478308
e3_yearbir_None2004	-0.1209720606
e3_yearbir_None2005	0.0775549602
e3_yearbir_None2006	0.1151189975
e3_yearbir_None2007	0.1266194158
e3_yearbir_None2008	0.0652023471
e3_yearbir_None2009	0.4242776869
hs_cd_c_Log2	-0.0081890500
...
1-10 of 231 rows
## Group LASSO RMSE with 10-fold CV: 0.8748226
The group LASSO model for predicting BMI Z-score using diet, chemical, metabolomic data, and covariates produced an RMSE of 0.9334 on the test set and an improved RMSE of 0.8748 with 10-fold cross-validation. The optimal lambda for this model was found to be 0.014. The model identified several key metabolites with significant coefficients. On the positive side, metabolite 161 had the highest positive coefficient (2.8164), followed by metabolites 95 (1.3657), 88 (0.8329), 59 (0.7794), and 124 (0.7499). These positive coefficients suggest that higher levels of these metabolites are associated with an increase in BMI Z-score. Conversely, metabolite 160 had the highest negative coefficient (-3.2241), indicating a strong negative association with BMI Z-score, followed by metabolites 89 (-1.8773), 82 (-1.4959), 138 (-1.0762), and 125 (-1.0322). These negative coefficients indicate that higher levels of these metabolites are associated with a decrease in BMI Z-score.

Group Ridge
## Group Ridge RMSE: 0.9424999
## Optimal lambda: 0.02446636
Variable
<chr>
Coefficient
<dbl>
hs_child_age_None	-0.144696523
e3_sex_Nonefemale	-0.186682840
e3_sex_Nonemale	0.186682840
e3_yearbir_None2004	-0.121966602
e3_yearbir_None2005	0.027392637
e3_yearbir_None2006	0.042900372
e3_yearbir_None2007	0.033202771
e3_yearbir_None2008	-0.034971941
e3_yearbir_None2009	0.244784928
hs_cd_c_Log2	-0.003195596
...
1-10 of 231 rows
## Group Ridge RMSE with 10-fold CV: 0.8849928
The group ridge model’s optimal lambda value identified through cross-validation was 0.024, which balances the model’s complexity and fit. The top five positive coefficients include metabolomic variables: metab_161, metab_95, metab_90, metab_59, and metab_177, suggesting these metabolites are positively associated with the outcome. Conversely, the top five negative coefficients, metab_160, metab_89, metab_82, metab_135, and metab_138, indicate a negative association with BMI Z-score. The model’s RMSE for the test set was 0.942, and the RMSE with 10-fold cross-validation was 0.885, demonstrating good predictive performance and suggesting the inclusion of these variables captures significant variance related to BMI Z-score.

Group Elastic Net
## Group Elastic Net RMSE: 0.9440745
## Optimal lambda: 0.0185079
Variable
<chr>
Coefficient
<dbl>
hs_child_age_None	-0.143644690
e3_sex_Nonefemale	-0.186367794
e3_sex_Nonemale	0.186367794
e3_yearbir_None2004	-0.121499288
e3_yearbir_None2005	0.026941250
e3_yearbir_None2006	0.042489109
e3_yearbir_None2007	0.033671755
e3_yearbir_None2008	-0.034371481
e3_yearbir_None2009	0.243607566
hs_cd_c_Log2	-0.003365152
...
1-10 of 231 rows
## Group Elastic Net RMSE with 10-fold CV: 0.8844928
The group elastic net model demonstrated an RMSE of 0.9441 on the test set, which improved to 0.8845 with 10-fold cross-validation, indicating a strong predictive performance. The optimal lambda value was 0.0185. The top five positive coefficients, reflecting variables with the strongest positive associations, included metabolomic variables metab_161, metab_95, metab_90, metab_59, and metab_177, with metab_161 showing the highest positive coefficient of 3.6039. Conversely, the variables metab_160, metab_89, metab_82, metab_135, and metab_138 had the most substantial negative associations, with metab_160 exhibiting the largest negative coefficient of -4.0738. These results suggest that these specific metabolites have significant associations with the BMI Z-scores, either increasing or decreasing them, which could provide insights into the biological pathways influencing BMI in children.

Decision Trees


## Full Decision Tree RMSE: 1.243108
## 
## Regression tree:
## rpart(formula = hs_zbmi_who ~ ., data = train_data, method = "anova")
## 
## Variables actually used in tree construction:
##  [1] hs_cu_c_Log2        hs_dde_cadj_Log2    hs_pcb170_cadj_Log2
##  [4] metab_100           metab_129           metab_140          
##  [7] metab_141           metab_142           metab_157          
## [10] metab_161           metab_176           metab_47           
## [13] metab_58            metab_8             metab_94           
## [16] metab_95           
## 
## Root node error: 1254/841 = 1.4911
## 
## n= 841 
## 
##          CP nsplit rel error  xerror     xstd
## 1  0.089116      0   1.00000 1.00275 0.052776
## 2  0.069078      1   0.91088 0.94590 0.050339
## 3  0.037249      2   0.84181 0.91981 0.049729
## 4  0.034324      3   0.80456 0.90111 0.048711
## 5  0.025576      4   0.77023 0.89055 0.049604
## 6  0.021936      5   0.74466 0.90166 0.048993
## 7  0.021276      6   0.72272 0.90895 0.049515
## 8  0.020244      8   0.68017 0.90807 0.050310
## 9  0.016938      9   0.65992 0.91277 0.050356
## 10 0.015553     10   0.64299 0.90306 0.050272
## 11 0.015178     11   0.62743 0.90122 0.050368
## 12 0.014756     12   0.61226 0.90066 0.050300
## 13 0.014022     13   0.59750 0.91203 0.051412
## 14 0.013859     14   0.58348 0.92227 0.051732
## 15 0.012010     15   0.56962 0.93488 0.053622
## 16 0.011088     16   0.55761 0.93327 0.053609
## 17 0.011027     17   0.54652 0.92988 0.053560
## 18 0.010000     18   0.53549 0.93467 0.053891




## Pruned Decision Tree RMSE: 1.12821
## Best cp value from cross-validation: 0.036




## Unpruned Decision Tree RMSE: 1.243108
## Pruned Decision Tree RMSE with Best cp: 1.127666
The key variables identified include polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2), metab_95, metab_129, and several metabolomics variables such as metab_161, metab_140, and metab_176. The unpruned model had an RMSE of 1.243, while the pruned model, which used the optimal cp value from cross-validation, had an RMSE of 1.128. This indicates that pruning improved the model’s accuracy by reducing overfitting, resulting in better performance on the test data.

Random Forest
##                       IncNodePurity
## hs_child_age_None         4.7927709
## e3_sex_None               0.5707810
## e3_yearbir_None           5.3687139
## hs_cd_c_Log2              4.8057550
## hs_co_c_Log2              5.5171622
## hs_cs_c_Log2              5.0356667
## hs_cu_c_Log2             12.4603237
## hs_hg_c_Log2              6.5609155
## hs_mo_c_Log2              9.6711331
## hs_pb_c_Log2              6.0711093
## hs_dde_cadj_Log2         13.2357957
## hs_pcb153_cadj_Log2      42.5218764
## hs_pcb170_cadj_Log2      78.6536355
## hs_dep_cadj_Log2          5.7451267
## hs_pbde153_cadj_Log2     28.0252092
## hs_pfhxs_c_Log2           5.4200119
## hs_pfoa_c_Log2            9.0245854
## hs_pfos_c_Log2            6.9947002
## hs_prpa_cadj_Log2         5.0401167
## hs_mbzp_cadj_Log2         4.4169868
## hs_mibp_cadj_Log2         4.0028339
## hs_mnbp_cadj_Log2         5.0996136
## h_bfdur_Ter               2.8968599
## hs_bakery_prod_Ter        2.9013737
## hs_dairy_Ter              1.2216138
## hs_fastfood_Ter           0.9580573
## hs_org_food_Ter           1.1570809
## hs_readymade_Ter          1.4572844
## hs_total_bread_Ter        1.1592172
## hs_total_fish_Ter         1.4961459
## hs_total_fruits_Ter       1.1767595
## hs_total_lipids_Ter       1.3061318
## hs_total_potatoes_Ter     1.2547008
## hs_total_sweets_Ter       0.9540810
## hs_total_veg_Ter          1.0142937
## metab_1                   4.5011841
## metab_2                   4.1531041
## metab_3                   3.4379265
## metab_4                   5.7831834
## metab_5                   2.9178829
## metab_6                   9.2084145
## metab_7                   4.5028527
## metab_8                  36.1613265
## metab_9                   2.8921966
## metab_10                  3.3253911
## metab_11                  4.0194203
## metab_12                  3.3756205
## metab_13                  4.1227190
## metab_14                  5.2837840
## metab_15                  4.4314031
## metab_16                  2.6462109
## metab_17                  2.4025892
## metab_18                  3.0563512
## metab_19                  2.2951339
## metab_20                  3.9067077
## metab_21                  2.8607845
## metab_22                  2.6869075
## metab_23                  2.8972758
## metab_24                  3.7219939
## metab_25                  3.4797174
## metab_26                  7.4516177
## metab_27                  3.3263961
## metab_28                  3.6858414
## metab_29                  3.3029111
## metab_30                 18.5312981
## metab_31                  3.4436727
## metab_32                  3.0545040
## metab_33                  5.2038360
## metab_34                  2.4118531
## metab_35                  7.7143364
## metab_36                  3.8489845
## metab_37                  3.5293186
## metab_38                  2.5404708
## metab_39                  2.5165610
## metab_40                  5.1546331
## metab_41                  3.8921235
## metab_42                  6.1284140
## metab_43                  3.4008043
## metab_44                  3.5698540
## metab_45                  3.6758543
## metab_46                  5.1802108
## metab_47                  6.2120208
## metab_48                 11.7806465
## metab_49                 33.0932505
## metab_50                  9.9343588
## metab_51                  6.2231737
## metab_52                  3.3042007
## metab_53                  5.1286048
## metab_54                  4.9482602
## metab_55                  7.9980726
## metab_56                  4.6904911
## metab_57                  4.7919533
## metab_58                  3.2769554
## metab_59                  5.7319035
## metab_60                  3.9192335
## metab_61                  3.0283668
## metab_62                  4.3267745
## metab_63                  4.8698592
## metab_64                  3.9307501
## metab_65                  3.8785658
## metab_66                  2.5032525
## metab_67                  2.7330496
## metab_68                  3.5029673
## metab_69                  2.4526201
## metab_70                  3.2796735
## metab_71                  4.6222410
## metab_72                  3.4044271
## metab_73                  3.0460977
## metab_74                  2.7018733
## metab_75                  3.8889307
## metab_76                  2.8113720
## metab_77                  4.7832198
## metab_78                  4.9096271
## metab_79                  4.0912870
## metab_80                  3.5334220
## metab_81                  3.3897748
## metab_82                  4.6950398
## metab_83                  3.3638699
## metab_84                  3.0885189
## metab_85                  4.6423208
## metab_86                  3.2104952
## metab_87                  3.8282082
## metab_88                  2.8852207
## metab_89                  2.7940235
## metab_90                  2.6775937
## metab_91                  3.2999703
## metab_92                  3.4644294
## metab_93                  2.8208312
## metab_94                  8.2011811
## metab_95                 51.6744901
## metab_96                  8.1118854
## metab_97                  3.0816526
## metab_98                  3.2655000
## metab_99                  4.4506345
## metab_100                 3.9391564
## metab_101                 3.6374127
## metab_102                 5.7070910
## metab_103                 4.1270357
## metab_104                 5.6319496
## metab_105                 3.3000728
## metab_106                 3.4540736
## metab_107                 3.8068032
## metab_108                 4.0689264
## metab_109                 5.3846332
## metab_110                 7.8695016
## metab_111                 2.7218197
## metab_112                 2.7613608
## metab_113                 5.5357192
## metab_114                 4.3740721
## metab_115                 4.3476546
## metab_116                 6.1735729
## metab_117                 7.0544259
## metab_118                 2.4601605
## metab_119                 5.4450427
## metab_120                 7.1242577
## metab_121                 3.7051871
## metab_122                 6.2282665
## metab_123                 3.2628782
## metab_124                 3.3382452
## metab_125                 3.4201616
## metab_126                 2.4057902
## metab_127                 5.0861475
## metab_128                 6.4178268
## metab_129                 4.2203870
## metab_130                 3.4512521
## metab_131                 3.2548319
## metab_132                 3.2654363
## metab_133                 2.6708217
## metab_134                 3.2328840
## metab_135                 5.2587159
## metab_136                 5.0406508
## metab_137                 6.3400908
## metab_138                 4.7455979
## metab_139                 3.7303384
## metab_140                 2.7325221
## metab_141                 7.9353350
## metab_142                13.5320442
## metab_143                 9.6865623
## metab_144                 3.9033383
## metab_145                 4.2785181
## metab_146                 4.2770667
## metab_147                 3.5426166
## metab_148                 3.3025573
## metab_149                 5.6260285
## metab_150                 4.9789354
## metab_151                 3.5939464
## metab_152                 4.7580724
## metab_153                 4.3991465
## metab_154                 5.0953881
## metab_155                 2.5069093
## metab_156                 2.8819060
## metab_157                 4.3767383
## metab_158                 3.9225685
## metab_159                 3.3643529
## metab_160                 7.0114089
## metab_161                28.1188870
## metab_162                 3.9630717
## metab_163                14.4399347
## metab_164                 7.1747718
## metab_165                 3.9310471
## metab_166                 3.8429719
## metab_167                 3.3589423
## metab_168                 3.1719266
## metab_169                 4.2720474
## metab_170                 4.2149550
## metab_171                 4.9419993
## metab_172                 3.7296383
## metab_173                 4.0956131
## metab_174                 4.6193564
## metab_175                 3.7661891
## metab_176                 6.2453467
## metab_177                14.2757880


## Diet + Chemical + Metabolomic + Covariates Random Forest RMSE: 1.247886
## 10-Fold CV Random Forest RMSE: 1.004854
The IncNodePurity values indicate that “hs_pcb170_cadj_Log2” is the most influential variable, followed by “metab_95,” “hs_pcb153_cadj_Log2,” and “metab_8.” The model has an RMSE of 1.0047 for the training set and 1.0048 for the 10-fold cross-validation, suggesting a consistent performance with minimal overfitting. Comparing the pruned and unpruned models, the pruned model with cross-validation resulted in a lower RMSE, indicating better generalization and reduced complexity without sacrificing accuracy.

GBM
## Iter   TrainDeviance   ValidDeviance   StepSize   Improve
##      1        1.4860             nan     0.0100    0.0031
##      2        1.4799             nan     0.0100    0.0042
##      3        1.4751             nan     0.0100    0.0037
##      4        1.4720             nan     0.0100    0.0007
##      5        1.4668             nan     0.0100    0.0043
##      6        1.4622             nan     0.0100    0.0017
##      7        1.4565             nan     0.0100    0.0049
##      8        1.4519             nan     0.0100    0.0038
##      9        1.4470             nan     0.0100    0.0034
##     10        1.4429             nan     0.0100    0.0026
##     20        1.3973             nan     0.0100    0.0033
##     40        1.3199             nan     0.0100    0.0026
##     60        1.2519             nan     0.0100    0.0015
##     80        1.1922             nan     0.0100    0.0020
##    100        1.1425             nan     0.0100    0.0008
##    120        1.0943             nan     0.0100    0.0013
##    140        1.0515             nan     0.0100    0.0003
##    160        1.0125             nan     0.0100    0.0003
##    180        0.9736             nan     0.0100    0.0003
##    200        0.9397             nan     0.0100    0.0008
##    220        0.9070             nan     0.0100    0.0012
##    240        0.8800             nan     0.0100    0.0009
##    260        0.8535             nan     0.0100   -0.0001
##    280        0.8275             nan     0.0100    0.0005
##    300        0.8029             nan     0.0100    0.0002
##    320        0.7809             nan     0.0100    0.0003
##    340        0.7594             nan     0.0100    0.0003
##    360        0.7400             nan     0.0100    0.0000
##    380        0.7220             nan     0.0100    0.0000
##    400        0.7042             nan     0.0100    0.0003
##    420        0.6874             nan     0.0100    0.0002
##    440        0.6711             nan     0.0100    0.0003
##    460        0.6552             nan     0.0100    0.0000
##    480        0.6392             nan     0.0100   -0.0001
##    500        0.6237             nan     0.0100   -0.0002
##    520        0.6107             nan     0.0100    0.0000
##    540        0.5974             nan     0.0100    0.0000
##    560        0.5852             nan     0.0100   -0.0002
##    580        0.5728             nan     0.0100    0.0001
##    600        0.5612             nan     0.0100   -0.0001
##    620        0.5500             nan     0.0100   -0.0004
##    640        0.5386             nan     0.0100    0.0002
##    660        0.5285             nan     0.0100    0.0000
##    680        0.5187             nan     0.0100   -0.0001
##    700        0.5086             nan     0.0100   -0.0001
##    720        0.4995             nan     0.0100   -0.0001
##    740        0.4900             nan     0.0100    0.0001
##    760        0.4813             nan     0.0100   -0.0001
##    780        0.4729             nan     0.0100   -0.0000
##    800        0.4645             nan     0.0100   -0.0001
##    820        0.4565             nan     0.0100   -0.0002
##    840        0.4491             nan     0.0100   -0.0001
##    860        0.4409             nan     0.0100    0.0000
##    880        0.4336             nan     0.0100   -0.0002
##    900        0.4267             nan     0.0100   -0.0001
##    920        0.4197             nan     0.0100   -0.0001
##    940        0.4133             nan     0.0100   -0.0001
##    960        0.4067             nan     0.0100   -0.0000
##    980        0.4007             nan     0.0100   -0.0002
##   1000        0.3943             nan     0.0100   -0.0001

 
 
var
<chr>
rel.inf
<dbl>
hs_pcb170_cadj_Log2	hs_pcb170_cadj_Log2	9.135890416
metab_95	metab_95	5.934215453
metab_161	metab_161	4.786362205
metab_8	metab_8	4.726338249
metab_49	metab_49	4.140728488
hs_pbde153_cadj_Log2	hs_pbde153_cadj_Log2	3.377977777
metab_163	metab_163	2.799558519
metab_142	metab_142	2.501077746
metab_48	metab_48	2.395935958
metab_177	metab_177	2.039847873
...
1-10 of 212 rows


## Diet + Chemical + Metabolomic + Covariates GBM RMSE: 0.9537
## 10-Fold CV GBM RMSE: 0.9526345
The GBM model shows that the most influential variable is polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2), followed by metab_95, metab_161, metab_8, and metab_49. The GBM model’s RMSE is 0.954, indicating good predictive performance. The cross-validated RMSE is 0.953, showing consistent performance across different folds. The variables polychlorinated biphenyl-170 and metab_95 have the highest relative influence, suggesting significant roles in predicting the outcome.

Model Comparison:
In the model comparison for the diet, chemical, metabolomic, and covariates dataset, the GBM performed the best with an RMSE of 0.9537, closely followed by the group LASSO model with an RMSE of 0.8748. The random forest model also showed strong performance with an RMSE of 1.0047. Key variables that consistently appeared across the models as important predictors include specific metabolites (metab_161, metab_95, metab_160, metab_8) and chemical exposure variables (hs_pcb170_cadj_Log2, hs_pbde153_cadj_Log2). These variables highlight the critical influence of specific PCB levels and metabolites in predicting health outcomes.

Conclusion
Overall Findings
Throughout the analysis, specific variables consistently emerged as significant predictors of BMI Z-scores in children. Variables such as polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2), polybrominated diphenyl ether-153 (hs_pbde153_cadj_Log2), and various metabolites (metab_161, metab_95, metab_160) were highlighted across multiple models, indicating their strong influence on the outcome. Notably, higher levels of copper (hs_cu_c_Log2) and certain metabolites (metab_161, metab_95) were consistently associated with an increased BMI Z-score, suggesting their role in contributing to higher BMI. Conversely, variables such as cadmium (hs_cd_c_Log2) and specific metabolites (metab_160, metab_89) showed negative associations with BMI Z-score, indicating a potential protective effect against increased BMI. These findings imply that both environmental chemical exposures and specific metabolic profiles play crucial roles in childhood BMI outcomes, emphasizing the need for comprehensive interventions targeting these factors to mitigate obesity risk and promote healthier growth trajectories.

The LASSO, ridge, and elastic net models consistently demonstrated strong performance across various datasets, achieving the lowest RMSEs, particularly when including diet, chemical, metabolomic, and covariates. The incorporation of metabolomic data significantly enhanced model performance, underscoring their predictive power concerning BMI. Decision trees generally exhibited moderate performance, with pruning enhancing RMSE values. Nonetheless, the full decision tree models were less effective compared to regularized regression models. Random Forest and GBM models exhibited robust performance, with GBM marginally surpassing Random Forest. The integration of diverse data types (diet, chemical, metabolomic) led to improved RMSE values, showcasing the advantage of a comprehensive data approach.

Among the models tested, the GBM with all variables exhibited the best overall performance with an RMSE of 0.9537, closely followed by the group LASSO model with an RMSE of 0.8748, demonstrating superior predictive accuracy and generalization capabilities.

The results imply that certain environmental chemicals and metabolites play crucial roles in influencing BMI Z-scores in children. The high predictive accuracy of models like GBM and group LASSO underscores the importance of these variables. Higher levels of certain metabolites and chemical exposures were associated with significant changes in BMI Z-scores, suggesting potential areas for intervention to manage or mitigate obesity in children. The findings indicate that environmental and dietary factors, alongside inherent covariates like age, have substantial impacts on children’s health outcomes, specifically BMI.

Limitations & Future
One of the limitations of this study is the exclusion of 103 rows with missing values from the combined dataset, which represents approximately 8% of the total data. This decision was made to ensure the integrity and robustness of our analysis, as many statistical methods and machine learning algorithms require complete data. However, this exclusion may have introduced some issues. The excluded rows might have specific characteristics that differ from the rest of the dataset. As a result, the cleaned dataset may not fully capture the diversity and variability of the original population, potentially limiting the representativeness of the study’s findings. In future studies, alternative methods such as imputation techniques could be explored to handle missing data, potentially preserving more information and reducing the risk of bias.

Some covariates related to pregnancy, such as sex and year of birth, were included in the analysis as they were considered potentially relevant. However, their direct relevance to the specific outcomes studied might be limited, which could introduce some noise or confounding effects. There may have been other variables that might have been relevant but have been overlooked in this study. So for future studies, it might be possible to look at the impact of other potential covariates and confounders on the outcomes of interest.
