**Overview**

	-> External vs Internal
	-> CloudFront
	-> ElasticCache
	-> DAX: DynamoDB
	-> Global Accelerator

**CloudFront**

	-> CDN
	-> reduce latency
	-> Edge Locations
	-> Settings
		-> Security: SSL
		-> GLobal Distribution
		-> Endpoint Support
		-> TTL

**ElastiCache**

	-> Overview
		-> AWS service to managed 2 open-source caching technologies
			-> Memcached
				-> Simple database catch solution (SQL query)
				-> can' act as a database
				-> no failover
			-> Redis
				-> supported as a caching solution
				-> functions as a standalone database
				-> failover and multi-AZ support

**Dax - DynamoDB 
	
	-> Overview
		-> In-memory Cache: reduce DynamoDB response time from mili to micro
		-> Location: live in VPC
		-> Control: node size, cluster count, data TTL, maintain and updates


**Global Accelerator**
Overview
	-> Networking service send traffic through AWS global network infrastructure via accelerators
	-> in crease performance and help deal with IP caching by using Anycast IP 
	-> TCP or UDP traffic

Components
	-> Accelerator: Direct user traffic to optimal AWS endpoints
	-> Listener: Processes inbound connections based on ports and protocols
	-> Endpoint: Resources that GA directs traffic to

High-Level View
	-> provided Two static Anycast IP addresses
	-> Dual-stack receives four static IP addresses (2 IPv4 + 2 IPv6)
	-> Static IPs act as a single, fixed entry for all client traffic
	-> Standard: traffic routed based on user location, health checks, and weights
	-> Custom: Traffic routed to specified EC2 instances and ports in a VPC
 