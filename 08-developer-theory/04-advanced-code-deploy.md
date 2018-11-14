# Advanced CodeDeploy - AppSpec File
- AppSpec File - is used to define the parameters that will be used for a CodeDeploy deployment; the file structure depends on whether you are deploying to Lambda or EC2/On-Premises
- AppSpec Files in Lambda deployments may be written in YAML or JSON and conains the following fields:
  - version: reserved for future use - currently the only allowed value is 0.0
  - resources: the name and properties of the Lambda function to deploy
  - hooks: specifies Lambda functions to run at set points in the deployment lifecycle to validate the deployment e.g validation tests to run before allowing traffic to be sent to your newly deployed instances

## Example: Lambda-type `appspec.yml`
```yaml
version: 0.0
resources:
  - myLambdaFunction:
    Type: AWS::Lambda::Function
    Properties:
      Name: "myLambdaFunction"
      Alias: "myLambdaFunctionAlias"
      CurrentVersion: "1"
      TargetVersion: "2"
hooks:
  - BeforeAllowTraffic: "LambdaFunctionToValidateBeforeTrafficShift"
  - AfterAllowTraffic: "LambdaFunctionToValidateAfterTrafficShift"
```

## Hooks: Lambda
- the following Hooks are available for use:
  - BeforeAllowTraffic - is used to specify the tasks or functions you want to run before traffic is routed to the newly deployed Lambda function e.g. test to validate that the function has been deployed correctly
  - AfterAllowTraffic - is used to specify the tasks or functions you want to run after the traffic has been routed to the newly deployed Lambda function e.g. test to validate that the function is accepting traffic correctly and behing as expected

## Hooks: EC2/On-Premises
- version: reserved for future use - currently the only allowed value is 0.0
- os: the operating system version you are using e.g. linux, windows, etc.
- files: the location of any application files that need to be copied and where they should be copied to (source and destination folders)
- hooks: lifecycle event hooks allow you to specif scripts that need to run at set points in the deployment lifecycle e.g. to unzip application files prior to deployment, run functional tests on newly deployed application, and to de-register and re-register instances with load balancer

## EC2/On-Premises
- the `appspec.yml` must be placed in the ROOT DIRECTORY of your revision - this is the directory containing your application source code, otherwise the deployement will fail
- typical setup looks like this:
```
/mywebapp
  appspec.yml
  /scripts
  /config
  /source
```

## Example: EC2-type `appspec.yml`
```yaml
version: 0.0
os: linux
files:
  - source: Config/config.txt
    destination: /webapps/Config
  - source: Source
    destination: /webapps/myApp
hooks:
  - BeforeInstall:
    - location: Scripts/UnzipResourceBundle.sh
    - location: Scripts/UnzipDatazBundle.sh
  - AfterInstall:
    - location: Scripts/RunResourceTests.sh
      timeout: 180
  - ApplicationStart:
    - location: Scripts/RunFunctionalTests.sh
      timeout: 3600
  - ValidateService:
    - location: Scripts/MonitorService.sh
      timeout: 3600
      runas: codedeployuser

```

## Supported Hooks for EC2/On-Premises
- BeforeBlockTraffic - run tasks on instances before they are deregistered from a load balancer
- BlockTraffic - deregister instances from a load balancer
- AfterBlockTraffic - run tasks on instances after they are deregistered from a load balancer
- ApplicationStop - gracefully stop the application in preparation for deploying the new revision
- DownloadBundle - the CodeDeploy agent copies the application revision files to a temporary location
- BeforeInstall - details of any pre-installation scripts e.g. backing up the current version, decrypting files
- Install - the CodeDeply agnt copies the application revision files from their temporary locaotin to their correct location
- AfterInstall - details of any post-installation scripts e.g. configuration tasks, change file permission
- ApplicationStart - restarts any services that were stopped during ApplicationStop
- ValidateService - details of any test to validate the service
- BeforAllowTraffic - runs tasks on instances before they are registered with a load balancer
- AllowTraffic - register instances with a load balancer
- AfterAllowTraffic - run tasks on isntance after they are registered with a load balancer

## Run Order of Hooks for CodeDeploy in a In-Place Deployment
1. start
2. BeforeBlockTraffic
3. BlockTraffic
4. AfterBlockTraffic
5. ApplicationStop
6. DownloadBundle
7. BeforeInstall
8. Install
9. AfterInstall
10. ApplicationStart
11. ValidateService
12. BeforeAllowTraffic
13. AllowTraffic
14. AfterAllowTraffic
15. end

## Summary
- the `AppSpec` file defines all the parameters needed for the deployment e.g. location of application files and prepost deployment validation tests to run
- for EC2/on-premisis systems, the `appspec.yml` file must be placed in the root directory of your revision (the same folder that contains your application code); written in YAML
- Lambda supports YAML or JSON
- the run order hooks is important for actual scenarios