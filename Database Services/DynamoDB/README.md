🧩 AWS DynamoDB Table Setup and Backup
📘 Overview

This project demonstrates how to create a DynamoDB table, insert items, take a backup, and then delete the table. It is a simple exercise to get familiar with DynamoDB operations in AWS.

🚀 Steps to Follow
1. Create a DynamoDB Table

Open the AWS Management Console → Navigate to DynamoDB.

Click Create table.

Provide the following details:

Table name: SampleTable

Partition key: ID (String type)

Keep other settings as default and click Create table.

2. Add 5 Items to the Table

After the table is created, go to the Items tab.

Click Create item and add 5 sample items such as:

ID	Name	Department	Age	Location
1	Alice	HR	29	New York
2	Bob	IT	32	California
3	Charlie	Finance	27	Texas
4	Diana	Marketing	30	Florida
5	Ethan	Operations	35	Washington

Click Create item for each record.

3. Take a Backup

Go to the Backups tab of your table.

Click Create backup.

Provide a name, for example: SampleTableBackup.

Click Create backup and wait for the backup process to complete.

4. Delete the Table

After verifying the backup, return to the Tables list.

Select your table (SampleTable).

Choose Delete table.

Confirm deletion when prompted.

🧾 Optional (Restore from Backup)

Navigate to Backups in DynamoDB.

Select the created backup.

Click Restore table to create a new table from the backup if needed.

✅ Outcome

You have successfully:

Created a DynamoDB table

Inserted data

Taken a backup

Deleted the table safely

🛠️ Tools Used

AWS DynamoDB

AWS Management Console
