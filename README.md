# SnapGuard: Event-Driven EC2 Snapshot Automation with AWS Lambda

##  Project Overview

SnapGuard is an AWS automation project designed to create automatic EBS snapshots of running EC2 instances using an event-driven serverless architecture.

This project uses Amazon EventBridge to trigger AWS Lambda, which then interacts with the EC2 API to create snapshots of attached EBS volumes. It helps automate backup operations, improve disaster recovery, and reduce manual efforts.

---

##  Architecture Diagram

<img width="1200" alt="SnapGuard Architecture" src="./Architecture.png">

---

###  Architecture Explanation

The SnapGuard architecture follows an event-driven workflow for automating EC2 backups.

### **1. Amazon EC2 Instance**

The process starts with a running EC2 instance containing attached EBS volumes. These volumes store application data and system files that require backups.


### **2. Amazon EventBridge**

Amazon EventBridge acts as the trigger mechanism. It initiates the Lambda function based on configured events such as:

* Scheduled cron jobs
* Manual triggers
* EC2 state changes
* Custom events

This makes the backup process fully automated.


### **3. AWS Lambda**

Once triggered, AWS Lambda executes the automation logic written in Python using Boto3.

The Lambda function:

* Identifies the EC2 instance
* Fetches attached EBS volumes
* Calls the EC2 Snapshot API
* Creates snapshots automatically




### **4. Amazon EC2 API**

The Lambda function interacts with AWS EC2 API using the CreateSnapshot operation.

This API handles the snapshot creation process.

### **5. Amazon EBS Snapshot**

After the API call, AWS stores the snapshot in Amazon EBS.

These snapshots can be used later for:

* Disaster recovery
* Data restoration
* Backup retention
* Migration


---

##  AWS Services Used

* Amazon EC2
* Amazon EventBridge
* AWS Lambda
* Amazon EBS
* IAM Role
* Python (Boto3)

---

##  Workflow

1. EC2 instance runs with attached EBS volume.
2. EventBridge triggers based on schedule or event.
3. EventBridge invokes the Lambda function.
4. Lambda executes Python automation code.
5. Lambda calls EC2 API to create snapshot.
6. Snapshot gets stored in Amazon EBS.

---

##  Implementation Steps

### Step 1: Create an EC2 Instance

* Launch an EC2 instance.
* Attach an EBS volume.
* Ensure the instance is in running state.

---

### Step 2: Create IAM Role

Attach these permissions:

* `AmazonEC2FullAccess`

Assign the IAM role to Lambda.

![alt text](<Screenshot (567).png>)
![alt text](<Screenshot (568).png>)
![alt text](<Screenshot (569).png>)
![alt text](<Screenshot (570).png>)
![alt text](<Screenshot (571).png>)

---

### Step 3: Create Lambda Function

* Go to AWS Lambda Console
* Click Create Function
* Runtime: Python 3.x
* Attach IAM role
![alt text](<Screenshot (559).png>)
![alt text](<Screenshot (560).png>)
![alt text](<Screenshot (561).png>)
![alt text](<Screenshot (562).png>)
![alt text](<Screenshot (563).png>)
![alt text](<Screenshot (564).png>)
![alt text](<Screenshot (565).png>)
![alt text](<Screenshot (566).png>)
![alt text](<Screenshot (572).png>)
![alt text](<Screenshot (573).png>)
![alt text](<Screenshot (574).png>)
---

### Step 4: Add Lambda Code

```python
import boto3

ec2 = boto3.client('ec2')

def lambda_handler(event, context):
    instance_id = 'your-instance-id'

    volumes = ec2.describe_volumes(
        Filters=[
            {
                'Name': 'attachment.instance-id',
                'Values': [instance_id]
            }
        ]
    )

    for volume in volumes['Volumes']:
        snapshot = ec2.create_snapshot(
            VolumeId=volume['VolumeId'],
            Description='Automated Snapshot by SnapGuard'
        )

        print(f"Snapshot Created: {snapshot['SnapshotId']}")

    return {
        'statusCode': 200,
        'body': 'Snapshot created successfully'
    }
```

---

### Step 5: Configure EventBridge

* Go to EventBridge
* Create Rule
* Select Schedule or Event Pattern
* Set Lambda as Target
![alt text](<Screenshot (576).png>)
![alt text](<Screenshot (577).png>)
![alt text](<Screenshot (578).png>)
![alt text](<Screenshot (579).png>)
![alt text](<Screenshot (580).png>)
![alt text](<Screenshot (581).png>)
![alt text](<Screenshot (582).png>)
![alt text](<Screenshot (583).png>)

Example:

* Daily backup
* Weekly backup
* Custom cron jobs

---

### Step 6: Test the Workflow

Trigger EventBridge manually or wait for schedule execution.

Verify snapshots in:

**EC2 → Snapshots**
![alt text](<Screenshot (575).png>)

---

##  Benefits

✔ Fully automated backup system
✔ Event-driven architecture
✔ Serverless and scalable
✔ Cost-effective solution
✔ Improved disaster recovery
✔ Minimal operational overhead

---

##  Future Enhancements

* Add snapshot deletion automation
* Add retention policy
* Add SNS notifications
* Add multi-instance support
* Add snapshot tagging

---

##  Learning Outcomes

Through this project, I learned:

* AWS Lambda automation
* EventBridge scheduling
* Boto3 integration
* EC2 snapshot APIs
* IAM permissions
* Event-driven architecture

---

##  Conclusion

SnapGuard is a practical AWS automation project that demonstrates how serverless services can automate infrastructure backup processes efficiently.

By combining EventBridge, Lambda, and EC2 Snapshot APIs, this project creates a reliable, scalable, and cost-effective backup system for EC2 instances.

This project strengthens real-world AWS, DevOps, and cloud automation skills.

---

##  Tags

`AWS` `Lambda` `EventBridge` `EC2` `EBS` `Boto3` `Python` `Automation` `DevOps`
