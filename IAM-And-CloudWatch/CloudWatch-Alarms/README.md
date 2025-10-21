CloudWatch Billing and EC2 CPU Utilization Alarms
Objective

This project demonstrates how to create CloudWatch alarms to monitor:

AWS account billing exceeding a defined threshold.

EC2 instance CPU utilization crossing a specified limit, with an SNS notification setup.

Tasks Overview
Task 1: Billing Alarm Setup

Goal: Trigger an alarm when the estimated AWS charges exceed $500.

Steps:

Go to the CloudWatch Console in the AWS Management Console.

Navigate to Alarms → All Alarms → Create Alarm.

Under Select Metric, choose:

Billing → Total Estimated Charge → Currency (USD)


Choose the metric name: EstimatedCharges.

Set the Threshold value to 500.

Under Conditions, choose:

Whenever EstimatedCharges is... Greater than 500.

Configure Actions:

Choose In Alarm → Send notification to an SNS topic.

Create a new SNS topic (e.g., BillingAlertTopic) and subscribe your email address.

Confirm the subscription through the verification email received.

Click Create Alarm.

Result:

You’ll receive an email alert when your AWS billing exceeds $500.

Task 2: EC2 CPU Utilization Alarm Setup

Goal: Trigger an alarm and send an SNS notification when CPU utilization exceeds 65%.

Steps:

Go to the CloudWatch Console.

Navigate to Alarms → All Alarms → Create Alarm.

Under Select Metric, choose:

EC2 → Per-Instance Metrics → [Select your EC2 instance ID]


Choose the metric name: CPUUtilization.

Set the Threshold value to 65.

Under Conditions, choose:

Whenever CPUUtilization is... Greater than 65%.

Under Actions, configure:

In Alarm → Send notification to an SNS topic.

Create or reuse an SNS topic (e.g., EC2HighCPUAlert) and add an email subscription.

Confirm your email subscription.

Click Create Alarm.

Result:

You’ll receive an email notification whenever your EC2 instance CPU usage exceeds 65%.

Verification

To test the billing alarm, you can lower the threshold temporarily to a smaller amount.

To test the CPU alarm, simulate high CPU load on the instance using:

sudo stress --cpu 4 --timeout 300


(Make sure stress package is installed.)

Deliverables

CloudWatch billing alarm configured for $500 threshold.

CloudWatch EC2 CPU utilization alarm configured for 65% threshold.

SNS topics created and verified for notifications.

