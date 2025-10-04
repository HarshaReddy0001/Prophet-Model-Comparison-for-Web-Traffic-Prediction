# Wikipedia Page View Forecasting with Prophet

## Table of Contents

1.  [Overview and Goal](#overview-and-goal)
2.  [Technologies Used](#technologies-used)
3.  [Methodology](#methodology)
4.  [Results / Conclusion](#results--conclusion)
5.  [Feature Importance](#feature-importance)
6.  [Business Value](#business-value)
7.  [Next Steps & Contact](#next-steps--contact)

## Overview and Goal

The goal of this project is to accurately forecast daily page views for a specific Wikipedia page using Meta's Prophet library. By analyzing historical page view data from the `example_wp_log_peyton_manning.csv` dataset, the project aims to build and evaluate different time series models to identify the most effective approach for predicting future web traffic trends.

## Technologies Used

*   **Programming Language:** Python
*   **Key Libraries:**
    *   `pandas`: Essential for data loading, manipulation, and preparing the time series data.
    *   `prophet`: The core library used for building and fitting the time series forecasting models.
    *   `matplotlib`: Used for visualizing the historical data, forecasts, and model components.
    *   `scikit-learn`: Provides metrics for evaluating the performance of the forecasting models (e.g., MAE, MAPE, R²).
    *   `numpy`: Used for numerical operations, particularly in calculating evaluation metrics.

## Methodology

The project follows these key steps for forecasting Wikipedia page views:

1.  **Data Loading and Preparation:** Load the daily page view data from the `example_wp_log_peyton_manning.csv` file into a pandas DataFrame. Ensure the 'ds' column is in datetime format and the 'y' column (log of page views) is in a suitable numerical format.
2.  **Model Experimentation with Prophet:** Implement and experiment with different configurations of the Prophet model to capture various aspects of the time series:
    *   Applying logistic growth to model potential saturation in page views.
    *   Adding custom seasonalities or utilizing built-in seasonalities (weekly, yearly) to capture recurring patterns.
    *   Tuning parameters related to trend changepoints (`n_changepoints`, `changepoint_prior_scale`) to better fit shifts in the long-term trend.
    *   Incorporating relevant holidays (like playoffs and superbowls as shown in the notebook) that might influence page views.
3.  **Forecasting Future Page Views:** Generate a future DataFrame with dates extending beyond the historical data. Use the trained Prophet models to predict page views for these future dates.
4.  **Model Evaluation:** Assess the performance of each model configuration by comparing the predicted values (`yhat`) to the actual historical 'y' values where available, and using metrics such as Mean Absolute Error (MAE), Mean Absolute Percentage Error (MAPE), and R-squared.
5.  **Visualization:** Plot the historical data alongside the forecasted values to visually inspect the model's fit and predictive capabilities. Visualize model components (trend, seasonality, holidays) to understand their influence on the forecast.

**Results / Conclusion**
After training and evaluating the three different Prophet models on the Wikipedia page view dataset, the following performance metrics were obtained:

Model	MAE	MAPE	R²
Model 1 (Logistic Growth)	0.3658	4.34%	0.6043
Model 2 (Custom Seasonality)	0.3576	4.23%	0.6223
Model 3 (Tuned Changepoints)	0.3228	3.84%	0.7013
Based on these metrics, Model 3 (Tuned Changepoints) performed the best. It achieved the lowest Mean Absolute Error (MAE) and Mean Absolute Percentage Error (MAPE), indicating that its predictions were closest to the actual values on average. Additionally, it had the highest R-squared (R²) value, suggesting that it explained the largest proportion of the variance in the historical page view data compared to the other models.

The conclusion drawn from these results is that tuning the n_changepoints and changepoint_prior_scale parameters significantly improved the Prophet model's ability to capture the underlying trends and variations in this specific time series dataset, leading to more accurate forecasts. While the other models also provided reasonable results, explicitly accounting for shifts in the trend proved most effective here.
## Feature Importance

For Prophet models, feature importance isn't calculated in the same way as traditional machine learning models. However, the impact of different components can be understood by analyzing the model's parameters and the component plots.

*(This section will discuss the relative impact of trend, seasonality (weekly, yearly, custom), and holidays on the page view forecasts based on the model's parameters and the component plots
## Business Value

Accurate forecasting of web traffic, even for something like Wikipedia page views, provides valuable insights with direct business applications:

*   **Content Performance Analysis:** Understanding and predicting page views helps assess the popularity and impact of specific content.
*   **Platform Capacity Planning:** Forecasting traffic load is crucial for planning and scaling the underlying infrastructure to ensure stability and performance.
*   **Understanding User Interest:** Analyzing trends and seasonal peaks can reveal insights into public interest related to specific topics or events.
*   **Identifying and Responding to Anomalies:** Predicting expected traffic allows for the detection of unusual spikes or drops that might indicate external factors, technical issues, or viral events.
*   **Marketing and Event Impact Assessment:** By incorporating holidays or external events, forecasts can help measure their influence on traffic.

## Next Steps & Contact

**Future Enhancements:**

*   Explore incorporating external regressors such as news mentions, social media trends, or search interest related to the topic.
*   Implement rigorous time series cross-validation to get a more reliable estimate of out-of-sample performance.
*   Investigate potential outliers in the data and their impact on the forecasts.
*   Develop a more automated workflow for data updating and forecasting.

**Contact:**

Feel free to connect with me for questions, feedback, or collaboration:

*   **GitHub:** [Your GitHub Username]
*   **LinkedIn:** [Your LinkedIn Profile URL]
*   **Email:** [Your Email Address]
