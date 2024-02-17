# Amazon Web Services (AWS)

Amazon Web Services (AWS) is a comprehensive and widely adopted cloud computing platform provided by Amazon. It offers a broad set of global compute, storage, database, analytics, application, and deployment services that help organizations move faster, lower IT costs, and scale applications.

## Benefits of AWS:
- **Scalability:** AWS allows you to scale resources up or down based on demand, providing flexibility and cost savings.
- **Reliability:** AWS offers a highly reliable infrastructure with multiple data centers and availability zones, ensuring high availability and fault tolerance.
- **Security:** AWS provides robust security features to protect data, applications, and infrastructure, including encryption, identity and access management, and compliance certifications.
- **Cost-Effectiveness:** AWS offers a pay-as-you-go pricing model, allowing you to pay only for the resources you use without any upfront investment, leading to cost savings.
- **Global Reach:** AWS has a global infrastructure footprint with data centers located in multiple regions around the world, enabling low-latency access and compliance with data residency requirements.

## Key Features of AWS:
- **Compute Services:** AWS provides a wide range of compute services, including Amazon Elastic Compute Cloud (EC2) for virtual servers, AWS Lambda for serverless computing, and Amazon Elastic Container Service (ECS) for containerized applications.
- **Storage Services:** AWS offers various storage services, such as Amazon Simple Storage Service (S3) for object storage, Amazon Elastic Block Store (EBS) for block storage, and Amazon Glacier for long-term archival storage.
- **Database Services:** AWS provides managed database services like Amazon Relational Database Service (RDS) for relational databases, Amazon DynamoDB for NoSQL databases, and Amazon Redshift for data warehousing.
- **Networking Services:** AWS offers networking services like Amazon Virtual Private Cloud (VPC) for isolated cloud networks, Amazon Route 53 for DNS management, and AWS Direct Connect for dedicated network connections.
- **Security and Identity Services:** AWS includes security and identity services such as AWS Identity and Access Management (IAM) for access control, AWS Key Management Service (KMS) for encryption key management, and AWS Shield for DDoS protection.
- **Analytics Services:** AWS provides analytics services like Amazon Athena for interactive query analysis, Amazon EMR for big data processing, and Amazon QuickSight for business intelligence.


# IAM (Identity and Access Management)

IAM (Identity and Access Management) is a crucial service in AWS that helps you manage access to AWS services and resources securely. IAM enables you to control who can access your AWS resources and what actions they can perform.

## Key Concepts:
- **Users:** IAM allows you to create and manage IAM users, which represent individuals or entities (such as applications) who interact with AWS.
- **Groups:** You can organize IAM users into groups and manage permissions collectively for those users.
- **Roles:** IAM roles are entities with permissions that determine what actions can be performed by entities that assume the role.
- **Policies:** IAM policies are JSON documents that define permissions for users, groups, and roles. Policies specify what actions are allowed or denied on what AWS resources.

## Features and Benefits:
- **Fine-Grained Access Control:** IAM enables you to define granular permissions, allowing you to grant only the necessary permissions for users, groups, or roles to access specific AWS resources.
- **Centralized Access Management:** IAM provides a centralized platform for managing access to AWS services, making it easier to enforce security policies and ensure compliance.
- **Security:** IAM enhances security by enabling multi-factor authentication (MFA), password policies, and integration with AWS Key Management Service (KMS) for encryption key management.
- **Integration with AWS Services:** IAM integrates seamlessly with various AWS services, allowing you to control access to resources such as Amazon S3 buckets, EC2 instances, and more.
- **Auditing and Monitoring:** IAM offers detailed logging and monitoring capabilities, allowing you to track user activity, monitor access patterns, and generate audit reports for compliance purposes.

## Use Cases:
- **User Authentication and Authorization:** IAM enables you to authenticate and authorize users to access AWS resources securely.
- **Identity Federation:** IAM supports identity federation, allowing you to grant temporary access to users authenticated through external identity providers (such as Active Directory, LDAP, or SAML).
- **Cross-Account Access:** IAM enables you to grant permissions for resources in one AWS account to users, groups, or roles in another AWS account.

