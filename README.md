# Build and configure a VPC in AWS

![6 VPC Architecture II](https://github.com/user-attachments/assets/be5958e0-9dca-475a-b600-9d967eddbefc)

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


### _Step 3: Create Subnets_ 

-	In the VPC Dashboard, go to **Subnets** and click **Create subnet**.
-	Select the VPC you created in Step 1.
-	**Create a Public Subnet**:
1.	Name it “Subnet-a.”
2.	Choose an Availability Zone and set the IP range (172.16.0.0/28).
3.	Create **Tags** to track resources
4.	Click **Create subne**t.
-	**Create a Private Subnet**:
1.	Repeat the steps to add a Private Subnet with a name (“Subnet-b”).
2.	Set an IP range (172.16.1.0/27).
3.	Create **Tags** to track resources
4.	Click **Create subnet**.

![9 Subnet](https://github.com/user-attachments/assets/5aa445e4-b5e9-4c7d-8736-8f89423627bb)
![10 Subnet](https://github.com/user-attachments/assets/ea34d6a4-a18b-4844-9880-bae74856abea)
![10 Subnet-B](https://github.com/user-attachments/assets/042dd145-eefc-4d59-8903-81af4709b09a)
![11 Public   Private Subnets](https://github.com/user-attachments/assets/2468c026-6302-477a-977d-be173ef3df36)



### _Step 4: Create a NAT Gateway_

-	Go to the **NAT Gateways** section in the VPC Dashboard and click **Create NAT Gateway**.
-	Select the Public Subnet and assign an Elastic IP address (click **Allocate Elastic IP** if needed).
-	Create **Tags** to track resources
-	Click **Create NAT Gateway**.

![12 NAT gateway](https://github.com/user-attachments/assets/7e54ec01-21bb-48eb-b79b-d94510e75cf7)
![13 NAT gateway](https://github.com/user-attachments/assets/affd279a-f84a-4634-888e-40b9047fcad8)


### _Step 5: Configure Route Tables_

-	In the VPC Dashboard, go to **Route Tables**.
#### Public Route Table:
-	Select the Route Table associated with your VPC’s main routing table (usually the default created for your VPC).
-	Name it (“DevDept-rtPublic”).
-	In the Routes section, add a route:
-	Create **Tags** to track resources
1.	Destination: 0.0.0.0/0 (for all traffic).
2.	Target: Select the **Internet Gateway**.
-	Go to the **Subnet Associations** tab, select **Edit subnet associations**, and associate it with the Public Subnet.

![14 Route Table](https://github.com/user-attachments/assets/d908279a-1319-4cdf-be67-c46045a773f4)
![15  Edit routes](https://github.com/user-attachments/assets/36d37f27-12ae-4961-b520-3a95282b6506)
![16 Subnet associations](https://github.com/user-attachments/assets/d2636543-3880-49bc-8e73-8a48ccc44d7e)



	
#### Private Route Table:
-	Go back to **Route Tables** and click **Create Route Table**.
-	Name it (“DevDept-rtPriv”) and associate it with your VPC.
- In the Routes section, add a route:
- Create **Tags** to track resources
1.	Destination: 0.0.0.0/0 (for outbound internet access).
2.	Target: Select the **NAT Gateway** created in Step 4.
- Go to **Subnet Associations** and associate this route table with the Private Subnet

![17 Subnet associations-2](https://github.com/user-attachments/assets/d59e21e7-28e1-4a4a-aca6-0ceb441bfbf4)
![18 Edit route table-2](https://github.com/user-attachments/assets/b9e1d57f-837c-49ae-8101-0cfc88b3a4a7)
![19 Subnet associations-3](https://github.com/user-attachments/assets/8e11b636-c067-4e35-aaf9-0c0295581bbb)


### _Step 6: Launch EC2 Instances_
-	Go to the EC2 Dashboard and click Launch Instance.
#### Public EC2 Instance:
-	For Instance Details, select the Public Subnet and ensure Auto-assign Public IP is enabled.
-	Configure other settings as needed (AWS Linux machine).
-	Select a security group with inbound rules to allow SSH/HTTP (as needed) for public access.
-	Launch the instance.

![20 EC2 instance-1](https://github.com/user-attachments/assets/a1d7d7b5-b102-492f-83de-97289b96f918)
![21 EC2 instance settings](https://github.com/user-attachments/assets/926eadd2-cc05-47ea-914c-322a793fc61f)
![22 EC2 instance settings-2](https://github.com/user-attachments/assets/f39f4d69-5e78-4843-9ccc-90b859adc48e)




#### Private EC2 Instance:
-	Launch a second EC2 instance (AWS Linux Machine) in the Private Subnet, with Auto-assign Public IP set to “Disable.”
-	Choose a security group that allows only private network traffic or internal applications.
-	Launch the instance.



![23 EC2 instance-2](https://github.com/user-attachments/assets/7f2ee492-1dca-406f-ab74-f1eafeb96705)
![24 EC2 instance-2 settings](https://github.com/user-attachments/assets/350a75c8-fc2d-4151-9ca9-d8932f8efa01)
![25 Instances](https://github.com/user-attachments/assets/ce358fd6-156b-4f02-af32-5c2179aa6afa)



### Key Learning Objectives
- Understanding VPC structure and components
- Configuring secure subnet routing with Internet and NAT Gateways
- Practicing public/private EC2 instance setup and secure access management

  
This project provided valuable hands-on experience with AWS networking, security groups, and VPC architecture essentials required for Cloud+ certification.







