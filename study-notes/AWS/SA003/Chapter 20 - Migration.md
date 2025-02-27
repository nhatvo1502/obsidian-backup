AWS Snow Family
	-> Overview
		-> set of secure appliances
		-> petabyte-scale data collection and processing solution

Snow Family
	-> AWS SnowCone
		-> 8 TB storage, 4GB mem, 2vCPUs
		-> smallest device
		-> easy
		-> IoT sensor integration
	-> AWS Snowball Edge
		-> 48TB - 81TB storage
		-> storage, compute, GPU flavors
	-> AWS Snowmobile
		-> truck
		-> 100PB storage
		-> exabyte-scale data center migration

Gateway Family
	-> Storage Gateway
		-> hybrid cloud storage 
		-> merge on-prem resources to cloud
	-> File Gateway
		-> NFS or SMB mount
		-> keep local copy and backup to AWS S3
		-> or keep most recent on prem, everything else on AWS S3
		-> Extend the file storage on prem to cloud
	-> Volume Gateway
		-> iSCSI mount
		-> backup disk or VM
	-> Tape Gateway
		-> Trick tape backup service into thinking this is tape

AWS DataSync
	-> agent-based migration
	-> one-time

Transfer Family
	-> Legacy application 
	-> from local storage to cloud

AWS Migration Hub
	-> Migrate all application 
	-> Aurora RDS
	-> Move everything

AWS Application Discovery Service
	-> help plan migrations to AWS via collection of usage and configuration
	-> Agentless
	-> Agent Based

AWS Application Migration Service MGN
	-> Automated lift and shift service
	-> RTO - Recovery Time Objective:
	-> RPO - Recovery Point Objective:

AWS Database Migration Service DMS
	-> Overview
		-> migration tool for db
		-> from cloud and back
	-> How it works
	-> Concepts
	-> SCT - Schema Creation Tool
		-> migrate same engine
		-> migrate different engines
		-> one endpoints must live in AWS
	-> Three different DB migration
		-> Full Load: all existing data is moved from sources to targets
		-> Full Load and Change Data Capture CDC:  Full + incremental -> guarantees transactional integrity
		-> CDC only: 