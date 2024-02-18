# Amazon Elastic Compute Cloud (EC2)

Amazon Elastic Compute Cloud (EC2) is a web service that provides resizable compute capacity in the cloud. It allows you to quickly scale compute resources up or down based on demand, making it easier to handle varying workloads and traffic patterns.

## Key Features of EC2:

### 1. Instances:
- **Virtual Servers**: EC2 instances are virtual servers in the cloud that can run various operating systems and applications.
- **Instance Types**: EC2 offers a wide selection of instance types optimized for different use cases, such as general-purpose, compute-optimized, memory-optimized, and storage-optimized instances.

### 2. Elasticity and Scalability:
- **Auto Scaling**: EC2 Auto Scaling allows you to automatically scale the number of EC2 instances based on demand, ensuring optimal performance and cost efficiency.
- **Elastic Load Balancing**: Combined with Elastic Load Balancing, EC2 instances can distribute incoming traffic across multiple instances to ensure high availability and fault tolerance.

### 3. Pricing and Billing:
- **Pay-As-You-Go**: With EC2, you pay only for the compute capacity you use, with no upfront costs or long-term commitments.
- **Reserved Instances**: EC2 offers Reserved Instances, which provide significant discounts compared to On-Demand pricing in exchange for a commitment to a one- or three-year term.

### 4. Security and Compliance:
- **Security Groups**: EC2 instances are secured using security groups, which act as virtual firewalls to control inbound and outbound traffic.
- **Compliance**: EC2 is compliant with various industry standards and certifications, including SOC, PCI DSS, HIPAA, and GDPR.

### 5. Integration and Flexibility:
- **Integration with AWS Services**: EC2 integrates with other AWS services, such as Amazon S3, Amazon RDS, and Amazon VPC, to provide a comprehensive cloud computing platform.
- **Flexibility**: EC2 provides flexibility to choose from a wide range of operating systems, AMIs (Amazon Machine Images), and software configurations to meet your specific requirements.

## Use Cases for EC2:
- Web Hosting and Application Hosting
- Development and Testing Environments
- Big Data and Analytics
- High-Performance Computing (HPC)
- Enterprise Applications and Databases
- Gaming and Media Streaming

Amazon EC2 offers a flexible and cost-effective solution for running virtual servers in the cloud, providing the foundation for building scalable and reliable applications.

# Creating an EC2 Instance

## Step 1: Choose an Amazon Machine Image (AMI)

- **AMI Selection**: Choose an AMI based on your operating system and software requirements.

## Step 2: Choose an Instance Type

- **Instance Type**: Select an instance type based on your workload requirements, such as general-purpose, compute-optimized, memory-optimized, or storage-optimized instances.

## Step 3: Configure Instance Details

- **Number of Instances**: Specify the number of instances to launch.
- **Network**: Choose the VPC (Virtual Private Cloud) and subnet for the instance.
- **Auto-assign Public IP**: Specify whether to assign a public IP address to the instance.
- **IAM Role**: Assign an IAM role to the instance for accessing AWS services.

## Step 4: Add Storage

- **Root Volume**: Specify the size and type (e.g., SSD or HDD) of the root volume for the instance.
- **Additional Volumes**: Add additional volumes as needed for data storage.

## Step 5: Configure Security Group

- **Security Group**: Create or select a security group to control inbound and outbound traffic to the instance.

## Step 6: Review and Launch

- **Review Configuration**: Review the instance configuration details.
- **Launch**: Confirm the configuration and launch the instance.

## Step 7: Connect to the Instance

- **SSH (Linux) or RDP (Windows)**: Use SSH (Secure Shell) for Linux instances or RDP (Remote Desktop Protocol) for Windows instances to connect to the instance.

## Step 8: Additional Configuration (Optional)

- **Instance Metadata**: Configure instance metadata, user data, and tags as needed.
- **Monitoring**: Enable detailed monitoring for the instance to collect performance metrics.
- **Instance Termination Protection**: Enable termination protection for the instance if required.

# Summary

Creating an EC2 instance involves selecting an AMI, choosing an instance type, configuring instance details, adding storage, configuring security groups, reviewing and launching the instance, connecting to the instance, and additional configuration as needed. Follow these steps to launch an EC2 instance tailored to your specific requirements.

# Connect to EC2 Instance Using PuTTY

## Step 1: Convert PEM Key to PPK Format

1. **Download PuTTY Tools**: Download and install PuTTY and PuTTYgen from the [PuTTY Download Page](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html).

2. **Convert PEM to PPK**:
   - Open PuTTYgen.
   - Click on "Load" and select your PEM private key file.
   - Click on "Save private key" to save the private key in PPK format.

## Step 2: Configure PuTTY Session

1. **Open PuTTY**: Launch PuTTY.

2. **Configure Session**:
   - Enter your instance's public DNS or IP address in the "Host Name (or IP address)" field.
   - Enter a name for your session in the "Saved Sessions" field and click "Save" to save the session.

3. **Configure SSH Auth**:
   - In the left panel, navigate to Connection > SSH > Auth.
   - Click on "Browse" and select the PPK private key file you generated in Step 1.

## Step 3: Connect to Instance

1. **Load Session**: Select the saved session from the list in the "Saved Sessions" field.

2. **Open Session**: Click "Open" to start the SSH connection.

3. **Authenticate**: If prompted, log in using the appropriate username for your instance (e.g., "ec2-user" for Amazon Linux, "ubuntu" for Ubuntu, "admin" for CentOS).

4. **Connected**: You are now connected to your EC2 instance via SSH using PuTTY.

# Summary

By following these steps, you can convert your PEM key to PPK format using PuTTYgen, configure a PuTTY session with the converted private key, and establish an SSH connection to your EC2 instance using PuTTY.

# Create EC2 Instance Using AWS CLI

## Step 1: Create SSH Key Pair (if not already created)

```bash
aws ec2 create-key-pair --key-name MyKeyPair --key-format ppk --query 'KeyMaterial' --output text > MyKeyPair.ppk
```

## Step 2: Create Security Groups

```bash
aws ec2 create-security-group --group-name SSHAccess --description "Security group for SSH access"
aws ec2 authorize-security-group-ingress --group-name SSHAccess --protocol tcp --port 22 --cidr 0.0.0.0/0
aws ec2 authorize-security-group-ingress --group-name HTTPAccess --protocol tcp --port 80 --cidr 0.0.0.0/0
```

## Step 3: Launch EC2 Instance

```bash
aws ec2 run-instances --image-id <AMI-ID> --count 1 --instance-type t2.micro --key-name MyKeyPair --security-groups SSHAccess HTTPAccess
```



