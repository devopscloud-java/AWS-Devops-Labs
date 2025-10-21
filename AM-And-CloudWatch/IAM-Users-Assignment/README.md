🧑‍💻 AWS IAM Users and Groups Setup
🎯 Objective

To manage user access and permissions efficiently by creating IAM users, groups, and assigning users to appropriate groups in AWS Identity and Access Management (IAM).

🪜 Steps Performed
1️⃣ Create IAM Users

Created four IAM users:

Dev1

Dev2

Test1

Test2

Each user was created with programmatic and console access (optional based on requirement).
Password reset was enabled for the first login for security.

2️⃣ Create IAM Groups

Created two IAM groups to organize and manage permissions:

Dev Team

Ops Team

3️⃣ Add Users to Dev Team

Added the following users to the Dev Team group:

Dev1

Dev2

This group can later be assigned developer-related permissions (e.g., AmazonEC2FullAccess, AmazonS3FullAccess).

4️⃣ Add Users to Ops Team

Added the following users to the Ops Team group:

Dev1

Test1

Test2

This team can be assigned operational-level permissions (e.g., CloudWatchReadOnlyAccess, AWSLambdaFullAccess).

✅ Verification

Checked user memberships under IAM → Users → Groups.

Confirmed group members listed correctly in IAM → Groups → Group Memberships.

📘 Summary
IAM User	Group Memberships
Dev1	Dev Team, Ops Team
Dev2	Dev Team
Test1	Ops Team
Test2	Ops Team


Groups:
  - Dev Team:
      Members: Dev1, Dev2
  - Ops Team:
      Members: Dev1, Test1, Test2

    🧾 Notes

IAM best practice: Assign permissions to groups, not individual users.

Use IAM Policies to control what each group can access.

