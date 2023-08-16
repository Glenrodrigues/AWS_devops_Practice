# DEVOPS CICD PIPELINE USING AWS TOOLS.

## CI/CD services

For CI/CD, we use the following AWS services: 

* AWS CodeBuild – A fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy.
* AWS CodeCommit – A fully managed source control service that hosts secure Git-based repositories.
* AWS CodeDeploy – A fully managed deployment service that automates software deployments to a variety of compute services such as Amazon Elastic Compute Cloud 
  (Amazon EC2), AWS Fargate, AWS Lambda, and your on-premises servers.
* AWS CodePipeline – A fully managed continuous delivery service that helps you automate your release pipelines for fast and reliable application and infrastructure 
  updates.
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/main.png)

We just have a basic java webapp which uses maven and appache tomcat to run.

## Creating a CodeCommit repository

 To begin, navigate to the AWS console to create a new CodeCommit repository for your state machine and push all code to it using git command.

 ![Image][]
### Breakdown of repository structure

In the CodeCommit repository above we have the following folder and files structure:
* Buildspec – this is where all of the YML code is for our AWS CodeBuild jobs.
* appspec – this is where we have YML code for codeDeploy job.
* src – java Code which will be deploy on ec2.
* Scripts – Contains bash script to step us the environment on ec2 instance

## Code build 

### Step 1
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/CD_app1.png)

Create Application under code deploy and choose `EC2` as we are doing `on-premises` deploy

### Step 2
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app2.png)

create a service role which has permission of `code_deploy_power_user`

### Step 3
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app3.png)

### Step 4
### Note run 2 instance and assign a ROLE to it which has code deploy policy and give same tag name for both the instance ,in my case i have given KEY=env , value:Prod

As we are deploying webapp on EC2 select Ec2 and their tags


![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app4.png)

### Step 5

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app5.png)

Uncheck the load balancer as we are not using it for this tutorial and create application 

### Step 6
Go to `Application > [your_Application_name]` and create deployment group , in my case i named it as `namigroup'

In this step we have to mention the path of `artifacts` created by `code_deploy` which we have store in `S3`.

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/CD_app6.png)


As you can see i am in S3> [folder_name]>[file_name] (folder name and file name are mention in  buildspec file used in code deploy) 


### Step 7

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app7.png)


As you can see i am in S3> [folder_name]>[file_name],`folder name and file name are mention in  buildspec file used in code deploy`

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/CD_app8.png)


Now click on create and process will began, code deploy will deploy our code on EC2 

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/CD_app9.png)


After completing go on to Ec2 instance and run their Public IP in browser.
### Make sure you have given HHTP 80 in inbound security group.

## Codepipeline 
### Step 1
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/pipe_1.png)

Select Create pipeline and attach service role to it which has permission of codepipeline.
There are 4 step in code pipline 

### Select source  

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/pipe_2.png)

Select codecommit repo and its branch.


### Select code build

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/pipe_3.png)


### Select code deploy 

![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/pipe_4.png)


Make changes in your code and push it to code commit then codepipline will deploy that changes on EC2 instance.
