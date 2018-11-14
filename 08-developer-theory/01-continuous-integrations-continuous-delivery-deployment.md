# Continuous Integrations & Continuous Delivery/Deployment
- CI & CD are best practices for software development and deployment
- they enable frequent software changes to be applied whilst maintaining system and service stability
- companies like AWS, Netflix, Google and Facebook have pioneered this approach to releasing code, successfully applying thousands of changes per day

## Example Integration
- multiple developer working in on different features or bug fixes
- all contributing to the same application
- sharing the same code repository (e.g. Git)
- workflow
  1. frequently pushing their updates into the shared repo (at least daily)
  2. repository is integrated with a build management system
  3. code changes trigger and automated build
    - we need a way to ensure that any code change does not break the build or introduce new bugs in the application
  4. automated test system runs on the newly built application
    - identifies any bugs, preventing issues from being introduced into the `master` branch of code
- CI focuses on small code changes which frequently committed into the main repository once they have been successfully tested

## Continuous Delivery/Deployment (CD)
- a development practice where merged changes are automatically built, tested, and prepared for release into staging and eventually production environments
- there is usually a manual decision process to initiate deployment of the new code
- takes the idea of automation and automatically deploys the new code following successful testing, eliminating manual steps
- the new code is automatically released as soon as it passes through the stages of your release process(build > test > package for release)
- small changes are released early and frequently
- both practices require the build, test, and deployment processes to be fully automated but CD also automates the release process as well

## Example CI-to-CD
1. developers commit approved feature(s) through pull requests (AWS CodeCommit)
2. repository prompts the build management system to create application (CodeBuild)
3. application code is ran through a test framework
4. passing the tests the application code is released to a deploy packaged applications (CodeDeploy)
5. released application code is relased into the respective environments
6. the result of this is the AWS CodePipeline when using AWS services

## Summary
- weighted heavily in the associate exam
- [White Paper](https://d1.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf) is highly recommended to be read
- CI is about integrating or mergin the code changes frequently
  - at least once per day, enables multiple devs to work on the same application
- continuous delivery is all about automating the build, test and deployment functions
- continuous deployment fully automates the entire release process, code is deployed into production as soon as it has successfully passed through the release pipeline
- AWS CI/CD Tools
  - CodeCommit - source control service
  - CodeBuild - compile source code, run tests and package code
  - CodeDeploy - automated deployment to EC2, on-premises systems and/or Lambda
  - CodePipeline - CI/CD workflow tool, fully automates the entire release process (build, test, deployment)