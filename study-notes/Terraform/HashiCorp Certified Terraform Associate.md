#terraform

# 1. Intro
## Infrastructure as Code (IaC)
What? - Write down what you want to deploy
Why? - tracked in version, better visibility, collab across teams, reduce human flaws
How? - written declaratively via code

## Advantages
Automate Software Defined Networking
Interacts and takes care of communication with control layer APIs with ease
Supports a vast array of private and public cloud vendors
Tracks state of each resource deployed

## Terraform Workflow:
Write -> Plan -> Apply

## Commands
*terraform int*
run after the initial code

*terraform plan*
read the code and show a plan of execution/deployment
allow user to review the action before executing anything
use authentication credentials to connect to cloud infrastructure

*terraform apply*
deploys the code
tracking with "state file"

*terraform destroy*
destroy all resources created by the code
non-reversible command

#### configuring provider
```
provider "aws" {
	credentials = file("credentials.json")
	region = "us-east-1"
}
```

#### configuring resource
```
resource "aws_instance" "web" {
	ami = "ami-a1b2c3d4"
	instance_type = "t2_micro"
}

resource_address = aws_instance.web
```

#### data source
use to call existing resource
```
data "aws_instance" "my-vm" {
	instance_id = "i-123456789"
}

instance_address = data.aws_instance.my-vm
```
#### terraform providers registry
https://registry.terraform.io/browse/providers

# 2. Installation
## Method 1: Download, Unzip
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

## Method 2: Set up Terraform Repository on Linux
https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli

# 3. Terraform State
terraform.tfstate
*terraform state list* list out all resources tracked by the Terraform State file
*terraform state rm* delete a resource from the Terraform State file
*terraform state show* show details of a resource tracked in the Terraform State file

#### local storage
default behavior

#### remote storage
collab, store on s3
```
# backend.tf

terraform {
	required_providers {
		docker = {
			source = "nhat/docker"
		}	
	}
	required_version = ">= 0.13"
	backend = "s3" {
		profile = "demo"
		region = "us-east-1"
		key = "terraform.tfstate"
		bucket = "myawesomes3bucket3344"
	}
}
```
# 4. Variables

#### declaration
```
variable "my-var" {
	default = "default value"
}

variable_address = variable.my-var
```

#### validation
```
variable "my-var" {
	description = "My Test Variable"
	type = string
	default = "hello"
	validation {
		condition = length(var.my-var) > 4
		error_message = "The string must be more than 4 characters"
	}
}
```
#### censor
```
variable "my-var" {
	description = "My Test Variable"
	type = string
	default = "Hello"
	sensitive = true
}
```
Base Types: string, number, bool
Complex Types: list, set , map, object, tuple
#### list type
```
variable "availability_zone_names" {
	type = list(string)
	default = ["us-west-1a"]
}
```

#### list of Objects
```
variable "docker_ports" {
	type = list(object({
		internal = number
		external = number
		protocol = string	
	}))
	default = [
		{
			internal = 8300
			external = 8300
			protocol = "tcp"
		}
	]
}
```

#### output
use to show on the shell after running
```
output "instance_ip" {
	description = "VM's Private IP"
	value = aws_instance.my-vm.private_ip
}
```

# 5. Provisioners

#### create
run with *terraform apply*
```
resource "null_resource" "dummy_resource" {
	provisioner "local-exec" {
		command = "echo '0' > status.txt"
	}
}
```

#### destroy
run with *terraform destroy*
```
resource "null_resource" "dummy_resource" {
	provisioner "local-exec" {
		when = destroy
		command = "echo '1' > status.txt"
	}
}
```

#### local-exec
run on the local machine where Terraform is executed
```
resource "null_resource" "resource_status" {
	provisioner "local_exec" {
		when = destroy
		command "echo '1' > status.txt"
	}
}
```

