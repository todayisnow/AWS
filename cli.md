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
```
aws --version
```


4. **Optional Configuration:**
- **Profiles:** If you have multiple IAM users or roles, you can configure AWS CLI profiles to switch between them easily.
- **Environment Variables:** You can set environment variables to specify AWS credentials and configurations instead of using `aws configure` every time.

5. **Access AWS Services:**
Once AWS CLI is installed and configured, you can start using it to interact with various AWS services and resources from the command line. For example, you can list S3 buckets, create EC2 instances, manage IAM users, etc.

[Back to Main](readme.md)
