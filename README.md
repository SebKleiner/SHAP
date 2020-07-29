# SHAP
This is an adaptation of Shir Meir's (Lead Data Scientist @ Intuit) notebooks.

Please, go to this Github https://github.com/shirmeir/notebooks for notebooks that I've based my analysis.

My main goal was to add the SHAP module explanations to her notebooks in order to produce meaningful insights to her models. The main analysis is performed over an XGBoost model with features replaced as conditional probabilities to predict income from census income data UCI repository.

**SHAP**

What is SHAP (SHapley Additive exPlanations)? It is a game theoretic approach to explain the output of any machine learning model. It connects optimal credit allocation with local explanations using the classic Shapley values from game theory and their related extensions. Basically, it analyzes the marginal contribution of each variable to the dependent one.

![alt text](https://github.com/SebKleiner/SHAP/blob/master/shap0.png?raw=true)

**Visualize single prediction**

![alt text](https://github.com/SebKleiner/SHAP/blob/master/shap1.png?raw=true)

The above explanation shows features each contributing to push the model output from the base value (the average model output over the training dataset we passed) to the model output. Features pushing the prediction higher are shown in red, those pushing the prediction lower are in blue

**Visualize many predictions**

![alt text](https://github.com/SebKleiner/SHAP/blob/master/shap2.png?raw=true)

**SHAP summary plot**

This is the graph that I love most from SHAP modules.

![alt text](https://github.com/SebKleiner/SHAP/blob/master/shap3.png?raw=true)

Rather than use a typical feature importance bar chart, we use a density scatter plot of SHAP values for each feature to identify how much impact each feature has on the model output for individuals in the test dataset. Features are sorted by the sum of the SHAP value magnitudes across all samples. It is interesting to note that the marital status feature has more total model impact than the captial gain feature, but for those samples where capital gain matters it has more impact than age. In other words, capital gain affects a few predictions by a large amount, while age affects all predictions by a smaller amount.

**SHAP dependence plots**

SHAP dependence plots show the effect of a single feature across the whole dataset. They plot a feature's value vs. the SHAP value of that feature across many samples. SHAP dependence plots are similar to partial dependence plots, but account for the interaction effects present in the features, and are only defined in regions of the input space supported by data. The vertical dispersion of SHAP values at a single feature value is driven by interaction effects, and another feature is chosen for coloring to highlight possible interactions.

Please refer to the notebook to view multiple graphs between dependent variables.
