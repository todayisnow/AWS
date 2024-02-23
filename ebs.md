# Amazon Elastic Block Store (EBS)

Amazon Elastic Block Store (EBS) provides block-level storage volumes for use with Amazon EC2 instances. It offers highly available and reliable storage volumes that can be attached to EC2 instances to meet a wide range of storage requirements.

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
5. To show volume specs after connecting to EC2 instance
   ```
   lsblk
   ```

For more information, refer to the [Amazon EBS Documentation](https://docs.aws.amazon.com/ebs).


# Amazon EBS Volume Types and Categories

Amazon Elastic Block Store (EBS) provides a range of volume types designed to meet different performance and use case requirements for block-level storage in AWS. EBS volumes are categorized based on their performance characteristics, durability, and cost. Here are the main EBS volume types and categories:

## 1. SSD (Solid State Drive) Based Volumes

### General Purpose SSD (gp2)
- General Purpose SSD volumes offer a balance of price and performance for a wide variety of workloads, including boot volumes and low-latency interactive applications. They deliver a baseline of 3 IOPS (Input/Output Operations Per Second) per GB with the ability to burst to higher levels for short periods.

### gp3
- gp3 volumes are the next-generation General Purpose SSD volumes that provide a higher baseline performance level and a lower cost per gigabyte compared to gp2 volumes. They offer a baseline performance level that is configurable based on the volume size, allowing you to tailor performance and cost to your application's needs.

### Provisioned IOPS SSD (io1/io2)
- Provisioned IOPS SSD volumes are designed for I/O-intensive workloads that require predictable and consistent performance `NoSql` and `relational databases`, such as database workloads. They allow you to provision a specific level of IOPS (Input/Output Operations Per Second) based on your application's requirements, offering the highest performance and lowest latency among EBS volumes.

### io2 Block Express
- io2 Block Express volumes are designed for the most demanding storage workloads, providing ultra-low-latency, high-throughput, and consistent I/O performance. They are optimized for applications that require high-performance storage with sub-millisecond latency and the ability to scale to hundreds of terabytes in size.

## 2. HDD (Hard Disk Drive) Based Volumes

### Magnetic (Standard)
- Magnetic volumes, also known as Standard volumes, provide the lowest cost per GB among EBS volume types and are designed for workloads with light I/O requirements or infrequent access. They offer a baseline performance level and are suitable for low-cost storage options.

### Throughput Optimized HDD (st1)
- Throughput Optimized HDD volumes are designed for large, sequential workloads that require high throughput at a low cost `big data`, `data warehouse` and `log prosessing`, such as big data and data warehousing applications. They deliver consistent baseline performance and are optimized for streaming workloads with high throughput.

### Cold HDD (sc1)
- Cold HDD volumes are designed for large, sequential workloads with infrequent access that require low-cost storage. They offer the lowest cost per GB among EBS volume types but with higher latency compared to SSD-based volumes.

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




[Back to Main](readme.md)
