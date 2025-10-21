AWS Lambda with SQS Trigger
Task Overview

This task demonstrates how to create a simple AWS Lambda function in Python and configure it to be triggered automatically by messages sent to an Amazon SQS queue.

Steps to Perform
1. Create an SQS Queue

Go to the Amazon SQS console.

Click on Create queue.

Choose Standard queue (or FIFO if needed).

Give it a name, e.g., LambdaTriggerQueue.

Leave other settings as default and click Create Queue.

2. Create a Python Lambda Function

Navigate to the AWS Lambda console.

Click on Create function → choose Author from scratch.

Provide details:

Function name: SQSMessageProcessor

Runtime: Python 3.12 (or latest available)

Click Create function.

3. Add the Lambda Function Code

Replace the default code with the following sample:

Click Deploy to save the function.

4. Set the SQS Queue as a Trigger

In the Lambda function console, go to the Configuration tab → Triggers.

Click Add Trigger.

Choose SQS as the trigger source.

Select the queue you created earlier (LambdaTriggerQueue).

Click Add.

Ensure the Lambda execution role has permissions for SQS:

Policy: AWSLambdaSQSQueueExecutionRole

5. Test the Setup

Go to the SQS queue.

Click Send and receive messages.

Send a sample message, for example:

{"task": "Test Lambda SQS Integration", "status": "Pending"}


Wait a few seconds for Lambda to be invoked.

6. Verify the Invocation

Go to the Lambda function → Monitor → Logs.

Open the CloudWatch Logs for the latest invocation.

You should see the message printed:

Event received from SQS:
Message Body: {"task": "Test Lambda SQS Integration", "status": "Pending"}

Expected Output

Lambda automatically processes the message from SQS and logs its content in CloudWatch.

Conclusion

This setup demonstrates how to:

Create a Lambda function in Python.

Connect it to an SQS queue as a trigger.

Automatically process and log incoming messages.
