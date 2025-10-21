AWS IAM Role for Controlled Access to VPC and DynamoDB
🎯 Objective

Create a role that allows only user1 and user2 from Task 1 to assume it, giving them complete access to VPC and DynamoDB services.
Then, log in as user1 and assume the role to verify that it works correctly.

🪜 Steps to Perform
Step 1: Create IAM Role

Sign in to the AWS Management Console as an admin user.

Navigate to IAM → Roles → Create role.

Choose Trusted entity type:
➤ Select AWS account → “This account.”

Under Permissions policies, attach:

AmazonVPCFullAccess

AmazonDynamoDBFullAccess

Click Next, provide:

Role name: VPC-DynamoDB-Access-Role

Description: “Allows full access to VPC and DynamoDB for user1 and user2.”

Click Create role.

Step 2: Modify Trust Policy

Open the role VPC-DynamoDB-Access-Role → Trust relationships → Edit trust policy.

Replace the policy with the following JSON (update with correct ARNs of user1 and user2):



Save changes.

Step 3: Test Role with user1

Sign out of admin and log in as user1.

Navigate to IAM → My Security Credentials → Switch role.

Enter:

Account ID: <Your Account ID>

Role name: VPC-DynamoDB-Access-Role

Click Switch Role.

Step 4: Verify Access

Navigate to VPC → Your VPCs and try to create or modify a VPC.

Open DynamoDB → Tables and create a new table to test access.

Try accessing another service (e.g., EC2) — it should deny access, proving the role restriction works.

✅ Expected Outcome

user1 and user2 can assume the VPC-DynamoDB-Access-Role.

They have full access to VPC and DynamoDB only.

Access to other AWS services is restricted.

🧠 Key AWS Concepts

IAM Role: Grants temporary access permissions to trusted entities.

Trust Policy: Defines who can assume the role.

Permission Policy: Defines what actions can be performed.

