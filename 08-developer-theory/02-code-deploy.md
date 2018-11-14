# CodeDeploy
- an automated deployment service which allows you to deploy your application code automatically to EC2 instances, on-premise systems and Lambda functions
- allows you to quickly release new features, avoiddowntime during application deployments, and avoid the risks associated with manual processes
- automatically scales with your infrastructure and integrates with various CI/CD tools e.g.Jenkins, GitHub, Atlassian, AWS CodePipeline as well as config management tools like Ansible, Puppet, and Chef
- 2 deployment approaches are available:
  - in-place
  - blue/green

## In-Place Deployment
- the application is stopped on each instance and the latest revision installed
- the instance is out of service during this time and your capacity will be reduced
- if the instances are behind a load balancer, you can configure the load balancer to stop sending requests to the instances which are being upgraded
- in-place is also known as a Rolling Update
- it can only be used for EC2 and on-premise systems - it is not supported for Lambda
- if you need to roll back your changes, the previous version of the application will need to be re-deployed

## Blue/Green Deployment
- instances are provisioned and the latest version is installed on the new instances; blue represets the active deployment, green is the new release
- the new instances are registered with an Elastic Load Balancer, traffic is then routed to the new instance and the original instances are eventually terminated
- advantages of a blue/green deployement are that the new instances can be created ahead of time and the code released to production by simply switching all traffic to the new servers
- switching back to the original environment is faster and more reliable and is just a case for routing the traffic back to the originl servers (as long as you haven't terminated them)

## Terminology
- deployment group - a set of EC2 instances or Lambda functions to which a new revision of the software is to be deployed
- deployment the process and components used to apply a new revision
- deployment configuration - a set of deployment rules as well as success/failure conditions used during development
- AppSpec File - defines the deployment actions you want AWS CodeDeploy to execute
- revision - everything needed to deploy the new version: AppSpec file, application files, executables, config files
- application - unique identifier for the application you want to deploy; to ensure the correct combination of revision, deplyment configuration and deployment group are referenced during deployment

## Summary
- AWS CodeDeploy is a fully managed automated deployment service and can be used as part of a CD process
- remember the different types of deployment approaches:
  - in-place or rolling update: you stop the application on each hose and deploy the latest code; EC2 and on-premises systems only -- to roll back you must re-deploy the previous version of the application
  - blue/green: new instances are provisioned nad the new pplication is deployed to these new instances; traffice is routed to the new instances according to your own schedule; supported for EC2, on-premises systems and Lambda functions; roll back is easy, jsut route the traffic back to the original instances -- blue is the active deployment and green is the new release

## In-Practice
- creating a CodeDeploy
  1. create a VPC
    - create Internet Gateway
    - create Route Table
  2.  create IAM permissions for CodeDeploy to access resources (S3, Lambda, etc.
  3. add Tags to VPC to identify multiple application deployments
  4. configure security groups for SSH and HTTP
  5. ssh into VPC(EC2) instance and install CodeDeploy [Example from Udemy](https://www.udemy.com/aws-certified-developer-associate/learn/v4/t/lecture/6502118?start=0)
  6. configure local machine to work with CodeDeploy
    - create IAM role for local machine
    - prepare application build file `appspec.yaml`
      - configure scripts for application build (start, stop, test, etc.)
      - create dependencies file for `appspec.yaml` to work off of e.g `package.json` for Node.js or `requirements.txt` for PIP (Python) and the like
  7. from local machine create application in CodeDeploy and push it to designated S3 bucket as a compressed file which CodeDeploy creates[Example from Udemy](https://www.udemy.com/aws-certified-developer-associate/learn/v4/t/lecture/2314496?start=0)
  8. create Deployment Group with its environment configuration in CodeDeploy console
    - using the tag from the EC2 instance or VPC we can choose it directly
    - deploy the revision; revision is stored as a compressed file as well when viewed in the details of the Application Details view of CodeDeploy for that revision