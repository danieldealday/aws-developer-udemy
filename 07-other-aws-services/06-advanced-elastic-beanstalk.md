# Advanced Elastic Beanstalk

## Configuring Elastic Beanstalk
- you can customize your Elastic Beanstalk environment using Elastic Beanstalk configuration files
  - e.g. you can define packages to install, create Linux users and groups, run shell commands, specifiy services to enable or configure your load balancer, etc.)
- these are files written in YAML or JSON format - they can have a filename of your choice but must have a `.config` extension and be saved inside a folder called `.ebextensions`

## Location of Configuration Files
- the `.ebextensions` folder must be included in the top-level directory of your application source code bundle
- this means that the configuration files can be placed under source control along with the rest of your application code

## myhealthcheckurl.config Example
```javascript
{
  "options_settings":
  [
    {
      "namespace" : "aws:elasticbeanstalk:application",
      "option_name" : "My Application Healthcheck URL",
      "value" : "/healthcheck"
    }
  ]
}
```
- this `.config` file configures an Application Health check URL which will be used by the Elastic Load Balancer

## Tips
- you can customize your Elastic Beanstalk environment by adding configuration files
- the files are written in YAML or JSON
- files have a `.config` extension
- the `.config` files are saved to the `/.ebextensions` folder
- your `/.ebextensions` folder must be located in the top level directory of your application source code bundle