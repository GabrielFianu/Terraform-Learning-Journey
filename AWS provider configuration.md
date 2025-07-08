# Terraform AWS Provider Configuration

## Introduction

This guide outlines how to configure Terraform to communicate with AWS using the AWS Provider. 
The setup allows Terraform to authenticate with AWS so it can manage resources using your credentials.
It assumes you have AWS credentials and Terraform installed.

---

## Requirements

- [Terraform](https://developer.hashicorp.com/terraform/downloads) (v1.0+)
- [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) (configured)
- AWS IAM User 

---

## Steps to Configure

### 1. Set up AWS Credentials

Using Your terminal type the command below. For this guide, I used Windows Command Prompt.

```bash
aws configure
```


You'll be prompted to enter:

- AWS Access Key ID
- AWS Secret Access Key
- Default region (e.g., `us-east-1`)
- Default output format (e.g., `json`)


<img width="331" height="279" alt="Image" src="https://github.com/user-attachments/assets/6d515790-2257-4b56-ad13-cf54d6bf7a75" />

This creates a file at `~/.aws/credentials`.

---

Alterantively, you can use the method below

#### Manually (Environment Variables)

```bash
export AWS_ACCESS_KEY_ID="your-access-key-id"
export AWS_SECRET_ACCESS_KEY="your-secret-access-key"
export AWS_DEFAULT_REGION="us-east-1"
```

---

### 2. Confirm you configuration

Use the following commands below to check you aws configuration

```bash
aws sts get-caller-identity
```

The aws sts get-caller-identity command returns details about the AWS entity making the request, including:

- Account: The AWS account ID associated with the entity.
- Arn: The Amazon Resource Name (ARN) of the entity.
- UserId: The unique identifier of the entity.

<img width="579" height="181" alt="Image" src="https://github.com/user-attachments/assets/6374d380-5845-47c1-bbb6-9977d0d25ac9" />


```bash
aws configure get region
```

This command returns the default region

<img width="608" height="134" alt="Image" src="https://github.com/user-attachments/assets/203f667d-cf3f-482c-8dbe-8448b1fcc3c2" />
