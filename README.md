Setup Terraform and Launch an Instance
Getting Started with Terraform
Terraform Example to provision a ec2 Instance

Terraform is an easy to use tool to build and scale the infrastructure with ease. All you need to do is create configuration file and simply run terraform apply command and you are done with building the infrastructure.

Still confused??? Let's explore by example from scratch...

 
The video tutorial of this blog post is below
Install Terraform
Install the required binary package (depending upon your OS) from Download page

Unzip the .zip file to the bin directory as as per the your OS

For mac


unzip terraform_0.7.2_darwin_amd64.zip -d /usr/local/bin

Type terraform command to see if the command is available or not
Writing Configuration File
Make a terraform directory in which we will keep our files.  Name of this directory could be anything you want.


mkdir ~/terraform
cd ~/terraform


Create an example file to launch an instance on AWS. The file could be in json format or in *.tf format. Let's use .tf format.


vi launch_instance.tf

Put the following configurations in the file


provider "aws" {
        access_key = "XXXXXXXXXXXXXXXX"
        secret_key = "XXXXXXXXXXXXXXXXXXXXXX"
        region = "ap-southeast-1"
}

resource "aws_instance" "example" {
        ami = "ami-a59b49c6"
        instance_type = "t2.micro"
        key_name = "mykey"
        security_groups= ["sample-sg"]
        tags {
         Name = "terraform-instance"
        }
}


Replace the access_key and secret_key and other AWS parameters as per your need.

Now run terraform plan to see what terraform will if the above file is executed.


terraform plan

Now run the command terraform apply to run the above file

terraform apply

Now check AWS, the instance is launched. This is the power of Terraform, on a single command you can build the entire infrastructure.
