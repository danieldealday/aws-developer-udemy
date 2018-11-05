# Updating Elastic Beanstalk

## EBS Deployment Policies
- all-at-once
- rolling
- rolling with additional batch
- immutable

### All-At-Once Deployment Policy
- updates will...
  - deploy the new version to all instances simultaneously
  - all of your instances are out of service while the deployment takes places
  - you will experience an outage while the deployment is taking place - not ideal for mission-critical production systems
  - if the update fails, you need to roll back the changes by re-deploying the original version to all your instances

### Rolling Deployment Policy
- udpates will...
  - deploy the new version in batches
  - each batch of instances is taken out of service while the deployment takes place
  - not ideal for performance sensitive systems
  - if the update fails, you need to perform an additional rolling update to roll back the changes

### Rolling with Additional Batch Policy
- updates will...
  - launches an additional batch of instances
  - deploys the new versino in batches
  - maintains full capacity during the deployment process
  - if the update fails, you need to perform an additional rolling update to roll back the changes

### Immutable Deployment Policy
- updates will...
  - deploys the new version to a fresh group of instances in their own new autoscaling group
  - when the new instances pass their health checks, they are moved to your existing auto scaling group; and finally, the old instances are terminated
  - maintains full capacity during the deployment process
  - the impact of a failed update is far less and the rollback process requires only terminating the new auto scaling group
  - preferred option for Mission Critical production systems