#### remote-exec
run on the on the remote resource
```
# Create a resource and run bootstrap to setup Apache webserver using Provisioners remote-exec then putput the public_ip back to local computer


# main.tf
resource "aws_instance" "webserver" {
  ami                         = data.aws_ssm_parameter.webserver-ami.value
  instance_type               = "t3.micro"
  key_name                    = aws_key_pair.webserver-key.key_name
  associate_public_ip_address = true
  vpc_security_group_ids      = [aws_security_group.sg.id]
  subnet_id                   = aws_subnet.subnet.id
  provisioner "remote-exec" {
    inline = [
      "sudo yum -y install httpd && sudo systemctl start httpd",
      "echo '<h1><center>My Test Website With Help From Terraform Provisioner</center></h1>' > index.html",
      "sudo mv index.html /var/www/html/"
    ]
    connection {
      type        = "ssh"
      user        = "ec2-user"
      private_key = file("~/.ssh/id_rsa")
      host        = self.public_ip
    }
  }
  tags = {
    Name = "webserver"
  }
}

# Output.tf
output "Webserver-Public-IP" {
	value = aws_instance.webserver.public_ip
}
```



# 6. Modules
### directory
```
main directory = ./terraform_project
module directory = ./terraform_project/modules/my_modules
module main = ./terraform_project/modules/my_modules/main.tf
module output = ./terraform_project/modules/my_modules/output.tf
```

### syntax
```
module "module_name" {
	source = "./modules/my_modules"
	version = "0.0.0.1"
	region = var.region -> can be passed as variable
}
```

### accessing module
```
resource "aws_instance" "my-vpc-module" {
	subnet_id = module.my-vpc-module.subnet_id
}
```

# 7. Built-ins Functions
#### Terraform comes pre-packed with functions
#### User-defined functions are not allow

### terraform console
```
terraform console
max(5, 1, 2, 3)
> 5

timestamp()

join()

contains()
```

### variable primitive
```
single type value
number,s tring, bool

replicas = 3
name = "cluster2"
backup = true
```

#### (complex) collections
```
a list of same type variables

variable "training" {
	type = list(string)
	default = ["ACG", "LA"]
}
```

#### (complex) structural
```
a list of more than one type of variables

variable "traoning" {
	type = object({
		name = string
		age = number
	})
}
```

#### (complex) any
```
a placeholder for a primitive type yet to be decided
variable "training" {
	type = list(any)
}

```

# 8. Dynamic Blocks
#### Dynamically

# 9. Terraform CLI

#### Terraform Format
```
terraform fmt
```
Format Terraform code for readability
Help keeping the code consistent

#### Terraform Taint
```
terraform taint <resource_address>
```
Mark a resource to be deleted and re-created on the next *terraform apply*

#### Terraform Import
Take an existing resource which is not managed by Terraform and map it into terraform resource using ID
ID is vendor specific. Ex: AWS EC2 instance provide instance ID
Import same resource to multiple Terraform resources can cause unknown behavior and not recommended
```
terraform import resource_address <id>
```

#### Terraform Workspace
*create workspace*
```
terraform workspace new <WORKSPACE-NAME>
```

*select workspace*
```
terraform workspace select <WORKSPACE-NAME>
```

# 10. Debugging
#### Setting logging environment variable for Terraform
```
export TF_LOG=TRACE
export TF_LOG_PATH=./terraform.log
```

#### debugger can be set to the follow levels
```
TRACE, DEBUG,INFO, WARN, ERROR, OFF
```


# 11. Terraform Enterprise
#### Terraform Sentinel
- Enforce policies on terraform code
- has it own language - Sentinel language
- designed to be approachable by non-programmers
- Benefits: sandbox, codification, version control, testing and automation
- Use case: enforcing CIS standards across AWS accounts, make sure only certain of instance types are used, ensuring SG do now allow traffic on port 22
#### Harshicorp Vault:
	- Secrets management software
	- Dynamically provisions credentials and rotates them
	- encrypts sensitive data in transit and at rest and provides fine-grained access to secrets using ACLs

#### Terraform Registry
- A repo of publicly available Terraform providers and modules
- you can publish and share your own modules
- https://registry.terraform.io
- you can collaborate with other contributors to make changes and modules

#### Terraform Cloud Workspaces
- Workspace hosted on cloud
- versioning
- share and collab
- records of all execution activity
- all terraform commands executed on "managed" Terraform Cloud VMs

#### Terraform OSS Workspaces
- Stores alternate state files in same working directory
