# LambdaZip - Serverless File Compression with AWS

##  Project Overview

LambdaZip is a serverless AWS project that automatically compresses files uploaded to an S3 bucket into `.zip` format.
It uses **Amazon S3**, **Amazon EventBridge**, and **AWS Lambda** to create an event-driven architecture.

Whenever a user uploads a new file to the S3 bucket, EventBridge detects the upload event and triggers the Lambda function. The Lambda function downloads the file, compresses it, and uploads the compressed `.zip` file back into the same S3 bucket.

---

##  Architecture

![alt text](Architecture.png)

## Architecture Explanation

The **LambdaZip** project follows a fully serverless and event-driven architecture on AWS to automate file compression.

### 1. User Uploads File

The workflow begins when a user uploads a file (such as `.jpg`, `.pdf`, `.txt`, etc.) into the Amazon S3 source bucket. This bucket acts as the storage layer for incoming files.

### 2. Amazon S3 Stores the File

Once the file is uploaded, Amazon S3 securely stores the object and generates an **Object Created** event.

### 3. EventBridge Captures the Event

Amazon EventBridge continuously listens for object creation events from the S3 bucket. When a new file is uploaded, EventBridge captures the event details such as:

* Bucket Name
* Object Key
* Event Time

This removes the need for direct polling and enables real-time event-driven processing.

### 4. EventBridge Triggers AWS Lambda

After detecting the event, EventBridge triggers the Lambda function automatically. This makes the architecture fully serverless because no servers are managed manually.

### 5. AWS Lambda Processes the File

The Lambda function performs the following tasks:

* Downloads the uploaded file from the S3 bucket into temporary storage (`/tmp`)
* Compresses the file into `.zip` format using Python’s `zipfile` library
* Creates a new compressed version of the file

### 6. Upload Compressed File Back to S3

After compression, Lambda uploads the `.zip` file back into the same S3 bucket inside the `compressed/` folder.

Example:

**Original File:**

```text
Snapchat-490068034.jpg
```

**Compressed File:**

```text
compressed/Snapchat-490068034.jpg.zip
```

### 7. IAM Role Permissions

The Lambda function uses an IAM role to securely interact with Amazon S3. Required permissions include:

* `s3:GetObject`
* `s3:PutObject`
* `s3:HeadObject`

These permissions allow Lambda to download, verify, and upload files.

---

## Benefits of this Architecture

* **Fully Serverless** – No server management required
* **Event-Driven** – Automatically reacts to new file uploads
* **Scalable** – Handles multiple uploads efficiently
* **Cost-Effective** – Pay only when Lambda executes
* **Automated Workflow** – Reduces manual file compression tasks

This architecture demonstrates how AWS serverless services can be integrated to build a scalable and automated file processing pipeline.


### Workflow:

1. User uploads a file into the S3 bucket.
2. Amazon S3 generates an **Object Created** event.
3. EventBridge captures the event.
4. EventBridge triggers the Lambda function.
5. Lambda downloads the uploaded file.
6. Lambda compresses the file into `.zip`.
7. Lambda uploads the compressed file back to S3.

---

##  AWS Services Used

* **Amazon S3** – Stores uploaded and compressed files.
* **Amazon EventBridge** – Monitors S3 object creation events.
* **AWS Lambda** – Compresses files automatically.
* **IAM Role** – Grants permissions to Lambda.


---

##  Lambda Function Logic

* Fetch bucket name and object key from EventBridge event.
* Download the file to Lambda temporary storage (`/tmp`).
* Compress the file using Python `zipfile`.
* Upload the `.zip` file back to S3.

---

## 🔑 IAM Permissions

Required IAM Policy:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject",
        "s3:HeadObject"
      ],
      "Resource": "arn:aws:s3:::your-bucket-name/*"
    }
  ]
}
```

---

##  EventBridge Rule Pattern

```json
{
  "source": ["aws.s3"],
  "detail-type": ["Object Created"]
}
```

---

##  Example

### Uploaded File:

![alt](./Screenshot%20(645).png)

### Compressed Output:

![alt](./Screenshot%20(644).png)


---

##  Key Features

✅ Fully serverless architecture<br>
✅ Automatic file compression<br>
✅ Event-driven workflow<br>
✅ Scalable and cost-efficient<br>
✅ No manual intervention required<br>

---

## Steps :
- 1 Create Buket

![alt](./Screenshot%20(593).png)
![alt](./Screenshot%20(594).png)
![alt](./Screenshot%20(595).png)
![alt](./Screenshot%20(596).png)

- 2 Create IAM Roles

![alt](./Screenshot%20(601).png)
![alt](./Screenshot%20(602).png)
![alt](./Screenshot%20(603).png)
![alt](./Screenshot%20(604).png)
![alt](./Screenshot%20(605).png)
![alt](./Screenshot%20(606).png)

- 3 Create Lambda funtion 

![alt](./Screenshot%20(607).png)
![alt](./Screenshot%20(608).png)
![alt](./Screenshot%20(609).png)
![alt](./Screenshot%20(610).png)
![alt](./Screenshot%20(611).png)
![alt](./Screenshot%20(612).png)
![alt](./Screenshot%20(613).png)
![alt](./Screenshot%20(614).png)
![alt](./Screenshot%20(615).png)
![alt](./Screenshot%20(615).png)
![alt](./Screenshot%20(617).png)

- 4 Create EventBridge

![alt](./Screenshot%20(620).png)
![alt](./Screenshot%20(621).png)
![alt](./Screenshot%20(622).png)
![alt](./Screenshot%20(623).png)
![alt](./Screenshot%20(626).png)
![alt](./Screenshot%20(627).png)
![alt](./Screenshot%20(628).png)
![alt](./Screenshot%20(629).png)
![alt](./Screenshot%20(630).png)
![alt](./Screenshot%20(631).png)

- 5 Get the code from chatgpt,add in lambdacode, deploye

![alt](./Screenshot%20(636).png)

- 6 Create Test in Lambda to test our code

![alt](./Screenshot%20(637).png)
![alt](./Screenshot%20(638).png)
![alt](./Screenshot%20(639).png)

 Add this code in Test Event 
![alt](./Screenshot%20(646).png)

- 7 Test it

![alt](./Screenshot%20(643).png)





##  Conclusion

LambdaZip demonstrates the power of AWS serverless services by automating file compression using event-driven architecture. This project improves efficiency, reduces manual work, and provides a scalable solution for handling uploaded files in real time.
