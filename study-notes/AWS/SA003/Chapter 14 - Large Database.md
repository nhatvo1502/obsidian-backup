**The 3 Vs of Big Data**

    -> Volume: terabytes to petabytes
    -> Variety: wide range of resource and formats
    -> Volocity: collected, stored, processed, and analyzed data

**Amazon RedShift**

    -> Fully Managed, petabytes Warehouse RDS
    -> Size:
        -> 16 PB
    -> Relational
        -> standard
    
    -> HA
        -> only support 2 AZ at this time

    -> SnapShot
        -> incremental and PIT in S3

    -> DR
        ->
    
    -> Recommended for large data

    -> Spectrum and Enhanced VPC Routing
        -> Spectrum
            -> query and retrieve data from S3
        -> Enhanced VPC Routing
            -> All copy and unload traffic between cluster and repo through VPC

**Elastic MapReduce EMR**

    -> ETL: structure to handle data from organization
        -> usecase:
            -> Extract: data from the source
            -> Transform: manipulate data
            -> Load: into AWS services

    -> EMR

    -> EMR Storage
        -> Hadoop Distributed File System HDFS
        -> EMR File System
        -> Local file system
    -> Amazon EMR Clusters and Nodes
        -> Primary Nodes
            -> manage cluster, coordinate distribution of data and tasks
        -> Core Nodes
            -> Hadoop distribued file System HDFS
        -> Task Nodes
            -> runs task with no storage (like a vm)
    -> Pricing
        -> On-Demand
        -> Reserved
        -> Spot

**Kinesis**

    -> Overview

    -> Kinesis Data Streams
        -> Real time streaming for ingesting data
        -> Real time
        -> You responsible for creating the consumer and scaling stream

    -> Kinesis Data Firehose
        -> Data transfer tool to get information to S3, Redshift, Elasticsearch, or Splunk
        -> Near real time (within 60 seconds)
        -> Plug and play with AWS
    
    -> Structure
        -> Kinesis Data Sream
            -> Producer->Kinesis->Consumer->Storage
        -> Kinesis Data Firehose
            -> Input->DataFirehose->Storage
    
    -> Data Analytics
        -> Analyze data using standard SQL

    -> offer real-time big data transfer

**Athena**

    -> interactive query service analyz data in S3 using SQL

Glue
    -> design a schema for Athena
    -> serverless data integration
    -> perform ETL workloads without managing underlying servers

**Amazon QuickSight**

    -> Overview
        -> serverless BI data visualization service

    -> Feature
        -> Useful for business data visualizations, ad-hoc data analytics, BI insights
        -> integrates with Amazon RDS, Amazon Aurora, Athena, S3
        -> SPICE: advance calculation
        -> Column-Level Security CLS
 
    -> Dashboards, Users and Groups

**AWS Data Pipeline**

    -> automating movement and transformation data
    -> Features:
        -> Data Driven: dependencies between tasks and activities
        -> AWS Storage integration
        -> EC2 and EMR Compute integration
        -> SNS notification
    -> Use case:
        -> Processing data in EMR using Hadoop streaming
        -> import/export DynamoDB data
        -> copy CSV files/dta between S3 buckets
        -> export RDS data to S3
        -> copy data to Redshift

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

Amazon ECS - Container Orchestration
    -> Amazon Elastic Container Service
    -> launch and manage Docker containers running on AWS compute

    -> Features:
        -> manage thousand of containers
        -> place and keep container online
        -> register containers with load balancers as they come online/offline
        -> attach roles individual containers
        -> easy to set up and scale
        -> recommend in AWS over EKS
        
Amazon EKS
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

**Amazon EventBridge**

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

Amazon EKS Distro
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
    
