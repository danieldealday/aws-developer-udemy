# Serverless 101

## History of Cloud Computing
- Amazon EC2 launches in 2006 (infastructure as a service; infrastructure as a service)
- Amazon provides infrastructure to server rack space by allowing users to spin up virtual machines from anywhere in the world
- PaaS (platform as a service) for Amazon is called ElasticBeanstalk
- containers are lightweight alternatives to full-blown virtualization; still need to be deployed to a server
  -  keep containers running
  - scaling and response to load
- AWS Lambda is serverless computing
  - allows you to take your code without any need to provision servers, install software, deploy containers, or worry about any low-level details
  - your code can be run in massive parallel in response to events
  - the cloud provider takes care provisioning and management of the infrastructure and the developer doesn't even need to think about it
  - e.g. Amazon Alexa, anytime you are talking to it you are talking to Lambda