**Serverless**

    -> Offloading physical burden on the cloud central
    -> focusing on code and infra
    -> pay as you go

**Lambda**
 
    -> Overview
        -> serverless compute 
        -> code only

    -> Features
        -> Pricing
            -> 1,000,000 requests and 400,00 GBs compute per month
            -> pay per request after that
        -> Large variety of integration
        -> built-in monitoring
        -> Scale:
            -> memory can use up to 10,240MB
            -> CPU scale with memory
        -> Short-term execution 15min

    -> Building Functions
        -> runtime
            -> environment your code run in (python)
        -> permissions
            -> attach role (AWS IAM)
        -> networking
            -> define VPC, subnet and SG
        -> resources
            -> memory, cpu
        -> trigger
            -> define what trigger lambda

**Amazon MSK**

    -> serverless
    -> fully compatible with Apache Kafka
    -> MSK connect: stream data from and to Kafka

    -> Apache Kafka serverless
        -> open-source streaming data platform
        -> Constrol-plan: CRUD clusters as required
        -> leverage CRUD operations for producing and consuming streaming data 
        -> support existing apps, tools, and plugins

    -> Components and Concepts
        -> Broker Nodes: allow to specify amount of broker nodes per AZ
        -> Zookepper Nodes: handle election
        -> Producer/ Consumers
        -> Cluster Operations: console, aws cli, APIs
    
    -> Resilency
        -> Recovery
        -> Autodetect unhealthy node to replace
        -> Reuse storage from older broker to reduce data replication
        -> Low impact time
        -> Allow producers and consumer apps continue to communicate with the same broker IP

**OpenSearch**

    -> <3 log
    -> to run search and analytics engines
    -> successfor to Amazon ElasticSearch
        -> Amazon ElasticSearch
            -> log analytics, full-text search, security intelligence, etc

**AWS Serverless Application Repository**

    -> Overview
        -> allow users to fine, deploy, publish their own serverless apps
        -> share privately or publicly
        -> Manifest: update code as manifest file - AWS SAM template
        -> integrate with AWS Lambda
    
    -> Options:
        -> Publish
            -> publish apps make them available for other to find and deploy
            -> define apps with AWS SAM templates
            -> private by default
            -> explicitly share

        -> Deploy
            -> find and deploy published applcations
            -> browse app with AWS account
            -> with AWS account, can browse within AWS Lambda console
            -> careful with trusting all applications
            
**Container**

    -> Overview
        -> standard unit of software that pack code and all dependencies
        -> can be deployed quickly and reliably

    -> Terminology
        -> Dockerfile
            -> text doc contains all commands and instructions to build image
        -> Image
            -> Immutable file that contains code, libraries, dependencies, and configuration
        -> Registry
            -> Stores Docker images for distribution
            -> can be private or public
        -> Container
            -> running copy of the image that has been created

**Amazon ECS - Container Orchestration**

    -> Amazon Elastic Container Service
    -> launch and manage Docker containers running on AWS compute

    -> Features:
        -> manage thousand of containers
        -> place and keep container online
        -> register containers with load balancers as they come online/offline
        -> attach roles individual containers
        -> easy to set up and scale
        -> recommend in AWS over EKS
        
**Amazon EKS**

    -> AWS-managed version of open-source Kubernetes
    -> Pros: work with both AWS and other 
    -> Cons: requires a lot more work to setup
    -> recommend in AWS over EKS

**Fargate**

    -> Overview
        -> serverless compute engine to run docker containers
        -> use with ECS or EKS
        -> support Linux and Windows

    -> Fargate vs EC2
        -> AWS responsible for OS
        -> Price based on resource and time ran
        -> Short-running task
        -> Isolted envinroment = more secure
        -> can be mounted EFS file system together

    -> Farget vs Lambda
        -> Suit for more consistent workloads
        -> Greate control across organization

Amazon EventBridge
    -> Overview
        -> central service to design an event driven system
        -> pass events from a source to an endpoint

    -> Concepts
        -> Events
            -> record change in AWS envinroment, SaaS partner, or another applications or services. Scheduled events
        -> Rules
            -> match incoming events and send them to the appropriate targets
            -> based on event patterns or schedules
        -> Event Bus
            -> router that receives events and delivers them to targets
            -> every account has a default bus
            -> can creae custom buses

**Amazon Elastic Container Registry**

    -> Overview
        -> AWS Storage service to store customer Docker Images in AWS

    -> Components
        -> Registry
            -> A private registry provided each AWS account
            -> can be created more

        -> Authorization Token
            -> auth requires for pushing/pulling images to and from repo

        -> Repository
            -> contains Docker Images, OCI images, OCI artifacts

        -> Repo Policy
            -> control all access to repos and images

        -> Image
            -> container images lives inside repo

    -> Life cycle Policy
        -> management image
        -> cleaning up unused images
        -> test rules before applying

    -> Image Scanning
        -> identify software vulnerbility
        -> scan on push
        -> report
    
    -> Sharing
        -> cross-region
        -> cross-account

    -> Cache Rules

    -> Tag Mutability

    -> Integration
        -> Image in ECR can be pulled/pushed from and to ECS, EKS and BYO Docker Orchestration System

**Amazon EKS Distro**

    -> Overview
        -> EKS-D: fully managed by user

**Amazon EKS Anywhere vs EKS**

    -> Control Plane
        -> managed by customer
    -> Location
        -> customer datacenter
    -> Updates
        -> managed by customer
    -> Require Enterprise subscription
    -> Not common

**Amazon ECS Anywhere**

    -> A feature within Amazon ECS
    -> Location
        -> anywhere but still managed by AWS\
    -> How
        -> SSM Agent-> to run scripts
        -> ECS-> container management

**Amazon Aurora**

    -> Overview
        -> On-Demand
        -> Automate
        -> Billing per-second = budget friendly
    
    -> Concepts
        -> Aurora Capacity Units - ACUs
            -> measurements on how cluster scal
            -> set minumum and maximum
        -> 2GiB mem, matching CPU + networking capability
        -> 6 copies of data across 3 AZs
        -> HA
            -> multi-AZ deployment

**AWS X-Ray**

    -> Overview
        -> collects app data -> viewing, filtering, gain insight
        -> downstream AWS resources, microservices APIs and DB
        -> tracibility
        -> tracing headers, send trace data, run X-Ray daemon

    -> Concepts 
        -> Segments: data containing resource name, details, etc
        -> Subsegments: more granular timing information and details
        -> Service graph
        -> Trace: trace ID
        -> Tracing header: X-Amzn-Trace-Id

    -> Integration
    
**AWS AppSync**

    -> Overview
        -> scalable GraphQL interface
        -> combines data from multiple source DynamoDB and lambda
        -> GraphQL: Data language emables app to fetch data from servers
        -> seemless integration with Native React