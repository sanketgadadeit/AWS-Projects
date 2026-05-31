
#  Microservices E-Commerce Application on Application Load Balancer

A modern **Microservices-based E-Commerce Website** deployed using **AWS Application Load Balancer (ALB)** with separate services for **Home, Phones, and Laptops**. Each service is independently hosted and routed through **path-based routing** using AWS ALB.

---

##  Project Overview

This project demonstrates a **microservices architecture** for an e-commerce platform using:

- **AWS Application Load Balancer (ALB)**
- **Amazon EC2**
- **Nginx**
- **Static HTML/CSS UI**
- **GitHub for Version Control**

Each page of the website runs as an independent microservice:

- **Home Service**
- **Phone Service**
- **Laptop Service**

The Application Load Balancer routes traffic based on URL paths.

---

##  Tech Stack

| Technology | Purpose |
|------------|---------|
| HTML5 | Frontend Structure |
| CSS3 | Styling & Responsive UI |
| Nginx | Static Website Hosting |
| Amazon EC2 | Hosting Microservices |
| AWS ALB | Load Balancing & Routing |
| GitHub | Source Code Management |

---

##  Architecture Diagram



![](Architecture.png)

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
    ├── index.html
    └── style.css

```

---

##  AWS Architecture

### Application Load Balancer Routing

| Route Path | Service |
|------------|---------|
| `/` | Home Service |
| `/phones` | Phone Service |
| `/laptops` | Laptop Service |

---

##  Application Workflow

1. User accesses the website through the browser.
2. Request goes to **AWS Application Load Balancer**.
3. ALB checks the request path.
4. Traffic is routed to the correct microservice:
   - `/` → Home Service
   - `/phones` → Phone Service
   - `/laptops` → Laptop Service
5. The service is hosted on an independent **EC2 instance with httpd**.

---

#  Project Screenshots
```
See the url, project accessed by DNS/endpoint of Load Balancer
```
![](<Screenshot (290).png>)

##  AWS Application Load Balancer




![](<Screenshot (275).png>)
---

##  EC2 Instances

![](<Screenshot (248).png>)

---

##  Deployment Steps

### 1. Launch EC2 Instances
Create separate EC2 instances for:
- Home Service
- Phone Service
- Laptop Service

### 2. Install Apache

```bash
sudo apt update
sudo apt install httpd -y
```

### 3. Deploy Static Files

Move your HTML and CSS files:

```bash
sudo cp -r * /var/www/html/
```

Restart Nginx:

```bash
sudo systemctl restart httpd
```

### 4. Configure Application Load Balancer

- Go to EC2 dashboard
![](<Screenshot (250).png>)

- see the Application Load Balance and click on create
![](<Screenshot (251).png>)

- Select the AZ and Subnets for make LB on each AZ and Subnet
![](<Screenshot (254).png>)
- Select default security group that allow 80 port 
![](<Screenshot (255).png>)
- Here we are going to forwad this trafic to target groups
![](<Screenshot (256).png>)
- Firstly create TG follow the steps
![](<Screenshot (257).png>)
![](<Screenshot (258).png>)
![](<Screenshot (259).png>)
- Once you select instances don't forget to click on **include as pending below**
![](<Screenshot (260).png>)
![](<Screenshot (261).png>)
- make same proess for other 2
![](<Screenshot (264).png>)
![](<Screenshot (265).png>)
![](<Screenshot (266).png>)
![](<Screenshot (267).png>)
![](<Screenshot (268).png>)
![](<Screenshot (269).png>)
![](<Screenshot (270).png>)
![](<Screenshot (271).png>)
- Click on create load balancer
![](<Screenshot (274).png>)
![](<Screenshot (275).png>)
- Here we are going add rules
![](<Screenshot (276).png>)
![](<Screenshot (277).png>)
![](<Screenshot (278).png>)
![](<Screenshot (279).png>)
![](<Screenshot (280).png>)
![](<Screenshot (281).png>)
![](<Screenshot (282).png>)
![](<Screenshot (283).png>)
![](<Screenshot (284).png>)
![](<Screenshot (285).png>)
![](<Screenshot (286).png>)
![](<Screenshot (287).png>)
![](<Screenshot (288).png>)
- Here our LB is successfuly crated, copy DNS and peast DNS in browser
![](<Screenshot (289).png>)

- Application is Live
![](<Screenshot (290).png>)

### 5. Test the Application

Access:

```text
http://your-alb-dns-name/
http://your-alb-dns-name/phones
http://your-alb-dns-name/laptops
```

---

##  Features

✅ Microservices Architecture  
✅ AWS Application Load Balancer  
✅ Path-Based Routing  
✅ Responsive UI Design  
✅ Independent Service Deployment  
✅ Nginx Web Server  
✅ EC2 Hosting  

---

##  Learning Outcome

Through this project, I learned:

- AWS Application Load Balancer
- Path-based routing
- Microservices deployment
- Amazon EC2 management
- Nginx configuration
- Static website hosting
- Cloud architecture design

---

##  Conclusion

This project demonstrates the implementation of a **Microservices-based E-Commerce Application** using **AWS Application Load Balancer (ALB)** with **path-based routing**. The application is divided into independent services (**Home, Phone, and Laptop**) to achieve better scalability, maintainability, and deployment flexibility.

By completing this project, I gained hands-on experience with **AWS EC2, Application Load Balancer, Nginx, Microservices Architecture, and Static Website Hosting**. This project also helped me understand how modern cloud applications are deployed and managed in a scalable environment.

Overall, this project serves as a practical example of deploying a **microservices application on AWS cloud infrastructure** while following real-world architecture concepts.



##  Author

**Sanket Gadade**

If you like this project, feel free to ⭐ this repository!