## Example Policy: " allows full access (s3:*) to objects within the example-bucket S3 bucket."
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:*",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```
# IAM Resources
## Users

IAM users are entities within your AWS account that represent the people, services, or applications that interact with AWS resources. Each user has a unique name and security credentials (access key ID and secret access key or password) used for programmatic or console access. Users can be assigned individual permissions or be members of IAM groups.

### Features:
- **Individual Permissions:** Each IAM user can have specific permissions assigned directly to them.
- **Security Credentials:** IAM users can have access keys for programmatic access and passwords for console access.
- **Granular Access Control:** Permissions can be finely tuned for each IAM user, allowing for precise access control.

## Groups

IAM groups are collections of IAM users. You can organize users into groups to efficiently manage permissions. Instead of assigning permissions to individual users, you can assign them to groups, and users inherit the group's permissions. This simplifies permissions management, especially for large organizations with multiple users.

### Features:
- **Permission Inheritance:** Users in a group inherit the permissions assigned to the group.
- **Efficient Permissions Management:** Permissions are managed at the group level, reducing the need for repetitive individual user permissions management.
- **Logical Grouping:** Groups can represent teams, departments, or roles within an organization.

## Roles

IAM roles are entities with permissions that determine what actions can be performed by entities that assume the role. Roles are not associated with a specific IAM user or group; instead, they are meant to be assumed by entities like AWS services, applications, or EC2 instances. Roles are often used to grant temporary permissions for specific tasks.

### Features:
- **Temporary Permissions:** Roles can be assumed temporarily to perform specific tasks and then revoked.
- **Cross-Account Access:** Roles can be used to grant access to AWS resources in different AWS accounts.
- **Service-Linked Roles:** AWS services have pre-defined roles with permissions necessary for their specific tasks, such as accessing other AWS services on your behalf.

## Policies

IAM policies are JSON documents that define permissions. Policies can be attached to users, groups, or roles and specify what actions are allowed or denied on what AWS resources. Policies are the primary way to manage permissions within IAM and are used to grant or restrict access to AWS services and resources.

### Features:
- **Policy Types:** IAM supports several types of policies, including identity-based policies, resource-based policies, and inline policies.
- **Versioning:** Policies support versioning, allowing you to manage and track changes to policies over time.
- **Policy Conditions:** Policies can include conditions that must be met for the policy to be applied, providing additional control over access.

## Access Keys

IAM access keys are long-term credentials associated with an IAM user that are used for programmatic access to AWS services via the AWS API, CLI, or SDKs. Each IAM user can have up to two access keys, consisting of an access key ID and a secret access key.

### Features:
- **Programmatic Access:** Access keys are used for programmatic access to AWS services, enabling automation and integration with other applications.
- **Rotation:** Best practices recommend regularly rotating access keys to enhance security.
- **Limited Lifespan:** Access keys can be set to expire after a specified period, improving security.

## Multi-Factor Authentication (MFA)

MFA adds an extra layer of security to IAM users' accounts by requiring them to provide two or more forms of authentication (typically something they know, like a password, and something they have, like a mobile device or hardware token) before they can access AWS resources.

### Features:
- **Enhanced Security:** MFA provides an additional layer of protection against unauthorized access.
- **Supported Devices:** MFA supports various authentication devices, including virtual and hardware tokens.
- **Required for Sensitive Actions:** MFA can be required for specific IAM users or roles when performing sensitive actions, such as modifying IAM policies.

## Identity Providers (IdPs)

IAM identity providers enable you to federate access to AWS resources by using external identity sources like Active Directory, LDAP, or SAML. This allows you to manage user identities outside of AWS and grant them access to AWS resources using their existing credentials.

### Features:
- **Single Sign-On (SSO):** IdPs enable SSO, allowing users to access multiple applications and services with a single set of credentials.
- **Integration with Existing Systems:** IdPs integrate with existing identity systems like Active Directory, simplifying user management and access control.
- **Centralized Identity Management:** IdPs provide centralized identity management across multiple applications and platforms, improving security and user experience.

