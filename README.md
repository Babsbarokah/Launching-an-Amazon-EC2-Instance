# Deploying and Managing an EC2 Instance on AWS

Setting up a reliable and efficient cloud environment begins with deploying the right compute resources. In this project, I launched and configured an Amazon EC2 instance, making key decisions to balance performance, security, and cost. From selecting the appropriate instance type to configuring network settings, storage, and security measures, each step was guided by best practices to ensure a seamless deployment.

This documentation captures the entire process, highlighting the reasoning behind each choice and its impact on the overall infrastructure.

---


## Step 1: Choosing the Right EC2 Instance Type
With over 750 instance types in AWS, selecting the right one requires understanding application demands for compute, memory, storage, and networking. Under-provisioning leads to performance bottlenecks, while over-provisioning results in unnecessary costs. For this project, I chose a **t3.micro** instance (2 vCPUs, 1 GiB RAM) to balance efficiency and cost-effectiveness. 



## Step 2: Configuring Secure Access with a Key Pair
To ensure secure access to the instance, I generated a key pair. Amazon EC2 uses public-key cryptography for authentication, requiring the private key during connection. By specifying the key pair at launch, I established a secure means of accessing the instance.



## Step 3: Setting Up Networking and Security
Networking configurations determined the accessibility and security of the instance. I assigned the instance to a Lab VPC and created a Web Server security group to define access rules. The security group functioned as a virtual firewall, controlling inbound and outbound traffic. To enhance security, I removed SSH access, limiting potential attack vectors.



## Step 4: Adding Storage
For persistent storage, I used Amazon Elastic Block Store (EBS) and maintained the default **8 GiB root volume**, ensuring sufficient space for the web server while keeping storage costs optimized. Additional storage configurations could be made depending on future requirements. 



## Step 5: Configuring Advanced Settings
To automate server setup, I leveraged **user data scripts** that executed on launch. The script:
- Installed **Apache (httpd)**
- Enabled and started the web server
- Deployed a basic HTML page confirming the instance was running successfully
This eliminated manual configuration, streamlining the deployment process.



## Step 6: Launching the Instance
After finalizing the configurations, I launched the instance. It transitioned from Pending to Running, indicating successful initialization. A public DNS name was assigned, allowing internet access.



## Step 7: Monitoring the Instance
Monitoring ensured reliability and performance. Using the EC2 Status Checks tab, I confirmed both system and instance reachability checks passed. Metrics were observed via Amazon CloudWatch, enabling real-time insights into resource utilization. 



## Step 8: Enabling Web Access and Security Group Updates
Initially, HTTP requests were blocked due to security group restrictions. To resolve this, I updated the security group to allow inbound traffic on **port 80**, making the web server accessible via its public IP. This step reinforced the importance of **least privilege access**, granting only necessary permissions. 



## Step 9: Scaling: Resizing the Instance and Storage
As workloads change, so should infrastructure. To test scalability, I:
- Stopped the instance and **upgraded it from t3.micro to t3.small**, doubling the memory
- Increased the **EBS volume from 8 GiB to 10 GiB**
This demonstrated how AWS enables seamless scaling without major disruptions.



## Step 10: Testing Termination Protection
To prevent accidental deletions, termination protection was enabled. When attempting to delete the instance, AWS blocked the request. After disabling termination protection, I successfully terminated the instance, completing the lifecycle management process. 



### Reflection
This project reinforced best practices for deploying secure, scalable, and cost-efficient AWS infrastructure. By systematically selecting, configuring, automating, and managing an EC2 instance, I gained hands-on experience in cloud operations, security, and scalability, crucial for real-world cloud architecture and DevOps roles.



