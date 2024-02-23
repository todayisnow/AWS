# AWS Storage Components and Services


   - **Amazon S3**:
     - Object storage.
     - Highly scalable, durable, and cost-effective.
     - Suitable for storing large amounts of unstructured data.
   - **Amazon EBS**:
     - Block storage.
     - Low-latency performance for EC2 instances.
     - Ideal for databases, file systems, and applications requiring frequent updates.
   - **Amazon EFS**:
     - File storage.
     - Scalable and elastic file storage accessible from multiple EC2 instances.
     - Suitable for content management and data sharing.

   - **Amazon Glacier**:
     - Data archival service.
     - Low-cost long-term archival with retrieval times ranging from minutes to hours.
     - Ideal for compliance, regulatory requirements, and disaster recovery.
   - **Amazon RDS**:
     - Managed relational database service.
     - Automates administrative tasks like patching, backups, and scaling.
     - Suitable for hosting relational databases such as MySQL, PostgreSQL, SQL Server, and Oracle.
   - **Amazon DynamoDB**:
     - Fully managed NoSQL database service.
     - Provides single-digit millisecond latency at any scale.
     - Commonly used for gaming, IoT, mobile apps, and real-time applications.

### When to Use Each:
- **Amazon S3**: Use for scalable object storage of various data types with different access patterns.
- **Amazon EBS**: Use for low-latency block storage volumes for EC2 instances, especially for databases and frequently updated applications.
- **Amazon EFS**: Use for scalable file storage accessible from multiple EC2 instances, suitable for content management and data sharing.
- **Amazon Glacier**: Use for long-term data archival where retrieval times are not critical, such as compliance and disaster recovery.
- **Amazon RDS**: Use for managed relational databases, simplifying database management tasks for your application.
- **Amazon DynamoDB**: Use for highly scalable, low-latency NoSQL databases for real-time applications and high availability scenarios.

Each service offers distinct capabilities tailored to specific use cases, so choose the one that best fits your application requirements.



[Back to Main](readme.md)
