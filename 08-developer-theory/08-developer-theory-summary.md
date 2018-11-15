# Developer Theory Summary
- heavily weighted for the exam
- [White Paper](https:///d0.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf)
- Continuous Integration is about integrating or merging the code changes frequently -- at least once/day, enable multiple devs to work on the same application
- Continuous Delivery is all about automating the build, test and deployment functions
- Continuous Deployment fully automates the entire release process, code is deployed into Production as soon as it has successfully passed hrough the release pipeline

## AWS CI/CD Tools
- AWS CodeCommit - source control service (Git)
- AWS CodeBuild - compile source code, run tests and package code
- AWS CodeDeploy - automated deployment to EC2, on premises systems and Lambda
- AWS CodePipeline - CI/CD workflow tool, fully automates the entire release process (build, test, deployment)

## CodeCommit
- Git-based
- centralized repostory for all your code, binaries, images, and libraries
- tracks and manages code changes
- maintains version history
- manages updates from multiple sources and enable collaboration

## CodeDeploy
- a fully manages automated deployment service and can be used as part of a Continuous Delivery or Continuous Deployment process
- Types of Deployment Approaches
  - In-Place or Rolling Update
    - you stop the application on each host and deploy the latest code
    - EC2 and on-premise systems only
    - to roll back you must re-deploy the previous version of the application
  - Blue/Green
    - new instances are provisioned and the new application is deployed to these new instance
    - traffic is routed to the new instances according to your own schedule
    - support for EC2, on-premises systems and Lambda functions
    - roll back is easy, just route the traffic back to the original instances if available
      - blue is active deployment
      - green is the new release
  - Advanced Settings
    - the `AppSpec` file defines all the parameters needed for the deployment e.g. location of application files and pre/post deployment validation tests to run
    - for EC2/on-premises systems, the `appspec.yml` file must be placed in the root directory of your revision (the same fodler that contains your application code) -- written in YAML
    - Lambda supports YAML or JSON
    - Run Order of Hooks
      1. BeforeBlockTraffic > BlockTraffic > AfterBlockTraffic
      2. ApplicationStop
      3. BeforeInstall
      4. Install
      5. AfterInstall
      6. ApplicationStart
      7. ValidateService
      8. BeforeAllowTraffic > AllowTraffic > AfterAllowTraffic

## Docker & CodeBuild
- Docker allows you to package up your software into Containers which you can run in Elastic Container Service (ECS)
- a Docker Container includes everything the software needs to run including code, libraries, runtime and environment variables etc.
- we use a special file called a docker file to specify the instructions needed to assemble your Docker image
- once built, Docker images can be stored in Elastic Container Registry (ECR) and ECS can then use the image to launch Docker containers

## Docker
- Docker commands to build, tag (apply an alias) and push your Docker image to the ECR repository
`docker build -t myimagerepo`
`docker tage myimagerepo:latest 725350006743.dkr.ecr.eu-central-1.amazonaws.com/myimagerepo:latest`
`docker push 725350006743.dkr.ecr.eu-central-1.amazonaws.com/myimagerepo:latest`

## CodeBuild
- a fully managed build service, it can build source code, run tests and produce software packages based on commands that you define yourself
- by default the `buildspec.yml` defines the build commands and settings used by CodeBuild to run your build
- you can completely override the settings in `buildspec.yml` by adding your own commands in the console when you launch the build
- if your build fails, check the build logs in the CodeBuild console and you can als oview the full CodeBuild log in CloudWatch

## CodePipeline
- CI/CD service
- automates you end-to-end software release process based on a user defined workflow
- can be configured to automatically trigger your pipeline as soon as a change is detected in your source code repository
- integrates with other services from AWS like CodeBuild and CodeDeploy, as well as third party and custom plug-ins