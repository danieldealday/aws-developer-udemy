# Version Control with Lambda
- when you use `versioning` in AWS Lambda, you can publish one or more versions of your Lambda function; as a result, you can work with different variations of your Lambda function in your development workflow, such as development, beta and production
- each lambda function version has a unique Amazon Resource Name (ARN); after you publish a version, it is immutable
- lambda maintains your latest function code in the `$LATEST` version; when you update your function code, AWS Lambda replaces the code in the `$LATEST` version of the Lambda function

## Qualified/Unqualified ARNs
- you can refer to this function using its Amazon Resource Name (ARN); there are 2 ARNs associated with this initial version
- Qualified ARN - the function ARN with the version suffix
  ```
  arn:aws:lambda:aws-region:acct-id:function:helloworld:$LATEST
  ```
- Unqualified ARN - the function ARN without the version suffix
  ```
  arn:aws:lambda:aws-region:acct-id:function:helloworld
  ```

## Alias
- After initially creating a lambda function (the `$LATEST` version), you can publish a version 1 of it. By creating an alias named `PROD` that points to version 1, you can now use the PROD alias to invoke version 1 of the lambda function
  - Now, you can update the code (the `$LATEST` version) with all of your improvements and then publish another stable and improved version (version 2). You can promote version 2 to production by remapping the `PROD` alias so that it points to version 2. If you find something wrong, you can easily roll back the production version to version 1 by remapping `PROD` alias so taht it points to version 1

## Tips
- can have multiple versions of lambda functions
- latest version will use `$LATEST`
- qualified version will use `$LATEST`, unqualified will not have it
- versions are immutable
- can split traffic using aliases to different versions
  - can not split traffic with `$LATEST`, instead create alias to latest