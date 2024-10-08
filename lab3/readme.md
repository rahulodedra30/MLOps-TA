
# Vertex AI: Training and Serving a Custom Model

## Overview
In this lab, you will learn how to use Vertex AI to train and serve a TensorFlow model using code in a custom container. While we are using TensorFlow in this example, It could easily replaced by any another framework. We will be focussing on Training, Prediction, and Notebooks in this lab.

![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/flow.png)

## Learning Objectives
- Build and containerize model training code in Vertex Notebooks.
- Submit a custom model training job to Vertex AI.
- Deploy your trained model to an endpoint and use that endpoint to get predictions.

## Steps to Run the Lab

### Task 1: Set Up Your Environment
1. Sign in to GCP console.
2. Open the Google Cloud Console and sign in using the lab credentials.
3. Enable the following APIs:
   - Compute Engine API
   - Vertex AI API
   - Container Registry API
4. Launch a Vertex AI Notebooks instance:
   - Navigate to Vertex AI > Workbench.
   - Create a new notebook instance with TensorFlow Enterprise 2.11.

![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/workbench.png)
![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/JupyterLab.png)

### Task 2: Containerize Training Code
1. create a directory
2. Create a Dockerfile
3. Add the necessary commands to your Dockerfile (see lab details for the complete Dockerfile content).
4. Create a Cloud Storage bucket to export your trained model:
   ```bash
   PROJECT_ID='your-cloud-project'
   BUCKET_NAME="gs://${PROJECT_ID}-bucket"
   gsutil mb -l "REGION" $BUCKET_NAME
   ```
5. Create a directory for your training code and a Python file:
   ```bash
   mkdir trainer
   touch trainer/train.py
   ```
6. Add your model training code in `train.py` (see lab details for the complete code).

### Task 3: Run a Training Job on Vertex AI
1. Build and test the container locally:
   ```bash
   IMAGE_URI="gcr.io/$PROJECT_ID/mpg:v1"
   docker build ./ -t $IMAGE_URI
   docker run $IMAGE_URI
   docker push $IMAGE_URI
   ```
2. Kick off the training job:
   - Navigate to the Model Registry section in Vertex AI and create a new training job using the custom container.

![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/training.png)

### Task 4: Deploy a Model Endpoint
1. Once training is complete, deploy the model to an endpoint:
   - Go to the Model Registry, select your model, and click Deploy & Test.
   - Create a new endpoint and configure the deployment settings.
     
2. Get predictions from the deployed model using the Vertex AI API in a Python notebook:
   ```python
   !pip3 install google-cloud-aiplatform --upgrade --user
   from google.cloud import aiplatform
   endpoint = aiplatform.Endpoint(endpoint_name="projects/YOUR-PROJECT-NUMBER/locations/REGION/endpoints/YOUR-ENDPOINT-ID")
   response = endpoint.predict([test_mpg])
   print('API response: ', response)
   print('Predicted MPG: ', response.predictions[0][0])
   ```
![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/model%20registry.png)
![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/deployment.png)
![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/deployed%20model%20details.png)
![](https://github.com/rahulodedra30/MLOps-TA/blob/main/lab3/Images/endpoint%20prediction.png)

## Conclusion
You have successfully trained and deployed a TensorFlow model using Vertex AI and a custom container. You can now make predictions using the deployed model endpoint.
