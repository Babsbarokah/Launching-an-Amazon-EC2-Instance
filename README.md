# Launching-an-Amazon-EC2-Instance
Launching, resizing, managing, and monitoring an Amazon EC2 instance


### INTRODUCTION

Amazon EC2 (Elastic Compute Cloud) provides resizable compute capacity in the cloud, designed to make cloud computing easier for developers. With EC2, I was able to quickly scale computing resources up or down based on needs, paying only for the capacity used. EC2 also enables the creation of failure-resilient applications that are protected against common failure scenarios.

---

### Topics Covered:
In this project, I focused on launching a web server with termination protection enabled, monitoring the EC2 instance, modifying the security group to allow HTTP access, resizing the EC2 instance, testing termination protection, and terminating the EC2 instance.

---

### Launching an EC2 Instance
Termination protection was set up to prevent accidental termination of the EC2 instance. I used a User Data script to deploy a simple web server. This walkthrough utilized the AWS Management Console, which provides a graphical interface for managing resources.

---

### Step-by-Step Process:

#### Step 1: Select a Region
After logging into the AWS Management Console, I searched for **EC2** in the search bar. I then selected the region best suited for the project based on factors such as latency and redundancy. I made sure to choose the appropriate region from the top navigation bar to ensure optimal performance.

#### Step 2: Name the EC2 Instance
When naming the EC2 instance, I created a key-value pair where the key was "Name" and the value was the name I chose for the instance, "TheXProject." I ensured that the instance was properly tagged to make it easy to identify in the console after launch. Consistent tagging practices were applied to maintain organization and improve resource management.

#### Step 3: Choose an Amazon Machine Image (AMI)
I selected an AMI, which is a template that includes an operating system, preinstalled software, and other necessary components for launching the instance. The **Quick Start** section provided a list of commonly used AMIs, but I also had the option to create my own AMI or choose one from the **AWS Marketplace**. The AMI was important as it determined the environment in which the EC2 instance would run.

---
