<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-ec2)

**Author:** Shane Brown  
**Email:** shanebrown848@gmail.com

---

## Launching VPC Resources

![Image](http://learn.nextwork.org/encouraged_yellow_silly_yeti/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a virtual network in AWS that lets you create and control your own isolated networking environment in the cloud. It allows you to define IP address ranges, create public and private subnets, set up routing, and apply security controls like security groups and network ACLs. Amazon VPC is useful because it gives you full control over how your resources communicate, improves security by isolating resources, and provides a scalable foundation for building secure and reliable cloud applications.

### How I used Amazon VPC in this project

I used Amazon VPC to create and manage a custom network environment for my AWS resources. I set up a VPC with defined IP address ranges, created public and private subnets, configured route tables and an internet gateway, and applied security groups and network ACLs to control traffic. I then launched EC2 instances into both the public and private subnets to see how resources communicate securely within the VPC and how access is controlled based on subnet design.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how confusing it can be learning Networking, I am not a fan of it but it is something I have to learn for my Pentesting career.

### This project took me...

This project took me about 1 hour. I took my time.

---

## Setting Up Direct VM Access

Directly accessing an EC2 instance means connecting to the virtual machine’s operating system and using its command line or desktop as if the server were physically in front of you. This allows you to run commands, install software, change configurations, and troubleshoot issues at the operating system level. Access is usually done securely over the network using tools like SSH and a key pair instead of a password.

### SSH is a key method for directly accessing a VM

SSH stands for Secure Shell. SSH traffic means encrypted network communication used to securely connect to and manage a remote server, such as an EC2 instance. It allows users to log in, run commands, and transfer data while protecting the connection from eavesdropping or unauthorized access.

### To enable direct access, I set up key pairs

A key pair is a set of two cryptographic keys used to securely access an EC2 instance. It consists of a public key, which is stored on the EC2 instance, and a private key, which is kept by the user. When connecting to the instance, AWS uses these keys to verify identity and allow secure access without using passwords. This helps protect the instance from unauthorized access.

A private key’s file format refers to the way the cryptographic key is stored so that operating systems and applications can read and use it correctly. Different systems support different key formats, so choosing the right one matters for compatibility. My private key’s file format was .pem, which is widely supported and commonly used for securely connecting to EC2 instances.

---

## Launching a public server

I had to change my EC2 instance’s networking settings by editing the Network settings during the instance launch process. I selected my custom VPC instead of the default VPC, chose the public subnet I created earlier, and attached an existing security group that allows the required network traffic. This ensured the EC2 instance was launched inside the correct VPC and subnet with proper internet access and security rules applied.

![Image](http://learn.nextwork.org/encouraged_yellow_silly_yeti/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because it needs stricter access controls than the public server. The private server should not be accessible from the internet, so its security group limits traffic to trusted resources inside the VPC, such as the public EC2 instance. This separation improves security by reducing the attack surface and following the principle of least privilege.

My private server’s security group’s source is the NextWork Public Security Group, which means only EC2 instances that belong to that public security group are allowed to connect to the private server. This prevents direct access from the internet and ensures that only trusted resources inside the VPC can communicate with the private instance.

![Image](http://learn.nextwork.org/encouraged_yellow_silly_yeti/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC. This time, I used the VPC creation wizard to automatically create the VPC and its core networking resources, including subnets, route tables, and an internet gateway. I adjusted the number of availability zones and subnets, customized the CIDR blocks, and disabled optional features like NAT gateways and VPC endpoints. This approach saved time while still letting me see how all the networking components are connected through the VPC resource map.

A VPC resource map is a visual diagram in the AWS console that shows all the networking resources inside a VPC and how they are connected to each other. It displays components like subnets, route tables, internet gateways, and NAT gateways, and highlights the relationships between them. This helps you quickly understand your network layout, troubleshoot connectivity issues, and see how traffic flows within the VPC.

My new VPC has a CIDR block of 10.0.0.0/16. It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because VPCs are isolated from each other within AWS. As long as the VPCs are not directly connected through peering, VPNs, or other networking links, they can use the same IP address ranges without causing conflicts.

![Image](http://learn.nextwork.org/encouraged_yellow_silly_yeti/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: one public subnet or two public subnets. This was because the number of public subnets is tied to the number of Availability Zones selected during the VPC setup, and AWS creates at most one public subnet per Availability Zone to maintain a balanced and highly available network design.

The setup page also offered to create NAT gateways, which are AWS-managed networking services that allow resources in private subnets to access the internet securely. NAT gateways let private instances download updates or reach external services while blocking inbound internet traffic, so the instances remain protected. They are commonly used when private resources need outbound internet access without being directly exposed to the public internet.

![Image](http://learn.nextwork.org/encouraged_yellow_silly_yeti/uploads/aws-networks-ec2_8ee57662)

---

---