# IAM Request Handling and Authorization Logic

IAM (Identity and Access Management) serves as the gatekeeper for all access requests to AWS resources, whether initiated by users, applications, or machines. This section outlines the fundamental principles of IAM request handling and authorization logic:

- **Principal:** The principal refers to the user, application, or machine seeking access to an AWS resource. Requests can be made through API calls or the AWS Management Console.
- **Request Flow:** Any access request to an AWS resource is intercepted by IAM first. The request includes information about the principal, the action being requested, and the target resource.
- **Authentication and Authorization:** IAM performs both authentication and authorization checks on the incoming request. Authentication verifies the identity of the principal, while authorization determines whether the principal is allowed to perform the requested action on the specified resource.
- **Request Handling:** If a request involves multiple actions and at least one action is denied by IAM policies, the entire request is denied.
- **Default Denial:** By default, all resource access is denied. Unless there is a specific IAM policy granting permission for the requested action, access will be prohibited. The only exception is for the root account, which has full access by default.
- **Policy Evaluation:** If a principal is associated with multiple policies, IAM follows a "deny by default" logic. If there is at least one policy denying the action, regardless of any allowing policies, access will be denied.

This framework ensures that access to AWS resources is tightly controlled and follows a strict authorization logic governed by IAM policies. It emphasizes the importance of defining precise policies to grant or restrict access based on the specific needs of the organization.

---

# Setup AWS CLI – Prerequisites and Environment

## Prerequisites:
1. **AWS Account:** You need an AWS account to access AWS services and resources.
2. **IAM User with Access Key:** Create an IAM user with programmatic access and permissions to use AWS CLI. Obtain the access key ID and secret access key for this IAM user.

