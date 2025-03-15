# Deploying and Managing an EC2 Instance on AWS


<img width="908" alt="ec2 architecture" src="https://github.com/user-attachments/assets/3c5bb147-4974-4a3d-80c7-018bef626794" />

Setting up a reliable and efficient cloud environment begins with deploying the right compute resources. In this project, I launched and configured an Amazon EC2 instance, making key decisions to balance performance, security, and cost. From selecting the appropriate instance type to configuring network settings, storage, and security measures, each step was guided by best practices to ensure a seamless deployment.

This documentation captures the entire process, highlighting the reasoning behind each choice and its impact on the overall infrastructure.

---

## Step 1: Select a Region
After logging into the AWS Management Console, I navigated to EC2 and selected a region based on factors like latency and redundancy. The region selection ensures optimal performance for my application.

![Screenshot 2025-03-15 at 14 37 35 2](https://github.com/user-attachments/assets/56116111-1bb4-4192-b5f6-251e0997ca1f)


## Step 2 & 3: Naming the EC2 Instance & Choosing an Amazon Machine Image (AMI)
I assigned a meaningful name to my instance using the Name tag, following a structured tagging strategy for easy identification. For 3, I selected an Amazon Machine Image (AMI) that included the necessary OS and software. AWS provides pre-configured AMIs, but users can also create custom ones or explore options in the AWS Marketplace.

<img width="964" alt="Screenshot 2025-03-15 at 16 01 25" src="https://github.com/user-attachments/assets/5128b438-fb5f-4ef9-92e1-c988caf5cdce" />




## Step 4: Choosing the Right EC2 Instance Type
With over 750 instance types in AWS, selecting the right one requires understanding application demands for compute, memory, storage, and networking. Under-provisioning leads to performance bottlenecks, while over-provisioning results in unnecessary costs. For this project, I chose a **t3.micro** instance (2 vCPUs, 1 GiB RAM) to balance efficiency and cost-effectiveness. 

![Screenshot 2025-03-15 at 14 39 22 2](https://github.com/user-attachments/assets/f90d1bc5-db6d-404b-83e2-c1603731cc47)


## Step 5: Configuring Secure Access with a Key Pair
To ensure secure access to the instance, I generated a key pair. Amazon EC2 uses public-key cryptography for authentication, requiring the private key during connection. By specifying the key pair at launch, I established a secure means of accessing the instance.

![Screenshot 2025-03-15 at 14 42 24](https://github.com/user-attachments/assets/c7350481-4238-45a1-b89d-0d4ce5307a40)


## Step 6: Setting Up Networking and Security
Networking configurations determined the accessibility and security of the instance. I assigned the instance to a Lab VPC and created a Web Server security group to define access rules. The security group functioned as a virtual firewall, controlling inbound and outbound traffic. To enhance security, I removed SSH access, limiting potential attack vectors.

![Screenshot 2025-03-15 at 14 44 50 2](https://github.com/user-attachments/assets/191664f0-33c7-4eda-8a0b-f2ac92d7afae)


## Step 7: Adding Storage
For persistent storage, I used Amazon Elastic Block Store (EBS) and maintained the default **8 GiB root volume**, ensuring sufficient space for the web server while keeping storage costs optimized. Additional storage configurations could be made depending on future requirements. 

![Screenshot 2025-03-15 at 14 45 12](https://github.com/user-attachments/assets/5b1447a5-9c0a-409f-b883-5f938258b4ba)



## Step 8: Configuring Advanced Settings
To automate server setup, I leveraged **user data scripts** that executed on launch. The script:
- Installed **Apache (httpd)**
- Enabled and started the web server
- Deployed a basic HTML page confirming the instance was running successfully
This eliminated manual configuration, streamlining the deployment process.
Noteworthy that I enabled termination protection here.

![Screenshot 2025-03-15 at 14 47 51](https://github.com/user-attachments/assets/b09a1066-a5ca-4ff2-b0fb-0f2379b96343)


## Step 9: Launching the Instance
After finalizing the configurations, I launched the instance. It transitioned from Pending to Running, indicating successful initialization. A public DNS name was assigned, allowing internet access.

![Screenshot 2025-03-15 at 14 48 15](https://github.com/user-attachments/assets/fb12c41f-3e91-4b93-8141-21370678d543)


## Step 10: Monitoring the Instance
Monitoring ensured reliability and performance. Using the EC2 Status Checks tab, I confirmed both system and instance reachability checks passed. Metrics were observed via Amazon CloudWatch, enabling real-time insights into resource utilization. 

![Screenshot 2025-03-15 at 14 53 52](https://github.com/user-attachments/assets/32eb86b3-eeae-465c-9394-1930f5454151)


## Step 11: Enabling Web Access and Security Group Updates
Initially, HTTP requests were blocked due to security group restrictions. To resolve this, I updated the security group to allow inbound traffic on **port 80**, making the web server accessible via its public IP. This step reinforced the importance of **least privilege access**, granting only necessary permissions. 

![Screenshot 2025-03-15 at 15 01 15](https://github.com/user-attachments/assets/87ee8cec-497a-4b83-bfb9-2f5b41e9ce31)


## Step 12: Scaling: Resizing the Instance and Storage
As workloads change, so should infrastructure. To test scalability, I:
- Stopped the instance and **upgraded it from t3.micro to t3.small**, doubling the memory
- Increased the **EBS volume from 8 GiB to 12 GiB**
- restartoing the instance
This demonstrated how AWS enables seamless scaling without major disruptions.

![Screenshot 2025-03-15 at 15 11 48](https://github.com/user-attachments/assets/8c920eac-06c6-4cef-977d-862ab0833bda)

![Screenshot 2025-03-15 at 15 12 19](https://github.com/user-attachments/assets/c2da03ab-d504-495f-b673-03cd8ce56f82)



## Step 13: Testing Termination Protection
To prevent accidental deletions, termination protection was enabled. When attempting to delete the instance, AWS blocked the request. After disabling termination protection, I successfully terminated the instance, completing the lifecycle management process. 

![Screenshot 2025-03-15 at 15 13 19](https://github.com/user-attachments/assets/41b2fc03-070a-4721-8ed7-e0a965305ed3)

<img width="880" alt="Screenshot 2025-03-15 at 16 06 21" src="https://github.com/user-attachments/assets/74ab1140-2058-4abc-bae7-8902a03cba8b" />

<img width="1047" alt="Screenshot 2025-03-15 at 16 12 59" src="https://github.com/user-attachments/assets/6f6f9f07-614d-45c0-b756-2272e6ee78a1" />



<img width="1197" alt="Screenshot 2025-03-15 at 16 07 15" src="https://github.com/user-attachments/assets/2c58d968-b71e-4de2-aa36-a7b5a56c665e" />


<img width="1440" alt="Screenshot 2025-03-15 at 16 10 01" src="https://github.com/user-attachments/assets/ac992d09-6358-4186-8d39-f6c09288fde0" />





### Reflection
This project reinforced best practices for deploying secure, scalable, and cost-efficient AWS infrastructure. By systematically selecting, configuring, automating, and managing an EC2 instance, I gained hands-on experience in cloud operations, security, and scalability, crucial for real-world cloud architecture and DevOps roles.



