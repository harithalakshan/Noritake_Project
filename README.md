Modeling Foot Warpage in Porcelain Manufacturing: A Beta Regression Approach

📌 Project Overview

This project addresses a critical industrial challenge in porcelain cup manufacturing: foot warpage. Conducted in collaboration with Noritake Lanka Porcelain Private Limited, this study aims to identify, quantify, and model the relationship between key manufacturing process variables and the final defect rate (warp percentage).By developing a robust predictive framework, the ultimate goal is to optimize the jiggering and drying processes to minimize defects and improve overall yield accuracy.

🎯 ObjectivesAnalyze

the relationship between physical clay properties (hardness, moisture) and resulting foot warpage.Identify the most significant process variables contributing to the defect using statistical analysis and regression modeling.Develop a predictive decision framework to control warpage during the manufacturing lifecycle.

📊 Data & Variables

Process data was tracked across multiple stages of the cup-making workflow. Due to production scheduling constraints, an expanded dataset was simulated using company-specified standard parameters to demonstrate the viability of the analytical workflow.Key Process Variables Analyzed:Clay Hardness: Measured prior to shaping.Clay Moisture (%): Calculated pre-jiggering.Drying Temperature 1 & 2 (°C): Recorded during the first and second drying phases.Unloading Moisture 1 & 2 (%): Measured after respective drying stages.Target Variable: warp_percentage (a continuous proportion bounded between 0 and 1).

🧠 Methodology: Beta Regression

Standard linear models (like OLS) and count models (Poisson, Negative Binomial) were unsuitable because the target variable is a continuous proportion strictly within the (0, 1) interval.To handle the inherent heteroscedasticity and non-normal distribution of proportional data, a Beta Regression model with a logit link function was implemented:

$logit(\mu_{i})=ln(\frac{\mu_{i}}{1-\mu_{i}})=\beta_{0}+\beta_{1}X_{1}+\beta_{2}X_{2}+...+\beta_{k}X_{k}$ 

Model Development & ValidationFeature Selection: 

Iterative backward and forward selection based on Akaike Information Criterion (AIC) and Pseudo $R^2$ values.Interaction Effects: Identified a highly significant two-way interaction between clay_moisture and drying_temperature_1.Validation: 10-fold cross-validation was applied to the training dataset to ensure robustness.Diagnostics: Comprehensive residual analysis was conducted, confirming no severe multicollinearity (VIF < 10) and no significant influential outliers via Cook's Distance.

📈 Performance Metrics

The final model demonstrated strong predictive performance and excellent generalization to unseen testing data.Test $R^2$: 0.7718 Test RMSE: 0.0435 Pseudo $R^2$ (Training): 0.7225 

💡 Key Business Insights & Recommendations

Based on the marginal effect plots and model coefficients, the following preliminary process adjustments were identified to minimize defect rates:
Clay Hardness: Maintain Durometer readings strictly below 80.
Moisture Control: Ensure First Unloading Moisture remains above 20% and Second Unloading Moisture remains above 10% for dimensional stability.
Temperature-Moisture Balance: Optimize the drying process by maintaining initial clay moisture between 25-30% while keeping drying temperatures below 50°C.
