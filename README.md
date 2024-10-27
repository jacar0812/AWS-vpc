# Build and configure a VPC in AWS

![6 VPC Architecture](https://github.com/user-attachments/assets/fed59636-a933-449c-96c8-4ca11dd8f305)

## Introduction

This tutorial contains the configuration details and setup steps for an AWS Virtual Private Cloud (VPC) project designed to enhance my understanding of AWS networking in preparation for the CompTIA Cloud+ exam.


## Project Overview
In this project, I created a custom network environment on AWS with the following components:

- **VPC**: A secure, isolated network environment.
- **Subnets**: One public subnet for internet-facing resources and one private subnet for internal-only resources.
- **Internet Gateway**: Provides internet access to resources in the public subnet.
- **NAT Gateway**: Allows resources in the private subnet to securely access the internet.
- **Route Tables**: Configured to manage routing for both subnets, enabling secure and effective network traffic flow.
- **EC2 Instances**: Launched in each subnet for testing access configurations and security.



### _Step 1: Create a VPC_
 
-	**Go to the VPC Dashboard** in the AWS Management Console.
-	Select **Create VPC** and choose the **VPC only** option.
-	Name your VPC (“DevDept”) and select an IP address range ( 172.16.0.0/23).
-	Create **Tags** to track resources
-	Click **Create VPC**.
  
![1 VPC](https://github.com/user-attachments/assets/bc338095-e2de-4786-92e2-6c17bf90a3b8) 
![2 VPC](https://github.com/user-attachments/assets/83acfabd-d8d3-4c11-97c0-a386f5702ff4)
![3 VPC](https://github.com/user-attachments/assets/756e73ea-f24b-4c59-b7b0-acfd0c2bd8b0)
![4 VPC](https://github.com/user-attachments/assets/45b627d6-05a8-4ad1-9637-c1fb0db9dd27)


### _Step 2: Attach an Internet Gateway_

-	In the VPC Dashboard, go to **Internet Gateways** and select **Create Internet Gateway**.
- Create **Tags** to track resources
-	Name it (“DevDept-igw”) and click **Create Internet Gateway**.
-	Select the Internet Gateway, click **Actions**, then **Attach to VPC**.
-	Select the VPC you created and attach it.

![5  Gateway](https://github.com/user-attachments/assets/2b71e254-a909-4270-bffb-282e7a0c0cd9)
![6  Gateway](https://github.com/user-attachments/assets/78c909fc-682a-48ba-bf02-cde523516642)
![7  Gateway](https://github.com/user-attachments/assets/fc961851-66f4-4357-ad00-86beddceeef1)
![8  Gateway](https://github.com/user-attachments/assets/b37ffefc-3705-4d80-a68b-467149ce9f94)


### _Step 2: Create Subnets_ 

-	In the VPC Dashboard, go to **Subnets** and click **Create subnet**.
-	Select the VPC you created in Step 1.
-	**Create a Public Subnet**:
1.	Name it “Subnet-a.”
2.	Choose an Availability Zone and set the IP range (172.16.0.0/28).
3.	Click **Create subne**t.
-	**Create a Private Subnet**:
1.	Repeat the steps to add a Private Subnet with a name (“Subnet-b”).
2.	Set an IP range (172.16.1.0/27).
3.	Click **Create subnet**.

![9 Subnet](https://github.com/user-attachments/assets/5aa445e4-b5e9-4c7d-8736-8f89423627bb)
![10 Subnet](https://github.com/user-attachments/assets/ea34d6a4-a18b-4844-9880-bae74856abea)
![10 Subnet-B](https://github.com/user-attachments/assets/042dd145-eefc-4d59-8903-81af4709b09a)
![11 Public   Private Subnets](https://github.com/user-attachments/assets/2468c026-6302-477a-977d-be173ef3df36)













