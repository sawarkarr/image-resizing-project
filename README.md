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


## Steps :


### Step 1 :- Creating Source and Designation s3 Buckets :

1. Navigate to the S3 Console.
2. Follow the outlined steps to create the source bucket and upload images.

![image-resizing-1](https://github.com/user-attachments/assets/3fba1135-6cd3-47bf-b0e2-7437fdf05b9d)
click on create bucket option



![image-resizing-2](https://github.com/user-attachments/assets/4f50f4d8-39bb-428f-b099-0d24371fae46)
Give Globally Unique bucket name


![image-resizing-3](https://github.com/user-attachments/assets/ba0e7ae3-4952-4ae1-9849-f41f81db17ea)
Dont change any other settings just scroll down and click create bucket


![image-resizing-4](https://github.com/user-attachments/assets/1002bda3-4e60-4565-a8ec-5b3bd6723a67)
You should now have two buckets: Source Bucket and Destination Bucket.

### Step 2: Setting Up SNS Notifications
Navigate to the SNS Console.

Follow the outlined steps below:
![image-resizing-5](https://github.com/user-attachments/assets/e593fa61-648d-4e29-b62c-0c1a8dee4905)
now create sns topic
![image-resizing-6](https://github.com/user-attachments/assets/ebfc41d5-a1a3-4f77-bf57-051201bd6bd8)
select standard type and give sns topic name
![image-resizing-7](https://github.com/user-attachments/assets/6b4cbdca-0bac-4e51-acb2-13d33bba5d5b)
Dont change any other settings just scroll down and click create topic

![image-resizing-8](https://github.com/user-attachments/assets/849e74d3-b579-499e-a990-43e7eed40ca2)
now click on create subscription
![image-resizing-9](https://github.com/user-attachments/assets/86004487-b554-4f48-b10d-288bd75a070d)
choose topic arn and choose protocol as email
![image-resizing-10](https://github.com/user-attachments/assets/3719c094-b499-44ac-96c6-a95680f446cb)
write your email id on endpoint
![image-resizing-11](https://github.com/user-attachments/assets/509dfac5-94f0-4d23-8777-b4cb6fc4cab5)
open your email and click confirm subscription
![image-resizing-12](https://github.com/user-attachments/assets/caaab325-07e0-47fe-8e2e-5ee6e6d53edb)


### Step 3:- 
![image-resizing-13](https://github.com/user-attachments/assets/2efa9048-1b61-42e8-92d6-91c9dfcd223b)
1.  go to aws lambda and click on create a function
![image-resizing-14](https://github.com/user-attachments/assets/99e28cb7-e63b-47c6-85d3-5d9c8336a6ec)
2.  choose author from scratch , give function name and give runtime as python3.9

3.  Now replace the default code with the image-resizing-s3.py and deploy the changes , Don't test the code now we have to do some more actions before testing.


4.  After that , We have to give some permission for our Lambda Function to do our process (resizing) , For that navigate to the IAM Console and follow the below steps.


![image-resizing-15](https://github.com/user-attachments/assets/46211066-7917-409f-9142-2e94db744cf4)
go to policies option 
![image-resizing-16](https://github.com/user-attachments/assets/bb92696f-238c-4424-ab14-bb7512920e60)
choose create policy option
![image-resizing-17](https://github.com/user-attachments/assets/21a341f9-ced0-4da0-b5bc-a878d2a6b5f6)
choose s3 and go next
![image-resizing-18](https://github.com/user-attachments/assets/a6f5d04d-9857-4703-93ac-5ea67eb40d6f)
choose s3 as all actions allowed
![image-resizing-19](https://github.com/user-attachments/assets/0d74f7a3-2596-4bf1-9ea0-2304253c5fb2)
select resource type all
![image-resizing-20](https://github.com/user-attachments/assets/4a1862f5-ba57-4411-b4a4-7da9731d223b)
select sns then choose all actions allowed
![image-resizing-21](https://github.com/user-attachments/assets/56a2033b-2adb-48c9-914a-27cfc6f3da9c)
select resource type all
![image-resizing-23](https://github.com/user-attachments/assets/b323dfe2-4cb3-475f-89aa-5a903015e4d6)
select lambda and search getlayerversion on action and allowed all access to resource
![image-resizing-24](https://github.com/user-attachments/assets/17c5e9dc-a420-4756-af54-09a913b09993)
now give policy name
![image-resizing-25](https://github.com/user-attachments/assets/97e07641-0d1c-413a-a736-f42fe198b857)
click on create policy
![image-resizing-26](https://github.com/user-attachments/assets/d503d974-4e6f-4549-b916-cda1e071b7fa)
go to lambda and choose configuration section and then choose permissions and select role name
![image-resizing-27](https://github.com/user-attachments/assets/c9b7474e-123c-458c-a247-fb91171e53d7)
click on add permissions and attach policy
![image-resizing-28](https://github.com/user-attachments/assets/8206835a-3b41-45b5-bb1c-38ce80db3d45)
search and select your created policy name and select add permission
![image-resizing-29](https://github.com/user-attachments/assets/d8f69346-46c5-43cb-9473-30b6c0c70366)
now go to triggers and select add trigger
![image-resizing-30](https://github.com/user-attachments/assets/acc5d3f3-1cfd-4471-b036-dddbfa3f0937)
select s3 and choose your source bucket name
![image-resizing-31](https://github.com/user-attachments/assets/910fb40b-94ef-4133-8f38-8fb90294f145)
select the checkbox and click on add 



1.   Now we have to go to code section , and scroll down to layers.

2.  We have to add layer.

4.  May be you can think , why ?
It's because for resize the image we upload in our source S3 bucket , We need a python library called pillow in our code to resize the image . We can manually add Pillow library also, But it's very time consuming and you have to do lot more , Instead of manually adding pillow library we are going to use layers for Some easy action.

5.  Follow the outlined Steps below
6.  scroll and go to add layer

![image-resizing-32](https://github.com/user-attachments/assets/8a6e7356-03ce-4213-bd46-6f6250c7f23d)


![image-resizing-33](https://github.com/user-attachments/assets/9267e7aa-bb4a-42d4-90d6-3e65e1b857ce)
7.  choose layer as as specify an ARN 
8.  You can copy the arn from below.

```
arn:aws:lambda:ap-south-1:770693421928:layer:Klayers-p39-pillow:1
```
9.  After done all the actions above.
![image-resizing-34](https://github.com/user-attachments/assets/307e7f67-79a1-4021-9d08-564268a57f19)

![image-resizing-43](https://github.com/user-attachments/assets/4a08ecc3-4330-4f35-ba24-a9cba063d04b)
10. now we can test our code.
![image-resizing-35](https://github.com/user-attachments/assets/789fad65-425b-4dcb-8ff7-e32825ce3f0d)
11. create an event for test

12. click on test and you will see this output
13. It will show some results like below , It runs successfully but return some error because we still not upload the images in S3 yet.


### Result:- 
Navigate to the S3 Console.
Upload Some images in Source Bucket.
![image-resizing-36](https://github.com/user-attachments/assets/0ebf3d32-8b03-4578-ae54-ff10e6f78d84)
select non-resized-image
![image-resizing-37](https://github.com/user-attachments/assets/20853577-f7de-4b4a-a118-5cb870207af2)
upload image
![image-resizing-38](https://github.com/user-attachments/assets/e1fd866e-c5c7-4598-8111-9f9e573ad4f6)
![image-resizing-39](https://github.com/user-attachments/assets/d2262596-7d16-43e2-9eda-e994ba2a48c8)
![image-resizing-40](https://github.com/user-attachments/assets/6e87271c-db85-4847-8b7c-4b177377855d)
you can see that automatically one folder is created and inside that folder we can see the resized images
![image-resizing-41](https://github.com/user-attachments/assets/4ccd349a-5b18-43e0-8401-2f506bcd0fc9)
you can see that our image has been resized and uploaded in our destination bucket

Once the images are uploaded, Lambda will automatically resize them and move them to the Destination Bucket.

You will receive a notification (via SNS) confirming that the image has been resized successfully.
![image-resizing-42](https://github.com/user-attachments/assets/316136ba-1f96-4532-92e2-ff6721b68479)

This process will automate image resizing, storage, and notification using AWS Lambda, S3, and SNS.

