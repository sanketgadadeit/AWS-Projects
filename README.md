# Static Website Deployment on Apache (Amazon Linux)

## Project Description
This project demonstrates how to deploy a static website using Apache Web Server on an AWS EC2 instance running Amazon Linux.

---

##  Tech Stack
- Amazon Linux
- Apache HTTP Server
- AWS EC2
- HTML, CSS

---
## Architecture
![alt text](image.png)

##  Step-by-Step Implementation

### 1. Launch EC2 Instance
- Choose Amazon Linux AMI
- Allow HTTP (Port 80) in Security Group
![](./Screenshot%20(132).png)

### 2. Connect to EC2
ssh -i your-key.pem ec2-user@<your-ec2-ip>


### 3. Update System
sudo yum update -y

### 4. Install Apache
sudo yum install httpd -y
![](./Screenshot%20(133).png)
### 5. Start and Enable Apache
sudo systemctl start httpd
sudo systemctl enable httpd
![](./Screenshot%20(134).png)
### 6. Deploy Website Files
cd /var/www/html

![](./Screenshot%20(135).png)
![](./Screenshot%20(136).png)
![](./Screenshot%20(137).png)

### 7. Create Database
![](./Screenshot%20(138).png)


### 8. Restart Apache
sudo systemctl restart httpd
  

### 9.Insert value in form and after submit you got the fatal error
![](./Screenshot%20(139).png)

##### Don't Panic install mysqli (it is a connector of php)
![](./Screenshot%20(144).png)
 
### Then refresh it or resubmit
![](./Screenshot%20(145).png)
---

## See data inserted in database
![](./Screenshot%20(146).png)


---


##  Features
- Hosted on AWS Cloud
- Public accessibility
- Apache server configuration

---

##  Learning Outcomes
- AWS EC2 setup
- Apache server server configuration
- Cloud deployment basics

## Conclusion
The deployment of a static website on an Apache web server using Amazon Web Services Linux (Amazon Linux) demonstrates a practical and efficient approach to hosting web applications in a cloud environment. By configuring the Apache server, setting up the required files, and managing permissions, the website was successfully made accessible over the internet.

This project provided valuable hands-on experience in Linux server management, web server configuration, and cloud deployment. It also helped in understanding key concepts such as instance setup, security groups, and remote server access. Overall, this deployment process highlights how cloud platforms can simplify hosting while ensuring scalability and reliability for modern web applications.