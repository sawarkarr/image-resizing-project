# Serverless Image Resizing and Transfer Management System Using AWS


## Project Description :

This project focuses on creating a robust, automated image processing system using AWS services. It streamlines tasks like resizing images, secure storage, and real-time notifications by leveraging serverless, scalable solutions. The system automatically processes image uploads, resizes them to predefined dimensions, stores them securely in S3, and notifies users about completion. Designed for efficiency, cost-effectiveness, and high availability, it simplifies image management within the AWS cloud ecosystem.


## Key Features :

1.    Automation: Images uploaded to S3 are automatically resized using AWS Lambda and stored in a secure S3 bucket.
2.    Secure Storage: Encrypted S3 buckets ensure data security, with lifecycle policies for cost optimization.
3.    Notifications: SNS delivers real-time alerts about processing status to stakeholders via email or SMS.
4.    Scalability: Serverless architecture (Lambda, S3) handles dynamic workloads with ease.
5.    Cost Efficiency: Pay-as-you-go model minimizes operational costs, leveraging AWS Free Tier benefits.


## Workflow :

1.    Image Upload: S3 triggers Lambda upon image upload.
2.    Processing: Lambda resizes images and transfers them to a designated S3 bucket.
3.    Notifications: SNS alerts stakeholders upon successful processing.
4.    Monitoring: CloudWatch tracks system performance and errors.

## AWS Services Used :

1.    S3: Stores raw and processed images.
2.    Lambda: Automates resizing tasks.
3.    SNS: Sends notifications.
4.    CloudWatch: Monitors logs and performance.
5.    IAM: Secures resource access.


## Overview :

![architecture of s3-lambda-sns](https://github.com/user-attachments/assets/26418588-71b4-4fba-bc86-a2299f765f9e)


