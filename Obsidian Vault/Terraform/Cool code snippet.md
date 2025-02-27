### condition in validation
check value parse to variable, only accept 8080 or 80
```
#variables.tf
variable "external_port" {
	type = number
	default = 8080
	validation {
		condition = can(regex("8080|80", var.external_port))
		error_message = "Port values can only be 8080 or 80."
	}
}
```

### create s3 bucket using awscli
```
aws configure
aws s3api create-bucket --bucket <bucket-name> --region <region>
```

### logic: deploy region depends on workspace
```
provider "aws" {
	region = terraform.workspace == "default" ? "us-east-2" : "us-west-1"
}
```