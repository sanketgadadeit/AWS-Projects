
#  VPC Shield: Scalable & Secure Java-Based Application in 3-Tier Architecture

##  Project Overview

**VPC Shield** is a secure, scalable, and highly available **3-tier Java-based web application architecture** deployed on **AWS Cloud**.

This project demonstrates real-world cloud deployment practices using **Amazon VPC**, **Nginx Reverse Proxy**, **Apache Tomcat Application Server**, and **Amazon RDS** while following security best practices and scalable infrastructure design.

The architecture is designed to ensure:

- High Availability  
- Scalability  
- Secure Communication  
- Network Isolation  
- Cost Optimization  
- Monitoring & Reliability  

---

##  Project Architecture

The application follows a **3-Tier Architecture**:

### 1. Presentation Layer (Proxy Server)

- Configured using **Nginx**
- Works as a **Reverse Proxy**
- Handles incoming client requests
- Routes traffic securely to application servers

### 2. Application Layer (App Server)

- Hosted on **Apache Tomcat**
- Deploys the **Java-based application**
- Processes business logic
- Runs inside private subnet for enhanced security

### 3. Database Layer

- Configured using **Amazon RDS**
- Stores application data securely
- Runs in private subnet
- Restricted database access

---

##  Architecture Diagram

![alt text](Architecture.png)
---
## Architecture Explanation

This project follows a **secure, scalable, and highly available 3-tier architecture** deployed on **AWS Cloud**. The infrastructure is designed using **Amazon VPC**, **Nginx Reverse Proxy**, **Apache Tomcat**, and **Amazon RDS**, ensuring security, fault tolerance, and scalability.

### 1️⃣ Network Layer (VPC)

The complete infrastructure is deployed inside a **Virtual Private Cloud (VPC)** to provide secure network isolation and controlled communication between resources.

The architecture spans across **multiple Availability Zones (AZs)** to ensure **high availability** and fault tolerance.

---

### 2️⃣ Web Tier (Presentation Layer)

The **Web Tier** consists of **Nginx Proxy Servers** hosted on **EC2 instances** inside the **Public Subnet**.

#### Responsibilities:
- Accept incoming user requests
- Work as a **Reverse Proxy**
- Route traffic to backend application servers
- Improve security by hiding internal services

The web tier is configured inside an **Auto Scaling Group (ASG)**, allowing automatic scaling during traffic spikes.

---

### 3️⃣ Application Tier (Business Logic Layer)

The **Application Tier** contains **Apache Tomcat Servers** running the **Java-based application** inside **Private Subnets**.

#### Responsibilities:
- Process application logic
- Handle business operations
- Communicate with the database layer

Since the application servers are deployed in **private subnets**, they cannot be accessed directly from the internet, improving overall security.

An **Internal Load Balancer** distributes traffic between multiple Tomcat servers for better performance and fault tolerance.

---

### 4️⃣ Database Tier (Data Layer)

The **Database Tier** uses **Amazon RDS (MySQL)** deployed in **Private Subnets**.

#### Responsibilities:
- Store application data securely
- Handle database transactions
- Support backend application connectivity

The database is configured using **Multi-AZ deployment**, ensuring high availability and automatic failover in case of infrastructure failure.

---

### 5️⃣ Security Implementation

Security is implemented using:

- **Public & Private Subnet Isolation**
- **Security Groups**
- **Reverse Proxy Architecture**
- **Restricted Database Access**
- **Controlled Internal Communication**

Only authorized traffic is allowed between layers:

```text
Internet → Nginx → Tomcat → RDS
```

---

### 6️⃣ Scalability & High Availability

The architecture ensures scalability and reliability using:

- **Auto Scaling Groups**
- **Multiple Availability Zones**
- **Load Balancing**
- **Multi-AZ RDS Deployment**

This allows the application to handle increased traffic while minimizing downtime.

---

### 🔄 Request Flow

```text
User
   ↓
Internet Gateway
   ↓
Nginx Proxy Server (Public Subnet)
   ↓
Internal Load Balancer
   ↓
Apache Tomcat Application Server (Private Subnet)
   ↓
Amazon RDS MySQL (Private Subnet)
   ↓
Response Back to User
```

---

###  Summary

