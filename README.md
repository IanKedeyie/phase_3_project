# phase_3_project
# Tanzanian Water Wells Status Prediction
# Overview
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

# Data Understanding
The dataset used for this analysis can be found here. It contains a wealth of information about waterpoints in Tanzania and the status of their operation. The target variable has 3 different options for it's status:

       functional - the waterpoint is operational and there are no repairs needed
       functional needs repair - the waterpoint is operational, but needs repairs
       non functional - the waterpoint is not operational
