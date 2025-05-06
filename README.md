Tuberculosis Tracker – Abdullo
📘 Overview
A web application to track and manage Tuberculosis data. Built with:

Frontend: HTML + JavaScript, hosted on Amazon S3

Backend: Flask (Python), hosted on Amazon EC2

Database: PostgreSQL on Amazon RDS

🚀 Features
Add new test TB records

View all existing records in a table

Delete individual records by ID

Fully integrated with AWS: S3, EC2, RDS

🔧 Step-by-Step Deployment
Dataset

Downloaded Tuberculosis_Trends.csv from Kaggle.

Database (RDS)

Launched PostgreSQL RDS instance (e.g., db-instance-name) in your AWS region.

Created database your-database-name and table your-table-name.

Imported CSV using a tool like DBeaver via the “Import Data” wizard.

Static Frontend (S3)

Created an S3 bucket (e.g., your-bucket-name) and enabled static website hosting.

Uploaded index.html.

Applied a public-read bucket policy to allow access to the static page.

Backend (EC2 + Flask)

Launched Ubuntu EC2 instance (e.g., t2.micro), opened ports 22 and 80.

SSH’d into the server, created a Python virtual environment.

Installed required packages: Flask, psycopg2, flask-cors.

Created app.py with endpoints /add, /delete, /records connected to your RDS instance.

Ran the app on port 80.

Testing

Frontend available at:
http://your-bucket-name.s3-website-your-region.amazonaws.com

Backend available at:
http://your-ec2-public-ip

