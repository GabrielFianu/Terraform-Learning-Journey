# Step-by-step Guide to Installing Terraform on Windows Using Command Prompt


## Introduction

Terraform enables Infrastructure as Code (IaC), allowing you to define and manage infrastructure using code, promoting version control, reuse, and consistency. 
It supports multi-cloud environments, automating infrastructure provisioning and management, and reducing manual errors. 
By using Terraform, you can ensure consistent infrastructure configurations, improve collaboration, and increase efficiency in your DevOps workflow

---

## Steps to Install Terraform

This guide provides a step-by-step walkthrough on installing Terraform on Windows using the Command Prompt.

### 1. Download Terraform

Navigate to the Install Terraform page (https://developer.hashicorp.com/terraform/install).

![Image](https://github.com/user-attachments/assets/affafba7-bba4-4457-8f88-9c7e24379bcb)

Under the "Install Terraform" section, navigate to **windows section**.

![Image](https://github.com/user-attachments/assets/81032889-fb8d-4cf6-a338-d740c6c1749a)

Click on "AMD64" to download Terraform binary for a 64-bit operating system (OS) or "386" for a 32-bit OS.

![Image](https://github.com/user-attachments/assets/81032889-fb8d-4cf6-a338-d740c6c1749a)

Navigate to your PC's Windows directory and create a new folder named terraform.

![Image](https://github.com/user-attachments/assets/4eda667d-d3a5-41ec-b97d-6f938bfa7638)

In your Downloads, right-click on the downloaded Terraform binary file and select "Extract files..." The window below will pop up.

![Image](https://github.com/user-attachments/assets/86a88a76-9747-4ae4-9e1a-d82afc2298c3)

Navigate to the terraform folder created earlier and select it. This is where you will extract the file. Click on **OK**

![Image](https://github.com/user-attachments/assets/ff8309ac-2659-4078-9ec3-2253f6aa38ee)

---

### 2. Set Terraform Path to System Environment Variables

In your Windows start menu, type environment and click "Edit system environment variables."

![Image](https://github.com/user-attachments/assets/c466ea57-3be1-4e4c-b0cc-b7c5a627cd2e)

Click on "Environment Variables" in the System Properties window.

![Image](https://github.com/user-attachments/assets/d5143e64-f4a6-4f46-99b2-1115e9212426)

Under "System variables," select the "Path", then click "Edit."

![Image](https://github.com/user-attachments/assets/920f3e12-3a0d-42e9-aabd-f1d2ecf49782)

Click "New" and enter the path of the Terraform folder, which is C:\terraform. Click "OK" to close each window.

![Image](https://github.com/user-attachments/assets/d518eeee-c616-4863-833e-1929209c96da)

---

### 3. Verify Terraform Installation and Configuration

Navigate to the folder path C:\terraform in a new command prompt window using the command below:
cd C:\terraform

![Image](https://github.com/user-attachments/assets/21d5099f-5510-44bd-8280-f9464489268f)

Type the terraform -version to verify the installed version.

![Image](https://github.com/user-attachments/assets/02adaffe-7d06-4354-a814-d806d9d8cb89)

---

### Conclusion

Installing Terraform on Windows using the Command Prompt is a straightforward process that enables you to manage infrastructure as code. 
With Terraform installed, you can leverage its powerful features to automate and streamline your infrastructure management tasks. 
Additionally, Terraform can be seamlessly used in PowerShell, providing flexibility in your workflow. 
By following this guide, you're now equipped to harness the full potential of Terraform for your infrastructure needs.

![Image](https://github.com/user-attachments/assets/6a2e5093-d4df-4a62-9f46-cdf9cce6847a)
