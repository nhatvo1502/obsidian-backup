
EBS Volumes
	-> virtual hard disk on the cloud
	-> type:
		-> gp2
			-> smaller than 1TB 3000 IOPS
			-> boot vol
		-> io1
			-> 64000 IOPS
			-> performance intensive
		-> st1
			-> Throughput optimized HDD
			-> low-cost

Volume
	-> same AZ with the attached EC2
	-> resizable
	-> type: gp2 io1 st1


Snapshot
	-> Point in time picture of a volume
	-> lives on S3
	-> can be full or incremental
	-> encrypted
	-> sharable

Encrypt an Unencrypted Volume
	1. Create a snapshot of the unencrypted root vol
	2. Create a copy with encryption
	3. Create AMI with this copy
	4. Use AMI to launch new encrypted instance

EC2 Hibernation
	-> saves the contents from instance RAM to EBS root vol
	-> ram less than 150GB
	-> less than 60 days
	-> no spot instance
	-> good for long-run process instance

EFS - Elastic File System
	-> managed NFS mountable on EC2 instance
	-> work with EC2 instances from multi AZs
	-> scalable
	-> expensive
	-> good for content management system

FSx for Windows
	-> run Windows Server Message Block SMB
	-> designed for Windows
	-> Support AD users, ACL, groups, etc

FSx for Luster
	-> high-speed, high-capacity storage
	-> HPC - high performance computing
	-> can store directly to S3

AMI - Amazon Machine Image
	-> Region
		-> root can be store on 
			-> EBS - instance can be stop and delete without losing data
			-> Instance store - stop/delete instance will lose data

AWS Backup
	-> Central backup solution
	-> Automation