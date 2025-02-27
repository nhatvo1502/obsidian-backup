DDoS
    -> Distributed Denial of Service
    -> Layer 4 DDoS attack
        -> SYN flood
        -> transport layer TCP
    -> Layer 7 attack
        -> GET/POST
        -> applications layer

AWS CloudTrail
    -> record AWS Management Console actions and API calls
    -> log into s3 bucket
        -> Metadata api calls
        -> identity of API caller
        -> time API caller
        -> source IP address of API caller
        -> request parameters
        -> response elements returned by service

AWS Shield
    -> Free DDoS Protection
    -> works on ELB, CloudFront and Route 53
    -> protects agaisnt SYN/UDP floods, layer 3 and 4 only
    -> 24/7 access to DDoS Response Team (DRT)
    -> Shield free. Shield Advanced $3,000 per month

AWS WAF
    -> Firewall for layer 7 protection
    -> Behaviors
        -> Allow all explicitly
        -> Block all explicitly
        -> Count requests that match the properties you specify
    -> Define conditions
        -> Ip addresses originate from
        -> Contry originate from
        -> Values in request headers
        -> SQK Code (sQL injection)
        -> cross-site scripting
        -> string appear in requests - regex patterns

AWS GuardDuty
    -> Overview
        -> threat detection that use Machine Learning to monitor for malicious Behaviors
            -> API calls
            -> IP addresses
            -> attempts to disable CloudTrail logging
            -> compromised instances
            -> port scanning
            -> failed logins

    -> Features
        -> alerts GuardDuty's console and CloudWatch events
        -> Receives feeds from third parties
        -> Monitor CloudTrail logs, VPC Flow Logs and DNS logs

AWS Firewall Manager
    -> Overview
        -> security management service in a single pane of glass (console)
        -> centrally setup and manage firewall rules across multiple AWS accounts and applications in AWS organization

AWS Macie
    -> Overview
        -> 

    -> Personally Identifiable Information PII
        -> Personal data used to identify a person
        -> social, home address, passport number, driver license, etc.

    -> Automated Analysis of Data by Macie
        -> Macie use ML and pattern matching to discover sensitive data stored in S3
        -> identify PII, PHI, and financial data
        -> recommend for HIPPA, GPDR compliance

    -> Alerts
        -> sent to Amazon EventBridge
    -> Integration
        -> AWS Step Functions

AWS Inspector
    -> Overview
        -> automated security assessment service that helps improve the security and compliance of applications deployed on AWS
    -> How
        -> assess applications for vulnerabilities or deviations from best practices
    -> Visibility
        -> produces a detailed of security findings prioritized by level of severity
    -> Type
        -> Network Assessments
            -> check ports
            -> not require agent installed

        -> Host Assessment
            -> Vulnerable software CVE
            -> host hardening CIS benchmarks
            -> security best practices
            -> require Inspect agent installed

    -> Steps:
        -> Create assessment targets
        -> Install agents on EC2 instances
        -> Create assessment template
        -> Perform assessment run
        -> review findings agaisnt rules

AWS KMS
    -> Key Management Service
    -> Manage CMK with lifecycle and roles
    -> integrate with AWS services: EBS, S3, and RDS
    -> Rotation:
        -> AWS KMS automatically rotate  every year
    -> Policies
        -> who has access
        -> IAM
    -> Key Policies
        ->you must attach resource-based policies to CMKs

CMK - Csutomer master
    -> logical master key
    -> Includes:
        -> keyID, createion data, description, state
    -> Creation:
        1. key material generated within HSMs managed by AWS
        2. import key material from outside and associate with a CMK
        3. generated and used in AWS CloudHSM cluster

AWS HSM
    -> Hardware Security Module
    -> Physical computing device that safeguards and manages digital keys, encrypt/decrypt keys
    -> contains cryptoprocessor chips

KMS vs HSM
    -> KMS shared tenancy of HSM, auto key rotation, auto key genration
    -> HSM dedicated hardware for you, manual key rotation, manual key generation

AWS Secret Manager
    -> Overview
        -> AWS service to store credentials, keys

    -> Auto rotation
    -> Fine-grained role control

AWS Parameter Store
    -> Similarto Secret Manager but free with limitation
    -> 10,000 parameters
    -> no rotation

Presigned URL
    -> share an item in a private S3 bucket
    -> expiration in seconds

Presigned Cookies
    -> share multiple items in a private S3 bucket

Advanced IAM
    -> Amazon Resource Names (ARN)
        arn:partition:service:region:account_id:<end>

        <end>
            -> resource
            -> resource_type/resource/qualifier
            -> resource_type/resource:qualifier
            -> resource_type:resource
            -> resource_type:resource:qualifier

AWS Certificate Manager
    -> free SSL public and private
    -> automated renewals

AWS Audit Manager
    -> continually audit AWS usage to make sure it stays comply
    -> automated
    -> reports
    -> HIPPA, GDPR

AWS Artifact
    -> compliance-related informtion/document
    -> compliance reports
    -> HIPPA, GDPR

Amazon Cognito
    -> sign-in/sign-up options for apps
    -> guest sign-in
    -> identity broker between app and web id providers
    -> sync user data across multiple devices
    -> recommended for mobile apps that call AWS services

    -> use case:
        -> authentication
        -> 3rd party auth

    -> Components:
        -> User Pools: directory of users
        -> Identity pools: give user access to other AWS services

Amazon Detective (root cause)
    -> investigate root cause of potential security issues and sus activities
    -> use Machine Learning and graph theory

    -> Source:
        -> VPC Flow Logs, CloudTrails logs, EKS audit logs, GuardDuty findings

AWS Network Firewall
    -> managed service to deploy physical firewall protection across VPCs 
    -> Firewall IaaS filter and prevent intrusion for traffic before it reach Interget Gateway
    -> rules
    -> filter internet traffic
    -> filter outbound traffic
    -> inspect VPC across AWS accounts

AWS Security Hub
    -> Alert panel to view all security alerts from GuardDuty, Inspector, Macie, Firewall Manager
    -> across AWS account
    -> Conduct Cloud Securit Posture Management CSPM