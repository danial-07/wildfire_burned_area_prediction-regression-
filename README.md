# wildfire_burned_area_prediction-regression-
Predicts burned forest area using weather variables, fire indices, temporal features, and spatial location with machine learning.


# Results and Discussion
## Model Performance Comparison

Three regression models were evaluated to predict forest burned area using meteorological and spatial variables: a baseline mean predictor, a Gaussian Support Vector Machine (SVM), and a Random Forest (RF) model. All models were trained on a logarithmically transformed target variable, ln(area + 1), to address the strong skewness in burned area distribution.

The baseline model produced a Mean Absolute Error (MAE) of 1.20 and a Root Mean Squared Error (RMSE) of 1.48, serving as a reference point. The Gaussian SVM model, after hyperparameter tuning, achieved the lowest MAE (1.13) among all models, indicating superior accuracy in predicting typical fire events. However, its RMSE (1.61) was higher than that of the baseline model. The Random Forest model resulted in an MAE of 1.20 and an RMSE of 1.52, performing worse than the SVM and only marginally better than the baseline.

| Model                         | MAE (↓)   | RMSE (↓)  | Strengths               | Weaknesses                    |
| ----------------------------- | --------- | --------- | ----------------------- | ----------------------------- |
| **Baseline (Mean Predictor)** | 1.203     | **1.483** | Minimizes squared error | Cannot model fire behavior    |
| **Gaussian SVM (Tuned)**      | **1.133** | 1.609     | Best for small fires    | Sensitive to rare large fires |
| **Random Forest**             | 1.198     | 1.516     | Handles nonlinearity    | Limited by data skewness      |


## Interpretation of Error Metrics

The lower MAE achieved by the Gaussian SVM demonstrates its effectiveness in predicting small-scale fires, which constitute the majority of observations in the dataset. Since MAE assigns equal weight to all prediction errors, it is particularly suited to skewed datasets dominated by low target values.

In contrast, RMSE penalizes larger errors more heavily. The baseline mean predictor achieved the lowest RMSE because it consistently predicts moderate values and avoids extreme deviations. However, such behavior is not informative for practical fire prediction, as it fails to capture variability in fire severity.

The Random Forest model, despite its ability to model nonlinear relationships, struggled to outperform the SVM. This is attributed to the limited dataset size and the rarity of large fire events, which restrict the model’s ability to learn robust patterns for extreme burned areas.

## Comparison with Previous Studies

The observed results are consistent with findings reported by Cortez and Morais (2007), where Gaussian SVM models outperformed other approaches in terms of MAE but not RMSE. The authors similarly concluded that SVMs are more reliable for predicting frequent low-intensity fires, while large fires remain difficult to model due to their scarcity and stochastic nature.

## Implications and Limitations

These results highlight the inherent difficulty of predicting burned forest area using meteorological variables alone. While machine learning models such as SVMs can effectively predict small fire events, accurately modeling large-scale fires remains challenging. The limited number of extreme events, combined with high environmental variability, constrains model performance.

Future improvements may require the integration of additional explanatory variables such as fuel load, vegetation type, topography, and human activity indicators, as well as the use of hybrid or probabilistic modeling approaches.

## Overall Conclusion

Among the evaluated models, the Gaussian SVM demonstrated the best overall predictive performance for typical fire events, making it the most suitable model for this dataset. The results confirm that skewed environmental regression problems benefit from logarithmic transformations and error metrics that emphasize typical prediction accuracy rather than rare extremes.
