AWS IAM Policies and Group Attachments
Task Overview

This task involves creating and assigning custom IAM policies to user groups in AWS, providing specific levels of access to AWS services such as S3, EC2, RDS, CloudWatch, and Billing.

Steps Performed
1. Create Policy Number 1

Policy Name: Policy-1

Description:
This policy provides:

Full access to S3

Permission to create EC2 instances only

Full access to RDS
2. Create Policy Number 2

Policy Name: Policy-2

Description:
This policy provides:

Full access to CloudWatch and Billing

Permission to list EC2 and S3 resources only

3. Attach Policy 1 to Dev Team

Navigate to IAM → Groups → Dev Team → Permissions → Attach Policy

Search for Policy-1

Select and attach it to the Dev Team

Users in Dev Team:

Dev1

Dev2

4. Attach Policy 2 to Ops Team

Navigate to IAM → Groups → Ops Team → Permissions → Attach Policy

Search for Policy-2

Select and attach it to the Ops Team

Users in Ops Team:

Dev1

Test1

Test2

Verification

Login as Dev1 and verify permissions from both policies (since Dev1 is in both groups).

Login as Dev2 – should have Policy 1 permissions only.

Login as Test1/Test2 – should have Policy 2 permissions only.

Outcome

✅ IAM Policies created and configured successfully
✅ Policies attached to correct IAM Groups
✅ Permissions verified through user testing
