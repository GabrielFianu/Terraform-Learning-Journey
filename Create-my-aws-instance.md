# Creating and managing your infrastructure as code.

## Introduction

In this tutorial, I will use Terraform to provision an EC2 instance on Amazon Web Services (AWS). EC2 instances are virtual machines running on AWS and a common component of many infrastructure projects. 
To provision your infrastructure, you will write configuration to define your provider and instance, set environment variables for your AWS credentials, initialize a new local workspace, and then apply your configuration to create your instance.

---

### 1. Create infrastructure

**Create a new directory for the Terraform configuration**
```
mkdir learn-terraform-get-started-aws
```

**Change into the directory**
```
cd learn-terraform-get-started-aws
```

<img width="692" height="100" alt="Image" src="https://github.com/user-attachments/assets/7c1982d3-bdb6-4013-9d6b-ba31289a258c" /> 


**The terraform {} block**
The terraform block manages your Terraform settings, including provider versions and the version of Terraform itself.

Create the terraform.tf file and add the following configuration.

<img width="219" height="175" alt="Image" src="https://github.com/user-attachments/assets/edebd2e9-c8be-4090-b4a0-0b9b48012b4a" />

```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.92"
    }
  }

  required_version = ">= 1.2"
}
```


**Configuration blocks**
Terraform parses all .tf files in the working directory, allowing you to flexibly organize your configuration. We recommend a consistent pattern to make maintaining your configuration easier.

Create the main.tf file and add the following configuration. This configuration defines your AWS provider, accesses the latest Amazon Linux AMI, and creates an EC2 instance.

<img width="219" height="175" alt="Image" src="https://github.com/user-attachments/assets/edebd2e9-c8be-4090-b4a0-0b9b48012b4a" />


```
provider "aws" {
  region = "us-west-2"

  access_key                  = "anaccesskey"
  secret_key                  = "asecretkey"
  s3_use_path_style           = true
  skip_credentials_validation = true
  skip_metadata_api_check     = true
  skip_requesting_account_id  = true

  endpoints {
    ec2        = "http://localhost:4566"
  }
}

data "aws_ami" "linux" {
  most_recent = true

  filter {
    name = "name"
    values = ["amzn2-ami-hvm-2.0.*-x86_64-ebs"]
  }

  owners = ["137112412989"] # Amazon
}

resource "aws_instance" "app_server" {
  ami           = data.aws_ami.linux.id
  instance_type = "t2.micro"

  tags = {
    Name = "hashicorp-learn"
  }
}
```


**Format configuration**
You can use the **terraform fmt** command to update your configuration to match the canonical Terraform format and style. Terraform will print out the names of any files it updates. 

bash
```
terraform fmt
```
<img width="722" height="92" alt="Image" src="https://github.com/user-attachments/assets/c6d56809-d4b3-4edc-8ab1-52d029394036" />


**Initialize your workspace**
To create your infrastructure, you must first use terraform init to install your configuration's required components.

bash
```
terraform init
```

<img width="747" height="609" alt="Image" src="https://github.com/user-attachments/assets/f75ae956-63ae-409c-a0f5-8aff2b12fbb9" />


**Plan and Apply your configuration to create your EC2 instance.**

Run terraform plan to generate an execution plan for teraform. It shows you what actions terraform will take when you apply you configuration without actually making any changes.

bash
run
```
terraform plan
```

<img width="737" height="711" alt="Image" src="https://github.com/user-attachments/assets/eb72d760-fa65-417f-933d-8ad28b9146f9" />

Terraform will print out a plan to make this change, and wait for you to confirm it. Respond to the confirmation prompt with a yes to confirm the plan.

bash
```
terraform apply
```

<img width="747" height="694" alt="Image" src="https://github.com/user-attachments/assets/bc7a5f7b-ec36-48eb-ae68-36d7c0ca5ae7" />

<img width="746" height="624" alt="Image" src="https://github.com/user-attachments/assets/bc0f049b-cf96-4e2e-9f16-534bfd4058e3" />


**Inspect state**
Terraform stores your workspace's state in a file named terraform.tfstate.

List state
List the resources and data sources in your state with the terrafrom state list command.

bash
```
terraform state list
```

<img width="745" height="234" alt="Image" src="https://github.com/user-attachments/assets/f29b2b52-2b07-4890-b46b-37e6cc337518" />


**Show state**
Print out your workspace's entire state with terraform show.

bash
```
terraform show
```

<img width="741" height="768" alt="Image" src="https://github.com/user-attachments/assets/76c7238e-d522-4ec3-ad71-95048522ad3e" />


**Confirm from the console**

![Image](https://github.com/user-attachments/assets/59e94c70-b5c9-4b24-8d43-65ad4ecc1c68)


**Destroy workspace**
Destroy your workspace with terraform destroy. Terraform will create a plan to destroy all of the resources managed by your workspace. Respond to the confirmation prompt with a yes to confirm the plan.

bash
run

```
terraform destroy
```

<img width="740" height="632" alt="Image" src="https://github.com/user-attachments/assets/adf256e1-34ae-498c-a9eb-d95b961b7a7b" />

<img width="1366" height="768" alt="Image" src="https://github.com/user-attachments/assets/041bc0db-3cd4-4c9d-a268-0861bb193c81" />

<img width="739" height="713" alt="Image" src="https://github.com/user-attachments/assets/b4a67725-af95-4c52-8c74-dbab2114c4e5" />

![Image](https://github.com/user-attachments/assets/425d12a2-b4dc-4a75-b0a9-07eda0b9cba8)


**Inspect Terraform state**
Print out a list of your workspace's resources with terraform state list.

bash
run

```
terraform state list
```

<img width="743" height="272" alt="Image" src="https://github.com/user-attachments/assets/857fd1ef-a456-485b-b9f6-5a646bcde002" />


---
