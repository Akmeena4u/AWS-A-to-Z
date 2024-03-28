




## Today's Agenda: AWS IAM

Today, we'll focus on AWS Identity and Access Management (IAM). We'll start with a real-life scenario to understand IAM's importance, then delve into its components, including users, groups, policies, and roles. Finally, we'll engage in practical exercises to grasp how IAM functions in AWS.

### Real-Life Scenario: Bank Example

Imagine a bank with different service areas: customer service, employee areas, and sensitive data zones. To ensure security, the bank implements authentication and authorization processes. Similarly, in AWS, IAM serves the same purpose.

# AWS IAM (Identity and Access Management)

AWS IAM is a service provided by Amazon Web Services (AWS) that helps you manage access to your AWS resources. It's like a security system for your AWS account.

IAM allows you to create and manage users, groups, and roles. Users represent individual people or entities who need access to your AWS resources. Groups are collections of users with similar access requirements, making it easier to manage permissions. Roles are used to grant temporary access to external entities or services.

With IAM, you can control and define permissions through policies. Policies are written in JSON format and specify what actions are allowed or denied on specific AWS resources. These policies can be attached to IAM entities (users, groups, or roles) to grant or restrict access to AWS services and resources.

IAM follows the principle of least privilege, meaning users and entities are given only the necessary permissions required for their tasks, minimizing potential security risks. IAM also provides features like multi-factor authentication (MFA) for added security and an audit trail to track user activity and changes to permissions.

By using AWS IAM, you can effectively manage and secure access to your AWS resources, ensuring that only authorized individuals have appropriate permissions and actions are logged for accountability and compliance purposes.

## Components of IAM

### Users

IAM users represent individual people or entities (such as applications or services) that interact with your AWS resources. Each user has a unique name and security credentials (password or access keys) used for authentication and access control.

### Groups

IAM groups are collections of users with similar access requirements. Instead of managing permissions for each user individually, you can assign permissions to groups, making it easier to manage access control. Users can be added or removed from groups as needed.

### Roles

IAM roles are used to grant temporary access to AWS resources. Roles are typically used by applications or services that need to access AWS resources on behalf of users or other services. Roles have associated policies that define the permissions and actions allowed for the role.

### Policies

IAM policies are JSON documents that define permissions. Policies specify the actions that can be performed on AWS resources and the resources to which the actions apply. Policies can be attached to users, groups, or roles to control access. IAM provides both AWS managed policies (predefined policies maintained by AWS) and customer managed policies (policies created and managed by you).




### Practical Exercise

### 1. Authentication without Authorization

- Log in using the root account to demonstrate authentication.
- Attempt actions like listing S3 buckets to showcase lack of permissions without proper authorization.

### 2. Creating a User and Adding Permissions

- Access the IAM service within the AWS Management Console.
- Create a new IAM user (e.g., test-user) to represent an individual requiring access.
- Provide console access to the user and auto-generate a password.
- Demonstrate authentication using the newly created user credentials.
- Observe the user's inability to perform actions due to lack of authorization.
- Attach an AWS managed policy (e.g., Amazon S3 full access) to grant permissions.
- Reauthenticate with the user and verify access to listed S3 buckets and other authorized actions.

### 3. Utilizing IAM Groups

- Create an IAM group (e.g., Development Group) and assign permissions (e.g., S3 full access) to it.
- Add users (e.g., test-user) to the group to inherit its permissions.
- Modify group permissions to include additional services (e.g., EC2 full access) if required.
- Confirm that users in the group inherit updated permissions without manual intervention.

### Additional Notes

- Emphasize the importance of using IAM users and groups over the root account for improved security and accountability.
- Practice caution when granting permissions, adhering to the principle of least privilege.
- Encourage the use of IAM roles for advanced scenarios involving external services 
