# Chap 1 Intro
What is DevOps?
	1. Software engineering culture and practice that aims at unifying software development (dev) and software operation (ops)
	2. Aims at shorter development cycles, increased deployment frequency, more dependable releases, in close alignment with business objectives

History
	1. DevOps grow out of the Agile software development movement
	2. Agile seeks to develop software in small, frequent cycles to quick turn around delivery time
# Chap 2 Goals
1. Collaboration between Dev and Ops
2. Development wants to increase Speed to quickly delivery but Operation prioritize Stability and less on Speed.
3. With DevOps:
	1. Dev and Ops are playing on the same team
	2. Dev and Ops share the same goals
4. Fast time-to-market (TTM)
5. Few production failures
6. Immediate recovery from failures
# Chap 3 Concepts and Practices
## Build Automation
1. automation of the process of preparing code for deployment to a live environment
2. depending on what languages are used, code needs to be compiled, linted, minified, transformed, unit tested, etc.
3. Build automation means taking these steps and doing them in a consistent, automated way using a script or tool
4. The tools of build automation often differ depending on what programming languages and frameworks are used, but they have on thing in common: automation

why?
1. fast
2. consistent
3. repeatable
4. portable
5. reliable

## Continuous Integration
What is it?
	Continuous Integration (CI): the practice of frequently merging code changes done by dev using automation

CI Server
	When dev commits a code change, CI server sees the change an automatically performs a build, also executing automated tests
	If there is any problem, CI Server will notify dev
	CI Server keeps records of who committed
	Why?
		1. Early detection: notify bugs immediately to Devs
		2. Eliminate the scramble: code is constantly merged, no need to do a big merge at the end
		3. Frequent releases
		4. Continuous testing
		5. Good coding practices

## Continuous Delivery and Continuous Deployment
Continuous Deliver (CD): the practice of continuously maintaining code in a deployable state
Continuous Deployment: the practice of frequently deploying small code changes to production
Both are automated
If a deployment causes a problem it is quickly and reliably rolled back using automated process
Benefits:
	1. Faster TTM
	2. Fewer problems caused by the deployment process
	3. Lower risk
	4. Reliable rollbacks
	5. Fearless deployments

## Infrastructure as Code IaC
Infrastructure as Code (IaC): manage and provision infrastructure through code and automation
With IaC, instead of doing things manually, you use automation and code to create and change:
1. Servers
2. Instances
3. Environments
4. Containers
5. Other infrastructure
Benefits:
	1. Consistency in creation and management of resources
	2. Reusability - Code can be used to make the same change consistently across multiple hosts and can be used again in the future
	3. Scalability 
	4. Self-documenting
	5. Simplify the complexity

## Configuration Management
Configuration Management: maintaining and changing the state of pieces of infrastructure in a consistent, maintainable, and stable way
Configuration Management allows you to minimize configuration drift - the small changes that accumulate over time and make systems different from one another and harder to manage
Benefit from IaC
Why?
	Save time
	Insight - With good configuration management, you can know about the state of all pieces of a large and complex infrastructure
	Maintainability - A more maintainable infrastructure is easier to change in a stable way
	Less configuration drift

## Orchestration
1. Orchestration: automation that support processes and workflows, such as provisioning resources
2. With orchestration, managing a complex infrastructure is less like being a builder and more like conducting an orchestra
3. Why?
	1. Scalability - Resources can be quickly increase or decreased to meet changing needs
	2. Stability - Automation tools can automatically respond to fix problems before users see them
	3. Save time
	4. Self-service
	5. Granular insight into resource usage - Orchestration

## Monitoring
Monitoring: The collection and presentation of data about the performance and stability of services and infrastructure
Monitoring tools collect data over things such as:
	Usage of memory
	CPU
	Disk I/O
	Other resources over time
	Application logs
	Network traffic
	etc
Real-time notifications:
Postmortem analysis
Why?
	1. Fast recovery - the sooner a problem detected, the sooner it can be fixed
	2. Better root cause analysis - The more data you have, the easier it is to determine the root cause of a problem
	3. Visibility across teams - Good monitoring tools give useful data to both developers and operations people about the performance of code in production
	4. Automated response - Monitoring data be used alongside orchestration to provide automated responses to events, such as automated recovery from failures

