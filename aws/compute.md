## Containers

### ECS - fully managed container orchestrator
    - no need to manage control plane
    - manages deployments, autoscaling, self-healing
    - AWS proprietary orchestration 
    - Integrates seamlessly with other AWS services

### AWS Fargate
    - Serverless compute for containers
    - No EC2 AMIs to manage
    - Secure by default (isolated, patched, and compliant)
    - Elastic on-demand pricing model
    - resources provisioned based on cpu and memory defined

#### Networking
    - requires *awsvpc* network mode
    - each task gets its own ENI

#### Autoscaling
    - simplified model, you don't have to worry about EC2 instances and resource management

#### Limitations
    - no privileged containers
    - cannot specify hostport or hostnetwork
    - only run on private subjects with NAT gateway access to AWS services, not a direct route to IG
    - can't be deployed to AWS Outposts, AWS Wavelength, or AWS Local Zones
    - No EC2 IMDS

### AppRunner
    - fully managed
    - no need to worry about VPC, subnets, networking, EC2, etc
    - great fit for simple application synchronously responding to HTTP requests

#### Limitations
    - is accessible from the internet
    - no way to control incoming traffic
    - no external private container registries.  Must use public or ECR
    - limited to HTTP requests (e.g. WebSockets not supported)
    - GitHub is the only repo currently supported (this may have changed)

#### Autoscaling
    - can scale down to 0 by pausing instances on low traffic

[Fargate vs Apprunner](https://cloudonaut.io/fargate-vs-apprunner/)

### EKS - Kubernetes based container orchestration
    - Better for complex applications where more control is required
    - Requires more expertise
    - Scalability requires manual configuration

### ECS Anywhere 
    - run containers on customer-managed infrastructure (on-prem)

### EKS Anywhere
    - run Kubernetes on-prem




## IMPORTANT LINKS
[Exercism](https://exercism.org/dashboard)
[AWS Workshops](https://workshops.aws/)
[ECS Workshop](https://ecsworkshop.com)

