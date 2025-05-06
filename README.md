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
   - Downloaded Tuberculosis_Trends.csv from Kaggle.

2. **Database (RDS)**  
   - Launched PostgreSQL RDS instance db-abdullo in ap-northeast-2.  
   - Created database postgres and table tbl_abdullo_tuberculosis.  
   - Imported CSV via DBeaver’s “Import Data” wizard.

3. **Static Frontend (S3)**  
   - Created bucket s3bucket-abdullo and enabled static website hosting.  
   - Uploaded index_Abdullo.html.  
   - Applied public-read bucket policy.

4. **Backend (EC2 + Flask)**  
   - Launched Ubuntu EC2 t2.micro, opened ports 22/80.  
   - SSH’d in, created venv, installed Flask, psycopg2, flask-cors.  
   - Deployed app.py listening on port 80, connected to RDS.  
   - Verified Add/Delete/List via /add, /delete, /records endpoints.

5. **Testing**  
   - Frontend at http://s3bucket-abdullo.s3-website-ap-northeast-2.amazonaws.com  
   - Backend at http://<your-ec2-ip>
