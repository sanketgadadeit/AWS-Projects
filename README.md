
#  Microservices Application Deployment Using AWS Application Load Balancer & Auto Scaling Groups

A **Microservices-based E-Commerce Application** deployed on **AWS Cloud** using **Application Load Balancer (ALB)** and **Auto Scaling Group (ASG)** to achieve high availability, scalability, and fault tolerance.

This project demonstrates how multiple microservices can be independently deployed and managed behind an **AWS Application Load Balancer** with **path-based routing** and **Auto Scaling**.

---

##  Project Overview

This project contains three independent microservices:

-  **Home Service**
-  **Phone Service**
-  **Laptop Service**

Each service is hosted on **Amazon EC2 instances** managed by an **Auto Scaling Group** and served using **Apache**.

The **Application Load Balancer (ALB)** routes incoming traffic based on URL paths.

---

## 🛠️ Tech Stack

- **AWS EC2**
- **Application Load Balancer (ALB)**
- **Auto Scaling Group (ASG)**
- **Apache**
- **HTML5**
- **CSS3**
- **GitHub**

---

##  Architecture Diagram

![alt text](image.png)
---

##  Application Routing

| Route | Service |
|--------|----------|
| `/` | Home Service |
| `/phone` | Phone Service |
| `/laptop` | Laptop Service |

---

##  Project Structure

```text
microservices-ecommerce/
│── home-service/
│   ├── index.html
│   └── style.css
│
│── phone-service/
│   ├── index.html
│   └── style.css
│
│── laptop-service/
│   ├── index.html
│   └── style.css
│
└── README.md
```

---

##  AWS Services Used

### 1. Amazon EC2
Used to host the microservices application.

### 2. Auto Scaling Group
Automatically launches or terminates EC2 instances based on demand.

### 3. Application Load Balancer
Distributes traffic and performs **path-based routing**.

### 4. Nginx
Serves static HTML/CSS pages.

---



## 🔧 Deployment Steps

### Step 1: Create Lauch Templates

![alt text](<Screenshot (291).png>)
![alt text](<Screenshot (292).png>)
![alt text](<Screenshot (293).png>)
![alt text](<Screenshot (294).png>)
![alt text](<Screenshot (295).png>)
![alt text](<Screenshot (296).png>)

- Create same for the Phone and Laptop Launch templates
![alt text](<Screenshot (297).png>)
![alt text](<Screenshot (298).png>)

- Here our templates are created

![alt text](<Screenshot (299).png>)
### Step 2: Create Auto Scalling Groups

![alt text](<Screenshot (300).png>)
![alt text](<Screenshot (301).png>)
![alt text](<Screenshot (302).png>)
![alt text](<Screenshot (303).png>)
![alt text](<Screenshot (304).png>)
![alt text](<Screenshot (305).png>)
![alt text](<Screenshot (306).png>)
![alt text](<Screenshot (307).png>)

- Create same for Mobile-ASG and Laptop-ASG

![alt text](<Screenshot (308).png>)
![alt text](<Screenshot (309).png>)
![alt text](<Screenshot (310).png>)
 
 - see 6 instances created because we select 2,2,2 as a desired 
![alt text](<Screenshot (312).png>)

### Step 3: Create target group
![alt text](<Screenshot (313).png>)
![alt text](<Screenshot (314).png>)

- For Mobile
![alt text](<Screenshot (314).png>)
![alt text](<Screenshot (315).png>)

- For Laptop
![alt text](<Screenshot (316).png>)
![alt text](<Screenshot (317).png>)

- Here our Auto Scalling Groups
![alt text](<Screenshot (320).png>)

- Select ASG and click on Action and edit
![alt text](<Screenshot (321).png>)
![alt text](<Screenshot (322).png>)
![alt text](<Screenshot (323).png>)



### Step 4: Create Load Balancer
![alt text](<Screenshot (324).png>)
![alt text](<Screenshot (325).png>)

-Go to listner and rules and Add rule
![alt text](<Screenshot (327).png>)
![alt text](<Screenshot (326).png>)
Create same for Laptop also



### Step 5: Copy the DNS and peast it in Browser
![alt text](<Screenshot (328).png>)

## Output :

![alt text](<Screenshot (329).png>)
![alt text](<Screenshot (330).png>)



##  Features

✅ Microservices Architecture  
✅ Application Load Balancer  
✅ Auto Scaling Group  
✅ Path-Based Routing  
✅ High Availability  
✅ Responsive UI  
✅ Independent Service Deployment  
✅ EC2 + httpd Hosting  

---

##  Conclusion

This project demonstrates the deployment of a **Microservices-based E-Commerce Application** using **AWS Application Load Balancer (ALB)** and **Auto Scaling Group (ASG)**.

Through this project, I gained practical experience with **AWS EC2, Load Balancing, Auto Scaling, Apache, and Microservices Architecture**. The implementation of **path-based routing** and **Auto Scaling** helped improve application scalability, availability, and reliability.

This project strengthened my understanding of deploying cloud-native applications using real-world AWS infrastructure and DevOps concepts.

---

##  Author

**Sanket Gadade**

If you found this project useful, feel free to ⭐ this repository!

