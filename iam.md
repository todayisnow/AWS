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

![image](https://github.com/todayisnow/AWS/assets/22843851/ba06f0e7-38b6-483b-9bf4-d7b86bef192f)

### Features:
- **Temporary Permissions:** Roles can be assumed temporarily to perform specific tasks and then revoked.
- **Cross-Account Access:** Roles can be used to grant access to AWS resources in different AWS accounts.
- **Service-Linked Roles:** AWS services have pre-defined roles with permissions necessary for their specific tasks, such as accessing other AWS services on your behalf.
![image](https://github.com/todayisnow/AWS/assets/22843851/46838794-630c-4452-a97c-bdffa521c576)

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

## AWS IAM Account Alias

In AWS Identity and Access Management (IAM), an account alias is a customizable name for your AWS account. It allows you to replace the unique account ID assigned by AWS with a more user-friendly name. Account aliases are helpful for managing multiple AWS accounts or for providing a recognizable name for your organization's AWS resources.

### Benefits of Using Account Alias:

- **Improved Usability:** Account aliases make it easier to identify and remember your AWS accounts, especially when working with multiple accounts.
- **Enhanced Security:** By replacing the account ID with an alias, you can reduce the risk of exposing sensitive information, as account aliases are easier to communicate and share.
- **Simplified Resource Management:** Account aliases provide a more intuitive way to reference AWS resources and services associated with your account.

### How to Set Up an Account Alias:

1. **Sign in to the AWS Management Console:** Navigate to the IAM dashboard.

2. **Choose the Account Alias Section:** In the navigation pane, select "Account Alias."

3. **Enter Your Desired Alias:** Enter a unique alias for your AWS account. The alias must be unique within the AWS region.

4. **Save Your Changes:** Click on the "Save changes" button to confirm your account alias.

### Considerations:

- **Uniqueness:** Each AWS account alias must be unique within the AWS region. If you attempt to create an alias that is already in use by another account, you will receive an error message.
- **Length and Valid Characters:** Account aliases can contain alphanumeric characters, hyphens, and underscores. They must be between 3 and 63 characters long.

### Example:

Suppose your AWS account ID is "123456789012" and you set the account alias to "mycompany-dev." After setting up the account alias, you can use "mycompany-dev" to reference your AWS resources instead of the longer account ID.

By using account aliases, you can enhance the usability and security of your AWS accounts while simplifying resource management.


# IAM Identity-based Policy

In AWS Identity and Access Management (IAM), identity-based policies are used to specify permissions that are attached directly to IAM identities, such as users, groups, and roles. These policies define what actions are allowed or denied on AWS resources for the associated IAM entity. Here's an overview of IAM identity-based policies:

## Components of Identity-based Policies
- **Policy Document**: An IAM policy document is a JSON document that defines the permissions for the associated IAM identity. It consists of one or more statements, each specifying a set of permissions.
- **Statements**: Each statement in the policy document contains the following components:
  - **Effect**: Specifies whether the statement allows or denies access. It can be either "Allow" or "Deny".
  - **Action**: Defines the AWS actions (API operations) that are allowed or denied depend on the Effect.
  - **NotAction**: Defines the AWS actions (API operations) that are allowed or denied depend on the Effect .
  - **Resource**: Specifies the AWS resources to which the actions apply. It can be "*" to indicate all resources or specific resource ARNs.
  - **Condition**: Optionally, conditions can be added to the statement to further restrict access based on factors such as IP address, time, or request parameters.

## Types of Identity-based Policies
There are two main types of identity-based policies in IAM:
1. **Managed Policies**: These are standalone policies that you can attach to multiple IAM users, groups, or roles. Managed policies can be AWS managed, customer managed, or inline policies.
2. **Inline Policies**: These policies are embedded directly into a single IAM user, group, or role. They are defined and managed alongside the identity to which they are attached.

## Use Cases
- **Least Privilege**: Identity-based policies are used to implement the principle of least privilege by granting only the permissions necessary for users, groups, or roles to perform their tasks.
- **Access Control**: These policies are used to control access to AWS resources based on user roles and responsibilities within an organization.
- **Policy Inheritance**: IAM policies can be attached to IAM users, groups, or roles, allowing for policy inheritance and centralized management of permissions.


## Best Practices
- **Least Privilege**: Follow the principle of least privilege by granting only the permissions required for users to perform their tasks.
- **Use Managed Policies**: Prefer using managed policies over inline policies for better manageability and reusability.
- **Regular Review**: Regularly review and audit your identity-based policies to ensure they align with your security requirements and business needs.
- **Testing**: Test policies in a non-production environment before applying them in a production environment to avoid unintended consequences.
- **Policy Versioning**: Use policy versioning to track changes and rollback to previous versions if needed.
- **Follow Least Privilege**: Grant only the permissions required for users, groups, or roles to perform their intended tasks. Avoid granting excessive permissions.
- **Regular Review**: Regularly review and audit IAM policies to ensure they align with the organization's security and compliance requirements.
- **Use Conditions**: Leverage IAM policy conditions to add additional security constraints, such as IP address restrictions or time-based access controls.
- **Separation of Duties**: Implement separation of duties by assigning different permissions to different IAM users, groups, or roles to reduce the risk of unauthorized access.

## Example Identity-based Policy
Below is an example of an identity-based policy that allows full access to a specific table in dynamodb:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "dynamodb:*",
      "Resource": "arn:aws:dynamodb:us-east-2:123456123555:table/Books"
    }
  ]
}
```

## Conclusion
IAM identity-based policies are a fundamental aspect of AWS security, enabling granular control over access to AWS resources for IAM users, groups, and roles. By following best practices and carefully defining policies, organizations can maintain a secure and compliant environment in the AWS cloud.



# IAM Resource-based Policy

IAM resource-based policies are permissions policies that you can attach directly to AWS resources, such as Amazon S3 buckets, Lambda functions, or SNS topics. These policies define who can access the resource and what actions they can perform. Here are some key aspects of IAM resource-based policies:

## Overview
- **Attached to Resources**: Resource-based policies are attached directly to AWS resources and govern access to those resources.
- **JSON Syntax**: Similar to identity-based policies, resource-based policies are written in JSON format and consist of statements that specify the effect, action, principal, and optional conditions.
- **Principal**: The principal in a resource-based policy refers to the AWS account or IAM entity that is granted permissions to access the resource.
- **Actions**: Actions define the operations that the principal is allowed or denied to perform on the resource.
- **Resources**: Resources specify the AWS resource to which the policy applies. You can specify specific resources or use wildcards (*) to match multiple resources.
- **Effect**: The effect of a policy statement can be either "Allow" or "Deny," similar to identity-based policies.

## Use Cases
- **Cross-Account Access**: Resource-based policies are commonly used to grant cross-account access to AWS resources, allowing other AWS accounts to access the resources.
- **Resource Sharing**: These policies facilitate resource sharing between different AWS accounts or services within the same account, such as sharing S3 buckets or Lambda functions.
- **Fine-Grained Access Control**: Resource-based policies enable fine-grained access control over individual resources, allowing you to specify which principals can perform specific actions on the resource.

## Best Practices
- **Restrict Access**: Limit access to AWS resources by specifying only the necessary permissions in resource-based policies.
- **Use Conditions**: Apply conditions to resource-based policies to add additional security constraints, such as restricting access based on the requester's IP address or time of day.
- **Regular Review**: Regularly review and audit resource-based policies to ensure that only authorized entities have access to the resources.
- **Avoid Public Access**: Exercise caution when granting public access to AWS resources through resource-based policies, as it may lead to unintended exposure of sensitive data.



# IAM Security Token Service (STS)

The AWS Security Token Service (STS) is a web service that enables you to request temporary, limited-privilege credentials for IAM users or federated users. These temporary credentials can be used to access AWS resources securely and are valid for a specified duration, typically ranging from a few minutes to several hours.

![image](https://github.com/todayisnow/AWS/assets/22843851/ec2f7152-f018-4809-ba5e-28d1b2fe90bf)


## Key Features:
1. **Temporary Security Credentials:** STS issues temporary security credentials in the form of short-term AWS access keys, secret keys, and session tokens.
2. **Fine-Grained Permissions:** You can specify the permissions associated with the temporary credentials using IAM policies, allowing you to grant only the necessary permissions for a specific task.
3. **Federation:** STS supports federated access, allowing external identities (such as users authenticated by SAML, OpenID Connect, or custom identity providers) to access AWS resources.
4. **Cross-Account Access:** IAM users or roles from one AWS account can assume roles in another account using STS, enabling cross-account access for managing resources securely.
5. **Role-Based Access Control:** Users or applications can assume roles temporarily to access resources, following the principle of least privilege.
6. **Multi-Factor Authentication (MFA):** STS supports MFA for additional security when requesting temporary credentials, ensuring that users provide a second authentication factor before accessing sensitive resources.

## Operations Supported by STS:
1. **AssumeRole:** Allows IAM users, AWS services, or federated users to assume temporary roles with defined permissions. This operation is commonly used to delegate access to AWS resources across different accounts or services.
2. **GetSessionToken:** Retrieves temporary credentials (access key, secret key, and session token) for IAM users. Users can use these credentials to make requests to AWS services.
3. **AssumeRoleWithSAML:** Enables federated users to access AWS resources using SAML-based authentication. This operation is used in federated identity scenarios, such as single sign-on (SSO) solutions.
4. **AssumeRoleWithWebIdentity:** Allows web identity providers, such as Amazon Cognito, to authenticate users and provide temporary credentials for accessing AWS resources.

## Benefits of Using STS:
- **Enhanced Security:** Temporary credentials reduce the exposure of long-term credentials, mitigating the risk of unauthorized access.
- **Least Privilege Access:** You can grant temporary credentials with limited permissions, ensuring that users have only the necessary access required for their tasks.
- **Auditing and Compliance:** STS provides detailed logging and auditing capabilities, enabling you to track the usage of temporary credentials for compliance purposes.
- **Cross-Account Access:** STS facilitates secure access across AWS accounts, allowing you to centralize management and control access to shared resources.

By leveraging IAM Security Token Service (STS), you can implement secure and scalable access control mechanisms for your AWS resources while adhering to the principles of least privilege and least exposure.

## Considerations
When a user with full access assumes a role, their full access privileges are temporarily overridden by the permissions and policies associated with the assumed role. This allows the user to perform actions and access resources according to the rules defined for that role, rather than their original full access permissions.



[Back to main](readme.md)