## Microservices
Microservices: A microservice architecture breaks an application up into a collection of small, loosely-coupled services
Modularity - Microservices encourage modularity. In monolithic apps, individual pieces become tightly coupled, and complexity grows.
Technological flexibility - You don't need to use the same languages and technologies for every part of the app.
Optimized scalability - Scale individual parts of the app based upon resource usage and load. With a monolith, you have to scale up the entire application, even if only one aspect of the service actually needs to be scaled.

# Chap 4 DevOps Tools
## Introduction to DevOps tools
Jenkins is an open source continuous integration tool written in Java. Jenkins provides continuous integration services for software development. It is a server-based system running in a servlet container such as Apache Tomcat. It supports SCM tools including AccuRev, CVS, Subversion, Git, Mercurial, Perforce, Clearcase and RTC, and can execute Apache Ant and Apache Maven based projects as well as arbitrary shell scripts and Windows batch commands.

## Tools for Build Automation
Java - ant, maven, gradle
Javascript - npm, grunt, gulp
Make - widely used in Unix-based systems
Packer - build machine images and containers

Continuous Integration - Continuously merging code into a single branch or mainline
Continuous Integration tools usually consist of a server that integrate with source control
When source code is changed, the server responds by executing an automated build

CI:
	Jenkins
	TravisCI
		Open Source
		Built around Github integration
		Executes builds in clean VMs
	Bamboo
		Enterprise product by Atlassian
		Out-of-the-box integration with other Atlassian products like JIRA and Confluence

## Tools for Configuration Management
Configuration Management - Managing and changing the state of pieces of infrastructure in a consistent and maintainable way

Ansible:
	Open-source
	Declarative configuration: a method of managing infrastructure that allows developers to specify a desired state for a system, and then let the configuration management tool determine how to achieve it
	YAML configuration files
	No control server needed
Puppet:
	Declarative configuration
	Manage state through a UI
	Custom modules use Puppet DSL
	Pushes changes to clients using a control server and agents installed on clients
Chef:
	Procedural configuration
	Agent/server
	Uses Chef DSL
Salt
	Declarative configuration
	Agent (minions) / server (master) - but can support agentless
	Use YAML
	Support for event-driven automation

## Tools for Virtualization
Virtualization - Managing resources by creating virtual rather than physical machines
Hypervisor - Runs on bare metal and manages virtual machines (VMs)
Containers - Lightweight, isolated packages containing everything needed to run a piece of software
Docker - Docker is currently the leading container technology
Containers are still relatively new but very useful DevOps!

## Tools for Monitoring
Monitoring - Collecting and presenting data about the state and performance of applications
2 types of monitoring
	1. Infrastructure monitoring - focus on things related to infrastructure
	2. Application performance  - focus on performance and stability of individual part of the software

### Infrastructure monitoring
SenSu
	1. Designed as a modern replacement for Nagios
	2. Server/agent
	3. Agents push data to an AMQP broker

NewRelic
	1. Saas + agent
	2. Wide variety of metrics



### Application monitoring
AppDynamics - collects data points about applications and presents it in a centralized dashboard
	1. Code-level diagnostics - able to identify performance issues at the code level
	2. Server/agent

NewRelic - APM

### Aggregation and Analytics Tools
Aggregation and Analytics are about collecting monitoring data and doing something with it
Most monitoring tools have some aggregation and analytics features
Elastic Stack - pump data in and quickly create views to aggregate data and easily detect and diagnose problems

### Tools for Orchestration
Orchestration - automation that supports processes and workflows, such as provisioning resources

Docker Swarm 
	1. Docker native
	2. Orchestration for Docker containers

Kubernetes
	1. Open source
	2. Orchestration server
	3. Manage containerized apps across multiple hosts

Zookeeper
	1. Open source -Apache foundation
	2. Can work alongside Kubernetes
	3. Offer a centralized service registry that integrates with orchestration features

Terraform
	1. Combines orchestration and infrastructure as code
	2. Works well with other tools, like Ansible
	3. Works with AWS
	4. Integrates with Kubernetes


# Chap5 Cloud