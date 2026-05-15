# AWS EBS Volume Mounting Mini Project

## Project Overview

This project demonstrates how to create, attach, partition, format, and mount an Amazon EBS volume to an AWS EC2 Linux instance using  <span style="color:orange">**fdisk**</span>.

The mounted volume is used to store application/project data separately from the root volume.

---

#  Architecture Diagram

![alt text](image.png)

---

# 🎯 Objective

- Create a new EBS volume
- Attach it to EC2
- Create partition using `fdisk`
- Format volume with ext4
- Mount volume permanently

---

#  Services Used

- AWS EC2
- AWS EBS
- Linux
- fdisk
- XFS filesystem

---

#  Prerequisites

- AWS Account
- Running EC2 Instance
- Attached EBS Volume
- SSH Access to EC2

---

#  Implementation Steps

## Step 1: Create Volume and ensure the same az and region of volume with ec2


![alt text](<Screenshot (177).png>)<br><br>
![alt text](<Screenshot (178).png>)<br><br>
---

## Step 2: Attach Volume



![alt text](<Screenshot (179).png>)<br><br>
![alt text](<Screenshot (180).png>)<br><br>
![alt text](<Screenshot (181).png>)<br><br>
---

## Step 3: Check Available Disks



```bash
lsblk
```
![alt text](<Screenshot (182).png>)<br><br>
---

## Step 4: Create New Partition

Inside fdisk:

```bash
n
p
1
Enter
+1G (for choose the size 1GB)
w
```

![alt text](<Screenshot (183).png>)<br><br>
![alt text](<Screenshot (186).png>)<br><br>
![alt text](<Screenshot (187).png>)<br><br>
---

## Step 5: Create File System

```bash
sudo mkfs /dev/nvem1n1p1
```
![alt text](<Screenshot (188).png>)<br><br>
![alt text](<Screenshot (189).png>)<br><br>
---

## Step 6: Create Mount Directory / Permanent Mount

```bash
sudo vim /etc/fstab


```
![alt text](<Screenshot (190).png>)<br><br>
![alt text](<Screenshot (191).png>)<br><br>
![alt text](<Screenshot (192).png>)<br><br>
![alt text](<Screenshot (193).png>)<br><br>
---



#  Output

- Successfully created partition using fdisk
- Mounted EBS volume on EC2
- Persistent storage configured
![alt text](<Screenshot (194).png>)<br><br>
![alt text](<Screenshot (195).png>)<br><br>
![alt text](<Screenshot (196).png>)<br><br>

---

#  Learning Outcome

Through this project, I learned:

- AWS EBS management
- Linux disk partitioning
- File system creation
- Mounting storage in Linux
- Persistent storage configuration

---

#  Author

Sanket Gadade
