# Elastic Beanstalk 101
- a service for deploying and scaling web application developed in many popular languages: Java, .NET, PHP, Node.js Python, Ruby, Go and Docker onto widely used application server platforms like Apache Tomcat, Nginx, Passenger and IIS
- developers can focus on writing code and don't need to worry about any of the underlying infrastructure needed to run the application
- you upload the code and Elastic Beanstalk will handle deployment, capacity provisioning, load balancing, auto-scaling and application health
- you retain full control of the underlying AWS resources powering yoru application and you pay only for the AWs resources required to store and run you applications
  - e.g. EC2 instances and S3 buckets
- fastest and simplest way to deploy your application in AWS
- automatically sacles your application up and down
- you can select the EC3 instance type that is optimal for your application
- you can retain full administrative control over the resources powering yoru application or have Elastic Beanstalk do it for you
- Managed Platform Updates feature automatically applies updates your Operating System, Java, PHP, Node.js, etc.
- monitor and manage application health via a dashboard
- integrated with CloudWatch and X-ray for performance data and metrics

## Tips
- deploys and scales your web applications including the web application server platform where required
- supports widely used programming technologies - Java, PHP, Python, Ruby, Go, Docker, .NET, Node.js
- supports application-server platforms like Tomcat, Passenger, Puma, and IIS
- provision the underlying resources for you
- can fully manage the EC2 instaneces for you or you can take full administrative control
- updates, monitoring, metrics and health checks all included