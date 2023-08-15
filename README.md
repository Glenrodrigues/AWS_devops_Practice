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

In the CodeCommit repository above we have the following folder structure:
* config – this is where all of the Buildspec files will live for our AWS CodeBuild jobs.
* lambdas – this is where we will store all of our AWS Lambda functions.
* tests – this is the top-level folder for unit and end-to-end tests. It contains two sub-folders (unit and e2e).
* cloudformation – this is where we will add any extra CloudFormation templates.
