# Launching VPC Resources

**Project Link:** https://learn.nextwork.org/projects/aws-networks-ec2  
**Author:** Shane Brown  

---

## Overview

This project focuses on launching and securing compute resources inside an Amazon Virtual Private Cloud (VPC). The goal is to understand how EC2 instances are deployed into public and private subnets and how networking and security controls affect access and communication.

This project ties together VPC design, routing, and security concepts by deploying real servers into the network and validating how traffic flows between them. :contentReference[oaicite:0]{index=0}

---

## What I built

I launched and configured EC2 instances inside a custom VPC to demonstrate real-world cloud network behavior. This included:

- Launching an EC2 instance in a public subnet with internet access  
- Launching an EC2 instance in a private subnet with restricted access  
- Configuring security groups to control instance-to-instance communication  
- Using SSH key pairs to securely access virtual machines  
- Validating how subnet design impacts connectivity and security  

This setup reflects common production architectures where public-facing servers interact with protected backend systems. :contentReference[oaicite:1]{index=1}

---

## Key concepts learned

- How EC2 instances are launched into specific VPCs and subnets  
- Differences between public and private servers  
- How SSH enables secure remote access to virtual machines  
- How key pairs replace passwords for EC2 authentication  
- How security groups restrict traffic based on source and destination  
- How subnet placement directly affects exposure to the internet :contentReference[oaicite:2]{index=2}

---

## Public vs Private servers

- **Public Server**
  - Launched in a public subnet  
  - Has a route to an Internet Gateway  
  - Can be accessed from the internet (when allowed by security groups)  

- **Private Server**
  - Launched in a private subnet  
  - Has no direct internet access  
  - Accepts traffic only from trusted internal resources  

This separation reduces attack surface and follows cloud security best practices. :contentReference[oaicite:3]{index=3}

---

## Using the VPC creation wizard

I also explored creating a VPC using the AWS VPC creation wizard. This method automatically provisions core networking resources such as subnets, route tables, and internet gateways.

The VPC resource map provided a visual overview of how all networking components were connected, making it easier to understand traffic flow and troubleshoot configurations. :contentReference[oaicite:4]{index=4}

---

## Why this project matters

Launching compute resources securely is a core cloud skill. Understanding how EC2 instances interact with VPC networking and security controls is essential for cloud engineering, DevOps, and cloud security roles.

This project demonstrates how infrastructure design decisions directly impact accessibility, security, and reliability. :contentReference[oaicite:5]{index=5}

---

## Documentation

📄 **Full project documentation:**  
[documentation.md](./documentation.md)

This file includes detailed explanations, configurations, reflections, and screenshots from completing the project.

---

## Credits

Built as part of the **NextWork** AWS networking learning series.
