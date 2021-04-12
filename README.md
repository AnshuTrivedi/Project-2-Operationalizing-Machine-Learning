
# Operationalizing Machine Learning

# Project Overview
This project is formed by two parts:

The first part consists of creating a machine learning production model using AutoML in Azure Machine Learning Studio, and then deploy the best model and consume it with the help of Swagger UI using the REST API endpoint and the key produced for the deployed model.

The second part of the project is following the same steps but this time using Azure Python SDK to create, train, and publish a pipeline. For this part, I am using the Jupyter Notebook provided. The whole procedure is explained in this README file and the result is demonstrated in the screencast video.
For both parts of the project. The data is related with direct marketing campaigns (phone calls) of a Portuguese banking institution. The classification goal is to predict whether the client will subscribe a bank term deposit. The result of the prediction appears in column y and it is either yes or no.


## Architectural Diagram
![Project_overview and architectural diag](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/1.project_overview.png)

## Key Steps

The key steps of the project are described below:

### 1. Authentication:
       This step omitted since it could not be implemented in the lab space provided by Udacity,
       because I am not authorized to create a security principal. However, I am still mentioning it here as
       it is a crucial step if one uses their own Azure account.

### 2. Automated ML Experiment: 
       At this point, security is enabled and authentication is completed. This step involves the creation of
       an experiment using Automated ML, configuring a compute cluster, and using that cluster to run the
       experiment.
       
  #### Registered Dataset
  ![Dataset](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/2.%20registered_dataset.png)

  #### Registered dataset detailed view 
  ![data details](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/3.registered_data_details.png)
   
  #### Auto ML experiment configurations
   ![automl config](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/6.automml_config.png)

  #### Automl Experiment completed
   ![auto ml exp](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/7.automl_exp_completed.png)

  #### Best model 
   ![best model](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/8.best_automl_model.png)

### 3. Deploy the Best Model: 
       After the completion of the experiment run, a summary of all the models and their metrics are shown, including
       explanations.The Best Model will appear in the Details tab, while it will appear first in the Models tab. This
       is the model that should be selected for deployment. Its deployment allows to interact with the HTTP API service 
       and interact with the model by sending data over POST requests.
      
### 4. Enable Logging: 
      After the deployment of the Best Model, I enabled Application Insights and retrieve logs.
      
  #### Details tab of Endpoint showing application insights enabled
  ![insights enabled](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/11.insights_enabled.png)

  ####  Running logs script
  ![running logs](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/12.logs_details.png)
    

### 5. Swagger Documentation:
        This is the step where the deployed model will be consumed using Swagger. Azure provides a Swagger JSON file for deployed models.
        We can find the deployed model in the Endpoints section, where it should be the first one on the list.
        
   #### Running swagger script
   ![swagger run](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/13.swagger_run.png)

   #### Swagger response and methods
   ![](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/15.swagger_ui.png)

   ![](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/16.swagger_ui_param.png)

### 6. Consume Model Endpoints:
       Once the model is deployed, I am using the endpoint.py script to interact with the trained model. I run the script
       with the scoring_uri that was generated after deployment and -since I enabled Authentication- the key of the service. 
       This URI is found in the Details tab, above the Swagger URI.
       
   #### Endpoint script run
   ![end point script](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/17.endpoint.png)

### 7. Create and Publish a Pipeline: 
       In this part of the project, I am using the Jupyter Notebook with the same keys, URI, dataset, cluster, and model names already 
       created.
      
   #### Pipeline created
   ![pipeline created](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/17.pipeline_created.png)

   #### Pipeline Endpoint 
   ![pipeline endpoint](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/18.pipeline_endpoint.png)

   #### Published pipeline overview 
   ![pipeline overview](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/19.pipline_restendpoint.png)

   #### Jupyter Notebook showing *Use RunDetails Widget*
   ![widget run](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/20.widget_run.png)

   #### In ML Studio scheduled run
   ![ML scheduled run](https://github.com/AnshuTrivedi/Project-2-Operationalizing-Machine-Learning/blob/master/Images/21.mlstudio_runcompleted.png)

### 8. Documentation:
      The documentation includes:
      
      1. the screencast that shows the entire process of the working ML application.
      2. this README file that describes the project and documents the main steps.


## Screen Recording

[Screen recording](https://www.youtube.com/watch?v=ni_Oef4kiKQ)

## Standout Suggestions
1. I explored bank marketing dataset to understand better features and granularity of data, found high class imbalance between two classes which can impact model performance. 
2. Use of deep learning in automated ml model training:  explored option of using deep learning for model traing but in community  discusson I found not to use that option.

## References
1. [Dealing with imbalanced data in Auto ML](https://techcommunity.microsoft.com/t5/azure-ai/dealing-with-imbalanced-data-in-automl/ba-p/1625043)
2. [How to consume web services](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-consume-web-service?tabs=python)
3. [Swagger User interface documentation](https://swagger.io/docs/open-source-tools/swagger-ui/usage/installation/)
4. [How to deploy model on Azure](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-deploy-and-where?tabs=azcli)
