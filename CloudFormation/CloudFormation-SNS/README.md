# AWS CloudFormation Stack with SNS Notifications

## Overview

This project demonstrates how to create an **AWS CloudFormation stack** and integrate **Amazon SNS (Simple Notification Service)** to receive email notifications for every step of the stack creation process.

Using this setup, you can monitor the progress of your CloudFormation stack in real-time and get notified via email whenever a resource is created, updated, or encounters an error.

---

## Architecture

* **CloudFormation Stack:** Defines AWS resources (based on template from Task 1) such as EC2, S3, or other services.
* **SNS Topic:** Sends notifications to subscribed email addresses.
* **Email Subscription:** Receives notifications for stack events (CREATE, UPDATE, DELETE, etc.).

```
[CloudFormation Stack] --> [SNS Topic] --> [Email]
```

---

## Prerequisites

* AWS account with necessary IAM permissions for CloudFormation and SNS.
* Verified email address to receive SNS notifications.
* AWS CLI or AWS Management Console access.

---

## Steps to Deploy

1. **Create CloudFormation Stack**

   * Use the existing template from **Task 1** (replace `YourTemplate.yaml` with your template file).

   ```bash
   aws cloudformation create-stack \
       --stack-name MyStack \
       --template-body file://YourTemplate.yaml \
       --capabilities CAPABILITY_NAMED_IAM
   ```

2. **Add SNS Notifications**

   * Add an SNS topic in the CloudFormation template or create one manually:

   ```yaml
   Resources:
     MySNSTopic:
       Type: AWS::SNS::Topic
       Properties:
         DisplayName: "CloudFormationNotifications"
         Subscription:
           - Protocol: email
             Endpoint: your-email@example.com
   ```

3. **Subscribe to SNS Topic**

   * Confirm the subscription from the email you provided.
   * After confirmation, SNS will send notifications whenever there’s a change in stack events.

4. **Monitor Stack Creation**

   * You will receive an email for each step of the stack creation process.
   * You can also view events in the CloudFormation console:

   ```
   AWS Console → CloudFormation → Your Stack → Events
   ```

---

## CloudFormation Template Highlights

* **Resources**: Defines AWS resources (EC2, S3, RDS, etc.) as per Task 1.
* **SNS Integration**: CloudFormation uses `NotificationARNs` property to send stack notifications.

Example snippet in template:

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Resources:
  MyEC2Instance:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: ami-0abcd1234efgh5678
      InstanceType: t2.micro

# Attach SNS notifications
NotificationARNs:
  - !Ref MySNSTopic
```

---

## Benefits

* Real-time monitoring of stack creation/update/delete events.
* Immediate notification for failures or errors.
* Ensures transparency and quick response to infrastructure changes.

---

## License

This project is for learning purposes and is open for modification and personal use.

