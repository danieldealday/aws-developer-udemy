# Elastic Load Balancers (ELB)
- a software that helps balance the workload across multiple different servers equally so that no one web server would become overwhelmed and crash
- can be found in Dashboard>EC2>Load Balancers

## Types of Load Balancers
- application load balancer
- network load balancer
- classic load balancer

## Application Load Balancer
- best suited for load balancing of HTTP or HTTPS traffice
- operate at the OSI Layer 7
- application-aware
- able to create advanced request routing

## Network Load Balancer
- best suited for load balancing of TCP traffic for performance
- operate at the OSI Layer 4
- capable of handling millions of requests per second while maintaing very low latencies

## Classic Load Balancer
- able to load balancer HTTP(S) application
- can use OSI Layer 7 specific features
  - X-Forwarded sessions
  - sticky sessions
- can use strict OSI Layer 4 for pur TCP applications

## Load Balancer Errors
- 504 Error Response
  - application has stopped responding
  - application is having issues at either the Web Server layer or at the Database layer
  - Solution - identify where the application is failing, and scale it up or out where possible
- Receiving Private IP Address from Load Balancer and not User Public IP Address Error
  - an error that occurs when the load balancer is receiving the private IP address instead of the public IP address of the user
  - this is important so that the server knows where the user is coming from
  - Solution: you can find the user public IP address in the X-Forwarded-For Header

  ## Summary
  - 3 Types of Load Balancers
    - application
    - network
    - classic
  - 504 error - gateway has timed out
  - IPv4 address (user IP) missing from load balancer, look in the X-Forwarded-For header