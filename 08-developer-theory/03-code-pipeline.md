# CodePipeline
- a fully managed CI and CD service
- can orchestrate the build, test and even deployment of your application every time there is a chagne to your code - all based on a user defined software release process
- traditional manual approaches to code delivery can be slow and prone to errors, whereas an automated process allows developers to frequently release new features and bug fixes in a fast and reliable way
- allows you to model your release process as a workflow or pipeline made up of different tasks, such as the simple workflow represented below
- you define what happens and where for each of the different stages of the workflow and this can be modelled using the CodePipeline UI or CLI
- integrates with CodeCommit, CodeBuild, Lambda, Elastic Beanstalk, CloudFormation, Elastic Container Service as well as third party tools, like GitHub and Jenkins
- every code change pushed to your code repository automatically enters the workflow and triggers the set of actions defined for each stage of the pipeline
- the pipeline automatically stops if one of the stages fails -- for example, if one of your automated unit tests fails, this means that bugs are caught before the code is deployed while they are still easy to fix

## Additional CodePipeline Workflow
1. new commit to watched branch in a Git repository
2. CloudWatch sees the changes and triggers the CodePipeline
3. CodePipeline commands CodeDeploy to build the application for deployment

## Summary
- it is a CI/CD service
- automates your end-to-end software release process based on a user defined workflow
- can be configured to automatically trigger yoru pipeline as soon as a change is deteced in your source code repository
- integrates with other services from AWS like CodeBuild and CodeDeploy as well as thirds party and custom plugins