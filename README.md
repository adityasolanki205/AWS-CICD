# AWS-CICD

This is a repository for **learning and implementation** of CICD Pipeline of a GitHub repository on AWS. In this repository we will learn to build and deploy a html application using CodePipeline service on AWS. The complete process is divided into 5 parts:

1. **HTML website creation**
2. **Hosting the website on S3 bucket**
3. **Connecting AWS with GitHub**
4. **Building the code using CodePipeline**
4. **Integrating and Delivering the updated code**


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

### Step 0 - AWS Free tier account creation

- **AWS Account**: We will be using Free tier version of AWS for our demonstration. If you wish to create a new account please click [here](https://portal.aws.amazon.com/billing/signup?refid=em_127222&redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start/email)


### Step 1 - HTML website creation

-  **Website**: Here we could either create a website or copy a basic code from opensource platforms. In our case, we have used the code from open source website.


### Step 2 - Hosting the website on S3 bucket

-  **Bucket Creation**: Now we will create a S3 bucket.

    i. On the AWS console goto S3 buckets and click on "Create bucket"
    
    ii. Enter Bucket Name and choose the region. 
    
    iii. Uncheck "Block public access settings from this bucket settings" 
    
    iv. Leave everything as is and click on Create Bucket.
    
https://user-images.githubusercontent.com/56908240/220592446-eca375db-222b-4ec8-81a7-a137e4acece8.mp4


-  **Configure Static website settings**: 

    i. Open the newly created bucket and goto the properties.
    
    ii. Scroll to the bottom and click edit button on "Static website hosting"
    
    iii. Click on Enable button and fill the name "index.html" in index document.
    
    iv. Click on save changes.

https://user-images.githubusercontent.com/56908240/220592552-7c7518d5-f532-4a7c-a84e-3fd015211b0c.mp4


-  **Grant permissions**:

    i. Goto Bucket Policy, click on policy generator and create a policy for "GetObject" and click on generate policy.

```json
    {
    "Version": "2012-10-17",
    "Id": "Policy1676894398003",
    "Statement": [
        {
            "Sid": "Stmt1676894388176",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::testingstatic/*"
        }
      ]
    }
```

https://user-images.githubusercontent.com/56908240/220592663-1057ffb7-95c8-42cd-9a8a-98d92a458c90.mp4


### Step 3 - Connecting AWS with GitHub

-  **Creating connections**:  

    i. Goto CodePipelines.
    
    ii. Navigate to Settings and click on connections.
    
    iii. Click "Create Connection".
    
    iv. Select Private or Enterprise Github and click on Connect to Github.
    
    v. Select required repo to be connected and click connect.
    
https://user-images.githubusercontent.com/56908240/220592761-4598906a-2532-4408-84f1-ca29f0f27c93.mp4


### Step 4 - Building the code using CodePipeline
    
-  **Source Stage**:
    
    i. Navigate to CodePipeline.
    
    ii. Click on create new pipeline. Provide the name of the pipeline and click next.
    
    iii. Under Source provider select "GitHub (Version 2)". Then select the connection, Repository name, Branch name and click next.
    
https://user-images.githubusercontent.com/56908240/220592891-0cb7cc28-3546-42f3-a21e-d378027ec09d.mp4

    
-  **Build Stage**:
    
    i. In the build provider select CodeBuild and either click on create Project if you donot have a project or select the one from dropdown if already created .
    
    ii. If you clicked on Create project then select Managed Image, Ubuntu Operating system, Standard runtime, choose the latest version of the image, choose new service and click on continue. 
    
    iii. In this process a file named Buildspec.yml would be required. It contains shell commands to be run before, during, and after build process. We have provided a basic buildspec.yaml in this repo as well. This file must be present in the Root Directory of the repo.
    
    iv. Select Single option and click next
    
https://user-images.githubusercontent.com/56908240/220592944-15927a1b-96dd-45a0-afca-a74009b262ec.mp4


-  **Deploy Stage**: 
    
    i. Select Amazon S3 in deploy stage and the name of the bucket.
    
    ii. Check the " Extract File before Deploy " button as well. 
    
    iii. Click next and the pipeline will be deployed.

https://user-images.githubusercontent.com/56908240/220593038-9369c12c-7806-4319-b517-5be38a2f2037.mp4


### Step 5 - Integrating and Delivering the updated code

-  **Check if the code is working**: 
    
    i. Goto Amazon S3 bucket and select the bucket. Goto Properties and go to the bottom and click on "Static website Hosting" URL.
    
    ii. Verify if the page is loading perfectly
    
    
-  **Updating the code in Repo**: 
    
    i. Now goto the Repo and update index.html
    
    ii. Commit the code and push it to the root directory.
    
    iii. Verify if the CodePipeline is running.
    
    iv. Now click on "Static website Hosting" URL again and verify the changes.
    
    
### Step 6 - Deleting the resources(Optional)

-  **Delete all the resources**:

    i. Delete the Pipeline created for the site.
    
    ii. Delete S3 bucket created to host the website.
    
    iii. If no further pipelines are required, delete the S3 bucket created for codepipelines as well.
    
    iv. Delete the connection created with GitHub.
    
    v. Delete the CodeBuild Project that were created


## Credits
1. [Build a CI/CD pipeline on AWS](https://medium.com/nerd-for-tech/build-a-ci-cd-pipeline-on-aws-f806e427db22)
2. [Simple CI/CD pipeline with AWS CodePipeline](https://osusarak.medium.com/ci-cd-with-aws-codepipeline-d8d0538a52f2#:~:text=CI%2FCD%20is%20one%20of,is%2C%20CI%2FCD%20pipeline)
3. [About Us page](https://www.w3schools.com/howto/howto_css_about_page.asp)
