Task: Create Elastic Beanstalk Environment (PHP)
Objective

Set up an AWS Elastic Beanstalk environment with PHP runtime and deploy a basic PHP application.

Steps
Step 1: Create an Application in Elastic Beanstalk

Go to the AWS Management Console → Elastic Beanstalk.

Click Create application.

Enter:

Application name: php-app

Under Platform, choose:

Platform: PHP

Platform branch: Recommended version (e.g., PHP 8.2)

Leave other settings as default and click Create application.

Step 2: Prepare a Simple PHP File

Create a simple PHP file named index.php in your local system:

<?php
echo "Hello from AWS Elastic Beanstalk using PHP!";
?>


Compress the file into a .zip:

zip php-app.zip index.php

Step 3: Upload and Deploy the PHP Application

In the Elastic Beanstalk dashboard → Go to your application (php-app).

Click Upload and deploy.

Choose your php-app.zip file and click Deploy.

Wait until the Health status becomes Green.

Step 4: Test Your Application

Click the URL shown at the top of your Elastic Beanstalk environment dashboard.

You should see:

Hello from AWS Elastic Beanstalk using PHP!

✅ Verification

Application environment status: Green

PHP runtime: Running successfully

Output message visible in browser
