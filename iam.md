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

[Back to main](readme.md)
