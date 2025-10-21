AWS SQS & SES Hands-On

This repository contains hands-on tasks for AWS Simple Queue Service (SQS) and Simple Email Service (SES).

Task 1: Create a FIFO SQS Queue and Send Messages

Objective:
Create a FIFO (First-In-First-Out) SQS queue and test it by sending messages.

Steps Performed:

Login to AWS Console and navigate to SQS.

Click Create Queue and select FIFO Queue.

Enter the queue name (must end with .fifo, e.g., MyQueue.fifo).

Configure the following settings:

Content-Based Deduplication: Enabled (or provide MessageDeduplicationId)

Delivery Delay: 0 seconds

Maximum Message Size: Default (256 KB)

Message Retention Period: Default (4 days)

Click Create Queue.

Test: Send Messages

Select your FIFO queue and click Send and Receive Messages.

Enter a test message and click Send Message.

Click Poll for Messages to verify that your message is received.

✅ Result: FIFO queue created successfully and messages sent/received correctly.

Task 2: Send Test Email via SES

Objective:
Register your email in AWS SES and send a test email.

Steps Performed:

Login to AWS Console and navigate to SES.

Select Verified Identities → Create Identity → Email Address.

Enter your email address and click Verify.

Check your email inbox and click the verification link from AWS.

Test: Send Test Email

Go to SES → Email → Send Email.

Set the following fields:

From: Your verified email address

To: Your verified email address

Subject: Test Email from AWS SES

Body: “This is a test email from AWS SES.”

Click Send Email.

✅ Result: Test email successfully received in your inbox.

Notes:

SQS FIFO ensures that messages are delivered in order and exactly once.

SES requires email verification when in sandbox mode. To send emails to unverified addresses, request production access.