## Environment Setup:
1. **Install AWS CLI:**
   - **Windows:** Download and run the AWS CLI installer from the [AWS CLI official website](https://aws.amazon.com/cli/).
   - **macOS/Linux:** Install AWS CLI using pip (Python package manager) by running the following command in your terminal:
     ```
     pip install awscli
     ```

2. **Configure AWS CLI:**
   Run the following command in your terminal and provide the access key ID, secret access key, default region, and output format when prompted:
   Example:
   ``` 
    aws configure
   
    AWS Access Key ID [None]: YOUR_ACCESS_KEY_ID
    AWS Secret Access Key [None]: YOUR_SECRET_ACCESS_KEY
    Default region name [None]: YOUR_DEFAULT_REGION
    Default output format [None]: json
   ```

3. **Verify Installation:**
After configuring AWS CLI, you can verify the installation by running the following command in your terminal:
This command will display the installed version of AWS CLI.

4. **Optional Configuration:**
- **Profiles:** If you have multiple IAM users or roles, you can configure AWS CLI profiles to switch between them easily.
- **Environment Variables:** You can set environment variables to specify AWS credentials and configurations instead of using `aws configure` every time.

5. **Access AWS Services:**
Once AWS CLI is installed and configured, you can start using it to interact with various AWS services and resources from the command line. For example, you can list S3 buckets, create EC2 instances, manage IAM users, etc.

---

# Amazon S3 (Simple Storage Service)

Amazon S3 (Simple Storage Service) is a scalable object storage service offered by AWS that allows you to store and retrieve data from anywhere on the web. It is designed to provide high durability, availability, and scalability for storing a wide variety of data, including images, videos, documents, backups, and logs.

## Key Concepts:
1. **Buckets:** A bucket is a container for objects stored in Amazon S3. You can create multiple buckets to organize and manage your data.
2. **Objects:** Objects are the fundamental entities stored in Amazon S3. An object can be any file or data, along with metadata, stored as a key-value pair.
3. **Regions:** Amazon S3 is globally distributed across multiple geographical regions. You can choose the region where you want to create your buckets to optimize latency and compliance requirements.
4. **Storage Classes:** Amazon S3 offers different storage classes, including Standard, Standard-IA (Infrequent Access), One Zone-IA, Intelligent-Tiering, Glacier, and Glacier Deep Archive, each designed for specific use cases based on data access frequency and durability requirements.
5. **Lifecycle Policies:** You can define lifecycle policies to automatically transition objects between different storage classes or delete them after a specified period.

## Features:
- **Durability and Availability:** Amazon S3 is designed to provide 99.999999999% (11 nines) durability and 99.99% availability for your data.
- **Scalability:** S3 can scale to accommodate any amount of data, from a few gigabytes to petabytes or more, without any upfront provisioning.
- **Security:** S3 offers various security features, including encryption at rest and in transit, access control via IAM policies and bucket policies, and integration with AWS Key Management Service (KMS) for managing encryption keys.
- **Versioning:** You can enable versioning on your S3 buckets to preserve, retrieve, and restore every version of every object stored in the bucket.
- **Cross-Region Replication:** You can replicate objects across different AWS regions for disaster recovery, compliance, and low-latency access.
- **Event Notifications:** S3 supports event notifications that can trigger AWS Lambda functions, SNS topics, or SQS queues in response to object creation, deletion, or restore events.

## Use Cases:
- **Static Website Hosting:** Amazon S3 can host static websites by serving HTML, CSS, JavaScript, and other web assets directly from buckets.
- **Data Backup and Archiving:** S3 is commonly used for data backup and long-term archival storage due to its durability and cost-effectiveness.
- **Content Distribution:** S3 integrates with Amazon CloudFront, AWS's content delivery network (CDN), to distribute content globally with low latency and high transfer speeds.
- **Data Lakes:** S3 serves as a foundational component for building data lakes, allowing organizations to store and analyze large volumes of structured and unstructured data at scale.

# Steps to Create a Bucket in Amazon S3

1. **Sign in to the AWS Management Console:**
   Open a web browser and navigate to the [AWS Management Console](https://aws.amazon.com/console/). Sign in to your AWS account using your credentials.

2. **Navigate to Amazon S3:**
   Once logged in, search for "S3" in the AWS Management Console search bar, and click on the "Amazon S3" service in the search results. Alternatively, you can find Amazon S3 under the "Storage" category in the AWS Management Console.

3. **Create a New Bucket:**
   - Click on the "Create bucket" button to start the bucket creation process.
   - Enter a unique name for your bucket in the "Bucket name" field. Bucket names must be globally unique across all existing bucket names in Amazon S3.
   - Choose the AWS region where you want to create the bucket. Select the region closest to your users to minimize latency.
   - Click on the "Create" button to create the bucket.

4. **Configure Bucket Properties (Optional):**
   - After creating the bucket, you can configure optional properties such as versioning, server access logging, default encryption, and tags. These configurations can be adjusted later if needed.

5. **Set Bucket Permissions (Optional):**
   - By default, newly created buckets are private and can only be accessed by the bucket owner. If you want to grant public access or specific permissions to other AWS accounts or IAM users, you can configure bucket policies and access control lists (ACLs) in the "Permissions" tab.

6. **Confirmation:**
   - Once you have configured the bucket properties and permissions, click on the "Create bucket" button to confirm and create the bucket.
   - You will see a confirmation message indicating that the bucket has been successfully created.

7. **Access Your Bucket:**
   - After the bucket is created, you can start uploading objects (files) to the bucket using the Amazon S3 console, AWS CLI, SDKs, or third-party tools.

8. **Explore Additional Features:**
   - Explore additional features of Amazon S3 such as lifecycle policies, cross-region replication, event notifications, and object metadata to further customize and manage your bucket and its contents.

# Create Bucket, Set Public Access Block, and Upload File Using AWS CLI

## Create Bucket:
```bash
aws s3api create-bucket --bucket my-example-bucket --region us-west-2
```
## Set Public Access Block:
```bash
aws s3api put-public-access-block --bucket my-example-bucket --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=true,RestrictPublicBuckets=true"
```
## Upload file:
```bash
aws s3api put-object --bucket my-example-bucket --content-type image/jpeg --key myImage.jpg --body /mnt/c/aws/myImage.jpg
```
## Allow Public Read
```bash
aws s3api delete-public-access-block --bucket my-example-bucket

aws s3api put-object-acl --bucket my-example-bucket --key myImage.jpg --acl public-read
```
## Delete File
```bash
aws s3api delete-object --bucket my-example-bucket --key myImage.jpg
```
## Delete Bucket
```bash
aws s3api delete-bucket --bucket my-example-bucket --region us-west-2
```

# Security and Permissions on an Amazon S3 Bucket

Amazon S3 provides several mechanisms to control access to your buckets and objects, ensuring that only authorized users or applications can interact with your data. Here are some key aspects of security and permissions in Amazon S3:

## Bucket Policies:
- **Bucket-Level Access Control:** You can define bucket policies to control access to the entire bucket based on various conditions, including IP address, VPC endpoint, AWS account, or IAM identity.
- **JSON-based Policies:** Bucket policies are JSON documents that specify who can access the bucket and what actions they can perform. Policies can be attached to individual buckets to define granular access controls.
- **Cross-Account Access:** Bucket policies can grant access to resources in other AWS accounts, enabling cross-account sharing of objects.
- **Evaluation:** Bucket policies are evaluated before any other access control mechanisms, such as IAM policies or ACLs. They provide a centralized way to manage access control for all objects within the bucket.
- **Example:**
```json
{
    "Version": "2012-10-17",
    "Id": "ExamplePolicy01",
    "Statement": [
        {
            "Sid": "ExampleStatement01",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::123456789012:user/Dave"
            },
            "Action": [
                "s3:GetObject",
                "s3:GetBucketLocation",
                "s3:ListBucket"
            ],
            "Resource": [
                "arn:aws:s3:::awsexamplebucket1/*",
                "arn:aws:s3:::awsexamplebucket1"
            ]
        }
    ]
}

#cli
aws s3api put-bucket-policy --bucket my-example-bucket --policy file://polic
y.json
```

## Access Control Lists (ACLs):
- **Object-Level Access Control:** ACLs are another way to control access to individual objects within a bucket. ACLs can grant read, write, and delete permissions to specific AWS accounts or predefined groups.
- **Fine-Grained Control:** ACLs allow you to specify permissions for individual AWS accounts, predefined groups (e.g., authenticated users, all users), or specific email addresses.

## IAM Policies:
- **User-Level Access Control:** IAM (Identity and Access Management) policies are used to manage access permissions for IAM users and roles. IAM policies can grant access to specific S3 buckets and objects based on various conditions and actions.
- **Granular Permissions:** IAM policies support granular permissions, allowing you to specify which API actions (e.g., s3:GetObject, s3:PutObject) are allowed or denied for specific resources.
- **Temporary Access:** IAM roles can be used to grant temporary access to S3 resources for applications running on EC2 instances, Lambda functions, or other AWS services.

## Pre-Signed URLs:
- **Temporary Access Links:** Pre-signed URLs allow you to generate temporary URLs that grant access to specific objects in your bucket for a limited time period. Pre-signed URLs are often used for providing temporary access to private objects without requiring AWS credentials.

## Default Encryption:
- **Data Encryption:** Amazon S3 offers default encryption options to encrypt data at rest to protect against unauthorized access. You can enable default encryption for a bucket to automatically encrypt all objects stored in the bucket using server-side encryption (SSE) with Amazon S3-managed keys (SSE-S3) or customer-managed keys (SSE-C).

## Access Logging:
- **Audit Trail:** Amazon S3 provides access logging features that allow you to track requests made to your bucket and objects. Access logs capture details such as the requester's IP address, HTTP method, and response status, providing visibility into access patterns and potential security threats.

## Block Public Access:
- **Restrict Public Access:** Amazon S3 offers settings to block public access to your buckets and objects by default. You can enable block public access settings at the account level or individual bucket level to prevent accidental exposure of sensitive data to the public internet.

