# What is Terraform?
Terraform is an open-source Infrastructure as Code (IAC) tool developed by HashiCorp. It is designed to help automate and manage the provisioning and configuration of infrastructure resources in a declarative and efficient manner. Terraform allows you to define your infrastructure components, including virtual machines, networks, storage, databases, and more, as code using a domain-specific language called HashiCorp Configuration Language (HCL) or JSON.


# Terraform with AWS?
Terraform is a popular choice for managing infrastructure on Amazon Web Services (AWS) because it offers a powerful way to provision, configure, and manage AWS resources using Infrastructure as Code (IAC) principles. Here's how Terraform can be used with AWS:


# Provisioning EC2 instance using Terraform?
<pre>
#Define the AWS provider
provider "aws" {
  region = "ap-south-1"  
}

#Define the EC2 instance
resource "aws_instance" "demo_instance" {
  ami           = "ami-id"  
  instance_type = "t2.micro"          

  tags = {
    Name = "demo-Instance"
  }
}
</pre>


# Why not Ansible for IAC?
Both Terraform and Ansible can be used for Infrastructure as Code (IAC) purposes, but they excel in different areas. Terraform is typically preferred for infrastructure provisioning due to its declarative approach and strong support for managing cloud resources. Ansible, on the other hand, is often chosen for configuration management, application deployment, and orchestration tasks. The choice between them depends on your specific needs and use cases.


# How to secure AWS access and secret keys?
In above example instead of giving access and secret keys in the terraform file we can use AWS's provided IAM service.


# Extra Points:
1. Terraform's different files(.tf, tfvars, tfstate).
2. Terraform Output
3. Terraform Commands


=================================================================================================================================
# Terraform Learning:
If we've written subnet resource first and then vpc resource, terraform is smart enough to create vpc first then subnet.


