# RDS & Elastic Beanstalk
- Elastic Beanstalk supports 2 ways of integrating an RDS database with your Beanstalk Environment
- you can launch the RDS instance from within the Elastic Beanstalk console, which means the RDS instance is created within your Elastic Beanstalk environment - a good option for Dev and Test deployments
  - however this may not be ideal for production environments because it means the lifecycle of your database is tied to the lifecycle of your application environmentl if you terminate the environment, the database instance will be terminated too
- for Production environments, the preferred option is to decouple the RDS instance from your EBS environment: i.e. launch it outside of Elastic Beanstalk, directly from the RDS sections of the onsole
  - this option gives you a lot more flexibility, allows you to connect multiple environments to the same database, provides a wider choice of database types and allows you to tear down your application environment without affecting the database instance
  
## Access to RDS from Elastic Beanstalk
- to allow the EC2 instances in your Elastic Beanstalk environment to connect to an outside database, there are two additional configuration steps required:
  - an additional Security Group must be added to yoru environment's Auto Scaling group
  - you'll need to provide connection string configuration information to your application servers (endpoint, password using Elastic Beanstalk environ ment properties)

## Tips
- two different options for launching your launching your RDS instance:
  - Launch within Elastic Beanstalk
    - when you terminate the Elastic Beanstalk environment, the database will slo be terminated
    - quick and eay to add your data base and get started
    - suitable for Dev and Test environments only
  - Launch outiside of Elastic Beanstalk
    - additional configuration steps required - Security Group and Connection information
    - suitable for Production environments, more flexibility
    - Allows connections from multiple environments, you can tear down the application stack without impacting the database