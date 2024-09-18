# ![Google Cloud](https://avatars.githubusercontent.com/u/2810941?s=60&v=4) Google Cloud Vertex AI

This page contains notebooks, code samples, sample apps, and other resources that demonstrate how to use, develop and manage machine learning and generative AI workflows using Google Cloud Vertex AI.

## Model Development

### Training:

#### Train and use your own models
**AutoML**: Create and train models with minimal technical knowledge and effort. To learn more about AutoML, see [AutoML beginner's guide](https://cloud.google.com/vertex-ai/docs/beginner/beginners-guide).
**Custom training**: Create and train models at scale using any ML framework. To learn more about custom training on Vertex AI, see [Custom training overview](https://cloud.google.com/vertex-ai/docs/training/overview).

**AutoML**:  
  
Machine learning (ML) models use training data to learn how to infer results for data that the model was not trained on. AutoML on Vertex AI lets you build a code-free model based on the training data that you provide.
The workflow for training and using an AutoML model is the same, regardless of your datatype or objective:

1. Prepare your training data.
2. Create a dataset.
3. Train a model.
4. Evaluate and iterate on your model.
5. Get predictions from your model.
6. Interpret prediction results.

**Custom training**:

If none of the AutoML solutions address your needs, you can also create your own training application and use it to train custom models on Vertex AI. You can use any ML framework that you want and configure the compute resources to use for training, including the following:

1. Type and number of VMs.
2. Graphics processing units (GPUs).
3. Tensor processing units (TPUs).
4. Type and size of boot disk.

### Experiment:
Vertex AI Experiments is a tool that helps you track and analyze different model architectures, hyperparameters, and training environments, letting you track the steps, inputs, and outputs of an experiment run. Vertex AI Experiments can also evaluate how your model performed in aggregate, against test datasets, and during the training run. You can then use this information to select the best model for your particular use case.
[more details](https://cloud.google.com/vertex-ai/docs/experiments/intro-vertex-ai-experiments?authuser=2&_gl=1*1kqmify*_ga*MTA2NDIzMDcwNi4xNzI2NTI5OTQ2*_ga_WH2QY8WWF5*MTcyNjY5NTI1OC41LjEuMTcyNjY5NTgzMS42MC4wLjA.)

### Metadata:
Metadata helps you:
1. Analyze runs of a production ML system to understand changes in the quality of predictions.
2. Analyze ML experiments to compare the effectiveness of different sets of hyperparameters.
3. Track the lineage of ML artifacts, for example datasets and models, to understand just what contributed to the creation of an artifact or how that artifact was used to create descendant artifacts.
4. Rerun an ML workflow with the same artifacts and parameters.
5. Track the downstream usage of ML artifacts for governance purposes.



## Deploy and Use


#### Deploy a model to an endpoint: 

You must deploy a model to an endpoint before that model can be used to serve online predictions. 
When you deploy a model using the Vertex AI API, you complete the following steps:

1. Create an endpoint if needed.
2. Get the endpoint ID.
3. Deploy the model to the endpoint.

#### Getting predictions on Vertex AI: 

A prediction is the output of a trained machine learning model.

**Vertex AI offers two methods for getting prediction:**

**Online predictions** are synchronous requests made to a model that is deployed to an endpoint. Therefore, before sending a request, you must first deploy the Model resource to an endpoint. This associates compute resources with the model so that it can serve online predictions with low latency. Use online predictions when you are making requests in response to application input or in situations that require timely inference.

**Batch predictions** are asynchronous requests made to a model that isn't deployed to an endpoint. You send the request directly to the Model resource. Use batch predictions when you don't require an immediate response and want to process accumulated data by using a single request.

#### Monitoring:
Vertex AI Model Monitoring lets you run monitoring jobs as needed or on a regular schedule to track the quality of your tabular models. If you've set alerts, Vertex AI Model Monitoring informs you when metrics surpass a specified threshold.

## Manage

#### Ray on Vertex AI:

Ray is an open-source framework for scaling AI and Python applications. Ray provides the infrastructure to perform distributed computing and parallel processing for your machine learning (ML) workflow.



