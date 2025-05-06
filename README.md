# Tuberculosis Tracker – Abdullo

## 📘 Overview
A web application to track and manage Tuberculosis data. Built with:  
- **Frontend**: HTML + JavaScript, hosted on Amazon S3  
- **Backend**: Flask (Python), hosted on Amazon EC2  
- **Database**: PostgreSQL on Amazon RDS  

## 🚀 Features
- **Add** new test TB records  
- **View** all existing records in a table  
- **Delete** individual records by ID  
- **Fully integrated** with AWS: S3, EC2, RDS  

---

## 🔧 Step-by-Step Deployment

1. **Dataset**  
   - Download Tuberculosis_Trends.csv from Kaggle.

2. **Database (RDS)**  
   - Launch PostgreSQL RDS instance db-abdullo in ap-northeast-2.  
   - Creat database postgres and table tbl_abdullo_tuberculosis.  
   - Import CSV via DBeaver’s “Import Data” wizard.

3. **Static Frontend (S3)**  
   - Creat bucket s3bucket-abdullo and enabled static website hosting.  
   - Upload index_Abdullo.html.  
   - Apply public-read bucket policy.

4. **Backend (EC2 + Flask)**  
   - Launch Ubuntu EC2 t2.micro, opened ports 22/80.  
   - SSH’d in, created venv, installed Flask, psycopg2, flask-cors.  
   - Deploy app.py listening on port 80, connected to RDS.  
   - Verify Add/Delete/List via /add, /delete, /records endpoints.
