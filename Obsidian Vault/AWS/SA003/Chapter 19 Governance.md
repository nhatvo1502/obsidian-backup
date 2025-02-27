
**AWS Organizations**
Overview
	-> Free governance tool to create and manage AWS accounts from a single location
	
Account Types
	-> Management Account
		-> Payer account
		-> Primary (root)
	-> Member Account
		-> All other account that belong to 1 organizations
		
Features
	-> Consolidated Billing
	-> Usage Discounts
	-> Shared Savings

Concepts
	-> Multi-account
	-> Tag Enforcement
	-> Organizational Unit (OU)
		-> Logical grouping of multiple accounts
	-> Service Control Policies (SCPs)
		https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_policies_scps_evaluation.html
	-> Best Practices
		-> Create central service login accounts

AWS Resource Access Manager - RAM
	-> Overview
		-> Share resources across AWS accounts
		-> avoid creating duplicate resources across accounts
	-> Type of resources
	-> Permission:
		-> Ownership
			-> create and manage VPC resources that shared
			-> cannot delete or modify deployed resource by participant accounts
		-> Participant Account
			-> provision services into shared VPC subnet
			-> cannot modify or delete shared resources

Cross-account access
	-> Regional services
	-> Benefit:
		-> Secure
		-> organized
	-> Steps:
		1. Create new IAM role with a policy that has the least amount of privileges required
		2. Update the Trust Policy to allow role assumption from the Auditor Account IAM role
		3. Provide ARM of ourRole to external

AWS Config
	-> Overview
		-> inventory management and control toll
		-> show configuration history of infrastructure over time
		-> ability to create rules to make sure resources conform to the requirements
		-> receiving alerts
	->Rules
		-> AWS-managed config rules
		-> Custom config rules
		-> rules are evaluated on schedule or by a trigger
		-> meant for monitor not preventative
	-> Cost:
		-> 0.003 per item
	-> Remediation
		-> can enable automatic remediation via SSM Automation Documents
		-> Automation Documents can be AWS-managed or custom
		-> Custom Automation Documents can leverage Lambda functions for custom logic
		-> auto-remediation fails -> enable a retry
	-> Alerts
		-> SNS
		-> EventBridge

AWS Directory Service
	-> Overview
		-> allow to run AD inside AWS
	-> Use-case
		-> Managed Microsoft AD
		-> AD Connector
			-> tunnel between AWS with on-premises AD
		-> Simple AD
			-> Linux Samba Active Directory


AWS Cost Explorer
	-> Overview 
		-> visualize and analyze cloud costs
		-> custom reports
	-> Features
		-> Time
		-> Filter
			-> where is the spend coming from
			-> filter on tag, categories
		-> Service
			-> break down cost by service

AWS Budget
	-> Overview
	-> Types
		-> Cost: plan how much you want to spend on a service
		-> Usage: Plan how much you want to use on one or many services
		-> RI Utilization: Utilization threshold. See if any RI are unused or under-utilized
		-> RI Coverage: Coverage threshold. See how much of instance usage is covered by a reservation
		-> Savings Plans Utilization: Threshold
		-> Saving Plans Coverage: threshold

AWS Cost ad Usage Report CUR
	-> Overview
		-> most comprehensive and detailed view of AWS spending
		-> publishing billing reports to S3
		-> break down cost by the time span (hour, day, and month), service and resource or by tags
		-> CUR updates report in S3 once a day using CSV formats
		-> integrate with Athena, Redshift or QuickSight

AWS Compute Optimizer
	-> Optimizes: Analyzes configuration and utilization metrics
	-> Reporting: reports current usage optimizations and potential recommendations
	-> Graphs: 
	-> Inform decisions
	
AWS Organization
	-> use for an organization in management account
	-> can be use as a standalone account

AWS Saving Plans
	-> Types:
		-> Compute Savings
			-> Applies to ec2, lambda or FarGate
			-> 66% savings
		-> EC2 Instance
			-> Applies to EC2 instances of a specific instance family in specific Regions
			-> 72% Savings
		-> SageMaker Savings
			-> Only for SageMaker
			-> 64% Savings

AWS Trusted Advisor
	-> Overview
		-> fully managed best-practice auditing tool
		-> inspects your AWS environment then make recommendations:
			-> save money
			-> improve availability and performance
			-> security suggest
	-> How
		-> use industry and customer-established best practices to check AWS accounts
		-> account level scan, doesn't scan inside the instance
		-> Basic or Developer Support plans: all checks in Service Limits category + 6 checks in Security category
		-> Business, Enterprise, On-Ramp, or Enterprise support: full access to AWS Trusted Advisory checks + full integration with Amazon EventBridge
	-> Categories:
		-> Cost Optimization:
		-> Performance:
		-> Security:
		-> Fault Tolerance:
		-> Service Limits:

AWS Control Tower
	-> Overview
		-> quickest way to create and manage a secure, compliant, multi-account environment based on best practices
	-> Features
		-> Landing zone: Well-architected, multi-account environment based on compliance and security best practices
		-> Guardrails: High-level rules providing continuous governance for AWS environment
			-> Preventive: leverage Service Control Policies to prevent noncompliant actions
			-> Detective Guardrail: leverage AWS Config rules to detect and alert on violating actions or changes
		-> Account Factory: account template for standardizing pre-approved configs of new accounts
		-> CloudFormation StackSet: Automated deployments of templates deploying repeated resources for governance
		-> Share account: 3 

AWS License Manage
	-> Overview
		-> AWS service making license management simpler and more efficient
	-> Keywords:
		-> AWS-hosted license management
		-> Hybrid environment license management
		-> Preventing license abuse

AWS Health
	-> Overview
		-> health visibility
		-> alerts
		-> alert are specific to account + public announcement
		-> automate with alerts using EventBridge
	-> Concepts

AWS Service Catalog
	-> Overview
		-> AWS service that provides catalogs of preapproved services as CF templates
		-> allow end users in the org to deploy approved services into their own account

AWS Proton
	-> Overview
		-> IaC provisioning and deployments of serverless/container 
		-> support CF and Terraform
		-> self-service tool for developer

AWS Well-Architected Framework
	-> Overview
		-> a tool for measuring current workload against established AWS best practices
		