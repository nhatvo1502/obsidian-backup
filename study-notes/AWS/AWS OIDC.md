### 1. What is it?

AWS OIDC ([[OpenID Connect]]) is a protocol that 

---

### 2. Purpose

1. allows AWS services to authenticate users and application via an external identity provider (IdP), such as GitHub, Google, Okta, or any OIDC-compatible provider. 
2. eliminate the need to mange long-term AWS credentials by allowing federated authentication

---

### 3. Workflow

1. Identity Provider ([[IdP]]) setup
	- a third-part Idp (GitHub Actions, Google, or Okta) issues **OIDC identity tokens**
2. AWS Trust the IdP
	- AWS configures an **IAM Identity Provider** to trust the external IdP using an **OIDC URL**
3. Application Assume IAM Roles via OIDC
	- Applications authenticate to the IdP and receive OIDC token
	- The OIDC token is exchanged for **temporary AWS credentials** via an IAM Role

---

### 4. Example:

Instead of storing AWS_ACCESS_KEY_ID and AWS_SECRET_ACCESS_KEY, configure OIDC authentication in GitHub Actions workflows

#### Step 1: Add an OIDC Provider in AWS Console

1. AWS Console > IAM > Identity providers > Add providers > OpenID Connect
2. Provider URL = `https://token.actions.githubusercontent.com`
3. Audience (Client ID) = `sts.amazonaws.com`


#### Step 2: Attach assume role
 1. AWS Console > IAM > Roles > Create role > Web identity:
	 1. Provider URL = step 1
	 2. Audience = step 1
	 3. Organization = string
 2. Attach permission: Admin
 3. Copy ARN
 
 #### Step 3: GitHub Action

```yml
name: Authenticate with AWS using AWS OICD and list all S3 bucket

on:
  push:
    branches:
      - main
  workflow_dispatch:

permissions:
  id-token: write
  contents: read

jobs:
  run-script:
    runs-on: ubuntu-latest

    steps:
      - name: Configure AWS credentials
        uses: aws-actions/configure-aws-credentials@v2
        with:
          role-to-assume: <role-arn>
          aws-region: us-east-1
          
      - name: AWS CLI
        run: aws s3 ls
```

