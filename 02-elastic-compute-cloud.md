# Elastic Compute Cloud (EC2)
- a virtual server in the cloud
- a web service that provides resizable compute capacity in the cloud
- reduces the time required to obtain and boot new server instances to minutes, allowing quick scale capacity, both up and down, as your computing requirements change
- changes the economics of computing by allowing you to pay only for capacity that you actually use
- provides developers the tools to build failure resilient applications & isolate themselves from common failure scenarios

## Payment Options
- On Demand - allows you to pay fixed rate by the hour or by the second with no commitment
- Reserved - provides you with a capacity reservation adn offer a significant discount on the hourly charge for an instance (1 to 3 year terms)
- Spot - enables you to bid whatever price you want for instance capacity, providing for even greater savings if your applications have flexible start and end times
- Dedicated Hosts - physical EC2 server dedicated for your use; they can help you reduce costs by allowing you to use your existing server-bound software licenses

## On Demand
- perfect for user that want the low cost and flexibility without any up-front payment or long-term commitment
- application with short term, spiky or unpredictable workloads that cannot be interrupted
- applications being developed or tested on Amazon EC2 for the first time
- great for learning because you provision instances as you need it and then turn them off when you don't

## Reserved Instances
- applications with steady state or predictable usage
- applictions that require reserved capacity
- user can make up-front payments to reduce their total computing costs even further
  - standard reserved instances - up to 75% off on-demand
  - convertible reserved instances - up to 54% off on-demand - feauture the capability to change the attributes of the reserved instance as long as the exchange results in the creation of reserved instances of equal or greater value
  - scheduled reserved instances are available to launch within the time window you reserve; this option allows you to match your capacity reservation to a predictable recurring schedule that only requires a fraction of a day, a week, or a month

## Spot Instances
- applicaitons that have flexible start and end times
- applications that are only feasible at very low compute prices
- users with and urgent need for large amounts of additional computing capacity

## Dedicated Hosts
- userful for regulatory requirements that may not support multi-tenatn virtualization
- great for licensing which does not support multi-tenancy or cloud deployments
- can be purchase On-Demand (hourly)
- can be purchased as a reservation for up to 70% off the On-Demand price

## EC2 Instance Types
![AWS EC2 Instance](https://scriptcrunch.com/wp-content/uploads/2016/08/instance-deatils_mini.jpg "AWS EC2 Instance Types")
- F – FPGA
- I – IOPS
- G – Graphics
- H – High Disk Throughput
- T – Cheap general purpse
- D – Density
- R – RAM
- M – Main choice for general purpose apps
- C – Compute
- P – Pictures
- X – Extreme Memory

## Elastic Block Storage (EBS )
- a virtual disk in the cloud
- allows you to created storage volumes and attach them to EC2 instances
- create a file system
- run a database
- any functionality from a [block-device](https://en.wikipedia.org/wiki/Device_file#Block_devices)
- volumes are placed ina specific Availability Zone, where they are automatically replicated to protect you from the failure of a single component
- the EBS volume that is attached to your EC2 instance where Windows or Linux is installed is called the Root Volume

## EBS Volume Types
- General Purpose SSD (GP2)
  - general purpose, balances both price and performance
  - ratio of 3 [IOPS](https://en.wikipedia.org/wiki/IOPS) per GB with up to 10,000 IOPS and the ability toburst up to 3000 IOPS for extended periods of time for volumes at 3334 GB and above
- Provision IOPS SSD (IO1)
  - good for intensive applications, SQL & NoSQL databases
  - designed for I/O intensive applications such ars large relational or NoSQL databases
  - use if your need more than 10,000 IOPS
  - can provision up to 20,000 IOPS per volume
- Throughput Optimized HDD (ST1)
  - big data
  - data warehouses
  - log processing
  - cannot be a boot volume
- Cold HDD (SC1)
  - lowest cost storage for infrequently accessed workloads
  - file server
  - cannot be a boot volume
- Magnetic (Standard)
  - lowest cost per gigabyte of all EBS volume types that is bootable
  - magnetic volumes are ideal for workloads where data is accessed infrequently and applications where the lowest storage cost is important

## Summary
- On Demand - allows you to pay a fxed rate by the hour or by the second with no commitment
- Reserved - provides you with a capacity reservation and offer a significant discount on the hourly charge for an instance; 1 year to 3 year terms where the longer the term the greater the discount benefits on cost
- Spot - enables you to bid whatever price you want for the instance capacity, providing for even greater savings if your application have flexible start and end times; if terminated by Amazon, you wil not be charged for partial hour of usage, however, you will be charged that hour if you terminate the instance yourself
- Dedicated Hosts - physical EC2 server dedicated for your use; can help you reduce costs by allowing you to use your existing server-bound software licenses
- SSD
  - General Purpose SSD - balances price and performance for a wide variety of workloads
  - Provisioned IOPS SSD - highest-performance SSD volume for mission-critical low-latency or high-throughput workloads
- Magnetic
  - Throughput Optimized HDD - low cost HDD volume designed for frequently accessed, throughput-intensive workloads
  - Cold HDD - lowest cost HDD volume designed for less frequently accessed workloads
  - Magnetic - previous generation and can be a boot volume