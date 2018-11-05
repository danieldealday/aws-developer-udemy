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