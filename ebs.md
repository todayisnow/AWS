# Amazon Elastic Block Store (EBS)

Amazon Elastic Block Store (EBS) provides block-level storage volumes for use with Amazon EC2 instances. It offers highly available and reliable storage volumes that can be attached to EC2 instances to meet a wide range of storage requirements.

![image](https://github.com/todayisnow/AWS/assets/22843851/37cc419d-456b-46cf-9276-35ba207f3851)


## Features

### Block-Level Storage
- EBS provides block-level storage volumes that can be attached to EC2 instances as storage devices.
- Each EBS volume is an independent storage unit that can be formatted and used as a separate disk.

### Performance
- EBS volumes offer consistent and low-latency performance, making them suitable for a variety of workloads, including databases, enterprise applications, and file systems.
- You can choose from different volume types to optimize performance based on your specific requirements.

### Durability and Availability
- EBS volumes are designed for high durability and availability, with data replicated across multiple Availability Zones within a region.
- Snapshots of EBS volumes can be created to back up data and restore volumes to a previous state.

### Elasticity and Scalability
- EBS volumes can be easily resized to meet changing storage requirements without any downtime.
- You can also create multiple EBS volumes and attach them to EC2 instances as needed.

### Encryption
- EBS volumes support encryption at rest using AWS Key Management Service (KMS) keys.
- You can encrypt both new and existing volumes to protect data stored on EBS volumes.

### Integration with AWS Services
- EBS volumes integrate seamlessly with other AWS services, such as Amazon EC2, Amazon RDS, and AWS Lambda.
- You can use EBS volumes as primary storage for EC2 instances, database storage for RDS instances, and storage for Lambda functions.

## Use Cases

### Database Storage
- EBS volumes are commonly used as primary storage for database applications, including relational databases (e.g., MySQL, PostgreSQL) and NoSQL databases (e.g., MongoDB, Cassandra).
- They offer consistent and reliable storage performance for database workloads.

### Enterprise Applications
- EBS volumes are suitable for hosting enterprise applications such as ERP systems, CRM systems, and custom business applications.
- They provide scalable and durable storage for mission-critical applications.

### File Systems
- EBS volumes can be used to create file systems for storing and accessing files, documents, and media assets.
- They offer high-performance storage for file-sharing and content management systems.

## Getting Started

To get started with Amazon EBS, you can:
1. Sign in to the AWS Management Console and navigate to the EBS service.
2. Create a new EBS volume and specify the volume type, size, and configuration.
3. Attach the EBS volume to an existing EC2 instance or create a new EC2 instance and attach the volume during instance launch.
4. Use the EBS volume as storage for your EC2 instance, database, or file system.
5. To list devices after connecting to EC2 instance
   ```
   lsblk
   ```
6. To test volume preformance
   ```bash
      sudo apt update
   
      sudo apt install fio
   
      sudo fio --name=write_iops --size=4G --time_based --runtime=60s --ramp_time=2s --ioengine=libaio --direct=1
      --verify=0 --bs=16K --iodepth=256 --rw=randwrite  --group_reporting=1 --iodepth_batch_submit=256
      --iodepth_batch_complete_max=256
         
   ```
   
   - Small block sizes generally result in higher IOPS but potentially lower bandwidth.
   - Large block sizes generally result in lower IOPS but potentially higher bandwidth.
   
For more information, refer to the [Amazon EBS Documentation](https://docs.aws.amazon.com/ebs).


# Create Volume and Attach to EC2 Instance Using AWS CLI

## Step 1: Create Volume
```bash
aws ec2 create-volume --availability-zone us-east-1b --size 12 --iops 6000 --volume-type io2 --tag-specifications 'ResourceType=volume,Tags=[{Key=Name,Value=MyVolume}]'
```

## Step 2: Retrieve Instance ID and Volume ID
```bash
INSTANCE_ID=$(aws ec2 describe-instances --filters "Name=tag:Name,Values=Ebs-Test" --query "Reservations[*].Instances[*].InstanceId" --output text)
VOL_ID=$(aws ec2 describe-volumes --filters "Name=tag:Name,Values=MyVolume" --query "Volumes[*].VolumeId" --output text)
```

## Step 3: Attach Volume to Instance
```bash
aws ec2 attach-volume --volume-id $VOL_ID --instance-id $INSTANCE_ID --device /dev/sdf
```
## Step 4: Make volume available for use on linux
- Format the Volume
  ```
  sudo mkfs -t ext4 /dev/xvdf
  ```
- Create a Mount Point
  ```
  sudo mkdir /data
  ```
- Mount the Volume
  ```
  sudo mount /dev/xvdf /data
  ```
- Automatically Mount the Volume on Boot (Optional):
  ```
  sudo nano /etc/fstab
  ```
  - add the following entry `/dev/xvdf   /data   ext4   defaults,nofail   0   2`

- Delete volume
  ```
  aws ec2 delete-volume --volume-id $VOL_ID
  ```



# Amazon EBS Volume Types and Categories

Amazon Elastic Block Store (EBS) provides a range of volume types designed to meet different performance and use case requirements for block-level storage in AWS. EBS volumes are categorized based on their performance characteristics, durability, and cost. Here are the main EBS volume types and categories:

![image](https://github.com/todayisnow/AWS/assets/22843851/acc1173d-a030-4c6c-9b57-9fc82f593856)


## 1. SSD (Solid State Drive) Based Volumes

### General Purpose SSD (gp2)
- General Purpose SSD volumes offer a balance of price and performance for a wide variety of workloads, including boot volumes and low-latency interactive applications. They deliver a baseline of 3 IOPS (Input/Output Operations Per Second) per GB with the ability to burst to higher levels for short periods. Used for dev/test, small db, workloads performing small random I/O

### gp3
- gp3 volumes are the next-generation General Purpose SSD volumes that provide a higher baseline performance level and a lower cost per gigabyte compared to gp2 volumes. They offer a baseline performance level that is configurable based on the volume size, allowing you to tailor performance and cost to your application's needs. Used for dev/test, small db, workloads performing small random I/O

### Provisioned IOPS SSD (io1/io2)
- Provisioned IOPS SSD volumes are designed for I/O-intensive workloads that require predictable and consistent performance `NoSql` and `relational databases`, such as database workloads. They allow you to provision a specific level of IOPS (Input/Output Operations Per Second) based on your application's requirements, offering the highest performance and lowest latency among EBS volumes. Can be attached to muliple istance but it can be a root volume in this case. Used for large IOPS intensive, large db

### io2 Block Express
- io2 Block Express volumes are designed for the most demanding storage workloads, providing ultra-low-latency, high-throughput, and consistent I/O performance. They are optimized for applications that require high-performance storage with sub-millisecond latency and the ability to scale to hundreds of terabytes in size.

## 2. HDD (Hard Disk Drive) Based Volumes

### Magnetic (Standard)
- Magnetic volumes, also known as Standard volumes, provide the lowest cost per GB among EBS volume types and are designed for workloads with light I/O requirements or infrequent access. They offer a baseline performance level and are suitable for low-cost storage options.

### Throughput Optimized HDD (st1)
- Throughput Optimized HDD volumes are designed for large, sequential workloads that require high throughput at a low cost `big data`, `data warehouse` and `log prosessing`, such as big data and data warehousing applications. They deliver consistent baseline performance and are optimized for streaming workloads with high throughput. not recommendaed to be used as a boot  volume. Used for fast throughput like streaming , sequential I/O

### Cold HDD (sc1)
- Cold HDD volumes are designed for large, sequential workloads with infrequent access that require low-cost storage. They offer the lowest cost per GB among EBS volume types but with higher latency compared to SSD-based volumes.Used for infrequently access

## Categories

### Performance
- EBS volume types are categorized based on their performance characteristics, ranging from high-performance SSD volumes (Provisioned IOPS SSD) to lower-performance HDD volumes (Cold HDD).

### Durability
- All EBS volumes are designed for 99.999% durability and are replicated within an Availability Zone to protect against component failure.

### Cost
- EBS volume types vary in cost, with SSD volumes generally being more expensive than HDD volumes due to their higher performance characteristics.

| Feature           | gp3                    | gp2                        | io2 Block Express        | io2                      | io1                      |
|-------------------|------------------------|----------------------------|--------------------------|--------------------------|--------------------------|
| Volume Type       | General Purpose SSD    | General Purpose SSD        | Provisioned IOPS SSD     | Provisioned IOPS SSD     | Provisioned IOPS SSD     |
| Performance       | Baseline + Burst       | Baseline + Burst           | Ultra-low latency, high-throughput, consistent I/O performance | High baseline + Provisioned IOPS | High baseline + Provisioned IOPS |
| Durability        | 99.8%                  | 99.8%                      | 99.999%                  | 99.999%                  | 99.999%                  |
| Throughput        | Up to 4,750 MB/s       | Up to 250 MB/s             | Up to 256,000 IOPS, 4,000 MB/s | Up to 64,000 IOPS, 1,000 MB/s | Up to 64,000 IOPS, 1,000 MB/s |
| IOPS              | Up to 3,000             | Baseline + Burst IOPS      | Up to 4,000 IOPS          | Up to 64,000 IOPS         | Up to 64,000 IOPS         |
| Cost-effectiveness| Lower cost per GB      | Balanced cost and performance | High-performance storage with sub-millisecond latency and high throughput | High-performance storage with high throughput and low latency | High-performance storage with high throughput and low latency |
| Pricing           | Lower cost per GB      | Lower cost per GB           | Variable based on volume size and IOPS provisioned | Variable based on volume size and IOPS provisioned | Variable based on volume size and IOPS provisioned |




## Conclusion

Amazon EBS offers a range of volume types and categories to meet different performance, durability, and cost requirements for block-level storage in AWS. By understanding the characteristics and use cases of each volume type, you can choose the appropriate EBS volumes to optimize performance and cost-effectiveness for your workloads.

For more detailed information on Amazon EBS volume types and categories, refer to the [Amazon EBS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AmazonEBS.html).


# Amazon EBS Snapshots

Amazon Elastic Block Store (EBS) snapshots are point-in-time backups of Amazon EBS volumes, which are block-level storage devices used with Amazon EC2 instances. EBS snapshots capture the entire state of an EBS volume at the time the snapshot is taken, including all data, configurations, and metadata. Here's an overview of EBS snapshots:

![image](https://github.com/todayisnow/AWS/assets/22843851/eb0a5722-c8de-4cc9-a0a0-2eb0c91ffd48)


## Key Features

- **Incremental Backups**: EBS snapshots are incremental, meaning that only the blocks that have changed since the last snapshot are saved. This helps minimize storage costs and reduce the time required to create snapshots.
- **Block-Level Storage**: EBS snapshots capture data at the block level, enabling efficient storage and retrieval of data. This also allows for granular recovery of specific data blocks or files from a snapshot.
- **Data Encryption**: EBS snapshots can be encrypted using AWS Key Management Service (KMS) encryption keys to ensure data security and compliance with regulatory requirements.
- **Cross-Region Replication**: EBS snapshots can be replicated across AWS regions for disaster recovery and data redundancy purposes. Cross-region replication helps improve data durability and availability.
- **Lifecycle Management**: EBS snapshots support lifecycle management policies, allowing you to automate the creation, retention, and deletion of snapshots based on defined criteria such as age, number of snapshots, or specific tags.

## Use Cases

- **Data Backup and Recovery**: EBS snapshots are commonly used for data backup and recovery purposes, providing a reliable and efficient way to protect data stored on EBS volumes.
- **Disaster Recovery**: By replicating EBS snapshots across multiple AWS regions, organizations can implement robust disaster recovery strategies to ensure business continuity in the event of region-wide outages or disasters.
- **Data Migration and Cloning**: EBS snapshots can be used to migrate data between AWS regions or to create clones of existing volumes for testing, development, or staging environments.
- **Data Retention and Compliance**: EBS snapshots can be retained for long-term storage to meet data retention and compliance requirements, such as regulatory mandates or internal policies.

## Best Practices

- **Regular Snapshot Schedule**: Implement a regular snapshot schedule to ensure frequent backups of critical data, taking into account the recovery point objectives (RPO) and recovery time objectives (RTO) of your applications.
- **Automated Lifecycle Management**: Use lifecycle management policies to automate the creation, retention, and deletion of snapshots, reducing operational overhead and ensuring compliance with data retention policies.
- **Encrypted Snapshots**: Enable encryption for EBS snapshots using AWS KMS encryption keys to protect sensitive data and meet security requirements.
- **Cross-Region Replication**: Implement cross-region replication for critical snapshots to ensure data redundancy and disaster recovery preparedness.

## Conclusion

Amazon EBS snapshots are a fundamental component of data protection and disaster recovery strategies in AWS. By leveraging EBS snapshots, organizations can implement reliable and efficient backup solutions, improve data durability and availability, and meet compliance requirements for data retention and security.

For more information, refer to the [AWS documentation on Amazon EBS Snapshots](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSSnapshots.html).


# EBS Snapshot Lifecycle Policies with Amazon Data Lifecycle Management (DLM)

Amazon Data Lifecycle Management (DLM) allows you to automate the creation and retention of EBS snapshots by defining snapshot lifecycle policies. These policies enable you to manage snapshot lifecycles based on retention periods and automate the deletion of snapshots according to your specified criteria.

## Purpose

- **Automated Management**: DLM enables you to automate the creation, retention, and deletion of EBS snapshots, reducing manual intervention and ensuring consistent snapshot management practices.
- **Cost Optimization**: By automatically deleting obsolete snapshots, DLM helps optimize storage costs associated with EBS snapshots.

## Lifecycle Policies

- **Retention Periods**: You can define retention periods for snapshots to specify how long they should be retained before they are eligible for deletion.
- **Tags**: DLM supports tag-based lifecycle policies, allowing you to apply policies based on tags assigned to your EBS volumes.

## Automated Snapshot Creation

- **Frequency**: You can configure DLM to create snapshots on a regular schedule, such as daily, weekly, or monthly, to ensure regular backups of your EBS volumes.
- **Consistency**: Automated snapshot creation ensures consistent backup schedules and eliminates the need for manual snapshot creation.

## Deletion Policies

- **Age-based Deletion**: DLM can automatically delete snapshots based on their age, ensuring that outdated snapshots are removed to optimize storage usage.
- **Retention Limits**: You can set retention limits to control the maximum number of snapshots retained for each volume, ensuring that storage costs are kept in check.

## Monitoring and Notifications

- **Visibility**: DLM provides visibility into snapshot lifecycle policies and their associated actions, allowing you to monitor the status of snapshot management activities.
- **Notifications**: You can configure CloudWatch Events to receive notifications when snapshot lifecycle events occur, such as snapshot creation or deletion.

## Conclusion

EBS snapshot lifecycle policies with Amazon Data Lifecycle Management (DLM) offer a convenient and automated way to manage the lifecycle of your EBS snapshots. By defining policies for snapshot creation, retention, and deletion, you can ensure consistent backup practices, optimize storage costs, and simplify snapshot management tasks.

For more information, refer to the [Amazon Data Lifecycle Management (DLM) documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/snapshot-lifecycle.html).


# Amazon EBS Encryption

Amazon Elastic Block Store (EBS) encryption provides data-at-rest encryption for EBS volumes, ensuring that data stored on EBS volumes is encrypted and secure. EBS encryption helps protect sensitive data and ensures compliance with security and regulatory requirements. Here's an overview of EBS encryption:

![image](https://github.com/todayisnow/AWS/assets/22843851/a3abf693-2f4d-491f-9b8c-141b69cc216c)


## Key Features

- **Data-at-Rest Encryption**: EBS encryption encrypts data stored on EBS volumes, ensuring that data is encrypted at rest to protect against unauthorized access.
- **Transparent Encryption**: EBS encryption is transparent to users and applications, meaning that encryption and decryption are handled automatically by the EBS service without any additional configuration required.
- **Integrated with AWS Key Management Service (KMS)**: EBS encryption integrates seamlessly with AWS Key Management Service (KMS) to manage encryption keys used to encrypt and decrypt data. You can choose to use AWS managed keys (AWS Managed CMKs) or customer managed keys (Customer Managed CMKs) with EBS encryption.
- **Default Encryption for New Volumes**: You can enable encryption by default for new EBS volumes in your AWS account, ensuring that all new volumes are automatically encrypted when created.
- **Cross-Region Replication**: Encrypted EBS volumes can be replicated across AWS regions using features such as Amazon EBS Cross-Region Snapshots, providing data redundancy and disaster recovery capabilities.

## Use Cases

- **Protecting Sensitive Data**: EBS encryption is suitable for protecting sensitive data such as Personally Identifiable Information (PII), financial data, and healthcare records stored on EBS volumes.
- **Compliance Requirements**: EBS encryption helps meet compliance requirements for data encryption at rest, including regulatory mandates such as GDPR, HIPAA, and PCI DSS.
- **Data Privacy and Security**: Encrypting data stored on EBS volumes ensures data privacy and security, mitigating the risk of unauthorized access or data breaches.

## Best Practices

- **Enable Encryption by Default**: Enable encryption by default for new EBS volumes in your AWS account to ensure that all new volumes are encrypted when created.
- **Use AWS KMS for Key Management**: Use AWS Key Management Service (KMS) to manage encryption keys for EBS encryption. Consider using customer managed keys (CMKs) for greater control over key management.
- **Regularly Rotate Encryption Keys**: Regularly rotate encryption keys used for EBS volumes to enhance security and comply with key rotation best practices.
- **Monitor EBS Encryption Status**: Monitor the encryption status of EBS volumes using AWS CloudWatch or AWS Config to ensure that all volumes are encrypted as expected.

## Conclusion

Amazon EBS encryption provides data-at-rest encryption for EBS volumes, ensuring that data stored on EBS volumes is encrypted and secure. By leveraging EBS encryption, organizations can protect sensitive data, meet compliance requirements, and enhance data privacy and security in AWS.

For more information, refer to the [AWS documentation on Amazon EBS Encryption](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html).


# Creating and Sharing/Copying EC2 Amazon Machine Images (AMIs) (Golden AMI)

Amazon Machine Images (AMIs) serve as templates for launching EC2 instances. You can create, share, and copy AMIs to replicate EC2 instances across different regions or AWS accounts.  

![image](https://github.com/todayisnow/AWS/assets/22843851/97dc14f0-d70f-4dbd-8e42-2e4c9509b41b)


## Creating AMIs

### Using the AWS Management Console:
1. Navigate to the EC2 dashboard in the AWS Management Console.
2. Select the instance you want to create an AMI from.
3. Click on "Actions" > "Image and templates" > "Create image".
4. Provide a name and description for the AMI, and configure additional settings if needed.
5. Click "Create image" to initiate the AMI creation process.

### Using the AWS CLI:
```bash
aws ec2 create-image --instance-id <instance-id> --name <ami-name> --description <ami-description>
```

## Sharing/Copying AMIs
### Sharing AMIs:

    - Navigate to the EC2 dashboard in the AWS Management Console.
    - Select the AMI you want to share.
    - Click on "Actions" > "Image and templates" > "Modify permissions".
    - Specify the AWS account IDs with which you want to share the AMI.
    - Click "Save permissions" to apply the changes.

### Copying AMIs:

    - Navigate to the EC2 dashboard in the AWS Management Console.
    - Select the AMI you want to copy.
    - Click on "Actions" > "Image and templates" > "Copy AMI".
    - Choose the destination region for the copied AMI.
    - Optionally, modify the AMI name and description.
    - Click "Copy AMI" to initiate the copying process.

 ## Conclusion

Creating and sharing/copying EC2 Amazon Machine Images (AMIs) allows you to create templates for EC2 instances and replicate them across regions or share them with other AWS accounts. By following the provided steps, you can easily create, share, and copy AMIs to meet your deployment and collaboration needs.


# Setting Up EBS RAID (Redundant Array of Independent Disks) in AWS

Elastic Block Store (EBS) RAID (Redundant Array of Independent Disks) allows you to combine multiple EBS volumes into a single logical volume to improve performance, reliability, and fault tolerance.

## RAID Types

There are several RAID levels, each offering different benefits and trade-offs:

- **RAID 0**: Provides increased performance and capacity by striping data across multiple disks, but offers no redundancy.
- **RAID 1**: Mirrors data across multiple disks for redundancy, but offers no performance improvement.
- **RAID 5**: Distributes data and parity information across multiple disks, offering both performance and redundancy. Requires a minimum of three disks.
- **RAID 6**: Similar to RAID 5 but with additional parity information for increased fault tolerance. Requires a minimum of four disks.
- **RAID 10 (RAID 1+0)**: Combines mirroring (RAID 1) and striping (RAID 0) for both performance and redundancy. Requires a minimum of four disks.

## Setting Up EBS RAID

### Prerequisites
- Launch multiple EC2 instances with attached EBS volumes.
- Ensure that the EBS volumes are attached to the same instance and are of the same size and type.

### Steps
1. **Configure RAID Software**: Install and configure the appropriate RAID software on your EC2 instance. For example, you can use `mdadm` for Linux-based instances.
   
2. **Create RAID Array**: Use the RAID software to create a RAID array with the attached EBS volumes. Specify the RAID level (e.g., RAID 0, RAID 1, etc.) and configure any additional settings as needed.

3. **Format and Mount RAID Volume**: Format the RAID volume with the desired file system (e.g., ext4, XFS) and mount it to a directory in your file system.

4. **Configure Auto-mount**: Update the `/etc/fstab` file to ensure that the RAID volume is automatically mounted upon instance reboot.

5. **Test and Monitor**: Test the RAID setup to ensure proper functionality and monitor its performance and health regularly.

## Conclusion

Setting up EBS RAID allows you to leverage multiple EBS volumes to improve performance, reliability, and fault tolerance for your EC2 instances. By choosing the appropriate RAID level and following the provided steps, you can create a robust storage solution that meets your application's requirements.

For more information on RAID and EBS volume management, refer to the [AWS documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/raid-config.html).



[Back to Main](readme.md)
