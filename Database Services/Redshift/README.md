🚀 Amazon Redshift Data Warehouse Setup
📘 Overview

This project demonstrates how to create an Amazon Redshift Data Warehouse, load data into it using the Query Editor, and run SQL queries to analyze the data. Redshift is a fully managed, petabyte-scale data warehouse service in the cloud.

🧩 Steps to Implement
1. Create a Redshift Cluster

Go to the Amazon Redshift Console.

Click Create Cluster.

Configure the following:

Cluster identifier: redshift-demo-cluster

Node type: Choose dc2.large or ra3.xlplus

Number of nodes: 1 (for demo purposes)

Admin user: admin

Admin password: <your-password>

Choose an existing VPC or create a new one.

Make sure the Publicly accessible option is enabled.

Click Create Cluster.

2. Access the Query Editor

Open the Query Editor v2 from the Redshift console.

Connect using the admin credentials you created.

Select the database you want to work with (e.g., dev).

3. Create a Sample Table
CREATE TABLE employees (
    employee_id INT,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    department VARCHAR(50),
    salary DECIMAL(10,2)
);

4. Load Sample Data

You can insert some demo data using the Query Editor:

INSERT INTO employees VALUES
(1, 'John', 'Doe', 'HR', 50000.00),
(2, 'Jane', 'Smith', 'Finance', 65000.00),
(3, 'Sam', 'Williams', 'IT', 72000.00),
(4, 'Emma', 'Johnson', 'Marketing', 58000.00),
(5, 'David', 'Brown', 'IT', 80000.00);

5. Query the Data

Run SQL queries to view and analyze the data:

-- Retrieve all employee data
SELECT * FROM employees;

-- Find employees earning more than 60,000
SELECT first_name, last_name, department, salary
FROM employees
WHERE salary > 60000;

-- Average salary by department
SELECT department, AVG(salary) AS avg_salary
FROM employees
GROUP BY department;

6. (Optional) Load Data from S3

If you want to load larger datasets:

Upload your CSV file to an S3 bucket.

Use the COPY command:

COPY employees
FROM 's3://your-bucket-name/employee_data.csv'
IAM_ROLE 'arn:aws:iam::<your-account-id>:role/<your-redshift-role>'
FORMAT AS CSV
IGNOREHEADER 1;

✅ Verification

Run SELECT COUNT(*) FROM employees; to verify data load.

Check cluster performance metrics and query execution time.

🧹 Clean Up Resources

When done, delete the Redshift cluster to avoid incurring ongoing charges:

Go to Redshift Console → Select your cluster → Delete.

Optionally, take a final snapshot before deleting.

🗂️ Repository Structure
📁 redshift-demo
 ┣ 📜 README.md
 ┗ 📜 sample_queries.sql

💡 Notes

Ensure your IAM role has AmazonS3ReadOnlyAccess if you’re loading data from S3.

You can use Amazon QuickSight to visualize the queried results.
