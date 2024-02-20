# AWS CodeCommit

AWS CodeCommit is a fully-managed source control service that makes it easy for teams to host secure and highly scalable private Git repositories. It provides a secure and reliable platform for storing and managing your source code, enabling collaborative development workflows for teams of any size.

## Features

### Private Git Repositories
- CodeCommit allows you to create private Git repositories to securely store and manage your source code.
- Repositories are accessible only to authorized users and can be encrypted at rest to ensure data security.

### Fully Managed Service
- CodeCommit is a fully managed service, eliminating the need to manage infrastructure, backups, or scaling.
- AWS handles the underlying infrastructure, ensuring high availability, durability, and scalability of your repositories.

### Git Compatibility
- CodeCommit is compatible with Git, allowing you to use familiar Git commands and workflows.
- You can use Git command-line tools, Git clients, and popular Git integrations with CodeCommit repositories.

### Collaboration and Code Reviews
- CodeCommit supports collaboration and code reviews through pull requests.
- You can create pull requests to review and discuss changes, collaborate with team members, and enforce code review policies.

### Integration with AWS Services
- CodeCommit integrates seamlessly with other AWS services, such as AWS CodeBuild, AWS CodePipeline, and AWS CodeDeploy.
- You can build automated CI/CD pipelines, trigger deployments, and automate workflows using CodeCommit as your source control system.

### Security and Compliance
- CodeCommit provides built-in security features, including encryption at rest and in transit, access control policies, and AWS Identity and Access Management (IAM) integration.
- It helps you meet compliance requirements by providing audit logs, fine-grained access controls, and encryption options.

## Use Cases

### Software Development Projects
- CodeCommit is ideal for software development projects of any size, from small teams to large enterprises.
- It provides a secure and scalable platform for version control, collaboration, and continuous integration/continuous deployment (CI/CD) workflows.

### Continuous Integration and Delivery (CI/CD)
- CodeCommit integrates seamlessly with AWS CodeBuild and AWS CodePipeline to build automated CI/CD pipelines.
- You can use CodeCommit as your source control system to trigger builds, run tests, and deploy applications automatically.

### Team Collaboration
- CodeCommit enables team collaboration by providing a central repository for storing and managing source code.
- Team members can collaborate on code changes, review each other's code through pull requests, and track changes over time.

## Getting Started

To get started with AWS CodeCommit, you can:
1. Sign in to the AWS Management Console and navigate to the CodeCommit service.
2. Create a new repository or import an existing repository from GitHub or another Git provider.
3. Clone the repository to your local development environment using Git.
4. Add, commit, and push your code changes to the CodeCommit repository.

For more information, refer to the [AWS CodeCommit Documentation](https://docs.aws.amazon.com/codecommit).


# AWS CodeCommit Pricing

AWS CodeCommit offers a simple and flexible pricing model based on the number of active users, the storage used for your repositories, and data transfer.

## Pricing Components

### Active Users
- AWS CodeCommit pricing is based on the number of active users accessing your repositories each month.
- Active users are defined as unique AWS identities (IAM users, federated users, or roles) that perform at least one Git-based interaction in a month, such as cloning, pushing, pulling, or merging code.

### Storage
- CodeCommit pricing includes storage costs for the Git repositories hosted in the service.
- Storage is billed based on the total size of repositories, including all branches and objects stored in Git.

### Data Transfer
- CodeCommit pricing includes data transfer costs for network traffic between AWS CodeCommit and other AWS services or external networks.
- Data transfer is measured in gigabytes (GB) and includes both inbound and outbound data transfer.

## Free Tier
- AWS CodeCommit offers a generous free tier for new customers and existing customers who meet certain criteria.
- The free tier includes a monthly allotment of active users, storage, and data transfer, allowing users to get started with CodeCommit at no additional cost.

## Pricing Details
- For detailed pricing information, including current pricing rates, tiered pricing options, and regional pricing variations, refer to the [AWS CodeCommit Pricing](https://aws.amazon.com/codecommit/pricing/) page.

## Cost Estimation
- You can estimate the cost of using AWS CodeCommit using the [AWS Pricing Calculator](https://calculator.aws/).
- The pricing calculator allows you to input your usage requirements and estimate the monthly cost based on your specific usage patterns.


# Setting Up HTTPS and SSH Access for AWS CodeCommit

## HTTPS Access

To access AWS CodeCommit repositories over HTTPS, follow these steps:

1. **Install Git**: If you haven't already, install Git on your local machine. You can download Git from the official website: [Git Downloads](https://git-scm.com/downloads).

2. **Configure Git Credentials**:

    - **Option 1: Use IAM Credentials**:
        - Generate Git credentials for IAM users or IAM roles using the AWS Management Console or AWS CLI.
        - Configure Git to use these credentials by running the following commands in your terminal:
            ```bash
            git config --global credential.helper '!aws codecommit credential-helper $@'
            git config --global credential.UseHttpPath true
            ```

    - **Option 2: Use AWS CLI Configuration**:
        - If you have the AWS CLI installed and configured with IAM credentials, Git can use these credentials automatically.
        - Ensure that the AWS CLI is configured with the necessary IAM credentials using the `aws configure` command.

3. **Get the HTTPS Git URL**:
    - In the AWS CodeCommit console, navigate to your repository and copy the HTTPS Git URL provided.

4. **Clone the Repository**:
    - Open a terminal or command prompt and navigate to the directory where you want to clone the repository.
    - Run the following command, replacing `<HTTPS_GIT_URL>` with the URL copied from the CodeCommit console:
        ```bash
        git clone <HTTPS_GIT_URL>
        ```

5. **Authenticate and Push Changes**:
    - When prompted, enter your Git credentials (username and password) or allow Git to use IAM credentials configured in step 2.
    - After authentication, you can push changes to the CodeCommit repository using HTTPS.

## SSH Access

To access AWS CodeCommit repositories over SSH, follow these steps:

1. **Generate SSH Key Pair**:
    - Generate an SSH key pair using the following command:
        ```bash
        ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
        ```
    - Follow the prompts to save the key pair to a specific location (e.g., `~/.ssh/id_rsa`).

2. **Add Public Key to AWS CodeCommit**:
    - Navigate to IAM in the AWS Management Console and select the IAM user.
    - Under the "Security credentials" tab, choose "SSH keys for AWS CodeCommit" and upload the public key (`id_rsa.pub`).

3. **Configure Git to Use SSH**:
    - Configure Git to use SSH by running the following commands in your terminal:
        ```bash
        git config --global user.name "Your Name"
        git config --global user.email "your_email@example.com"
        ```

4. **Clone the Repository Using SSH**:
    - In the AWS CodeCommit console, navigate to your repository and copy the SSH Git URL provided.
    - Open a terminal or command prompt and navigate to the directory where you want to clone the repository.
    - Run the following command, replacing `<SSH_GIT_URL>` with the URL copied from the CodeCommit console:
        ```bash
        git clone <SSH_GIT_URL>
        ```

5. **Authenticate and Push Changes**:
    - When prompted, use SSH authentication to access the CodeCommit repository.

## Note:
- Ensure that IAM users/roles have the necessary permissions to access the CodeCommit repository.
- HTTPS and SSH access provide secure ways to access AWS CodeCommit repositories, with HTTPS suitable for environments where SSH is not an option.







[Back to Main](readme.md)
