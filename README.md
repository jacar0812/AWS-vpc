# Build and configure a VPC in AWS

![6 VPC Architecture](https://github.com/user-attachments/assets/fed59636-a933-449c-96c8-4ca11dd8f305)

## Introduction

This tutorial contains the configuration details and setup steps for an AWS Virtual Private Cloud (VPC) project designed to enhance my understanding of AWS networking in preparation for the CompTIA Cloud+ exam.


# Project Overview
In this project, I created a custom network environment on AWS with the following components:

- **VPC**: A secure, isolated network environment.
- **Subnets**: One public subnet for internet-facing resources and one private subnet for internal-only resources.
- **Internet Gateway**: Provides internet access to resources in the public subnet.
- **NAT Gateway**: Allows resources in the private subnet to securely access the internet.
- **Route Tables**: Configured to manage routing for both subnets, enabling secure and effective network traffic flow.
- **EC2 Instances**: Launched in each subnet for testing access configurations and security.