This architecture demonstrates a **production-ready AWS deployment model** for a **Java-based application**, combining **security, scalability, high availability, and efficient traffic management** using modern cloud best practices.


##  AWS Services Used

| Service          | Purpose                        |
| ---------------- | ------------------------------ |
| Amazon EC2       | Hosting Nginx & Tomcat Servers |
| Amazon VPC       | Secure Network Isolation       |
| Security Groups  | Traffic Control                |
| Nginx            | Reverse Proxy Server           |
| Apache Tomcat    | Java Application Deployment    |
| Amazon RDS       | Managed Relational Database    |
| Auto Scaling     | Scalability                    |
| CloudWatch       | Monitoring & Logging           |
| Internet Gateway | Public Internet Access         |

---

##  Security Features

* Private Subnet for App Server
* Private Database Access
* Controlled Security Group Rules
* Nginx Reverse Proxy
* Restricted Database Connectivity
* VPC Network Isolation

---

##  Tech Stack

| Category             | Technology                                  |
| -------------------- | ------------------------------------------- |
| Cloud Platform       | AWS                                         |
| Operating System     | Amazon Linux / Linux                        |
| Proxy Server         | Nginx                                       |
| Application Server   | Apache Tomcat                               |
| Programming Language | Java                                        |
| Database             | Amazon RDS (MySQL)                          |
| Monitoring           | CloudWatch                                  |
| Networking           | VPC, Subnets, Route Tables, Security Groups |

---

##  Project Workflow

1. User sends request through browser
2. Request reaches **Nginx Proxy Server**
3. Nginx forwards request to **Apache Tomcat Server**
4. Application processes request
5. Data fetched/stored in **Amazon RDS**
6. Response returned back to user

---

##  Deployment Steps

### Step 1: Create VPC

* Configure CIDR Block


![alt text](<Screenshot (381).png>)
![alt text](<Screenshot (382).png>)


* Create Public & Private Subnets

![alt text](<Screenshot (385).png>)
![alt text](<Screenshot (386).png>)
![alt text](<Screenshot (387).png>)
![alt text](<Screenshot (388).png>)
![alt text](<Screenshot (389).png>)
- Public subnet
![alt text](<Screenshot (383.1).png>)
![alt text](<Screenshot (383.2).png>)
![alt text](<Screenshot (383.3).png>)


* Configure Route Tables

![alt text](<Screenshot (390).png>)
![alt text](<Screenshot (391).png>)
![alt text](<Screenshot (392).png>)
![alt text](<Screenshot (393).png>)
![alt text](<Screenshot (394).png>)
![alt text](<Screenshot (395).png>)
![alt text](<Screenshot (396).png>)

- Add internet gateway and NAT gateway

![alt text](<Screenshot (397).png>)
![alt text](<Screenshot (398).png>)
![alt text](<Screenshot (399).png>)
![alt text](<Screenshot (399.1).png>)
![alt text](<Screenshot (399.2).png>)

- NAT Gateway

 ![alt text](<Screenshot (400).png>)
 ![alt text](<Screenshot (401).png>)
 ![alt text](<Screenshot (403).png>)
 ![alt text](<Screenshot (404).png>)
 ![alt text](<Screenshot (408).png>)
 ![alt text](<Screenshot (409).png>)
 ![alt text](<Screenshot (410).png>)
 ![alt text](<Screenshot (411).png>)
 ![alt text](<Screenshot (416).png>)







### Step 2: Configure Amazon RDS

* Create RDS Instance

 ![alt text](<Screenshot (417).png>)
 ![alt text](<Screenshot (418).png>)
 ![alt text](<Screenshot (420).png>)
 ![alt text](<Screenshot (421).png>)
 ![alt text](<Screenshot (422).png>)

* At this movment from the new updatation of AWS there is problem of selecting instance here we are going with default VPC and Easy create option in RDS

![alt text](<Screenshot (432).png>)
![alt text](<Screenshot (433).png>)
![alt text](<Screenshot (434).png>)
![alt text](<Screenshot (435).png>)
![alt text](<Screenshot (436).png>)
![alt text](<Screenshot (437).png>)
![alt text](<Screenshot (438).png>)
![alt text](<Screenshot (439).png>)
![alt text](<Screenshot (440).png>)
![alt text](<Screenshot (441).png>)
![alt text](<Screenshot (442).png>)
![alt text](<Screenshot (443).png>)
![alt text](<Screenshot (444).png>)
![alt text](<Screenshot (445).png>)
![alt text](<Screenshot (447).png>)
![alt text](<Screenshot (448).png>)
![alt text](<Screenshot (449).png>)
![alt text](<Screenshot (450).png>)
![alt text](<Screenshot (451).png>)

