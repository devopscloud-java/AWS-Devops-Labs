# Auto Scaling and Load Balancer Setup

**Purpose**

This README explains how to implement automatic scaling of compute resources and a load balancer to distribute traffic in AWS. It covers:

* Scale out (add instances) when CPU utilization > 80%
* Scale in (remove instances) when CPU utilization < 60%
* Use an Application Load Balancer (ALB) to distribute incoming traffic
* Deployment options: CloudFormation (preferred), AWS CLI, and manual Console steps

---

## Architecture Overview

* **Application Load Balancer (ALB)** in a public subnet receives incoming requests.
* **Auto Scaling Group (ASG)** spans multiple private/public subnets and manages EC2 instances created from a Launch Template.
* **CloudWatch Alarms** monitor the ASG average `CPUUtilization` and trigger scaling policies.

```
Internet --> ALB (public subnets) --> Target Group --> Auto Scaling Group (EC2 instances in private subnets)
                                      ^
                                      |-- Health checks (ALB)
```

---

## Prerequisites

1. AWS account with privileges to create: VPC, Subnets, Security Groups, IAM roles, Launch Template, Auto Scaling Group, ALB, Target Group, CloudWatch alarms, and EC2 instances.
2. AWS CLI configured (`aws configure`) or CloudFormation permissions.
3. A simple application (e.g., a small web server) baked into an AMI or provided via UserData script.

---

## Security & Networking Notes

* ALB should be in public subnets and allow inbound HTTP/HTTPS (e.g., 80/443) from `0.0.0.0/0` or your CIDR.
* EC2 instances may live in private subnets; ensure the ALB's Target Group can reach them (health checks and security groups allow ALB -> EC2 on instance port, e.g., 80).
* Launch Template or Launch Configuration must attach instances to the correct security group and role (for e.g., SSM access).

---

## Testing

* Use a load generator (e.g., `ab`, `wrk`, or a small script) to generate traffic to the ALB DNS name.
* Monitor the Auto Scaling Group activity and CloudWatch metrics. When average CPU across the ASG surpasses 80% for the evaluation period, ASG should scale out by one instance. When CPU drops below 60%, it should scale in.

---

## Notes & Best Practices

* Use **Target Tracking Scaling Policy** (recommended) for simpler management: set target CPU utilization (e.g., 70%) and AWS will add/remove instances automatically. This often produces smoother scaling than simple threshold alarms.
* Use **Lifecycle Hooks** if you need to perform bootstrapping, draining, or graceful shutdowns.
* Use **Health checks** with ALB and enable `deregistration delay` so in-flight requests are allowed to complete before instance termination.
* Use proper **cooldown** periods so the group doesn't thrash (frequent scaling actions).
* Prefer **Auto Scaling scheduled actions** for predictable load changes (e.g., business hours).
* Consider **cost controls**: set sensible `MaxSize` and use instance families that match your workload.

---

## Cleanup

To avoid ongoing charges, delete the CloudFormation stack or manually remove the ALB, ASG, Launch Template, and the EC2 instances.

---

## References & Further Reading

* AWS Auto Scaling Groups
* AWS Application Load Balancer
* CloudWatch Alarms & Metrics
* Target Tracking vs Step Scaling



