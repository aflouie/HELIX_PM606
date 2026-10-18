# HELIX_PM606

Download PM606Report.html to look at interactive report.

Analysis of Environmental Exposures, Diet, and Metabolomics on Child BMI Z-Score
Abstract
Background: Identifying the key predictors of childhood Body Mass Index (BMI) is crucial for informing effective health interventions, given the significant impacts of diet, chemical exposures, and metabolomic profiles on health outcomes. Understanding the multifactorial influences is crucial for developing effective interventions and policies.

Objective: This study aims to predict childhood BMI Z-scores by integrating comprehensive data on postnatal diet, chemical exposures, and serum metabolomics, using advanced statistical models.

Methods: Data from the HELIX study, including 1301 mother-child pairs aged 6-11 years, were analyzed. Data was split into training (70%) and test (30%) sets. Various modeling approaches, including LASSO, ridge, elastic net, decision tree, random forest, and gradient boosting machine (GBM), with 10-fold cross-validation used to evaluate model performance and ensure robustness. Models were evaluated based on their Root Mean Squared Error (RMSE) and the significance of the predictors identified.

Results: The results demonstrate that models incorporating a comprehensive set of variables (diet, chemicals, metabolomics, and covariates) consistently outperformed those with fewer variables. The inclusion of metabolomic data significantly improved model performance. GBM model with all variables demonstrated the best performance with a cross-validated RMSE of 0.9537, followed closely by the group LASSO model with an RMSE of 0.8748. Key predictors identified across the models included age and sex, specific metabolites such as metab_161 (coefficient 3.5751), metab_95 (1.3657), and metab_160 (-3.2241), along with chemical exposures like polychlorinated biphenyl-170 (hs_pcb170_cadj_Log2). The random forest model also showed strong performance with an RMSE of 1.0047.

Conclusion: Integrating demographic, dietary, chemical, and metabolomic data provides robust predictions for BMI in children. Advanced machine learning techniques, particularly GBM and Random Forest, significantly enhance predictive performance. These findings underscore the importance of utilizing diverse data types to understand and address childhood obesity effectively.
