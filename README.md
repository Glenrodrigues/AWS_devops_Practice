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
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app5.png)
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app6.png)
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app7.png)
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app8.png)
![image](https://github.com/Glenrodrigues/AWS_devops_Practice/blob/main/java%20cicd/cd_app9.png)
  
