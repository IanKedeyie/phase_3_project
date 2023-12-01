
# Tanzanian Water Wells Status Prediction
# Project Overview
Tanzania is a developing country that struggles to get clean water to its population of 59 million people. According to WHO, 1 in 6 people in Tanzania lack access to safe drinking water and 29 million don't have access to improved sanitation. The focus of this project is to build a classification model to predict the functionality of waterpoints in Tanzania given data provided by Taarifa and the Tanzanian Ministry of Water. The model was built from a dataset containing information about the source of water and status of the waterpoint (functional, functional but needs repairs, and non functional) using an iterative approach and can be found here. The dataset contains 60,000 waterpoints in Tanzania and the following features will be used in our final model:

      amount_tsh - Total static head (amount water available to waterpoint)
      gps_height - Altitude of the well
      installer - Organization that installed the well
      longitude - GPS coordinate
      latitude - GPS coordinate
      basin - Geographic water basin
      region - Geographic location
      population - Population around the well
      recorded_by - Group entering this row of data
      construction_year - Year the waterpoint was constructed
      extraction_type_class - The kind of extraction the waterpoint uses
      management - How the waterpoint is managed
      payment_type - What the water costs
      water_quality - The quality of the water
      quantity - The quantity of water
      source_type - The source of the water
      waterpoint_type - The kind of waterpoint
The first sections focus on investigating, cleaning, wrangling, and reducing dimensionality for modeling. The next section contains 6 different classification models and evaluation of each, ultimately leading to us to select our best model for predicting waterpoint status based on the precision of the functional wells in the model. Finally, I will make recommendations to the Tanzanian Government and provide insight on predicting the status of waterpoints.

# Business Problem
The Tanzanian government has a severe water crisis on their hands as a result of the vast number of non functional wells and they have asked for help. They want to be able to predict the statuses of which pumps are functional, functional but need repair, and non functional in order to improve their maintenance operations and ensure that it's residents have access to safe drinking water. The data has been collected by and is provided by Taarifa and the Tanzanian Ministry of Water with the hope that the information provided by each waterpoint can aid understanding in which waterpoints will fail. I have partnered with the Tanzanian government to build a classification model to predict the status of the waterpoints using the dataset provided. I will use the precision of the functional wells as my main metric for model selection, as a non functional well being predicted as a functional well would be more detrimental to their case, but I will provide and discuss several metrics for each model.
# Objectives
  1. To develop a classification model that predicts the functionality of waterpoints, categorizing them as functional,                functional but in need of repair, or 
     non-functional.

  2. Establish a foundation for data-driven decision-making in water resource management.
# Data Understanding

The dataset comprises information on 60,000 waterpoints across Tanzania, encompassing a diverse set of features. These features include data such as the amount of available water, installation details, geographic coordinates, population around the well, and various socio-economic indicators. The richness of the dataset allows for a comprehensive analysis of factors influencing the functionality of waterpoints. The data contains a wealth of information about waterpoints in Tanzania and the status of their operation. The target variable has 3 different options for it's status:

    functional - the waterpoint is operational and there are no repairs needed
    functional needs repair - the waterpoint is operational, but needs repairs
    non functional - the waterpoint is not operational
The data is available and it can be downloaded from the link  on DrivenData 
 https://www.drivendata.org/competitions/7/pump-it-up-data-mining-the-water-table/page/23/

# Exploratory Analysis Data
## Target feature distribution
![image](https://github.com/IanKedeyie/phase_3_project/assets/142450582/89e6b0aa-275e-41a2-8291-f7b91911c0e4)
We have the most functional wells at 32259, followed by non functional wells at 22,824, and the minority class, functional needs repair at 4317.

# Modeling
## 1. Dummy Classifier Model

![image](https://github.com/IanKedeyie/phase_3_project/assets/142450582/214b32a4-6ae7-435c-8b88-bde3eb7f0334)

Our baseline dummy model performed very poorly with an accuracy score of 61.5%%. Our data is heavily imbalanced, which explains how our ternary model performed poorly beause this model on focuses on the majority class which was functional
## 2. Logistic regression Model

![image](https://github.com/IanKedeyie/phase_3_project/assets/142450582/44447558-1496-44d8-aa88-87298843551c)

Our logistic regression model is improved to 81% accuracy over the dummy model. This model struggled to predict wells that were functional due to class imbalances.The precision is 82%
## 3. K Nearest Neighbors Model
The K Nearest Neighbors model outperformed the Logistic Regression model. Number of neighbors was hypertuned by running and GridSearch and optimal parameters were put into our pipe. Our K Nearest Neighbors model is not overfitting as the accuracy of training and test sets are 85.39% and 82.16%, respectively. The precision of the functional class is 83%, which is a huge improvement from our Logistic Regression model at 81%.

![image](https://github.com/IanKedeyie/phase_3_project/assets/142450582/7b6f5880-d207-47f1-8da6-d0b46e76a747)

## 4. Decision tree model

![image](https://github.com/IanKedeyie/phase_3_project/assets/142450582/2282866c-b79b-4654-93b5-830f42405041)

Our decision tree model once again improved our functional class precision scores to 85%, but the model is highly overfitting with training accuracy at 99% and test accuracy at 81%.

## 5. XGboost model
Our best performing model ended up being the XG Boost model with tuned hyperparameters, although the random forests model was not far behind with 61% precision for the functional wells class. The model has overfitted the training data with a training accuracy of 87.91% and test accuracy at 81.73%, but this model boasted the highest precision score for the functional wells class at 86%.

![image](https://github.com/IanKedeyie/phase_3_project/assets/142450582/e247909e-7069-47c4-9047-8aa2dcf7c547)

# Conclusion
Based on my findings, I am confident to partner with the Tanzanian government to help solve their water crisis by predicting water pump failure. As i illustrated above, there is a high rate of non functional waterpoints in the southeast corner of Tanzania in Mtwara and Lindi, as well as up north in Mara, and the southwest in Rukwa. These areas need immediate attention as the situations here are critical. There are a high number of functional wells in Iringa, Shinyanga, Kilimanjaro, and Arusha. There is a cluster of functional but need repair waterpoints in Kigoma, these should be addressed to prevent failure which can be more expensive to repair.

Several of our models showed one of it's most important features to be quantity enough for the waterpoint. There are over 8,000 waterpoints that have enough water in them but are non functional. These are a high priority to address as well since there is water present. Wells with no fees are more likely to be non functional

XGBoost, especially after hyperparameter tuning, stands out with the highest accuracy and balanced performance on both classes. Techniques like oversampling were applied in some models to address this. so we can choose it to be our best performing model

# Recommendation

Future work for this project involve improving the quality of the data moving forward. Better trained data in our model will improve the predictions. We will also monitor the wells and update the model regularly to continuously improve our strategy.








