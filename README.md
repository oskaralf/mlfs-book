# mlfs-book
This lab predicts pm25 values for St-eriksgatan, Stockholm, Sweden, based on weather data. This repo was expanded to incorporate 3 days prior data of pm25 values, and is avaialbe on this link:

[Expanded version](https://github.com/sthaji/mlfs-book/tree/main?fbclid=IwY2xjawGq3Z5leHRuA2FlbQIxMAABHReTVSV80f-auioj1kCr_Mr2yQ0hmc3nSs0uI4c0TVZVawtPo-rP7VQ0GA_aem_6pZ83v3ekp84AN7pLPeJww
)

Scripts:

    1_air_quality_feature_backfill.ipynb
        Takes in historical weather data and pm values
        Cleans data and creates new columns
        creates two feature groups saved in Hopsworks
    2_air_quality_feature_pipeline.ipynb
        Gets todays pm25 value, adds lagging values from previous days to new data row
        Gets forecasted weather data
        inserts new values into feature groups in Hopsworks
    3_air_quality_batch_inference.ipynb
        Creating a feature view by combining different columns from feature groups
        creates a schema for a xgboost model
        trains and tests the model
        saves the model in a model registry in Hopsworks
    4_air_quality_batch_inference.ipynb
        Get weather forecast data and pm25 data from feature group
        batch inference sequentially using weather forecast data + lagging values from each day before
        Saving predictions to a feature group for monitoring
        based on monitored values, for those days we have both a predicted value and actual value, add to a hindcast graph (1 new data point added everyday)



[Dashboards for our Air Quality tracker](https://oskaralf.github.io/mlfs-book/)