### Step 3: Configure Security Groups

* Allow HTTP (80)
* Allow HTTPS (443)
* Allow Tomcat Port (8080) internally
* Allow Database Port (3306) privately
![alt text](<Screenshot (457).png>)


 ### Step 4: Launch EC2 Instances
 - Proxy_server
- App_server

- DB_server



### Step 5: Configure Nginx Reverse Proxy

```bash
sudo yum update -y
sudo amazon-linux-extras install nginx1 -y
sudo systemctl start nginx
sudo systemctl enable nginx
```

![alt text](<Screenshot (459).png>)
![alt text](<Screenshot (460).png>)

![alt text](<Screenshot (478).png>)
![alt text](<Screenshot (479).png>)



### Step 6 :Configure App server for jump
![alt text](<Screenshot (501).png>)

![alt text](<Screenshot (477).png>)

### Step 7: Install Apache Tomcat

```bash
sudo yum install java-17-amazon-corretto -y
wget https://downloads.apache.org/tomcat/tomcat-9/v9.0118.xx/bin/apache-tomcat-9.0,118.xx.tar.gz
tar -xvf apache-tomcat-9.0.118.xx.tar.gz
cd apache-tomcat-9.0.118.xx/bin
./startup.sh
```

![alt text](<Screenshot (483).png>)

![alt text](<Screenshot (485).png>)
![alt text](<Screenshot (486).png>)

![alt text](<Screenshot (489).png>)

![alt text](<Screenshot (491).png>)
![alt text](<Screenshot (492).png>)
![alt text](<Screenshot (493).png>)


### Step 8: Deploy Java Application

```bash
scp your-application.war ec2-user@private-ip:/opt/tomcat/webapps/
```
![alt text](<Screenshot (494).png>)


### Step 9: Verify Deployment

* Access Application using Proxy Server Public IP

![alt text](<Screenshot (504).png>)


### Step 10 :
Configure Database and Server
![alt text](<Screenshot (506).png>)

![alt text](<Screenshot (508).png>)
![alt text](<Screenshot (509).png>)
![alt text](<Screenshot (510).png>)

![alt text](<Screenshot (512).png>)

![alt text](<Screenshot (514).png>)
![alt text](<Screenshot (515).png>)
![alt text](<Screenshot (516).png>)

- Go to App Server and Add connector


![alt text](<Screenshot (519).png>)

![alt text](<Screenshot (522).png>)
![alt text](<Screenshot (523).png>)
![alt text](<Screenshot (524).png>)

- After that Restart nginx from proxy server

![alt text](<Screenshot (525).png>)

### Output :
![alt text](<Screenshot (526).png>)

- Go to DB server and run this cmd


![alt text](<Screenshot (531).png>)

## Additional Step :

![alt text](<Screenshot (534).png>)

![alt text](<Screenshot (538).png>)

![alt text](<Screenshot (543).png>)

![alt text](<Screenshot (546).png>)

![alt text](<Screenshot (550).png>)




 
---

##  Future Enhancements

* Add Application Load Balancer (ALB)
* Docker Containerization
* CI/CD Pipeline using Jenkins/GitHub Actions
* Infrastructure as Code using Terraform
* SSL Certificate for HTTPS Security

---

##  Project Screenshots

Add screenshots here:

* VPC Architecture
* EC2 Instances
* Security Groups
* RDS Configuration
* Final Application Output

---

##  Conclusion

This project demonstrates the implementation of a **secure and scalable 3-tier architecture on AWS** for deploying a **Java-based application**. By integrating **Nginx as a reverse proxy**, **Apache Tomcat for application hosting**, and **Amazon RDS for database management**, the architecture ensures **security, reliability, and efficient traffic handling**.

The use of **VPC, private subnets, security groups, monitoring, and scalability features** makes this deployment closely aligned with real-world **Cloud and DevOps engineering practices**.


