# Infrastructure Description

This document describes the infrastructure used to deploy the application.

## **Cloud Services**
- **AWS Elastic Beanstalk**: Manages application deployment.
- **AWS RDS (PostgreSQL)**: Database service for storing app data.
- **AWS S3**: Stores frontend assets.

## **Architecture**
- **Frontend**: Hosted on AWS S3 as a static site.
- **Backend**: Node.js application deployed using AWS Elastic Beanstalk.
- **Database**: PostgreSQL database managed by AWS RDS.
- **CI/CD**: Automated using CircleCI.

---
### RDS - Database
- PostgresSQL
- db instance: udagram-database
- db name: postgres
- allows inbound config from anywhere (0.0.0.0/0)
- port: 5432

### ElasticBeanstalk - Backend API
- environment: Udagram-app-env 
- application: udagram-app
- port: 8080

### S3 - Frontend
- ACLs enabled, public s3 bucket
- Bucket policy:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Stmt1625306057759",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::udagram-proj-bucket/*"
        }
    ]
}
```
- CORS config:
```
[
 {
     "AllowedHeaders": [
         "*",
         "Content-Type",
         "Authorization",
         "Access-Control-Allow-Origin",
         "Access-Control-Allow-Headers",
         "Access-Control-Allow-Methods"
     ],
     "AllowedMethods": [
         "POST",
         "GET",
         "PUT",
         "DELETE",
         "HEAD"
     ],
     "AllowedOrigins": [
         "*"
     ],
     "ExposeHeaders": []
 }
]
```