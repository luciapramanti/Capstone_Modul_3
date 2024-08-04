---

# **Machine Learning Prediction on Bike Sharing Data**

---

Capital Bikeshare is one of the companies engaged in the provision of bicycle-sharing services. The digital nature of the Capital BikeShare system enables the collection of data pertaining to users, the number and duration of trips, travel routes, and other relevant information. In this case, The objective is to forecast the number of bicycles required at a specific time and under a given weather condition, utilising the most appropriate regression model for the metrics provided in this dataset.

<br>

**Attributes Information**

| **Attribute** | **Data Type** | **Description** |
| --- | --- | --- |
| dteday | Object  | date |
| hum | Float | Normalized humidity The values are divided into 100 (max) |
| weathersit | Integer | Wheather condition score (1-4) |
| holiday | Integer | Holiday (1) or not (0) |
| season | Integer | Season (1: winter, 2: spring, 3: summer, 4: fall) |
| atemp | Float | Normalized feeling temperature in Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-16, t_max=+50 (only in hourly scale) |
| temp | Float | Normalized temperature in Celsius. The values are derived via (t-tmin)/(tmax-tmin), tmin=-8, t_max=+39 (only in hourly scale) |
| hr | Integer | Hour (0 to 23) |
| casual | Integer | Count of casual users |
| registered | Integer | Count of registered users |
| cnt | Integer | Count of total rental bikes including both casual and registered |

> *Note :* \
> Wheather condition score (weathersit):\
> 1 = Clear, Few clouds, Partly cloudy, Partly cloudy\
> 2 = Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist\
> 3 = Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds\
> 4 = Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog

<br>

<br>

**Analytic Approach**
* In this project, the 5 regression models will be applied: Linear Regression, K Nearest Neighbor Regressor, Decision Tree Regressor, Random Forest Regressor, XGB Regressor
* After model evaluation, hyperparametric tuning for XGBRegressor model is done.
* Prediction is made with the best parameter from hyperparametric tuning process

<br>

**Metric Evaluation**
* Root Mean Squared Error (RMSE)
* Mean Absolute Error (MAE)
* R-squared

<br>

**Conclusion**
* This model get a RMSE score of 65.12 means, MAE score of 44.92 and R² score of 0.826. The MAE score suggests that the model's predictions are 44.92 units away from the actual values. That means this model's prediction of count values is off by around 45 on average. This is a lot considering the count values have a median  of 136 and mean of 173. R² score of 0.826 means 82.6% variance in the dependent variable can be explained by the features in the model. It is also possible that the prediction misses much further as there are alse some large outliers or predictions.
  
* Regarding the machine learning model applied in this project, it is evident from the residual analysis that the largest 10% of values in this model are not accurate. Thus it is recommended that the model be used for "count" values 1-580 (~90% target value). 
   
* Based on the modelling that has been done, the features 'hour_sin', 'hour_cos' are the most influential features on 'count'. "hour_sin" signify the AM hours and "hour_cos" signify PM hour. In other words, the time plays significant role to the number of bikes used.

---
