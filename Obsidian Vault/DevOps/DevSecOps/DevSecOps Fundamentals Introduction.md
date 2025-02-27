# Fundamentals
### Software Security
Software Development Lifecycle:
1. Planning: obtain requirements from the targeted customer and market
2. Defining: define and refine requirement targets and objectives of the software
3. Designing: organize requirements and create the best architecture
4. Development: write software
6. Testing: QA
7. Deployment: release + maintenance

AppSec
1. Using best practices when developing software
2. Identify vulnerabilities
3. Implementing security controls
4. Teams:
	1. Blue Team: Defensive security team approach that focus on security techniques to prevent and alert on attacks
	2. Red Team: Offensive security team approach that provides a security perspective from the attacker's point of view
	3. Purple Team: Collaborative approach in which the Blue Team is notified when penetration testing is been performed, and the Red Team simulate real-world attack techniques

DevOps vs DevSecOps
1. DevOps: collaborate between development and IT
2. DevSecOps: collaborate between dev, IT and Security Team

### LifeCycle
CI/CD
1. Automation
2. Efficiency

# Planning and Coding Secure Software
Planning
Coding

# Building and Testing

### Building
Static Application Security SAST
	1. White-box approach that requires access to source code
	2. Automated review and analysis of the source code
	3. Used as code is developed
	4. Identifies security issues early on within software's development

Software Composition Analysis (SCA)
	1. Third-part dependencies
	2. Tool that scan and analyze open-source software in order to identify security vulnerabilities in code dependencies and libraries

Common Vulnerabilities and Exposures (CVE)
### Testing
Testing Stage
	Perform dynamic application security testing before proceeding with the software release
	Unit testing: testing particular component of a software application
	Fuzzing: random or crafted input into an application and examining the results

Dynamic Application Security Testing (DAST)
	1. Black-box approach that does not require source code access
	2. Tests the application during runtime
	3. Requires running a build of the application

OWASP and Zed Attack Proxy

GCP Web Security Scanner
	Web App DAST Tool
	Provide remedy steps


# Releasing and Deploying Secure Software
## Releasing Secure Software
Releasing Stage
1. Plan
2. Code
3. Build
4. Test
5. Release

Shared responsibility

Configuration Management
1. Baseline and changes
2. Audit and document

Access Management
1. Container security
2. IAM
3. Network security

Data Security
1. Key management
2. DLP
3. Secret Manager

## Deploying Secure Software
Deploying Stage

Environment
1. Development environment: used to writing the software
2. Staging environment: used for testing
3. Production environment: live environment used by actual end users

IaC

Penetration Test: designed to simulate a real-world attack on an organization's website and/or network environment. The key attribute of a penetration test is that discovered vulnerabilities are exploited by the tester
	Reconnaissance -> Enumerate -> Identify -> Exploit -> Report