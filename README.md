<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Access S3 from a VPC

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-s3)

**Author:** Bao Luong  
**Email:** baodevops21@gmail.com

---

## Access S3 from a VPC

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-s3_3e1e79a2)

---

## Introducing Today's Project!

### What is Amazon VPC?

(Virtual Private Cloud) is a service that lets you provision a logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define. Think of it as your own private, isolated network within AWS.

It's incredibly useful because it gives you complete control over your virtual networking environment, including your own IP address range, subnets, route tables, and network gateways.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to securely interact with other AWS services, like Amazon S3. I learnt how to set up the necessary credentials (access keys) for the EC2 instance to communicate with S3 buckets, all while operating within the isolated and controlled network of the VPC.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how the default security group settings for the EC2 instance are handled. In Step 1, when I create a new security group, it automatically allows all inbound SSH traffic by default. This is different from some previous setups where I needed to manually add an inbound rule for SSH.

### This project took me...

This project took me an hour

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will create a VPC and launching an EC2 instance.  This is important, because it sets up the foundations of today's project where we will how to use access keys to enable the EC2 to interact with AWS account and with S3.

### Step 2 - Connect to my EC2 instance

In this step, I will connect to the EC2 instance and try access an AWS service!

### Step 3 - Set up access keys

In this step, I will set up access keys because EC2 instance needs credentials to access AWS services.

---

## Architecture set up

I started my project by launching an EC2 instance then we will connect to it using EC2 instance connect.

I uploaded two png files into the S3 bucket we created.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-s3_4334d777)

---

## Running CLI commands

AWS CLI stands for Amazon Web Services Command Line Interface. It's a powerful tool that allows you to interact with AWS services directly from your command line or terminal. Instead of using the AWS Management Console, you can use text commands to manage your AWS resources.

You have access to the AWS CLI because it comes pre-installed on EC2 instances. This allows you to run commands and manage AWS services directly from your instance's terminal. Engineers often use the CLI to automate tasks and manage AWS resources efficiently using scripts.

The first command I ran was aws s3 ls, which is a command used to list the S3 buckets in your account

The second command I ran was aws configure. This command is used to configure your AWS CLI with the necessary credentials, specifically your Access Key ID and Secret Access Key. These keys act like a username and password, allowing your EC2 instance to securely interact with other AWS services like Amazon S3.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-s3_e7fa8776)

---

## Access keys

### Credentials

The aws configure command is used to set up your AWS CLI with the necessary credentials. These credentials include your Access Key ID and Secret Access Key, which act like a username and password. By providing these, you enable your environment (like an EC2 instance or AWS CloudShell) to securely interact with and manage other AWS services, such as Amazon S3.

Access keys are credentials for your applications and other servers to log into AWS and talk to your AWS services/resources.

Secret access keys are the password that pairs with your access key ID (your username). You need both to access AWS services.

Secret is a key word here - anyone who has it can access your AWS account, so we need to keep this away from anyone else!

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use AWS CloudShell is a browser-based, pre-authenticated shell that you can use directly from the AWS Management Console. It provides a Linux environment with common AWS CLI tools, SDKs, and utilities pre-installed, allowing you to quickly manage your AWS resources without needing to set up a local environment.

---

## In the second part of my project...

### Step 4 - Set up an S3 bucket

In this step, I will create a bucket in Amazon S3. After creating this bucket, we'll learn how to access it from our EC2 instance and do things like checking what objects are in the bucket

### Step 5 - Connecting to my S3 bucket

In this step, I will get the EC2 instance to interact with the S3. 

---

## Connecting to my S3 bucket

The first command I ran was aws s3 ls, which is a command used to list the S3 buckets in your account

When I ran the command aws s3 ls again, the terminal responded with the EC2 that we created. This indicated the EC2 has access to S3. 

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-s3_4334d778)

---

## Connecting to my S3 bucket

Another CLI command I ran was aws s3 ls s3://nextwork-vpc-project-bao which returned the two images we uploaded into S3.

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-s3_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command sudo touch /tmp/test.txt.

This command creates a blank .txt file in your EC2 instance.

The second command I ran was aws s3 cp /tmp/test.txt s3://nextwork-vpc-project-bao.

This command will upload that file into your bucket.

The third command I ran was aws s3 ls s3://nextwork-vpc-project-bao which validated that what objects are listed in the bucket now,

![Image](http://learn.nextwork.org/stimulated_brown_festive_kaffir_lime/uploads/aws-networks-s3_3e1e79a2)

---

---
