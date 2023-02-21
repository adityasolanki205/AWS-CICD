# AWS-CICD

This is a repository for **learning and implementation** of CICD Pipeline of a GitHub repository on AWS. In this repository we will learn to build and deploy a html application using CodePipeline service on AWS. The complete process is divided into 5 parts:

1. **HTML website creation**
2. **Hosting the website on S3 bucket**
3. **Connecting AWS with GitHub**
4. **Building the code using CodeBuild**
4. **Deploying the code**


## Motivation
For the last few years, I have been part of a great learning curve wherein I have upskilled to move into a Machine Learning and Cloud Computing. This project was practice project for all the learnings I have had. This is one of the many more to come. 
 

## Services used

<b>Built with</b>
- [CodePipeline](https://docs.aws.amazon.com/codepipeline/latest/userguide/welcome.html)
- [CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/welcome.html)
- [Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [GitHub](https://docs.github.com/en)


## Repo Cloning

```bash
    git clone https://github.com/adityasolanki205/AWS-CICD.git
```

## Implementation

Below are the steps to setup the enviroment and run the models:

### Step 1 - HTML website creation

-  **Website**: Here we could either create a website or copy a basic code from opensource platforms. In our case we have used the code from 
open source website


### Step 2 - Hosting the website on S3 bucket

-  **Model Training**: Now we will try to train the model.

    i. Click on Train new model button.
    
    ii. Select Classification for objective.
    
    iii. In Model details select "Salary" column as target. 
    
    iv. Leave training options as is.
    
    v. Provide Maximum node hours as per the requirement and enable early stopping and Click on Start Training.
    
    vi. With this dataset Training takes around 6 to 8 hours. 

https://user-images.githubusercontent.com/56908240/211068315-23dbcfbb-3176-473d-b8b0-beb7d973d657.mp4

### Step 3 - Connecting AWS with GitHub

-  **Endpoint Creation**:  

    i. Goto model repository.
    
    ii. Click on the Trained Model and its relavant version.
    
    iii. Click on Deploy and Test button.
    
    iv. Click on Deploy on endpoint.
    
    v. Fill in all the details as per the requirement.

https://user-images.githubusercontent.com/56908240/211163203-d713330e-d6cb-4097-bd32-715b8fb0497c.mp4

### Step 4 - Building the code using CodeBuild
    
-  **Online Prediction**:
    
    i. Goto new endpoint created.
    
    ii. Below the endpoint we will see test your model tab with prefilled details. Either prefilled values could be used  to test the model, or we can provide our own values. There is a way to test through API as well. 
    
    iii. As soon as we click on Predict an output will be displayed along with confidence percentage

https://user-images.githubusercontent.com/56908240/211163159-c54d2ec2-6958-4364-b8d0-4856330d63fe.mp4

-  **Batch Prediction**:

    i. Create a new folder in **automl-testing-table** bucket that we created previously.
    
    ii. Save the test file we created previously(remove the Target Label "Salary").
    
    iii. Now in Vertex AI goto Model registry and click on Create Batch Prediction.
    
    iv. Provide path to test file in the required column. Also provide output path where the output will be saved.
    
    v. Click on continue and create. When the Prediction job completes , a mail will be received.
    
https://user-images.githubusercontent.com/56908240/211206708-84aa8ec8-a812-4774-991c-d8d5f38357b9.mp4

### Step 5 - Deploying the code

-  **Batch Prediction Job** : Delete the Batch Predition Job

-  **Endpoint** : To delete endpoint, first remove the endpoint from the model and then delete the endpoint

-  **Model** : Delete the Model

-  **Trainig Job** : Delete the training job from the training pipelines tab

-  **Dataset** : Delete the Training Dataset from Dataset tab

-  **Bucket** : Delete all the buckets created for this process.

## Credits
1. Akash Nimare's README.md: https://gist.github.com/akashnimare/7b065c12d9750578de8e705fb4771d2f#file-readme-md
2. AutoML tables: https://cloud.google.com/vertex-ai/docs/tabular-data/overview
