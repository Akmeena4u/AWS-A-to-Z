

# Introduction to EC2

## What is EC2, and why is it important?

- Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides secure, resizable compute capacity in the cloud.
- Access reliable, scalable infrastructure on demand. Scale capacity within minutes with SLA commitment of 99.99% availability.
- Provide secure compute for your applications. Security is built into the foundation of Amazon EC2 with the AWS Nitro System.
- Optimize performance and cost with flexible options like AWS Graviton-based instances, Amazon EC2 Spot instances, and AWS Savings Plans.

## EC2 Use Cases

- Deliver secure, reliable, high-performance, and cost-effective compute infrastructure to meet demanding business needs.
- Access the on-demand infrastructure and capacity you need to run HPC applications faster and cost-effectively.
- Access environments in minutes, dynamically scale capacity as needed, and benefit from AWS’s pay-as-you-go pricing.
- Deliver the broadest choice of compute, networking (up to 400 Gbps), and storage services purpose-built to optimize price performance for ML projects.

## EC2 Instance Types

### General Purpose

General Purpose instances are designed to deliver a balance of compute, memory, and network resources. They are suitable for a wide range of applications, including web servers,
small databases, development and test environments, and more.

### Compute Optimized

Compute Optimized instances provide a higher ratio of compute power to memory. They excel in workloads that require high-performance processing such as batch processing,
scientific modeling, gaming servers, and high-performance web servers.

### Memory Optimized

Memory Optimized instances are designed to handle memory-intensive workloads. They are suitable for applications that require large amounts of memory, such as in-memory databases,
real-time big data analytics, and high-performance computing.

### Storage Optimized

Storage Optimized instances are optimized for applications that require high, sequential read and write access to large datasets.
They are ideal for tasks like data warehousing, log processing, and distributed file systems.

### Accelerated Computing

Accelerated Computing Instances typically come with one or more types of accelerators, such as Graphics Processing Units (GPUs),
Field Programmable Gate Arrays (FPGAs), or custom Application Specific Integrated Circuits (ASICs).
These accelerators offload computationally intensive tasks from the main CPU, enabling faster and more efficient processing for specific workloads.


---

# Notes on AWS EC2 Instance Creation and Jenkins Installation

## Introduction to AWS Regions and Availability Zones

- AWS provides data centers across the world in various regions.
- Regions are geographical locations where AWS has data centers.
- Users can choose in which region to create their resources.
- Importance of selecting the appropriate region:
  - Compliance with data residency regulations.
  - Minimization of latency for end-users.
- AWS also offers availability zones within regions for high availability.
- Availability zones provide redundancy and fault tolerance within a region.

## Creating an EC2 Instance

1. Log in to the AWS console.
2. Access the EC2 service.
3. Click on "Launch Instance" to create a new EC2 instance.
4. Choose instance details:
   - Provide a name for the instance.
   - Select the desired operating system and version (e.g., Ubuntu).
   - Choose the appropriate instance type (e.g., T2.micro for free tier eligibility).
5. Configure instance settings:
   - Choose or create a key pair for SSH access to the instance.
   - Select networking settings (can leave default for now).
   - Optionally, increase storage size if needed.
6. Launch the instance.
7. Access the instance via SSH using the key pair and public IP address.
8. Update packages on the instance (e.g., `sudo apt update` for Ubuntu).
9. Install Jenkins on the instance:
   - Install Java as a prerequisite.
   - Download and install Jenkins using appropriate commands.
10. Start the Jenkins service (`sudo systemctl start jenkins`).
11. Configure inbound traffic rules in the security group to allow access to port 8080.
12. Access Jenkins from the browser using the public IP address and port 8080.
13. Complete Jenkins setup by providing the initial admin password and following the setup wizard.


# Notes on EC2 Instance Setup and Jenkins Deployment

## EC2 Instance Setup

- **Instance Name:** my-first-instance
- **Key Pair:** aws_login
- **Access Instructions for Windows:**
  - Use PuTTY (C:\Program Files\PuTTY\) or MobaXterm.
  - <details>
    <summary>MobaXterm setup</summary>
   # Accessing EC2 Instances from Windows using MobaXterm

## Introduction
- Aimed at assisting Windows users in accessing EC2 instances without needing Oracle VirtualBox.
- Demonstrates how to connect to an EC2 instance using MobaXterm.

## Steps:

1. **Launch EC2 Instance:**
   - Name: test-windows
   - OS: Ubuntu (for demonstration)
   - Key Pair: Windows demo (.pem file)

2. **Download and Install MobaXterm:**
   - Search and download MobaXterm Community Edition.
   - Choose the installer version for ease of installation.

3. **Extract and Install MobaXterm:**
   - Navigate to the downloads folder.
   - Extract the downloaded ZIP file.
   - Open the extracted folder and run the installer.
   - Follow installation instructions.

4. **Connect to EC2 Instance:**
   - Get the public IP address of the EC2 instance.
   - Open MobaXterm.
   - Go to "Sessions" and select "SSH".
   - Enter the EC2 instance IP address as the hostname.
   - Set the username as "ubuntu" (for Ubuntu instances).
   - Click on "Advanced SSH settings".

5. **Configure SSH Settings:**
   - Check "Use private key".
   - Select the private key (.pem file) downloaded earlier (e.g., windows_demo.pem).
   - Click "OK" to save settings.

6. **Authenticate and Connect:**
   - Accept any pop-up prompts.
   - MobaXterm will authenticate and connect to the EC2 instance.

7. **Verify Connection:**
   - Upon successful connection, a terminal session will open within the EC2 instance.
   - Execute commands like `sudo apt update` to verify functionality.

## Conclusion:
- MobaXterm simplifies accessing EC2 instances from Windows machines without requiring Oracle VirtualBox.
- Following these steps, users can connect to EC2 instances swiftly and efficiently.
- This guide aims to assist Windows users in overcoming accessibility challenges when working with AWS services.
  </details>
  - Public IP: <public ip>
  - SSH Command: `ssh -i aws_login.pem ubuntu@<public-IP>`
  - If permission error, use `chmod 600 filename`.
- **Access Instructions for MobaXterm or PuTTY Not Required:**
  - SSH Command: `ssh -i aws_login.pem ubuntu@<public-ip>`

### Basic Commands to Test

- `whoami`: Display current user.
- `sudo su -`: Switch to root user.
- `apt update`: Update packages.
- `logout`: Log out of root user.

## Jenkins Deployment on EC2 Instance

1. **Install Java:**
   - Command: `apt install openjdk-11-jdk`
   - Verify Java installation: `java --version`

2. **Install Jenkins:**
   - Go to Jenkins website for Ubuntu.
   - Copy URL for weekly release.
   - Paste URL in MobaXterm.

3. **Verify Jenkins Installation:**
   - Check Jenkins service status: `systemctl status jenkins`.
   - Note the port Jenkins is running on.



## Conclusion

- Successfully created an EC2 instance on AWS.
- Installed Jenkins on the EC2 instance.
- Accessed Jenkins from the browser.
- Demonstrated basic AWS networking concepts such as security groups and inbound traffic rules.
- Future videos will cover more advanced topics in AWS and DevOps.
