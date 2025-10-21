🖥️ EC2 Monitoring Dashboard using CloudWatch
📘 Task Overview

This task involves creating a dashboard in AWS CloudWatch that allows you to monitor the CPU utilization and network metrics of a specific EC2 instance.
The dashboard provides real-time insights into instance performance and helps in maintaining system reliability.

🧩 Steps to Perform
1. Open CloudWatch

Sign in to the AWS Management Console.

Navigate to CloudWatch under the Management & Governance category.

2. Create a Dashboard

Click on Dashboards in the left navigation pane.

Choose Create dashboard.

Enter a name for your dashboard (e.g., EC2-Monitoring-Dashboard).

Select Create dashboard.

3. Add a Widget

Choose Add widget → select Line or Number type (based on your preference).

Click Configure.

4. Add CPU Utilization Metric

Under Metrics, select:

EC2 → Per-Instance Metrics → CPUUtilization


Select your specific instance ID.

Click Create widget to add it to the dashboard.

5. Add Network Metrics

Repeat the same steps to add the following metrics:

NetworkIn → to monitor incoming network traffic.

NetworkOut → to monitor outgoing network traffic.

6. Customize Dashboard

Arrange widgets visually for better readability.

Optionally, add text widgets for labels or descriptions.

Click Save dashboard.

7. Verify Dashboard

Open the dashboard to view real-time graphs.

Ensure that CPU and Network metrics are updating based on EC2 activity.

📊 Example Dashboard Widgets
Metric	Namespace	Description
CPUUtilization	AWS/EC2	Displays CPU usage percentage
NetworkIn	AWS/EC2	Displays inbound traffic in bytes
NetworkOut	AWS/EC2	Displays outbound traffic in bytes
✅ Expected Outcome

You should now have a CloudWatch dashboard that provides:

CPU Utilization trends of your EC2 instance.

Network performance insights (inbound/outbound traffic).

Easy monitoring without manually checking metrics per instance.

📁 Deliverables

Screenshot or link to your CloudWatch dashboard.

Dashboard JSON file (optional export).

This README file uploaded to your GitHub repository
